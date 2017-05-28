1.	Опис на апликацијата: Апликацијата што ја развивме е едноставна 10 минутна игра за деца. Играта содржи различни објекти кои паѓаат и играч (херој), кој ги собира објектите, при што некои објекти носат поени, некои одземаат живот, а некои му даваат нов живот на играчот.

2.	Упатство за користење:

    2.1.	Нова игра
   
    <img width="830" alt="newgame" src="https://cloud.githubusercontent.com/assets/29012477/26529946/42e45d10-43cb-11e7-8563-58bb584616de.png">
 
 
     На почетокот на играта се отвара почетниот прозорец  на кој имаме можност да избереме нова игра(New Game), помош (Help) или приказ на најдобрите резултати(High scores)

    2.2.	Help
    
      <img width="561" alt="help" src="https://cloud.githubusercontent.com/assets/29012477/26529961/c26a0760-43cb-11e7-87a3-d903f9c25150.png">
 
     При клик на копчето Help од почетниот прозорец, се отвара нов прозорец во кој се прикажува слика која објаснува како се игра играта и има копче Continue. При клик на Continue се отвара нова игра.

    2.3.	 High scores
 
      <img width="265" alt="highscores" src="https://cloud.githubusercontent.com/assets/29012477/26530022/608155ba-43cd-11e7-9783-1265d9007229.png">
      
      При клик на копчето High scores се отвара прозорец во кој се наоѓаат најдобрите 5 резултати на играчот подредени во опаѓачки редослед. 

    2.4.	New Game
    
      При клик на кочето New Game од почетниот прозорец се отвара нова игра. Кога ќе истече времето или играчот ќе ги загуби сите животи, резултатот се запишува во текстуалната датотека scores.txt и се прикажува нов прозорец со резултатот(Game End).
 
    <img width="501" alt="game1" src="https://cloud.githubusercontent.com/assets/29012477/26530011/28f57b08-43cd-11e7-8c58-ae8541449334.png">
    
    <img width="501" alt="game2" src="https://cloud.githubusercontent.com/assets/29012477/26530081/252b627a-43ce-11e7-8dab-b572e25a27a2.png">

 

2.4.1.	Правила на играње:
  1.	Играчот може да се движе лево, десно и да скока нагоре
  2.	Секоj собран цвет носи 1 поен
  3.	При допир со чудовиште играчот губи 1 живот
  4.	Секоја собрана ѕвезда дава 1 нов живот
  5.	Доколку играчот не ја скокне црната топка, при допир со неа губи 1 живот
  6.	На секои собрани 50 поени играчот добива 1 минута повеќе за играње
  7.	Играта завршува кога ќе истече времето кое на почетокот е 10 минути или кога играчот ќе ги изгуби сите животи
  8.	На почетокот играчот има 3 животи
* Препорачливо е играта да се игра нa цел екран (Maximized)

2.5.	Game End

   <img width="423" alt="gameover" src="https://cloud.githubusercontent.com/assets/29012477/26530104/76067892-43ce-11e7-93c3-7026c04a5639.png">
 
  Кога играта ќе заврши се отвара нов прозорец, во кој се прикажуваат поените кои ги освоил играчот. Во овој прозорец играчот има опција да избере повторно нова игра. Со затворање на овој прозорец, апликацијата се гаси.

3.	Претставување на проблемот

    3.1.	Податочни структури
  
      Податоците и функциите на играта се претставени со различни класи. Класата FallingObjects е апстрактна класа која ги претставува паѓачките објекти. Од оваа класа наследуваат класите Flower, Monster и Star кои се специфични видови на паѓачки објекти (Играта лесно може да се прошири со уште нови видови на паѓачки објетки). Класата BlackBall ги содржи податоците и функциите кои ја претставуваат црната топка, додека класата Player го претставува играчот. Во класата Scene се чуваат сите објекти кои фигурираат во играта и функциите во оваа класа ја преставуваат нивната интеракција.
  
    3.2.	Алгоритми
  
      Откако ќе се постави играта во почетната состојба, главните фукнции во кои се наоѓа логиката за интеракција меѓу објектите се наоѓаат во класата Scene. Функциите GenerateBlackBall() и MoveBlackBall() се однесуваат на генерирање и движење на црната топка, при што при секое повикување на GenerateBlackBall() веројатноста да се генерира црна топка е 1/10. Функциите AddFallingObjects() и RemoveFallingObjects() генерираат и бришат паѓачки објекти, при што при генерирање на нови објекти веројатноста да се генерира цвет или чудовиште е 49/100, а ѕвезда е 2/100. Паѓачките објекти се бришат при допир со играчот или кога ќе излезат од формата. Функцијата TouchesBlackBall(Point position) во класата Player содржи алгоритам кој проверува дали правоаголник и круг се допираат, додека пак функцијата Touches(Point position, int width, int height) во класите Star, Monster и Flower проверува дали два правоаголници се допираат. Сите функции се повикуваат во одредно време според timers во главната форма. Сите функции во класите имаат коментар кој кажува што точно прави секоја функција.

    3.3.	 GUI
  
      За претставување на секој објект се користи Bitmap од сликата која го претставува објектот и овие Bitmaps се цртаат на платното на формата.

    3.4.	 Опис на класата Player
    
      3.4.1.	Податоци

    <img width="293" alt="player" src="https://cloud.githubusercontent.com/assets/29012477/26530133/042a6fb6-43cf-11e7-9fa4-a886728ff7cf.png">
 
3.4.2.	Функции

   •	МoveLeft() - го придвижува играчот со соодветната брзина во лево, во дозволените граници
  
   •	МovеRight() - го придвижува играчот со соодветната брзина во десно, во дозволените граници
  
   •	JumpUp() - го придвижува играчот со соодветната брзина нагоре
  
   •	JumpDown() - го придвижува играчот со соодветната брзина надолу(го враќа во почетната положба)
  
   •	TouchesBlackBall(Point position) - проверува дали играчот ја допира црната топка која се наоѓа на проследената позиција( интеракција помеѓу круг и правоаголник)
  
   •	IsDead() - враќа дали бројот на животи на играчот е 0
   
   
   
   Изработиле:
   Христовска Кристина 155001
   Христовска Сандра 155006
