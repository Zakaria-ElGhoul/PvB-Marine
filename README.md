# Proeve van Bekwaamheid Marine 

In deze repository vind je de informatie over het examen project.

# Meet the team

* Milan Breuren (Product owner & dev)
* Zakaria El Ghoul (Lead dev)
* Nanne Veldhuijzen van Zanten (SCRUM Master & dev)
* Lennard Hartog (3D artist)
* Yessie Blaas (2D artist)
* Isa Schulte (Lead 3D artist & notulist)
* Jesper Ceria (Lead 2D artist)

# De Opdracht

De opdracht die wij hebben gekregen was: Ontwikkel een maritieme strategiegame met minimaal 2 verschillende scenario’s of levels. De speler heeft in de game de taak om schepen te herkennen en deze op de juiste manier strategisch in te zetten. De strategische inzet is op basis van hun type en daarbij horende eigenschappen en functionaliteit. Door deze strategische inzet moet het doel van de game of het level worden bereikt. De game moet vooral draaien om herkenbare, vriendschappelijke, Nederlandse en internationale(NAVO) marineschepen. Jullie doen zelf onderzoek naar de verschillende schepen die interessant kunnen zijn om in de game te verwerken. Jullie zorgen ervoor dat de uit gewerkte game-mechanics goed aansluiten op de werkelijke toepassing van de gekozen schepen.

Het doel voor de klant is om jongeren aan te trekken tot de marine, dat willen wij bereiken door het spel simpel te maken en toegankelijk voor jongeren.
We hebben besloten om een strategisch kaartspel te maken in Unreal Engine 5 waar de speler goed moet focusen om de goede keuzes te kunnen maken om zo de vijand te kunnen verslaan. Tijdens de game leert de speler de verschillende sterktes en zwaktes van de schepen waar de speler mee speelt. Op deze manier willen we de speler interesse laten tonen in de marine. 

Lees een complete uitleg over het spel [hier](https://github.com/Zakaria-ElGhoul/PvB-Marine/wiki/Functioneel-ontwerp)

# Geproduceerde Game Onderdelen

Hier laten wij per teamlid ons meest belangrijke onderdeel van het spel zien. In het [technisch ontwerp](https://github.com/Zakaria-ElGhoul/PvB-Marine/wiki/Technisch-ontwerp) gaan wij hier verder op in.

Zakaria (dev):
  * [Buoyancy Shader](https://blueprintue.com/blueprint/vs0mdc-f/)
  * [A.I. BlackBoard]()
  * [Turn System]()
  * [U.I. Shader]()

Milan (dev):
  * [Card System](https://blueprintue.com/blueprint/57a-2_4j/)
  * [Action Visuals]()
  * [Enemy A.I.]()
  * [Attack System]()

Nanne (dev):
  * [Inspect Cards](https://blueprintue.com/blueprint/1pgupew1/)
  * [Resource System](https://blueprintue.com/blueprint/90r_fd0s/)
  * [Select Target System](https://blueprintue.com/blueprint/zbj60y91/)

## Enemy AI

Enemy AI heeft 3 states: DrawCard, PlayCard en Attack. In de eerste state kiest de AI één van de beschikbare kaarten uit, hij kijkt ook of hij genoeg 'mana' heeft om ze te gebruiken. Als hij dat allemaal gedaan hebt, dan slaat hij al die waardes op om ze vervolgens in de volgende state te gebruiken. In playCard pakt hij een willekeurige schip om vervolgens zijn kaart effect te boosten. Als dat gedaan is, dan gaat hij over naar attack, in attack kiest hij een willekeurige doelwit uit. nadat hij dat gedaan heeft, kan hij niet meer zijn behavior tree meer afgaan totdat de speler zijn zet heeft gedaan.

![Screenshot (107)](https://github.com/Zakaria-ElGhoul/PvB-Marine/assets/57196554/a848f7f0-4579-4116-9269-090679b3a68d)

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
    class ShipBase {
        - costType
        - name
        - description
        - cost
        - effectAmount
        - visual
        + attack()
    }

    class AlliedShip {
        + attack()
    }

    class EnemyShip {
        + attack()
    }

    ShipBase <|-- AlliedShip
    ShipBase <|-- EnemyShip
```


## Resource System

We hebben een resource systeem voor het spel gemaakt om de speler meer na te laten denken over wat hij kan doen in een zet. Elke kaart heeft een bepaalde cost om te kunnen spelen hierdoor moet je goed nadenken wat je in je huidige zet en volgende zet kan spelen om de vijand te slim af te zijn. Het werkt zo; aan het begin van het spel krijgen beide spelers 5 "mana". Telkens als het weer de beurt van de speler is dan komt er 5 "mana" bij. Dus de speler hebben elke turn een gelijk aantal aan resources. Als je genoeg resources heb en een kaart speel dan gaan de resources van die gespeelde kaart van je huidige resources af en eindigt je beurt. Als de turn switched dan worden je resources weer bd tot een maximaal aantal van 30.

[Blueprint](https://blueprintue.com/blueprint/_84l9xv1/)

![ezgif-5-9758fd17b7](https://github.com/Zakaria-ElGhoul/PvB-Marine/assets/43118035/93196a74-37ab-469a-9dea-f33ab90fff46)
