Jane Vrangeloski 171188

Ciklicna kompleksnost na grafot  e 10
## Control Flow Graph for `checkCart`

![CFG Diagram](images/CFG.png)


За да се постигне Every Statement критериумот, минималниот број на тест случаи е 2.
Тест случај 1:

    allItems: new ArrayList<Item>() (празна листа)
    cardNumber: "1234567890123456" (валиден број на картичка)

Очекуван резултат: 0.0 

Овој тест случај ги активира следниве изјави:

    if (allItems == null): Проверува дека allItems не е null.
    double sum = 0;: Ја иницијализира сумата.
    for (int i = 0; i < allItems.size(); i++): Влегува во for циклусот, но бидејќи allItems е празен, циклусот веднаш завршува.
    if (cardNumber != null && cardNumber.length() == 16): Проверува дали cardNumber е валиден.
    String allowed = "0123456789";
    char[] chars = cardNumber.toCharArray();
    for (int j = 0; j < cardNumber.length(); j++): Влегува во циклусот за проверка на карактери на картичката.
    char c = cardNumber.charAt(j);
    if (allowed.indexOf(c) == -1): Проверува дали карактерот е валиден.
    return sum;: Враќа 0.0.

Овој тест случај покрива голем дел од кодот, вклучувајќи ги почетните проверки и целосната валидација на бројот на картичката
Тест случај 2:

    allItems: Листа со следниве Item објекти:
        Item 1: name="Laptop", price=1200.0, discount=0.1, quantity=1 (активира попуст)
        Item 2: name="Mouse", price=25.0, discount=0.0, quantity=2 (без попуст)
        Item 3: name="Keyboard", price=350.0, discount=0.0, quantity=1 (цена > 300, активира sum -= 30)
    cardNumber: "1234567890123456" (валиден број на картичка)

Пресметка:

    Item 1: 1200∗(1−0.1)∗1=1080.0
    Item 2: 25∗2=50.0
    Item 3: 350∗1=350.0 (има 350>300, па sum -= 30)
    Вкупна сума: 1080.0+50.0+350.0−30.0=1450.0

Овој тест случај, во комбинација со првиот, ќе ги активира сите преостанати изјави:

