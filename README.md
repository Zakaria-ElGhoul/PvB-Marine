# Proeve van Bekwaamheid Marine 

In deze repository vind je de informatie over het examen project.

Omschrijf de examenopdracht evt de klant en wat het doel voor de klant is.
Omschrijf ook beknopt wat het idee van je game is. 
Een complete en uitgebreide beschrijving komt in het functioneel ontwerp (onderdeel van de [wiki](https://github.com/erwinhenraat/VoorbeeldExamenRepo/wiki))

# Geproduceerde Game Onderdelen

Geef per teammember aan welke game onderdelen je hebt geproduceerd. Doe dit met behulp van omschrijvingen visual sheets en screenshots.
Maak ook een overzicht van alle onderdelen met een link naar de map waarin deze terug te vinden zijn.

Bijv..

Student X:
  * [Wave System](https://github.com/erwinhenraat/VoorbeeldExamenRepo/tree/master/src/some)
  * [Some other mechanic X](https://github.com/erwinhenraat/VoorbeeldExamenRepo/tree/master/src/mechanic_x)
  * [Some other mechanic Y](https://github.com/erwinhenraat/VoorbeeldExamenRepo/tree/master/src/mechanic_y)
Student Y:
  * Water Shader
  * [Some textured and rigged model](https://github.com/erwinhenraat/VoorbeeldExamenRepo/tree/master/assets/monsters)

Student Z:
  * [Some beautifull script](https://github.com/erwinhenraat/VoorbeeldExamenRepo/tree/master/src/beautifull)
  * Some other Game object


## Wave System by Student X

Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line.

![Animation](https://user-images.githubusercontent.com/1262745/217570184-90dc4701-d60d-4816-80d0-5007fdd3f6be.gif)

### flowchart voor turn based combat system:
```mermaid

flowchart TD

Start((Start)) --> |Initialize Players and Enemies| SetTurn[Set Turn]
SetTurn --> TimerZero{HasTimerEnded} --> |Yes|PlayerDefeated 
TimerZero --> |No|PlayerTurn
PlayerTurn --> |Choose Action| PlayerAction[Player Action]
PlayerAction --> ChooseActionType[ChooseActionType] --> PlayerHeal[Heal] --> CanPerformAction{CanPerformAction} --> |No|EnemyTurn 
CanPerformAction --> |Yes| ApplyHeal[ApplyAction] --> CheckEnemyDefeated
ChooseActionType --> PlayerAttack --> CanPerformAction
ApplyDamage -->|Check if Enemy Defeated| CheckEnemyDefeated
CheckEnemyDefeated -->|Enemies Defeated| EnemyDefeated[End Combat - Player Victory]
CheckEnemyDefeated -->|Enemies Remaining| EnemyRemaining[Enemies Remaining]
EnemyRemaining --> EnemyTurn[Enemy's Turn]
EnemyTurn -->|Choose Action| EnemyAction[Enemy Action]
EnemyAction -->|Attack| EnemyAttack[Perform Attack]
EnemyAttack -->|Apply Damage| ApplyDamage
ApplyDamage -->|Check if Player Defeated| CheckPlayerDefeated
CheckPlayerDefeated -->|Player Defeated| PlayerDefeated[End Combat - Player Defeat]
CheckPlayerDefeated -->|Player Alive| PlayerAlive[Player Alive]
PlayerAlive --> PlayerTurn



```
### class diagram voor game entities:

```mermaid
classDiagram

Unit <|-- Tower:Is A
Unit <|-- Monster
Unit <|-- Boss
Unit : +int life
Unit : +int speed
Unit: +isMovable()
Unit: +Destroy()
class Tower{
+String turretType
+target()
+shoot()
}
class Monster{
-int reward
-regenerates()
}
class Boss{
+bool is_unique
+specialSkill()
}
```


## Some other Mechanic X by Student X

Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.

![example](https://user-images.githubusercontent.com/1262745/189135129-34d15823-0311-46b5-a041-f0bbfede9e78.png)

## Some other Mechanic Y by Student X

Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.

![example](https://user-images.githubusercontent.com/1262745/189135129-34d15823-0311-46b5-a041-f0bbfede9e78.png)

## Water Shader by Student Y

Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.

![example](https://user-images.githubusercontent.com/1262745/189135129-34d15823-0311-46b5-a041-f0bbfede9e78.png)

## Some textured and rigged model by Student Y

Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.

![example](https://user-images.githubusercontent.com/1262745/189135129-34d15823-0311-46b5-a041-f0bbfede9e78.png)

## Some beautifull script by Student Z

Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.

![example](https://user-images.githubusercontent.com/1262745/189135129-34d15823-0311-46b5-a041-f0bbfede9e78.png)

## Some other Game object by Student Z

Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.

![example](https://user-images.githubusercontent.com/1262745/189135129-34d15823-0311-46b5-a041-f0bbfede9e78.png)
