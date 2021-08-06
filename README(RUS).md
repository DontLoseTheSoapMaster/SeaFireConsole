Classical Console SeaFire (Java)
      Я создал это приложение в 2019 году. Моей основной целью было - 
      Создание ИИ, способного потягаться с человеком. ИИ в программе состоит
      Из двух логических блоков. Позже я объясню на пальцах, как он работает но для 
      Начала поговорим о геймплее.

     Игра полностью запускается в консоли. У вас должен быть установлена 
     Java, желательно не ниже 8 версии. Запуск осуществляется
     С консоли, а именно класса SeaFire. В консоли это будет 
     Выглядит следующим образом:

     >%путь до файла% Java SeaFire

     Пройдемся вкратце что вы там увидите. Ниже представлен пример
     Одного из игровых полей:
      
      N  ABCDEFGHIJ
      1  0000000000
      2  0000000000
      3  0000000000
      4  0000000000
      5  0000000000
      6  0000000000
      7  0000000000
      8  0000000000
      9  0000000000
      10 0000000000
      
ниже вы видите поле вашего противника:
      
      N  ABCDEFGHIJ
      1  0002662000
      2  0022222000
      3  0026620000
      4  0022220000
      5  0000000030
      6  3000000000
      7  0000003000
      8  0030430000
      9  0030000000         
      10 0000000000
      
Так будет выглядеть ваше поле, где-то в середине игры:
      
      N  ABCDEFGHIJ
      1  1001100000
      2  1022222210
      3  1026666210
      4  3022222210
      5  0100000000
      6  0001222200
      7  1034266200
      8  0000222200
      9  0000000100
      10 0010000000
      
И последнее. Ниже представлено Анализирующее поле противника.
Вообще оно не выводится. Но позже мы его обсудим
      
      N  ABCDEFGHIJ
      1  0330330330
      2  3033333333
      3  3333333303
      4  3333333330
      5  3033033033
      6  3303333303
      7  0333333330
      8  3033333333
      9  3303303303
      10 0330330330
     
Каждая цифра имеет определенное значение. Ниже приведены пояснения:
 
"0" - "Не тронутое" поле
"1" - часть вашего корабля
"2" - часть зоны вокруг уничтоженного корабля
"3" - Место куда выстрелил игрок или компьютер. Соответствует промаху. Это также место куда нельзя стрелять в анализирующем поле
"4" - Место куда выстрелил игрок или компьютер. Соответствует попаданию в корабль, однако не его уничтожению
"6" - часть уничтоженного корабля
      
Геймплей:
      
В начале вы видите 2 одинаковых поля, изображённых как поле внизу:
      
      N  ABCDEFGHIJ
      1  0000000000
      2  0000000000
      3  0000000000
      4  0000000000
      5  0000000000
      6  0000000000
      7  0000000000
      8  0000000000
      9  0000000000
      10 0000000000
      
После появления полей появится окошко для ввода со следующим сообщением:
      
      "Расположение. 1 - горизонт. 0 - вертикальное" 
      
На этом этапе вы должны вбить соответственно "1" или "0". Эти цифры  
Дают программе информацию о том, как вы собираетесь размещать корабль 
На поле. Если вы введёте 1 - значит вы его будете размещать горизонтально,
А если 0 - вертикально. В игре нужно будет разместить всего
10 кораблей. От самого большого, 4-х палубного, до 4-х маленьких,
Однопалубных. Ниже приведен список

      1. 4-палубник
      2. 3-палубник
      3. 3-палубник
      4. 2-палубник
      5. 2-палубник
      6. 2-палубник
      7. 1-палубник
      8. 1-палубник
      9. 1-палубник
      10. 1-палубник
      
После того, как мы указали положение корабля - необходимо ввести координаты корабля. Вводится
Они в 2 этапа в начале вводится Буква(Заглавная!!). Потом цифра. После указания положения,
Собственно, появится окно для ввода буквы. Оно содержат следующее сообщение:

      "ВВедите координату x(От A до J)"
      
So, u need to input Capital letter (from A to J), which defines the start
      
      "ВВедите координату y(От A до J)"
      
***So now, u need to input any numer from 1 to 9 or "10", which defines the starting point of the ship's position in y. 
After inputing that, for Example 5, u ship will got the position. First Ship is very long, it occupies 4 cells on the field. 
we'v Got in example position "A5", so, if we set vertical positioning - the ship will occupies cell A5 and 3 cells 
lower (A6,A7,A8), if we set horizontal positioning - the ship will occupies cell A5 and 3 cells righter (B5,C5,D5).
At the stage of positioning ships the concole printed 2 fields: Field with ur ships and "CanceledField". At the start of the game that fields is empty:
      
      N  ABCDEFGHIJ
      1  0000000000
      2  0000000000
      3  0000000000
      4  0000000000
      5  0000000000
      6  0000000000
      7  0000000000
      8  0000000000
      9  0000000000
      10 0000000000
      
