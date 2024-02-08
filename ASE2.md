# ASE2 - Guide

## Bases:
- Mettre un bit à 0: `registre &= ~(1 << numéro_de_bit);`
- Mettre un bit à 1: `registre |= (1 << numéro_de_bit);`
- Inverser un bit: `registre ^= (1 << numéro_de_bit);`
- Lire un bit spécifique: `registre & (1 << numéro_de_bit)`

## Boutons et leds

> La valeur entre parenthèse spécifie l'état de la broche lors de l'appui. 0 pour Pull-Up, et 1 pour Pull-Down

- Wakeup (1) = PA0
- Tamper (0) = PG13
- User (0) = PG8
- Joystick Haut (0) = PG15
- Joystick Bas (0) = PD3
- Joystick Gauche (0) = PG14
- Joystick Droit (0) = PG13
- Joystick Select (0) = PG7
- LEDS: PB8 à PB15

## Les registres

[//]: # (enable-port)
### Activation d'un port - RCC_APB2ENR 

|15|14|13|12|11|10|9|8|7|6|5|4|3|2|1|0|
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|X|X|TIME8EN|X|TIM1EN|X|X|IOP**G**EN|IOP**F**EN|IOP**E**EN|IOP**D**EN|IOP**C**EN|IOP**B**EN|IOP**A**EN|X|AFIOEN|

> Ce registre permet d'activer un port

`RCC->APB2ENR |= (1 << 3); // Activer le GPIOB`

### Activer une broche d'un port - GRPIOx_CRL & GPIOx_CRH (A<=x<=G)

|...|7|6|5|4|3|2|1|0|
|-|-|-|-|-|-|-|-|-|
|...|CNF1|CNF1|CNF1|CNF1|CNF0|CNF0|CNF0|CNF0|

> Ces registres permettent l'action des ports. De 0 à 7 pour GRPIOx_CRL et de 8 à 15 pour GPIOx_CRH. 
Les 4 ports désignent son fonctionnement. 0100 (0x4) pour entrée et 0011 (0x3) pour sortie.

`GPIOG->CRH = 0x30000004; //Activation de la broche 15 en sortie et la broche 8 en entrée du port G.`

### Lire un port - GPIOx_IDR (A<=x<=G)

|...|7|6|5|4|3|2|1|0|
|-|-|-|-|-|-|-|-|-|
|...|IDR7|IDR6|IDR5|IDR4|IDR3|IDR2|IDR1|IDR0|

> Chaque bit du registre désigne l'état de la broche du port associé (0 à 15).

`bouton = GPIOG->IDR & 0x0100; //Enregistrement de l'état de la broche 8 du port G`

### Ecrire dans un port - GPIOx_ODR (A<=x<=G)

|...|7|6|5|4|3|2|1|0|
|-|-|-|-|-|-|-|-|-|
|...|ODR7|ODR6|ODR5|ODR4|ODR3|ODR2|ODR1|ODR0|

> Chaque bit du registre peut être écrit avec 0 ou 1 (0 à 15).

`GPIOB->ODR = 0x8000; //Mise à l'état 1 de la broche 15 du GPIO B`

## Utiliser une LED (PB10 - Led n°10):

1. [Activer le port](#activation-dun-port---rcc_apb2enr): `RCC->APB2ENR |= (1 << 3); // Activer le GPIOB`
2. Activer la broche: `GPIOG->CRH = 0x00000300; //Activation de la broche 10 en sortie.`
3. Mettre l'état de la broche à 1: `GPIOB->ODR = 0x0400`;
4. Pour éteindre, remettre à 0: `GPIOB->ODR = 0x0000`;

## Utiliser un bouton (PD3 - Joystick bas):

1. Activer le port: `RCC->APB2ENR |= (1 << 5); // Activer le GPIOD`
2. Activer la broche: `GPIOD->CRL = 0x00004000; //Activation de la broche 3 en entrée.`
3. Lire l'état du bouton: `bouton = GPIOD->IDR & 0x0004;`;

## Utiliser un Timer (TIM8):

[STM32 Timer Calculator](https://deepbluembedded.com/stm32-timer-calculator/)
$$
temps = \frac{(PSC + 1) \times ARR}{f}
$$
Avec f = 72x10⁶.

> L'auto reload définit jusqu'à combien compte le timer.  
> Le prescaler divise le temps pour lequel le timer doit arriver à la valeur de l'auto reload.  
> Lorsque la valeur est atteinte le 1er bit de TIM1->SR passe à 1.

1. Activer le port: `RCC->APB2ENR |= (1 << 13); // Activer le TIMER 8`
3. Définir l'auto-reload: `TIM8->ARR = 62499;`
2. Définir le Prescaler: `TIM8->PSC = 575;`
4. Mettre en service le Timer: `TIM8->CR1 |= 0x0001;`
5. Obtenir la valeur du timer: `valeur = TIM8_CNT;`
6. Obtenir l'état du drapeau: `valeur = TIM8->SR & 0x0001`
7. Remettre le drapeau à 0: `TIM8->SR &= ~(1<<0);`

## 


