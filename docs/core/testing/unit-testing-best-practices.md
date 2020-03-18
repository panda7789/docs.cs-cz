---
title: Doporučené postupy pro psaní testů částí
description: Seznamte se s osvědčenými postupy pro psaní testů částí, které pohánějí kvalitu a odolnost kódu pro projekty .NET Core a .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 586373381bcb18384cbf29bb2ca2bd220a2b2d3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240958"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a>Doporučené postupy testování částí pomocí rozhraní .NET Core a .NET Standard

Existuje mnoho výhod pro psaní testů částí; pomáhají s regresí, poskytují dokumentaci a usnadňují dobrý design. Však těžko čitelné a křehké testy částí může způsobit zmatek na základu kódu. Tento článek popisuje některé osvědčené postupy týkající se návrhu testování částí pro projekty .NET Core a .NET Standard.

V této příručce se dozvíte některé osvědčené postupy při psaní testů částí, aby vaše testy odolné a snadno pochopitelné.

[John Reese](https://reese.dev) se zvláštním poděkováním [Roy Osherove](https://osherove.com/)

## <a name="why-unit-test"></a>Proč jednotkový test?

### <a name="less-time-performing-functional-tests"></a>Méně času při provádění funkčních testů
Funkční testy jsou drahé. Obvykle zahrnují otevření aplikace a provedení řady kroků, které musíte (nebo někdo jiný) provést, abyste ověřili očekávané chování. Tyto kroky nemusí být vždy známy testerovi, což znamená, že budou muset oslovit někoho, kdo je v této oblasti znalější, aby mohl provést test. Testování samo o sobě může trvat několik sekund pro triviální změny nebo minuty pro větší změny. A konečně, tento proces musí být opakován pro každou změnu, kterou provedete v systému.

Jednotkové testy, na druhé straně trvat milisekundy, lze spustit stisknutím tlačítka a nemusí nutně vyžadovat žádné znalosti systému jako celku. Zda test projde nebo neselže, je na testovacím běžci, ne na jednotlivci.

### <a name="protection-against-regression"></a>Ochrana proti regresi
Regresní vady jsou vady, které jsou zavedeny při změně aplikace. Je běžné, že testeři nejen otestují svou novou funkci, ale také funkce, které existovaly předem, aby ověřili, že dříve implementované funkce stále fungují podle očekávání.

S testování částí, je možné znovu spustit celou sadu testů po každém sestavení nebo dokonce po změně řádku kódu. Dává vám jistotu, že váš nový kód nepřeruší existující funkce.

### <a name="executable-documentation"></a>Spustitelná dokumentace
Nemusí být vždy zřejmé, co konkrétní metoda dělá nebo jak se chová daný vstup. Můžete se ptát sami sebe: Jak se tato metoda chová, když jí předávám prázdný řetězec? Null?

Pokud máte sadu dobře pojmenované testy částí, každý test by měl být schopen jasně vysvětlit očekávaný výstup pro daný vstup. Kromě toho by měl být schopen ověřit, že skutečně funguje.

### <a name="less-coupled-code"></a>Méně svázaný kód
Pokud je kód pevně spojen, může být obtížné jednotkový test. Bez vytváření testů částí pro kód, který píšete, může být párování méně zřejmé.

Psaní testů pro váš kód bude přirozeně oddělit váš kód, protože by bylo obtížnější otestovat jinak.

## <a name="characteristics-of-a-good-unit-test"></a>Charakteristika dobré jednotkové zkoušky

- **Rychle**. Není neobvyklé pro vyspělé projekty mít tisíce testů částí. Testy částí by mělo trvat velmi málo času ke spuštění. Milisekund.
- **Izolované**. Testy částí jsou samostatné, lze spustit izolovaně a nemají žádné závislosti na externích faktorech, jako je například systém souborů nebo databáze.
- **Opakovatelné**. Spuštění testování částí by měla být v souladu s jeho výsledky, to znamená, že vždy vrátí stejný výsledek, pokud nezměníte nic mezi spuštění.
- **Samokontroly**. Test by měl být schopen automaticky zjistit, zda prošel nebo selhal bez lidské interakce.
- **Včas**. Testování částí by nemělo trvat nepřiměřeně dlouho psát ve srovnání s testovaným kódem. Pokud zjistíte, testování kódu trvá velké množství času ve srovnání s psaní kódu, zvažte návrh, který je více testovatelné.

## <a name="lets-speak-the-same-language"></a>Mluvme stejným jazykem.
Termín *mock* je bohužel velmi zneužita, když mluví o testování. Následující definuje nejběžnější typy *padělků* při psaní testů částí:

*Fake* - Falešný je obecný termín, který lze použít k popisu buď pahýl nebo mock objektu. Zda se jedná o zástupný kód nebo mock, závisí na kontextu, ve kterém se používá. Takže jinými slovy, padělek může být pahýl nebo výsměch.

*Mock* - Mock objekt je falešný objekt v systému, který určuje, zda test jednotky prošel nebo se nezdařilo. Výsměch začíná jako Fake, dokud není uplatněna proti.

*Se zakázaným inzerováním* – zástupný kód je kontrolovatelnou náhradou existující závislosti (nebo spolupracovníka) v systému. Pomocí se zakázaným inzerováním můžete otestovat kód bez přímého řešení závislosti. Ve výchozím nastavení začíná falešný jako pahýl.

Zvažte následující fragment kódu:

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

To by byl příklad pahýlu, který je označován jako výsměch. V tomto případě je to pahýl. Jste právě kolem pořadí jako prostředek, aby bylo možné `Purchase` vytvořit konkretizovat (testovce systému). Název `MockOrder` je také velmi zavádějící, protože opět, pořadí není výsměch.

Lepším přístupem by bylo

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Přejmenováním třídy `FakeOrder`na , jste udělali třídy mnohem obecnější, třídy lze použít jako mock nebo se zakázaným inzerováním. Podle toho, co je lepší pro testovací případ. Ve výše uvedeném příkladu se `FakeOrder` používá jako zástupný kód. Nepoužíváte `FakeOrder` v žádném tvaru nebo formě během assert. `FakeOrder`byl právě předán `Purchase` do třídy, aby splňovaly požadavky konstruktoru.

Chcete-li jej použít jako mock, můžete udělat něco takového

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

V tomto případě kontrolujete vlastnost na Fake (uplatnění proti němu), takže ve výše uvedeném fragmentu `mockOrder` kódu je Mock.

> [!IMPORTANT]
> Je důležité, aby si tuto terminologii správné. Pokud nazýváte vaše zástupné procedury "mocks", ostatní vývojáři budou dělat falešné předpoklady o vašem záměru.

Hlavní věc, kterou je třeba mít na paměti o mocks versus zástupné procedury je, že mocks jsou stejně jako zástupné procedury, ale tvrdíte proti mock objektu, zatímco vy netvrdí proti pahýl.

## <a name="best-practices"></a>Osvědčené postupy

### <a name="naming-your-tests"></a>Pojmenování testů
Název testu by se měl skládat ze tří částí:

- Název testované metody.
- Scénář, podle kterého je testován.
- Očekávané chování při vyvolání scénáře.

#### <a name="why"></a>Proč?

- Pojmenování standardy jsou důležité, protože explicitně vyjádřit záměr testu.

Testy jsou více než jen ujistěte se, že váš kód funguje, ale také poskytují dokumentaci. Jen při pohledu na sadu testů částí, měli byste být schopni odvodit chování kódu, aniž by i při pohledu na samotný kód. Navíc při selhání testů můžete přesně zobrazit scénáře, které nesplňují vaše očekávání.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>Uspořádání testů
**Uspořádat, jednat, assert** je společný vzor při testování částí. Jak název napovídá, skládá se ze tří hlavních akcí:

- *Uspořádejte* objekty, vytvářejte a nastavujte je podle potřeby.
- *Jednat* na objekt.
- *Tvrdí,* že něco je podle očekávání.

#### <a name="why"></a>Proč?

- Jasně odděluje to, co je testováno, od *kroků uspořádat* a *uplatnit.*
- Menší šance na promíchání tvrzení s kódem "Act".

Čitelnost je jedním z nejdůležitějších aspektů při psaní testu. Oddělení každé z těchto akcí v rámci testu jasně zvýraznit závislosti potřebné k volání kódu, jak je volán kód a co se pokoušíte uplatnit. I když může být možné kombinovat některé kroky a zmenšit velikost testu, primárním cílem je, aby byl test co nejčitelnější.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>Zapsat minimálně absolvování testů
Vstup, který má být použit v testování částí by měl být nejjednodušší možné za účelem ověření chování, které jsou aktuálně testování.

#### <a name="why"></a>Proč?

- Testy se stanou odolnější vůči budoucím změnám v základu kódu.
- Blíže k testování chování nad implementací.

Testy, které obsahují více informací, než je nutné projít testmají vyšší pravděpodobnost zavedení chyby do testu a může záměr testu méně jasné. Při psaní testů se chcete zaměřit na chování. Nastavení dalších vlastností u modelů nebo použití nenulových hodnot, pokud není požadováno, pouze snižuje to, co se pokoušíte prokázat.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>Vyhněte se magické struny
Pojmenování proměnných v jednotkových testech je stejně důležité, ne-li důležitější než pojmenování proměnných v produkčním kódu. Testy částí by neměly obsahovat magické řetězce.

#### <a name="why"></a>Proč?

- Zabraňuje nutnosti pro čtenáře testu zkontrolovat výrobní kód, aby zjistili, co dělá hodnotu zvláštní.
- Výslovně ukazuje, co se snažíte *dokázat,* spíše než se snaží *dosáhnout*.

Magické řetězce mohou způsobit zmatek pro čtenáře testů. Pokud řetězec vypadá neobvyklé, mohou se divit, proč byla vybrána určitá hodnota pro parametr nebo vrácenou hodnotu. To může vést k bližšímu pohledu na podrobnosti implementace, spíše než se zaměřit na test.

> [!TIP]
> Při psaní testů, měli byste se snažit vyjádřit co největší záměr, jak je to možné. V případě magických řetězců je dobrým přístupem přiřadit tyto hodnoty konstantám.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>Vyhněte se logice v testech
Při psaní testů částí se vyhněte ručnímu `if` `while`zřetězení řetězců a logickým podmínkám, jako je například , , `for` `switch`, atd.

#### <a name="why"></a>Proč?

- Menší šance na zavedení chyby uvnitř vašich testů.
- Zaměřte se na konečný výsledek, spíše než podrobnosti implementace.

Když do testovací sady zavedete logiku, šance na zavedení chyby do ní se dramaticky zvyšuje. Poslední místo, které chcete najít chybu je ve vaší testovací sadě. Měli byste mít vysokou úroveň důvěry, že vaše testy fungují, jinak jim nebudete věřit. Testy, kterým nedůvěřujete, neposkytují žádnou hodnotu. Pokud test selže, chcete mít pocit, že je něco skutečně v nepořádku s kódem a že jej nelze ignorovat.

> [!TIP]
> Pokud logika v testu se zdá nevyhnutelné, zvažte rozdělení testu do dvou nebo více různých testů.

#### <a name="bad"></a>Chybně:
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>Preferujte pomocné metody pro nastavení a stržení
Pokud požadujete podobný objekt nebo stav pro testy, raději pomocnou metodu před využitím setup a Teardown atributy, pokud existují.

#### <a name="why"></a>Proč?

- Méně nejasnosti při čtení testů, protože všechny kód je viditelný z každého testu.
- Menší šance na nastavení příliš mnoho nebo příliš málo pro daný test.
- Menší pravděpodobnost sdílení stavu mezi testy, které vytváří nežádoucí závislosti mezi nimi.

V rámci testování `Setup` částí je volána před každý test jednotky v rámci testovací sady. Zatímco někteří mohou vidět jako užitečný nástroj, to obecně skončí vedoucí k nafouklé a těžko čitelné testy. Každý test bude mít obecně různé požadavky, aby se test zprovoznit. Bohužel, `Setup` nutí vás používat přesně stejné požadavky pro každý test.

> [!NOTE]
> xUnit odebral jak SetUp, tak TearDown od verze 2.x

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>Vyhněte se více násobným nepodmíněným výrazům
Při psaní testů se pokuste zahrnout pouze jeden assert na test. Běžné přístupy k použití pouze jeden assert patří:

- Vytvořte samostatný test pro každou neplatič.
- Použijte parametrizované testy.

#### <a name="why"></a>Proč?

- Pokud jeden Assert selže, následné Asserts nebudou vyhodnoceny.
- Zajišťuje, že neuplatňujete více případů v testech.
- Dává vám celý obraz o tom, proč vaše testy selhávají.

Při zavádění více nepodmíněných výrazů do testovacího případu není zaručeno, že všechny nepodmíněných výrazů budou provedeny. Ve většině rozhraní testování částí, jakmile kontrolní výraz selže v testování částí, zkoušky řízení jsou automaticky považovány za selhání. To může být matoucí jako funkce, která je skutečně funguje, se zobrazí jako selhání.

> [!NOTE]
> Obvyklou výjimkou z tohoto pravidla je při uplatnění proti objektu. V tomto případě je obecně přijatelné mít více nepodmíněných výrazů proti každé vlastnosti, aby bylo zajištěno, že objekt je ve stavu, ve které očekáváte, že bude.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>Ověření soukromých metod pomocí testování veřejných metod testování částí
Ve většině případů by nemělo být nutné testovat soukromou metodu. Soukromé metody jsou podrobnosti implementace. Můžete si to myslet takto: soukromé metody nikdy neexistují izolovaně. V určitém okamžiku bude existovat metoda, která bude čelit veřejnosti, která volá soukromou metodu jako součást jeho implementace. Co byste měli starat o konečný výsledek veřejné metody, která volá do soukromého.

Vezměme si následující případ

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

Vaše první reakce může být začít `TrimInput` psát test, protože chcete, aby se ujistil, že metoda funguje podle očekávání. Je však zcela možné, `ParseLogLine` `sanitizedInput` že manipuluje takovým způsobem, že neočekáváte, vykreslování test proti `TrimInput` k ničemu.

Skutečný test by měl být proveden `ParseLogLine` proti veřejnosti čelí metoda, protože to je to, co byste měli nakonec záleží.

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

S tímto hlediskem, pokud vidíte soukromou metodu, najděte veřejnou metodu a napište testy proti této metodě. Jen proto, že soukromá metoda vrátí očekávaný výsledek, neznamená, že systém, který nakonec volá soukromou metodu, používá výsledek správně.

### <a name="stub-static-references"></a>Statické odkazy se zakázaným inzerováním
Jednou ze zásad jednotkové zkoušky je, že musí mít plnou kontrolu nad zkoušenou soustavou. To může být problematické, pokud výrobní kód obsahuje volání `DateTime.Now`statických odkazů (např. ). Zvažte následující kód

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

Jak může být tento kód testován na jednotku? Můžete zkusit přístup, jako je

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

Bohužel si rychle uvědomíte, že s testy máte několik problémů.

- Pokud testovací sada je spuštěna v úterý, druhý test projde, ale první test se nezdaří.
- Pokud testovací sada je spuštěna na jiný den, první test projde, ale druhý test se nezdaří.

Chcete-li tyto problémy vyřešit, budete muset zavést *šev* do produkčního kódu. Jedním z přístupů je zalomit kód, který je třeba řídit v rozhraní a mají produkční kód závisí na tomto rozhraní.

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

Testovací sada se nyní stává

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

Nyní testovací sada má `DateTime.Now` plnou kontrolu nad a můžete se zakázaným inzerováním libovolnou hodnotu při volání do metody.
