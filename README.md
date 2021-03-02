# GodoRogue
#### a game by AikonCWD

![img](https://imgur.com/UpKL1DB.png)

![img](https://imgur.com/hKf4iXf.png)

### Información del Juego e Historia

Nos situamos en **Nulbadush**, en el Reinado de los Yunques de Tharlone. **Nulbadush** fue gobernada durante años por el malvado brujo **Sakku**, un *Lord Kobold* que le gustaba experimentar con magia negra. Antaño hubieron muchas guerras hasta que por fin, el rey de **Tharlone**, arrebató la vida de **Sakku** y puso fin al terror que asediaba la zona.

La vida prosperó feliz y de forma pacífica en **Nulbadush**, hasta que años más tarde emergió un agujero en la lejana montaña. Empezaron a salir monstruos dispuestos a aterrorizar al pueblo de **Nulbadush**. Es una antigua guarida de **Sakku**, en cuyo interior yace el **Amuleto de Yendor**. Un artefacto poderoso que permitirá sellar por completo la guarida de **Sakku** y devolver la paz.

Nuestro rey hace años que murió.

¿Quién tendrá ahora el valor suficiente para explorar la guarida de **Sakku**?
¿Quién se enfrentará a los monstruos y peligros que inundan la guarida?

### Diseño e Influencias

Se tratará de un videojuego roguelike, en 2D y más enfocado en trabajar mecánicas de combate que en la propia apariencia/gráficos. Estará basado en sprites de 16x16, pixelart y paleta de colores reducida. Su punto fuerte será la generación procedural de niveles, haciendo que cada partida sea única.

El juego recibe claras influencias de [Rogue](https://es.wikipedia.org/wiki/Rogue) y del mundo de fantasía Dungeons & Dragons. Se implementarán las características típicas que cualquier roguelike debe tener:

- :interrobang:Generación procedural
- :skull: Permadeath
- :eye: Vista top down
- :crossed_swords: Combate por turnos
- :triangular_ruler: Diseño cuadriculas y tiles
- :pencil: Eventos narrados

### Software utilizado

Para desarrollar este juego utilizaré [Godot](https://godotengine.org/). Para la parte gráfica [Aseprite](https://www.aseprite.org/). Los efectos de sonido con [sfxr](https://www.drpetter.se/project_sfxr.html). Utilizaré assets de [Oryx](https://www.oryxdesignlab.com/sprites) y [surt](https://opengameart.org/content/loveable-rogue).

### Seguimiento del desarrollo (devlog)

Dejaré mi Trello público, para quien quiera ver las características que están en desarrollo y la fase de cada una de ellas, así como las características que me faltan implementar o las que ya he completado:

https://trello.com/b/81ytwHMf/godorogue

### Probar el juego (Online)

https://aikoncwd.ovh/roguelike

### Imágenes del juego

![img](https://imgur.com/hv0uBH0.png)
![img](https://imgur.com/CJAPqjS.png)
![img](https://imgur.com/aHeiJmg.png)

----------------------------------------------------

# Guía del juego
## Puede contener spoilers

# Introducción
Para jugar a GodoRogue solo necesitas un teclado para moverte. Para sobrevivir dentro de la mazmorra necesitarás tener un amplio conocimiento del juego. Esta guía pretende cubrir vuestra falta de sabiduría en el juego.

[media]https://soundcloud.com/raliesin/dragones-y-mazmorras-dungeons-dragons[/media]

# Arquitectura
#### Habitaciones
La guarida de Sakku se compone de una mazmorra repleta de peligros y monstruos. En su interior podremos ir recogiendo herramientas útiles que otros héroes dejaron en sus intentos fallidos de explorar la mazmorra. Herramientas como armas y armaduras o incluso objetos mágicos como varitas, pociones, anillos o hechizos.

La mazmorra está maldita con un poderoso hechizo. Sus niveles descienden de forma infinita, y una vez que entras no puedes salir ni subir niveles hasta que no encuentras el **Amuleto de Yendor**. Se conoce que dicho amuleto está situado en el nivel 26 de la mazmorra. Tu objetivo será descender 26 niveles, recuperar el amuleto y subir de nuevo hasta la superficie.

Los aventureros más osados podrás seguir explorando pasado el nivel 26, para demostrar su valía, enfrentarse a poderosos monstruos y conseguir objetos más valiosos para aumentar su puntuación final.

Cada nivel se compone de diferentes habitaciones unidas por pasillos. Cada habitación mide entre 2x2 y 5x23. Puede estar iluminada o no. De vez en cuando es posible encontrar una habitación con innumerables tesoros, acompañada de un horrible olor que emana de ella...

#### Laberintos
A partir del nivel 15, es posible encontrarse con pequeños laberintos en lugar de habitaciones. Esto es una serie de pasillos oscuros en los que podremos encontrar valiosos objetos o poderosos enemigos.

#### Escaleras
La escalera te permite descender un nivel. Un hechizo mágico te prohíbe regresar al nivel superior (a no ser que hayas encontrado el **Amuleto de Yendor**). Los monstruos jamás usan las escaleras. Cada nivel contiene una escalera para seguir descendiendo.

#### Trampas
Cuando explores la mazmorra, es posible que te encuentres con trampas invisibles en el suelo, que se activarán al pisarlas. Los monstruos no se ven afectados por las trampas:

|               Imagen               |       Tipo       |           Efecto          | Daño |
|:----------------------------------:|:----------------:|:-------------------------:|:----:|
| ![](https://imgur.com/P9igcwB.png) |       Foso       |   Caes al nivel inferior  |  1d8 |
| ![](https://imgur.com/yBxF5s2.png) | Trampa para osos |   Inmovilizado 4 turnos   |  1d6 |
| ![](https://imgur.com/t0UUCx8.png) |   Gas somnífero  |   Inmovilizado 6 turnos   |  --- |
| ![](https://imgur.com/dpP4szz.png) |   Gas confusión  |   Confundido 3d10 turnos  |  --- |
| ![](https://imgur.com/ikweJ6T.png) | Pared de flechas |        Provoca daño       |  2d3 |
| ![](https://imgur.com/9DqmdxG.png) |  Dardo venenoso  |   Provoca daño y veneno   |  1d4 |
| ![](https://imgur.com/0YIhCI1.png) | Trampa corrosiva |     Oxida tu armadura     |  --- |
| ![](https://imgur.com/ldjUWtX.png) |     Teletransporte    | Te envía a otra ubicación |  --- |

# Monstruos
#### Distribución
La mazmorra está habitada por numerosos monstruos clasificados en 26 tipos. Un monstruo representado con cada letra de la A a la Z. Cada enemigo tiene unas cualidades que hay que tener en cuenta a la hora de afrontar un combate.

En cada nivel de la mazmorra encontraremos un número variable de monstruos, entre 1 y 4. A medida que descendemos por la mazmorra, el número de monstruos incrementará levemente; por ejemplo, a partir del nivel 20 encontraremos entre 3 y 6 monstruos. Cada monstruo estará quieto hasta que llames su atención (al entrar en la misma habitación). La *venus flytrap* jamás se moverá de su sitio. Algunos monstruos siempre estarán dormidos y otros te atacarán nada más verte.

Cada 80 turnos un nuevo monstruo emergerá entre las paredes. Siempre será un monstruo acorde al nivel actual y nunca será un *dragon, ice monster, venus flytrap, leprechaun, nymph o mimic.*

![](https://imgur.com/eU70LQl.png)

#### Características
| Letra |                                 Nombre                                 | HD | AC | Nivel |    Daño    |
|:------:|:--------------------------------------------------------------------:|:--:|:--:|:-----:|:------------:|
|    A   |     [url=https://aikoncwd.ovh/monsters/aquator.jpg]aquator[/url]     |  5 |  2 |  9-18 |    0d0   |
|    B   |         [url=https://aikoncwd.ovh/monsters/bat.jpg]bat[/url]         |  1 |  3 |  1-8  |      1d2     |
|    C   |     [url=https://aikoncwd.ovh/monsters/centaur.jpg]centaur[/url]     |  4 |  4 |  8-17 |    1d6+1d6   |
|    D   |      [url=https://aikoncwd.ovh/monsters/dragon.jpg]dragon[/url]      | 10 | -1 |  22-  | 1d8+1d8+3d10 |
|    E   |         [url=https://aikoncwd.ovh/monsters/emu.jpg]emu[/url]         |  1 |  7 |  1-7  |      1d2     |
|    F   |  [url=https://aikoncwd.ovh/monsters/flytrap.jpg]venus flytrap[/url]  |  8 |  3 | 15-24 |     incremental    |
|    G   |     [url=https://aikoncwd.ovh/monsters/griffin.jpg]griffin[/url]     | 13 |  2 |  19-  |  4d3+3d5+4d3 |
|    H   |   [url=https://aikoncwd.ovh/monsters/hobgoblin.jpg]hobgoblin[/url]   |  1 |  5 |  1-10 |      1d8     |
|    I   | [url=https://aikoncwd.ovh/monsters/ice monster.jpg]ice monster[/url] |  1 |  9 |  2-11 |      0d0     |
|    J   |  [url=https://aikoncwd.ovh/monsters/jabberwock.jpg]jabberwock[/url]  | 15 |  6 |  21-  |   2d12+2d4   |
|    K   |     [url=https://aikoncwd.ovh/monsters/kestrel.jpg]kestrel[/url]     |  1 |  7 |  1-6  |      1d4     |
|    L   |  [url=https://aikoncwd.ovh/monsters/leprechaun.jpg]leprechaun[/url]  |  3 |  8 |  7-16 |      1d1     |
|    M   |      [url=https://aikoncwd.ovh/monsters/medusa.jpg]medusa[/url]      |  8 |  2 |  18-  |  3d4+3d4+2d5 |
|    N   |       [url=https://aikoncwd.ovh/monsters/nymph.jpg]nymph[/url]       |  3 |  9 | 11-20 |      0d0     |
|    O   |         [url=https://aikoncwd.ovh/monsters/orc.jpg]orc[/url]         |  1 |  6 |  4-13 |      1d8     |
|    P   |     [url=https://aikoncwd.ovh/monsters/phantom.jpg]phantom[/url]     |  8 |  3 | 16-25 |      4d4     |
|    Q   |      [url=https://aikoncwd.ovh/monsters/quasit.jpg]quasit[/url]      |  3 |  2 | 10-19 |  1d2+1d2+1d4 |
|    R   | [url=https://aikoncwd.ovh/monsters/rattlesnake.jpg]rattlesnake[/url] |  2 |  3 |  3-12 |      1d6     |
|    S   |       [url=https://aikoncwd.ovh/monsters/snake.jpg]snake[/url]       |  1 |  5 |  1-9  |      1d3     |
|    T   |       [url=https://aikoncwd.ovh/monsters/troll.jpg]troll[/url]       |  6 |  4 | 13-22 |  1d8+1d8+2d6 |
|    U   |     [url=https://aikoncwd.ovh/monsters/unicorn.jpg]unicorn[/url]     |  7 | -2 | 17-26 |   3x1d3+4d6  |
|    V   |     [url=https://aikoncwd.ovh/monsters/vampire.jpg]vampire[/url]     |  8 |  1 |  20-  |     1d10     |
|    W   |      [url=https://aikoncwd.ovh/monsters/wraith.jpg]wraith[/url]      |  5 |  4 | 14-23 |      1d6     |
|    X   |       [url=https://aikoncwd.ovh/monsters/xeroc.jpg]xeroc[/url]       |  7 |  7 |  19-  |      3d4     |
|    Y   |        [url=https://aikoncwd.ovh/monsters/yeti.jpg]yeti[/url]        |  4 |  6 | 12-21 |    1d6+1d6   |
|    Z   |      [url=https://aikoncwd.ovh/monsters/zombie.jpg]zombie[/url]      |  2 |  8 |  5-14 |      1d8     |

- **Hits Dice:** La vida que tendrá el enemigo, calculado tirando un d8 tantas veces como HD tenga. Por ejemplo, un dragón tendrá una vida aleatoria entre 10 y 80.
- **Armor Class:** Clase de armadura usando la notación de D&D. A menor número, más defensa tiene y por tanto más complicado es asestar un golpe. Los monstruos pasados el nivel 26 tiene un AC menor del esperado.
- **Nivel:** Indica en que niveles encontraremos cada tipo de monstruo.
- **Daño:** La cantidad de daño. Se calcula tirando el dado. Múltiples dados indica varios ataques en un mismo turno. Por ejemplo un *quasit* puede atacar 3 veces un mismo turno. Algunos monstruos tienen habilidades especiales que veremos a continuación en forma de spoiler

#### Habilidades especiales
[spoiler=(Puede contener spoilers)]
- **Especial:** Efecto que se aplicará si el monstruo consigue golpearte.
- **Inmunidad:** Algunos enemigos son inmunes a diferentes tipos de ataques.
- **Drop:** La probabilidad de dropear un item. El *leprechaun* siempre dropeará oro. El resto de monstruos dropearán un objeto.
- **Flags:** Algunos enemigos tienen habilidades especiales:
    - (**M**)ean: Se despiertan y te atacarán nada más entrar en la habitación.
    - (**F**)ly: Se desplazan más rápido y se mueven mientras luchan.
    - (**R**)egenerate: Al empezar su turno, regenera 1d6 puntos de vida.
    - (**G**)reedy: Si hay oro en la habitación, se desplazará a protegerlo.
    - (**I**)nvisible: Auto explicativo

| Letra |                                 Nombre                                 |   Especial |  Inmunidad | Drop | Flags |
|:------:|:--------------------------------------------------------------------:|:----------:|:---------:|:-----:|:-----:|
|    A   |     [url=https://aikoncwd.ovh/monsters/aquator.jpg]aquator[/url]     |    rust    |           |       |   M   |
|    B   |         [url=https://aikoncwd.ovh/monsters/bat.jpg]bat[/url]         |            |           |       |   F   |
|    C   |     [url=https://aikoncwd.ovh/monsters/centaur.jpg]centaur[/url]     |            |           |   15  |       |
|    D   |      [url=https://aikoncwd.ovh/monsters/dragon.jpg]dragon[/url]      |    fire    |    fire   |  100  |   M   |
|    E   |         [url=https://aikoncwd.ovh/monsters/emu.jpg]emu[/url]         |            |           |       |   M   |
|    F   |  [url=https://aikoncwd.ovh/monsters/flytrap.jpg]venus flytrap[/url]  |  paralyze  |           |       |   M   |
|    G   |     [url=https://aikoncwd.ovh/monsters/griffin.jpg]griffin[/url]     |            |           |   20  |  MFR  |
|    H   |   [url=https://aikoncwd.ovh/monsters/hobgoblin.jpg]hobgoblin[/url]   |            |           |   10  |   M   |
|    I   | [url=https://aikoncwd.ovh/monsters/ice monster.jpg]ice monster[/url] |  paralyze  |    ice    |       |   M   |
|    J   |  [url=https://aikoncwd.ovh/monsters/jabberwock.jpg]jabberwock[/url]  |            |  lighting |   70  |       |
|    K   |     [url=https://aikoncwd.ovh/monsters/kestrel.jpg]kestrel[/url]     |            |           |       |   MF  |
|    L   |  [url=https://aikoncwd.ovh/monsters/leprechaun.jpg]leprechaun[/url]  | steal gold |           |  100  |       |
|    M   |      [url=https://aikoncwd.ovh/monsters/medusa.jpg]medusa[/url]      |  confusion | confusion |   40  |   M   |
|    N   |       [url=https://aikoncwd.ovh/monsters/nymph.jpg]nymph[/url]       | steal item |           |  100  |       |
|    O   |         [url=https://aikoncwd.ovh/monsters/orc.jpg]orc[/url]         |            |           |   15  |   G   |
|    P   |     [url=https://aikoncwd.ovh/monsters/phantom.jpg]phantom[/url]     |            |   arrows  |       |   IF  |
|    Q   |      [url=https://aikoncwd.ovh/monsters/quasit.jpg]quasit[/url]      |            |   magic   |   30  |   M   |
|    R   | [url=https://aikoncwd.ovh/monsters/rattlesnake.jpg]rattlesnake[/url] |   poison   |           |       |   M   |
|    S   |       [url=https://aikoncwd.ovh/monsters/snake.jpg]snake[/url]       |            |           |       |   M   |
|    T   |       [url=https://aikoncwd.ovh/monsters/troll.jpg]troll[/url]       |            |           |   50  |   MR  |
|    U   |     [url=https://aikoncwd.ovh/monsters/unicorn.jpg]unicorn[/url]     |            |   magic   |   20  |   M   |
|    V   |     [url=https://aikoncwd.ovh/monsters/vampire.jpg]vampire[/url]     |  reduce hp |           |   20  |   MR  |
|    W   |      [url=https://aikoncwd.ovh/monsters/wraith.jpg]wraith[/url]      | reduce lvl |   arrows  |       |       |
|    X   |       [url=https://aikoncwd.ovh/monsters/xeroc.jpg]xeroc[/url]       |    mimic   |           |   30  |       |
|    Y   |        [url=https://aikoncwd.ovh/monsters/yeti.jpg]yeti[/url]        |            |    ice    |   30  |       |
|    Z   |      [url=https://aikoncwd.ovh/monsters/zombie.jpg]zombie[/url]      |            |           |       |   M   |

- **Rust:** Los *aquators* no hacen daño, pero te oxidan cualquier armadura que no sea de piel y hace decrecer su nivel.
- **Fire:** El *dragon* puede lanzar una llamarada de fuego a distancia, provocando 3d6.
- **Poison:** La *rattlesnake* puede envenenarte en cada golpe. Decrece tu fuerza. Tu experiencia reduce la probabilidad de ser envenenado.
- **Paralyze:** La *venus flytrap* y los *ice monster* te paralizan durante 6 turnos. Los *ice monster* pueden paralizar a distancia.
- **Steal gold:** Si el *leprechaun* te golpea, te robará oro y desaparecerá. La cantidad es 2+1d(50+10 por nivel)\*5. Por ejemplo si estás en el nivel 8 perderás 2+1d130 multiplicado por 5.
- **Steal item:** Si la *nymph* te golpea, te robará un item aleatorio de tu inventario y desaparecerá. 
- **Confusion:** La *medusa* puede aplicar confusión con su mirada (a distancia) durante 20+1d20 turnos.
- **Mimic:** Imita otro objeto, incluso puede imitar escaleras. Ataca al ser atacado.
- **Reduce HP:** Pierdes un total de 1d5 puntos de HP máximos. Si llegas a 0 mueres.
- **Reduce lvl:** Pierdes un nivel completo en cada golpe. Si llegas a 0 mueres.

Los monstruos paralizados o dormidos reciben +4 en cada golpe.
[/spoiler]

# Objetos
#### Distribución
En cada nivel de la mazmorra aparecerán diferentes objetos. Es más probable encontrar más objetos a medida que descendemos niveles. Algunos objetos podrán estar bendecidos o maldecidos. La distribución será la siguiente:

|               Objeto               | Descripción | Aparición |
|:----------------------------------:|:-----------:|:---------:|
| ![](https://imgur.com/3PDwPoW.png) |     Arma    |     9     |
| ![](https://imgur.com/ArEEXcJ.png) |   Armadura  |     9     |
| ![](https://imgur.com/tof2nNV.png) |    Comida   |     17    |
| ![](https://imgur.com/mtGOKRe.png) |    Poción   |     26    |
| ![](https://imgur.com/NCKDVYR.png) |  Pergamino  |     27    |
| ![](https://imgur.com/Lbw9Vgr.png) |    Anillo   |     6     |
| ![](https://imgur.com/pGVrEVE.png) |    Varita   |     6     |

En los primeros 5 niveles encontraremos entre 2 y 5 objetos por nivel. En el nivel 20 encontraremos entre 5 y 8.

# Objetos Mágicos
#### ![](https://imgur.com/NCKDVYR.png) Scrolls

Los conjuros mágicos están escritos en pergaminos. Una vez lo lees, se aplica su efecto y desaparece para siempre. El principal handicap en la mayoría de objetos es que no conoces su efecto hasta que los utilizas. Es posible encontrar pergaminos de identificación que te revelarán los poderes ocultos de cualquier objeto desconocido. Aquí un listado:

| Nombre              | Descripción                                                                                                                                            |  % |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|:--:|
| Identificación      | Identifica un objeto de tu inventario.                                                                                                                 | 25 |
| Encantar arma       | El arma equipada brillará de color azul por un momento, mejorando su daño. Si el arma está maldita, dejará de estarlo.                                 | 10 |
| Encantar armadura   | La armadura equipada brillará de color azul por un momento, mejorando su daño. Si la armadura está maldita, dejará de estarlo.                         | 10 |
| Detectar comida     | Se muestra la ubicación de toda la comida que hay en el nivel.                                                                                         |  2 |
| Detectar oro        | Se muestra la ubicación de todo el oro que hay en el nivel.                                                                                            |  2 |
| Luz                 | Ilumina la habitación oscura en la que te encuentres.                                                                                                  |  7 |
| Mapa                | Este pergamino en realidad es un mapa del nivel. Muestra todas las habitaciones y pasillos.                                                            |  5 |
| Confundir monstruos | Tus manos se vuelven rojas. El siguiente monstruo golpeado queda confundido.                                                                           |  5 |
| Eliminar maldición  | Elimina la maldición de todos los objetos equipados.                                                                                                   |  6 |
| Dormir              | Te quedas dormido durante 4d3 turnos.                                                                                                                  |  3 |
| Teletransportación  | Eres teletransportado a una ubicación aleatoria del mismo nivel.                                                                                       |  5 |
| Atraer monstruos    | Todos los monstruos del nivel notan tu presencia y empiezan a perseguirte.                                                                             |  3 |
| Crear monstruo      | Crea un monstruo aleatorio delante de ti. El monstruo será apropiado al nivel.                                                                         |  3 |
| Paralizar monstruo  | Paraliza cualquier monstruo que esté delante de ti. Si atacas rompes el hechizo.                                                                       |  3 |
| Proteger armadura   | Protege tu armadura contra el óxido. Si la armadura está maldita, dejará de estarlo.                                                                   |  4 |
| Asustar monstruo    | Si lo dejas en el suelo, ningún monstruo pasará por encima de este pergamino.                                                                          |  3 |
| Genocidio           | Destruye el monstruo que hay frente a ti y cualquier otro monstruo del mismo tipo, afecta a toda la mazmorra. Solo existe una copia de este pergamino. |  1 |
| Vorpalizar arma     | Tu arma recibe +1 +1 y es más efectiva contra un monstruo aleatorio, que recibirá +4 +4. Si se usa 2 veces el arma se rompe.                           |  2 |
| En blanco           | Un pergamino en blanco que no hace nada.                                                                                                               |  1 |

La probabilidad de que aparezca un pergamino se calcula usando la columna **%**. El pergamino de **genocidio** solo aparece una vez por run. El resto de pergaminos pueden aparecer más de una vez respetando el % de aparición.

#### ![](https://imgur.com/mtGOKRe.png) Pociones
Las pociones son brebajes mágicos. Cuando los bebes, algo extraño te sucederá. Cada poción tendrá su color correspondiente pero dichos colores serán únicos en cada run.

| Nombre             | Descripción                                                                                                         |  % |
|--------------------|---------------------------------------------------------------------------------------------------------------------|:--:|
| Curación           | Te curas (nivel PJ)d4. Si estás curado completamente, añade +1. También cura la ceguera, confusión y alucinaciones. | 13 |
| Curación Extra     | Igual que una poción de curación, pero los efectos son dobles.                                                      |  5 |
| Fuerza             | Añade 1 punto a tu fuerza máxima.                                                                                   | 13 |
| Restaura Fuerza    | Restauras tu fuerza al valor máximo disponible.                                                                     | 13 |
| Veneno             | Pierdes 1d3 puntos de fuerza máxima. Si llevas el anillo **Mantener Fuerza**, aumenta. Cura alucinaciones.          |  8 |
| Ceguera            | Estás ciego durante 850 turnos. Evita que puedas ser confundido por Medusa.                                         |  5 |
| Parálisis          | No te puedes mover y pierdes 6 turnos.                                                                              |  5 |
| Confusión          | Te mueves de forma aleatoria durante 2d20 turnos.                                                                   |  5 |
| Alucinógena        | La apariencia de los monstruos y objetos cambia aleatoriamente durante 850 turnos.                                  |  6 |
| Adrenalina         | Tienes más probabilidad de atacar y esquivar durante 5d8 turnos. Si bebes 2 pociones seguidas te mueres.            |  5 |
| Levitación         | Levitas en el aire durante 3d10 turnos. Evitas trampas y es imposible recoger objetos o usar escaleras.             |  5 |
| Detectar Magia     | Muestra cualquier objeto mágico en el mapa. Incluyendo armas/armaduras que están encantadas o malditas.             |  5 |
| Detectar Monstruos | Muestra cualquier monstruo en el mapa.                                                                              |  5 |
| Experiencia        | Aumentas un nivel completo.                                                                                         |  2 |
| Ojo de gato        | Puedes ver monstruos invisibles durante 850 turnos. Cura la ceguera.                                                |  4 |
| Agua               | Es agua y no produce ningún efecto                                                                                  |  1 |

La probabilidad de que aparezca una poción determinada se calcula usando la columna **%**. El resto de pociones pueden aparecer más de una vez respetando el % de aparición.
En lugar de beber una poción, la podrás lanzar contra un monstruo.

#### ![](https://imgur.com/Lbw9Vgr.png) Anillos
Los anillos otorgan poderes especiales a su portador. Estos podrán ser poderosas ayudas o maldiciones. Cada tipo de anillo será identificado con una piedra en particular, pero al igual que las pociones, las piedras de los anillos serás únicos en cada run. Puedes llevar 2 anillos a la vez, uno en cada mano:

| Nombre             | Descripción                                                                       |  % | Hambre | Incremento |
|--------------------|-----------------------------------------------------------------------------------|:--:|:------:|:----------:|
| Fuerza             | Incrementa tu fuerza.                                                             |  9 |  +1,00 |     Sí     |
| Destreza           | Incrementa tu destreza.                                                           |  8 |  +0,33 |     Sí     |
| Protección         | Reduces la probabilidad que un monstruo te golpee.                                |  9 |  +1,00 |     Sí     |
| Provocar Daño      | Incrementa el daño de cada golpe.                                                 |  8 |  +0,33 |     Sí     |
| Observación        | Te ayuda a detectar puertas secretas y trampas.                                   | 10 |  +0,33 |            |
| Ojo de gato        | Te permite ver monstruos invisibles.                                              | 10 |  +0,25 |            |
| Proteger Armadura  | Evita que tu armadura se oxide.                                                   |  5 |  +1,00 |            |
| Regeneración       | Te curas más rápido. 1HP por turno.                                               |  4 |  +2,00 |            |
| Ayuno              | Te desplazas el doble antes de tener hambre. Con 2 anillos, jamás tendrás hambre. |  9 |  -0,5  |            |
| Ninja              | Los monstruos no pueden verte.                                                    |  7 |  +1,00 |            |
| Mantener Fuerza    | No puedes envenenarte con pociones, trampas o monstruos.                          |  5 |  +1,00 |            |
| Teletransportación | Te teletransportas de forma aleatoria cada 300 turnos.                            |  5 |   --   |            |
| Atraer monstruos   | Todos los monstruos del nivel notan tu presencia y empiezan a perseguirte.        | 10 |   --   |            |
| Adorno             | Es un anillo precioso, pero sin ningún poder.                                     |  1 |   --   |            |

El efecto de los anillos **Protección, Fuerza, Destreza** o **Provocar Daño** se determina por su incremento. Por ejemplo un **Anillo de Fuerza +2** añade 2 puntos de fuerza. Un **Anillo de Protección -1** aumentará en 5% la probabilidad de ser golpeado. Los anillos con incremento negativo estarán malditos y no te los podrás quitar a no ser que elimines la maldición. Los anillos de **Teletransportación** y **Atraer Monstruos** siempre estarán malditos.

Llevar casi cualquier anillo hará que pases hambre más rápido.

#### ![](https://imgur.com/pGVrEVE.png) Bastones y varitas
Los bastones y varitas lanzan un hechizo en la dirección deseada. Se pueden usar como arma también. Cada bastón o varita está hecho de un material en concreto, pero al igual que las pociones o anillos, cada run tendrá unos materiales únicos. La diferencia entre un bastón y una varita es que el bastón hace más daño al usarlo como arma cuerpo a cuerpo.

Cuando encuentras un bastón o varita, tendrá 2+1d8 usos. Una vez agotados los usos, solo se puede usar como arma de cuerpo a cuerpo.

| Nombre             | Descripción                                                                                                                                                                                |  % |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--:|
| Luz                | Ilumina la habitación en la que te encuentras. Tiene 1+1d5+1d10 usos.                                                                                                                      | 12 |
| Lucha              | Es un bastón para golear. Siempre acierta el golpe con 3+1d8. Cada 20 golpes provoca 9+3d8.                                                                                                |  5 |
| Fuego              | Dispara un rayo de fuego. El daño es de 6d8.                                                                                                                                               |  4 |
| Eléctrico          | Dispara un rayo eléctrico. El daño es de 5d8.                                                                                                                                              |  5 |
| Hielo              | Dispara un rayo de hielo. El daño es de 6d4.                                                                                                                                               |  6 |
| Magia              | Dispara un misil mágico. El daño es de 4d4.                                                                                                                                                |  7 |
| Adrenalina         | El monstruo tiene más probabilidad de atacarte.                                                                                                                                            |  7 |
| Invisibilidad      | Otorga invisibilidad al monstruo.                                                                                                                                                          |  4 |
| Polimorfosis       | Cambia el monstruo por otro tipo de monstruo.                                                                                                                                              | 15 |
| Lentitud           | El monstruo tiene menos probabilidad de atacarte.                                                                                                                                          | 10 |
| Drenar Vida        | Pierdes la mitad de tu vida. Provoca esa cantidad de daño al monstruo.                                                                                                                     |  9 |
| Teletransportación | Teletransporta el monstruo a una ubicación aleatoria del nivel.                                                                                                                            |  5 |
| Cancelación        | Cancela el poder mágico de un monstruo. Funciona contra Aquators, Dragones, Venus flytrap, Ice Monsters, Leprechauns, Medusas, Nymphs, Phantoms, Rattlesnakes, Vampiros, Wraiths y Xerocs. |  5 |
| Crear Monstruo     | Crea un monstruo aleatorio delante de ti.                                                                                                                                                  |  5 |
| Bastón             | Un bastón sin poder mágico. La única razón de llevar este item es para intentar que se lo lleve una Nymph en lugar de cualquier otro item de valor.                                        |  1 |

#### Amuleto de Yendor
El **Amuleto de Yendor** es único. Ubicado en algún lugar del piso 26. Cuando el jugador posee el amuleto, puede empezar a utilizar las escaleras para ascender. Si el jugador llega a la salida (piso 0) con el amuleto, habrá ganado la partida. El amuleto otorga algunos poderes especiales:

- Si no recoges el amuleto en el nivel 26 y sigues descendiendo, aparecerá en los siguientes niveles.
- Tu hambre desaparece, a no ser que lleves algún anillo.
- Tiene un valor de 1000 monedas de oro.
- Es un objeto mágico, así que aparecerá en el mapa si bebes la poción de **Detectar magia**.
- Se generan más trampas en los niveles.

# Objetos ordinarios
#### ![](https://imgur.com/3PDwPoW.png) Armas
Las armas serán tu principal fuente de daño y la herramienta más importante para luchar contra los monstruos.

|               Objeto               |    Nombre    | Golpe | Lanzar |
|:----------------------------------:|:------------:|:-----:|:------:|
| ![](https://imgur.com/RTj31kg.png) |     Dardo    |  1d1  |   1d3  |
| ![](https://imgur.com/k3OjUM8.png) |    Flecha    |  1d1  |   2d4  |
| ![](https://imgur.com/eKsup6j.png) |    Virote    |  1d2  |   2d6  |
| ![](https://imgur.com/lTeCNN7.png) |   Shuriken   |  1d2  |   2d3  |
| ![](https://imgur.com/BrR0mBF.png) |  Arco corto  |  1d1  |   1d1  |
| ![](https://imgur.com/G192KfF.png) |   Ballesta   |  1d1  |   1d1  |
| ![](https://imgur.com/AZVgMZI.png) |     Puñal    |  1d6  |   1d4  |
| ![](https://imgur.com/l5s73R0.png) |     Maza     |  2d4  |   1d3  |
| ![](https://imgur.com/xhwz0MN.png) |     Lanza    |  2d3  |   1d6  |
| ![](https://imgur.com/o0Ksc6Q.png) | Espada larga |  3d4  |   1d2  |
| ![](https://imgur.com/WhMIBTX.png) |    Espadón   |  4d4  |   1d2  |
| ![](https://imgur.com/dYrx8fE.png) |    Bastón    |  2d2  |   1d1  |
| ![](https://imgur.com/WCBp4Ln.png) |    Varita    |  1d1  |   1d1  |
|                                    |     Puños    |  1d4  |   ---  |

La munición hace más daño si la lanzas. En el caso de **Flechas** y **Virotes** provocarás la mitad de daño si no equipas el arma correspondiente.
Un arma puede tener un incremento de daño. Si el incremento es negativo el arma estará maldita y no la podrás desequipar hasta que uses un pergamino de **Encantar arma** o **Eliminar maldición**.

El 10% de las armas estarán malditas y el 5% estará encantadas.
Los bastones y varitas tienen un incremento de daño de +1 que no puede ser mejorado con pergaminos.

Tu aventura empieza con una Maza encantada +1 +1. El primer incremento otorga destreza y el segundo daño.

#### ![](https://imgur.com/ArEEXcJ.png) Armaduras
Las armaduras serán tu principal fuente de protección. Muy necesaria para luchar contra los monstruos.

|               Objeto               |           Nombre           | AC |  % |
|:----------------------------------:|:--------------------------:|:-----:|:--:|
|                                    |        Sin armadura        |   9   |    |
| ![](https://imgur.com/zKrDppE.png) |      Armadura de piel      |   8   | 20 |
| ![](https://imgur.com/z0LfJne.png) | Armadura de piel tachonada |   7   | 17 |
| ![](https://imgur.com/Oza52xP.png) |     Armadura de anillas    |   6   | 15 |
| ![](https://imgur.com/I2F29zn.png) |     Armadura de escamas    |   5   | 13 |
| ![](https://imgur.com/RrNBY4T.png) |     Armadura de cadenas    |   4   | 12 |
| ![](https://imgur.com/MOqf742.png) |     Armadura de placas     |   3   | 10 |
| ![](https://imgur.com/4r2USgK.png) |     Armadura reforzada     |   2   |  8 |
| ![](https://imgur.com/3dXgvaV.png) |      Armadura templada     |   1   |  5 |

Las armaduras, al igual que las armas, podrán tener un incremento que mejorará su defensa. Si el incremento es negativo la armadura estará maldita y no la podrás desequipar hasta que leas un pergamino de **Encantar armadura**, **Proteger armadura** o **Eliminar maldición**. Los **Aquators** y las **Trampas corrosivas** oxidarán cualquier armadura que no sea de piel, añadiendo un incremento negativo.

El 20% de las armaduras estarán malditas y el 8% estarán encantadas.

Las armaduras protegen más cuanto menor es su AC (Armor Class).
Una armadura de clase -5 te protege de **bats** y **hobgoblins**. Una armadura de clase -19 te protege de cualquier daño. (esto se explicará mejor en la sección de Combate).

#### ![](https://imgur.com/tof2nNV.png) Comida
Empiezas la aventura con una ración de comida. A medida que avanzas por la mazmorra podrás recolectar más comida. A veces encontrarás fruta. 1 de cada 10 raciones de comida será fruta.

La comida te permite aguantar 1500 turnos. A partir de 1500 turnos sin comer, empezarás a tener hambre. 150 turnos después, empezarás a sentirte débil. Si vuelven a pasar 150 turnos más sin comer, empezarás a perder 1d2 puntos de vida en cada turno hasta morir por inanición.

La fruta funciona igual que la comida, excepto que ganas algo de experiencia, 1d10, al comerla.

# Subir de nivel
#### Experiencia
Cuando matas un monstruo obtienes puntos de experiencia siguiendo esta tabla:

|                                Monstruo                               | Experiencia |                                Monstruo                               | Experiencia |
|:--------------------------------------------------------------------:|:----:|:--------------------------------------------------------------------:|:----:|
|     [url=https://aikoncwd.ovh/monsters/aquator.jpg]aquator[/url]     |  20  |       [url=https://aikoncwd.ovh/monsters/nymph.jpg]nymph[/url]       |  37  |
|         [url=https://aikoncwd.ovh/monsters/bat.jpg]bat[/url]         |   1  |         [url=https://aikoncwd.ovh/monsters/orc.jpg]orc[/url]         |   5  |
|     [url=https://aikoncwd.ovh/monsters/centaur.jpg]centaur[/url]     |  25  |     [url=https://aikoncwd.ovh/monsters/phantom.jpg]phantom[/url]     |  120 |
|      [url=https://aikoncwd.ovh/monsters/dragon.jpg]dragon[/url]      | 6800 |      [url=https://aikoncwd.ovh/monsters/quasit.jpg]quasit[/url]      |  32  |
|         [url=https://aikoncwd.ovh/monsters/emu.jpg]emu[/url]         |   2  | [url=https://aikoncwd.ovh/monsters/rattlesnake.jpg]rattlesnake[/url] |   9  |
|  [url=https://aikoncwd.ovh/monsters/flytrap.jpg]venus flytrap[/url]  |  80  |       [url=https://aikoncwd.ovh/monsters/snake.jpg]snake[/url]       |   1  |
|     [url=https://aikoncwd.ovh/monsters/griffin.jpg]griffin[/url]     | 2000 |       [url=https://aikoncwd.ovh/monsters/troll.jpg]troll[/url]       |  120 |
|   [url=https://aikoncwd.ovh/monsters/hobgoblin.jpg]hobgoblin[/url]   |   3  |     [url=https://aikoncwd.ovh/monsters/unicorn.jpg]unicorn[/url]     |  190 |
| [url=https://aikoncwd.ovh/monsters/ice monster.jpg]ice monster[/url] |  15  |     [url=https://aikoncwd.ovh/monsters/vampire.jpg]vampire[/url]     |  350 |
|  [url=https://aikoncwd.ovh/monsters/jabberwock.jpg]jabberwock[/url]  | 4000 |      [url=https://aikoncwd.ovh/monsters/wraith.jpg]wraith[/url]      |  55  |
|     [url=https://aikoncwd.ovh/monsters/kestrel.jpg]kestrel[/url]     |   1  |       [url=https://aikoncwd.ovh/monsters/xeroc.jpg]xeroc[/url]       |  100 |
|  [url=https://aikoncwd.ovh/monsters/leprechaun.jpg]leprechaun[/url]  |  10  |        [url=https://aikoncwd.ovh/monsters/yeti.jpg]yeti[/url]        |  50  |
|      [url=https://aikoncwd.ovh/monsters/medusa.jpg]medusa[/url]      |  200 |      [url=https://aikoncwd.ovh/monsters/zombie.jpg]zombie[/url]      |   6  |

A estos valores hay que agregar una bonificación de experiencia correspondiente a los puntos totales de vida (hit points). Por ejemplo, un **Aquator** puede tener entre 5 y 40 puntos de vida la experiencia recibida será entre 25 y 60.

Esta bonificación no se aplica a monstruos que otorgan menos de 10 puntos de experiencia base.

Este bonus de experiencia adicional se multiplica x2 para los monstruos con más de 5 HD y x10 para los monstruos con 10 HD o más. Pasado el nivel 25, recibes un bonus del 50% por cada monstruo eliminado. Ejemplos:

- **Troll** con 6 HD = 48 puntos de vida. Otorgará: 120 + (48 * 2) = 216 puntos de experiencia.
- **Dragón** con 10 HD = 80 puntos de vida. Otorgará 6800 + (80 * 10) = 7600 puntos de experiencia.

Comer fruta otorga 5 puntos de experiencia.

#### Nivel del personaje
Tu nivel se calcula con la siguiente tabla de experiencia. Cada vez que subes un nivel, tu vida actual y tu vida máxima se incrementa 1d10. Tus heridas sanarán más rápido y tendrás más probabilidad de golpear a los enemigos.

| Experiencia | Nivel | Regeneración (HP:turnos) |
|:-----------:|:-----:|:----------------------:|
|      0      |   1   |          1:18          |
|      10     |   2   |          1:17          |
|      20     |   3   |          1:15          |
|      40     |   4   |          1:13          |
|      80     |   5   |          1:11          |
|     160     |   6   |           1:9          |
|     320     |   7   |           1:7          |
|     640     |   8   |           1:3          |
|     1300    |   9   |          1d2:3         |
|     2600    |   10  |          1d3:3         |
|     5200    |   11  |          1d4:3         |
|    13000    |   12  |          1d5:3         |
|    26000    |   13  |          1d6:3         |
|    50000    |   14  |          1d7:3         |
|    100000   |   15  |          1d8:3         |

El nivel máximo es 25, que se consigue al alcanzar 128000000 puntos de experiencia. Regenerando un total de 1d18 puntos de vida cada 3 turnos.

# Combate
#### Probabilidad de golpear
Cuando atacas a un monstruo, tu probabilidad de asestar un golpe se calcula de la siguiente forma:
`5% + (5% * lvl) + (5% * monster AC)`

Por ejemplo si somos nivel 3 e intentamos golear un **emu**, nuestra probabilidad será:
`5 + (5 * 3) + (5 * 7) = 55%`
Si con el mismo nivel intentamos atacar a un **dragón**:
`5 + (5 * 3) + (5 * -1) = 15%`

Cada punto de destreza añade un 5% de probabilidad para asestar el golpe. La destreza se obtiene con el nivel del personaje, el nivel del arma y con un anillo.

-----------
#### Probabilidad de ser golpeado

Cuando un monstruo te ataca, la probabilidad de recibir un golpe se calcula así:
`20% + (5% * monster HD) + (5% player AC) - (5% * anillo protección)`

Por ejemplo si tenemos una armadura de escamas y nos golpea un zombie:
`20 + (5 * 2) + (5 * 5) - (5 * 0) = 55%`
Si tenemos un anillo de protección +1 con armadura de placas y nos ataca un dragón:
`20 + (5 * 10) + (5 * 3) - (5 * 1) = 80%`

#### Incremento de daño y destreza
La cantidad de daño que provocas a un monstruo se calcula tirando el dado de daño correspondiente al arma equipada + un bonus adicional correspondiente a tu fuerza actual:

|  Fuerza  | Daño | Destreza |
|:-----:|:---:|:---:|
|   3   |  -4 |  -4 |
|   4   |  -3 |  -3 |
|   5   |  -2 |  -2 |
|   6   |  -1 |  -1 |
|  7-15 |  0  |  0  |
|   16  |  1  |  0  |
|   17  |  1  |  1  |
|   18  |  2  |  1  |
| 19-20 |  3  |  1  |
|   21  |  4  |  2  |
| 22-29 |  5  |  2  |
|   30  |  6  |  3  |

Mención especial: A medida que subimos nuestra fuerza, también aumenta nuestra destreza. Esto significa que no solo golpearemos más fuerte, si no que tendremos más probabilidad de asestar el golpe. El nivel máximo de fuerza es 30, y eso equivaldría a golpear con un arma +3 +6 (15% probabilidad adicional para golpear y +6 de daño en cada golpe).

#### ¿Quién ataca primero?
Si te desplazas hacia una casilla adyacente a un monstruo, el monstruo atacará primero.
Si tú y el monstruo os desplazáis simultáneamente en casillas adyacentes, tu podrás atacar primero. Un monstruo dormido jamás atacará primero. Los monstruos paralizados o dormidos reciben +4 en cada golpe.

# Puntuación
Si consigues escapar con vida de la mazmorra podrás vender todo tu inventario y obtener oro por cada objeto. El propio **Amuleto de Yendor** tiene un valor de 1000 piezas de oro. El resto de objetos tienen el valor según las siguientes tablas:

[spoiler=Pergaminos]
| Pergamino           | Valor | Pergamino          | Valor |
|---------------------|:-----:|--------------------|:-----:|
| Genocidio           |  300  | Luz                |  120  |
| Vorpalizar arma     |  250  | Eliminar maldición |  105  |
| Asustar monstruo    |  200  | Identificación     |  100  |
| Paralizar monstruo  |  180  | Crear monstruo     |   75  |
| Teletransportación  |  165  | Detectar comida    |   50  |
| Encantar armadura   |  160  | Detectar oro       |   50  |
| Encantar arma       |  150  | Atraer monstruos   |   20  |
| Mapa                |  150  | Dormir             |   5   |
| Confundir monstruos |  140  | En blanco          |   5   |
| Proteger armadura   |  120  |                    |       |[/spoiler]

[spoiler=Anillos]
| Anillo        | Valor | Anillo             | Valor |
|---------------|:-----:|--------------------|:-----:|
| Ninja         |  470  | Proteger Armadura  |  380  |
| Regeneración  |  460  | Ojo de gato        |  310  |
| Destreza      |  440  | Mantener Fuerza    |  280  |
| Observación   |  420  | Ayuno              |  240  |
| Fuerza        |  400  | Teletransportación |   30  |
| Protección    |  400  | Atraer monstruos   |   10  |
| Provocar Daño |  400  | Adorno             |   10  |[/spoiler]

[spoiler=Pociones]
| Poción             | Valor | Poción      | Valor |
|--------------------|:-----:|-------------|:-----:|
| Experiencia        |  250  | Ojo de gato |  100  |
| Curación Extra     |  200  | Levitación  |   50  |
| Adrenalina         |  190  | Veneno      |   5   |
| Fuerza             |  150  | Ceguera     |   5   |
| Curación           |  130  | Parálisis   |   5   |
| Restaura Fuerza    |  130  | Confusión   |   5   |
| Detectar Monstruos |  130  | Alucinógena |   5   |
| Detectar Magia     |  105  | Agua        |   5   |[/spoiler]

[spoiler=Varitas y Bastones]
| Varita             | Valor | Varita         | Valor |
|--------------------|:-----:|----------------|:-----:|
| Lentitud           |  350  | Cancelación    |  280  |
| Teletransportación |  345  | Luz            |  250  |
| Fuego              |  340  | Lucha          |   75  |
| Eléctrico          |  335  | Crear Monstruo |   50  |
| Hielo              |  330  | Invisibilidad  |   10  |
| Magia              |  325  | Adrenalina     |   5   |
| Polimorfosis       |  310  | Bastón         |   5   |
| Drenar Vida        |  300  |                |       |[/spoiler]

[spoiler=Armaduras, Armas y Munición]
| Armadura                   | Valor | Arma         | Valor | Munición | Valor |
|----------------------------|:-----:|--------------|:-----:|----------|:-----:|
| Armadura templada          |  750  | Espadón      |   75  | Dardo    |   1   |
| Armadura reforzada         |  590  | Ballesta     |   30  | Shuriken |   2   |
| Armadura de placas         |  580  | Arco corto   |   15  | Flecha   |   3   |
| Armadura de cadenas        |  475  | Espada larga |   15  | Virote   |   4   |
| Armadura de escamas        |  330  | Maza         |   8   |          |       |
| Armadura de anillas        |  225  | Lanza        |   5   |          |       |
| Armadura de piel tachonada |  220  | Puñal        |   3   |          |       |
| Armadura de piel           |  120  |              |       |          |       |[/spoiler]

Para los anillos, cada incremento aumenta su valor en 20. Para las varitas y bastones, cada carga/uso añade 20 a su valor. Cualquier anillo con un decremento rebaja el valor a 50 piezas de oro. Por ejemplo un **Anillo de Fuerza +1** vale 420. Cualquier objeto sin identificar vale la mitad de su precio.

Para las armaduras, cada incremento añade o quita 110 a su valor.
Para las armas, cada incremento eleva/decrece x3 su valor base.
Para la munición, cada incremento eleva/decrece x2 su valor base.

Por ejemplo un **Espadón +2 +2** tiene un valor de: `75 + (75 * 3) * 4 = 950`
Ningún objeto tendrá un valor inferior a 0.

Las raciones de comida valen 3 piezas de oro.
