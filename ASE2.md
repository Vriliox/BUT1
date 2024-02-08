

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

## Les registres de bases

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
2. [Activer la broche](#activer-une-broche-dun-port---grpiox_crl--gpiox_crh-axg): `GPIOG->CRH = 0x00000300; //Activation de la broche 10 en sortie.`
3. [Mettre l'état de la broche à 1](#ecrire-dans-un-port---gpiox_odr-axg): `GPIOB->ODR = 0x0400`;
4. [ Pour éteindre, remettre à 0](#ecrire-dans-un-port---gpiox_odr-axg): `GPIOB->ODR = 0x0000`;

## Utiliser un bouton (PD3 - Joystick bas):

1. [Activer le port](#activation-dun-port---rcc_apb2enr): `RCC->APB2ENR |= (1 << 5); // Activer le GPIOD`
2. [Activer la broche](#activer-une-broche-dun-port---grpiox_crl--gpiox_crh-axg): `GPIOD->CRL = 0x00004000; //Activation de la broche 3 en entrée.`
3. [Lire l'état du bouton](#lire-un-port---gpiox_idr-axg): `bouton = GPIOD->IDR & 0x0004;`;

## Utiliser un Timer (TIM8):

[STM32 Timer Calculator](https://deepbluembedded.com/stm32-timer-calculator/)
$$
temps = \frac{(PSC + 1) \times ARR}{f}
$$
Avec f = 72x10⁶.

> L'auto reload définit jusqu'à combien compte le timer.  
> Le prescaler divise le temps pour lequel le timer doit arriver à la valeur de l'auto reload.  
> Lorsque la valeur est atteinte le 1er bit de TIM1->SR passe à 1.

1. [Activer le port](#activation-dun-port---rcc_apb2enr): `RCC->APB2ENR |= (1 << 13); // Activer le TIMER 8`
3. Définir l'auto-reload: `TIM8->ARR = 62499;`
2. Définir le Prescaler: `TIM8->PSC = 575;`
4. Mettre en service le Timer: `TIM8->CR1 |= 0x0001;`
5. Obtenir la valeur du timer: `valeur = TIM8_CNT;`
6. Obtenir l'état du drapeau: `valeur = TIM8->SR & 0x0001`
7. Remettre le drapeau à 0: `TIM8->SR &= ~(1<<0);`
## Utiliser les interruptions:
1. Chercher la position de l'interruption dans le NVIC
    - **NOM -> NVIC -> POSITION**
    - GPIO X0 -> EXTI0 -> 6
    - GPIO X1 -> EXTI1 -> 7
    - GPIO X2 -> EXTI2 -> 8
    - GPIO X3 -> EXTI3 -> 9
    - GPIO X4 -> EXTI4 -> 10
    - GPIO X5-X9 -> EXTI9_5 -> 23
    - GPIO X10-X15 -> EXTI15_10 -> 40
    - TIM1 -> TIM1_UP -> 25
    - TIM2 -> TIM2 -> 28
    - TIM3 -> TIM3 -> 29
    - TIM4 -> TIM4 -> 30
    - TIM5 -> TIM5 -> 50
    - TIM6 -> TIM6 -> 54
    - TIM7 -> TIM7 -> 55
    - TIM8 -> TIM8_UP -> 44
2. Activer l'interruption: `SETENAx |= (1 << position);`  
   > Un registre SETENA ne couvre que 32 interruptions. Il y a donc SETENA0, SETENA1... Ainsi la 1ère interruption de SETENA1 est la 32ème du tableau NVIC.  
   
   SETENA doit être défini comme:  
    - SETENA0 *(volatile unsigned long *)0xE000E100
    - SETENA1 *(volatile unsigned long *)0xE000E104
    - SETENA2 *(volatile unsigned long *)0xE000E108...
3. Pour les TIMERS:
   1. Activer l'interruption du côté Timer: `TIMx_DIER |= (1 << 0);` 
        >x Désigne le numéro du Timer (entre 1 et 8)
4. Pour les boutons:
   1. [Activer le port](#activation-dun-port---rcc_apb2enr): RCC->APB2ENR |= (1 << 0); // Activer le port AFIOEN
   2. Sélectionner la broche avec: `AFIO_EXTICRx = y;`
        > x Désigne le numéro du registre (de 1 à 4). Chaque numéro de broche (0, 1, 2..., 15) sont associé à 4 bits dans ces registres. Ainsi, dans la partie de 4 bits associé au numéro de broche souhaité, le **port** doit être sélectionné, allant de 0 (pour A) à 6 (pour G), cette valeur est y (au bon endroit). Par exemple, pour activer en E6 : `AFIO_EXTICR2 = 0x0400;`. 2 Car dans le 2nd registre et 4 car le port E.

        AFIO_EXTICR doit être défini comme:
        - AFIO_EXTICR4 *(volatile unsigned long *)0x40010014
        - Je ne sais pas pour les autres, je vous conseil donc: `AFIO->EXTICR[x-1]` (à vos risques et périls.)
    3. Détection de front montant ou descendant:
       1. Front montant: `EXTI->RTSR = (1 << numéroBroche)`
       2. Front descendant: `EXTI->FTSR = (1 << numéroBroche)`
    4. Masque d'interruption: `EXTI->IMR = (1 << numéroBroche)` 
    5. Etat de l'interruption: `valeur = EXTI->IMR & (1 << numéroBroche)`
    6. Remettre l'interruption à **1**: `EXTI->PR |= numéroBroche;`
        > Le numéro de broche est par exemple 13 pour TAMPER, 0 pour WAKEUP...
 5. Ecrire la fonction en retrouvant le nom dans le fichier de démarrage. Le numéro de la ligne dans ce fichier est le même que dans le NVIC.
        