After inputing ship into positioning, for Example - horizontal A5, the  fields will change. The fields now looks like this:
      
      N  ABCDEFGHIJ
      1  0000000000
      2  0000000000
      3  0000000000
      4  0000000000
      5  1111000000
      6  0000000000
      7  0000000000
      8  0000000000
      9  0000000000
      10 0000000000
      Cancel Field:
      N  ABCDEFGHIJ
      1  0000000000
      2  0000000000
      3  0000000000
      4  3333300000
      5  3333300000
      6  3333300000
      7  0000000000
      8  0000000000
      9  0000000000
      10 0000000000
      
So, in the first field 4 "0" was replaced 4 "1". So, it's our 4-Cell ship in the position. 
In the Canceled field lower, u can see a zone from A4 to E6 fully filled nummer 3. 
Canceled field show zones, where u can't placed ships (and this zones are marked as "3"). 
So, how u can see, after positioning ship on the certain place - next ship can't cross zone placed ship and zone around that ship. 
you must position every ship  in such a way that all the cells that it occupies fall into "0"
      
At the end of this stage 2 Fields will looking, for example, such way:
      
      N  ABCDEFGHIJ
      1  0111010000
      2  0000010011
      3  0010010000
      4  0000000001
      5  0111100000
      6  0000000000
      7  0000000000
      8  1001100100
      9  0000000100
      10 0000100000
      Запретное поле игрока:
      N  ABCDEFGHIJ
      1  3333333333
      2  3333333333
      3  0333333333
      4  3333333033
      5  3333330033
      6  3333330000
      7  3333333330
      8  3333333330
      9  3333333330
      10 0003333330
      
Next Stage - Game. U'll see only enemy's field. An At the begining it's looking such way:
      
      N  ABCDEFGHIJ
      1  0000000000
      2  0000000000
      3  0000000000
      4  0000000000
      5  0000000000
      6  0000000000
      7  0000000000
      8  0000000000
      9  0000000000
      10 0000000000
      
The shoot is making same way, that was descriped earlier (that place in text marked ***). When u make shoot, the coordinate, where u shooting will change:
      
      If it replaced from 0 to 3 - That's mean, u'r are missing and next shoot'll made enemy
      if it replaced from 0 to 4 - That's mean, u'r hit the ship. But! It's not destroyed yet! And u'll got additional shoot
      if it replaced from 0 to 6 - That's mean, u'r destroy the ship. Zone around ship will replace from any value to 2
      
How Computer works?
How i say earlier, computer have 2 logical blocks. First logical blocks activate, when computer need to finish off the damaged ship, other
- in another situation. Second block is activate in the begining of the game. And this block have 2 steps:
1. Generating Random Coordinates
2. Get The Value From AnaliseField, given as argument the generated coordinates. If the getting value is "3" then GoTo Step 1. 
If The Value is "0" - computer'll made shoot in that coordinates.
If the computer missed or damaged the computer, the coordinate in AnaliseField will replace from 0 to 3
If the computer destroy the ship - then all cells of a ship, and zone around ship will get value 3.
      
AnaliseField containing information about where computer can make shoot. 
It's collect all information during the game about where computer shoot, damaged of destroy computer. 
But this field also changes depending on the size of the largest ship you have not sunk yet. 
For Example, when the game begining, AnaliseField is looking SuchWay:
      
      N  ABCDEFGHIJ
      1  0333033303
      2  3033303330
      3  3303330333
      4  3330333033
      5  0333033303
      6  3033303330
      7  3303330333
      8  3330333033
      9  0333033303
      10 3033303330
      
Enemy didn't make any shoot yet, but he have already only 25 possible points for shoot (but the field contain 100 points). 
This is special sample for searching 4-cell ship. Thus, Analise Fild contain as information about where computer shoot, 
damaged of destroy computer,and this information is summed up with information from the template, 
forming a field where the computer can shoot, and where it cannot. 
Sample for 3-Cell, 2-Cell ships is different from 4-Cell Ship sample, and they contain much more points for shooting. 
So, When computer destroy 4-cell ship, the sample in analisefield is switches to 3-Cell ship sample and so on.

Well, let's get back and discuss first logical block. As i say write earlier: this block activate when computer need 
to destroy the damaged ship. This block discriped by a lot of raws of the code and it's not so easy to tell how it's
works. Shortly, block trying to make shoots around the first hit on the ship, remeber it to make this operation
for the minimum number of shots. You can look at code to see how it's works.

I play sometimes this game and win about 70-75% of the games. Maybe algoritm is not so strong, but it's pretty well, 
and quietly save felling of challenge
