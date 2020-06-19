---
title: Osvědčené postupy pro zápis testů jednotek
description: Naučte se osvědčené postupy pro psaní testů jednotek, které zajišťují kvalitu kódu a odolnost pro projekty .NET Core a .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 9115ff69b269e3723820fd8505d1a9f8ca278d12
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989370"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a>Osvědčené postupy testování částí pomocí .NET Core a .NET Standard

Při psaní testů jednotek je k dispozici mnoho výhod. pomáhají s regresí, poskytovat dokumentaci a usnadnit dobrý návrh. Nicméně těžko čitelný a poměrně křehký testování částí může wreak zmatek na vašem základu kódu. Tento článek popisuje některé osvědčené postupy týkající se návrhu testování částí pro projekty .NET Core a .NET Standard.

V této příručce se dozvíte, jaké jsou osvědčené postupy při psaní testů jednotek pro zajištění odolnosti vašich testů a jejich snadné pochopení.

Od [Jan Reese](https://reese.dev) se speciálním poděkováním [Roy Osherove](https://osherove.com/)

## <a name="why-unit-test"></a>Proč testování částí?

### <a name="less-time-performing-functional-tests"></a>Méně času provádění funkčních testů
Funkční testy jsou nákladné. Obvykle zahrnují otevření aplikace a provedení posloupnosti kroků (nebo někoho jiného), které je nutné provést, aby bylo možné ověřit očekávané chování. Tyto kroky nemusí být vždy známy testerovi, což znamená, že se budou muset obrátit na více znalostí v oblasti, aby bylo možné provést test. Testování může trvat několik sekund, než se u triviálních změn nebo minut pro větší změny. Nakonec je třeba tento proces opakovat pro každou změnu, kterou v systému provedete.

Testování částí na druhé straně může trvat milisekundy, které je možné spustit při stisknutí tlačítka a nemusí nutně vyžadovat, aby byly v systému velké znalosti. Bez ohledu na to, zda test projde nebo se nezdařil, je až do nástroje Test Runner, nikoli z jednotlivce.

### <a name="protection-against-regression"></a>Ochrana před regresí
Chyby regrese jsou chyby, které jsou představeny, když je provedena změna aplikace. Pro testery je běžné, že netestují pouze své nové funkce, ale také funkce, které existovaly předem, aby bylo možné ověřit, že dříve implementované funkce stále fungují podle očekávání.

Při testování částí je možné znovu spustit celou sadu testů po každém sestavení nebo dokonce i po změně řádku kódu. Máte jistotu, že nový kód neruší existující funkce.

### <a name="executable-documentation"></a>Dokumentace ke spustitelnému souboru
Nemusí vždy být zřejmé, co konkrétní metoda dělá nebo jak se chová podle určitého vstupu. Můžete se zeptat sami: jak se tato metoda chová, když ji předáte do prázdného řetězce? Platnost?

Máte-li sadu dobře pojmenovaných testů jednotek, každý test by měl být schopný jasně vysvětlit očekávaný výstup pro daný vstup. Kromě toho by měl být schopný ověřit, zda skutečně funguje.

### <a name="less-coupled-code"></a>Méně spojený kód
Když je kód pevně spojený, může být obtížné testování částí. Bez vytváření testů jednotek pro kód, který zapisujete, může být spojení neviditelné.

Zápis testů pro váš kód bude přirozeně oddělit váš kód, protože by bylo obtížnější ho testovat jinak.

## <a name="characteristics-of-a-good-unit-test"></a>Charakteristiky dobrého testu jednotek

- **Rychle**. Pro vyspělé projekty nemusíte mít k dispozici tisíce testů jednotek. Spuštění testů jednotek by mělo trvat velmi málo času. Milisekund.
- **Izolované**. Jednotkové testy jsou samostatné, můžou být spouštěny izolovaně a nesmí mít žádné závislosti na žádných jiných faktorech, jako je třeba systém souborů nebo databáze.
- **Opakuje**se. Spuštění testu jednotky by mělo být konzistentní s jeho výsledky, to znamená, že vždy vrátí stejný výsledek, pokud neměníte cokoli v průběhu spuštění.
- **Automatická kontrola**. Test by měl být schopný automaticky zjistit, jestli byl úspěšný nebo neúspěšný, bez jakékoli lidské interakce.
- **Včas**. Testování částí by nemělo mít v porovnání s testovaným kódem neúměrně dlouhou dobu. Pokud najdete testování kódu, které trvá v porovnání s psaním kódu velké množství času, zvažte návrh, který je více testovatelné.

## <a name="code-coverage"></a>Pokrytí kódu

Vysoké procento pokrytí kódu je často spojeno s vyšší kvalitou kódu. Měření samotné ale *nemůže* určit kvalitu kódu. Nastavení procentuálního cíle pokrytí kódu po výzvám souvisejícím může být counterproductive. Představte si složitý projekt s tisíci podmíněných větví a Představte si, že jste nastavili cíl 95% pokrytí kódu. V současné době projekt udržuje 90% pokrytí kódu. Doba, kterou bere v úvahu pro všechny hraniční případy v zbývajících 5%, by mohla být obrovským podnikem a rychle se zmenšuje její velikost.

Vysoké procento pokrytí kódu není indikátorem úspěchu, ani to neznamená vysokou kvalitu kódu. Jusst představuje množství kódu, který je pokryt jednotkovým testováním. Další informace najdete v tématu [testování rozsahu pokrytí kódu](unit-testing-code-coverage.md).

## <a name="lets-speak-the-same-language"></a>Pojďme hovořit o stejný jazyk
Při komunikaci s testováním je *Tento pojem velmi* nepoužit. Následující text definuje nejběžnější typy *napodobenin* při psaní testů jednotek:

*Napodobeniny* – napodobenina je obecný termín, který lze použít k popisu zástupné procedury nebo objektu objektu. Bez ohledu na to, jestli se jedná o zástupnou proceduru nebo objekt, závisí na kontextu, ve kterém se používá. Jinak řečeno, napodobenina může být zástupná procedura nebo maketa.

*Model* – objekt typu Object je falešným objektem v systému, který určuje, zda nebo není test jednotky úspěšný nebo neúspěšný. Napodobení se zahájí jako napodobenina, dokud není uplatněna na.

*Zástupná* procedura – zástupný kód pro existující závislost (nebo spolupracovníka) v systému je ovladatelné přístupnou náhradou. Pomocí zástupné procedury můžete testovat kód bez nutnosti pracovat přímo se závislostí. Ve výchozím nastavení se napodobenina zahájí jako zástupná procedura.

Vezměte v úvahu následující fragment kódu:

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Toto je příklad zástupné procedury, která se označuje jako objekt typu. V tomto případě se jedná o zástupnou proceduru. Právě předáváte v pořadí jako prostředek, který je možné vytvořit `Purchase` (testovaný systém). Název `MockOrder` je také velmi zavádějící, protože znovu není v pořádku.

Lepší přístup by byl

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Přejmenováním třídy na `FakeOrder` , jste vytvořili třídu a mnohem obecnější, třídu lze použít jako objekt typu nebo jako zástupnou proceduru. Podle toho, co je vhodnější pro testovací případ. Ve výše uvedeném příkladu `FakeOrder` se používá jako zástupná procedura. Nepoužíváte ho `FakeOrder` v žádném tvaru nebo formuláři během kontrolního výrazu. `FakeOrder`byla právě předána do `Purchase` třídy, aby splňovala požadavky konstruktoru.

Pokud ho chcete použít jako objekt, může to vypadat nějak takto.

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

V tomto případě kontrolujete vlastnost s napodobeninou (pro kterou je uplatněno), takže ve výše uvedeném fragmentu kódu `mockOrder` je objekt typu.

> [!IMPORTANT]
> Je důležité získat správnou opravu této terminologie. Pokud voláte své zástupné procedury, ostatní vývojáři budou mít na záměr nepravdivé předpoklady.

Hlavním aspektem, který si zapamatujete o postupných objektech oproti zástupným procedurám, je to, že jsou jako zástupné procedury stejné jako zástupné procedury.

## <a name="best-practices"></a>Osvědčené postupy

### <a name="naming-your-tests"></a>Pojmenovávání testů
Název testu by měl sestávat ze tří částí:

- Název testované metody.
- Scénář, pod kterým se testuje.
- Očekávané chování při vyvolání scénáře.

#### <a name="why"></a>Proč?

- Standardy pojmenování jsou důležité, protože explicitně vyjadřují záměr testu.

Testy jsou více, než pouze zajištění, že váš kód funguje, ale také poskytují dokumentaci. Stejně jako při prohlížení sady jednotkových testů byste měli být schopni odvodit chování kódu bez ohledu na samotný kód. Kromě toho, když testy selžou, vidíte přesně ty scénáře, které nesplňují vaše očekávání.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>Zájmu
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>Uspořádání testů
**Uspořádat, ACT a Assert** je běžný vzor při testování částí. Jak název naznačuje, skládá se ze tří hlavních akcí:

- *Uspořádejte* své objekty, vytvářejte je a nastavte je podle potřeby.
- *Pracovat* na objektu.
- Vyhodnotit *, že* je něco podle očekávání.

#### <a name="why"></a>Proč?

- Jasně odděluje, co je testováno z kroků *uspořádání* a *vyhodnocení* .
- Možnost Intermix kontrolní výrazy s kódem Act je menší.

Čitelnost je jedním z nejdůležitějších aspektů při psaní testu. Oddělení každé z těchto akcí v rámci testu jasně zvýrazní závislosti vyžadované pro volání vašeho kódu, způsob, jakým je váš kód volán a co se snažíte uplatnit. I když může být možné zkombinovat některé kroky a zmenšit velikost testu, primárním cílem je udělat co možná čitelnou zkoušku.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>Zájmu
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>Zápis s minimálním předáním testů
Vstup, který se má použít v testu jednotek, by měl být nejjednodušší, aby bylo možné ověřit chování, které právě testujete.

#### <a name="why"></a>Proč?

- Testy jsou odolnější vůči budoucím změnám v základu kódu.
- Blíže k testovacímu chování při implementaci.

Testy, které obsahují více informací, než je nutné k předání testu, mají větší šanci na zavedení chyb do testu a může udělat záměr méně jasného záměru testu. Při psaní testů, které chcete zaměřit na chování. Nastavení zvláštních vlastností pro modely nebo použití nenulových hodnot v případě potřeby, pouze odčítání od toho, co se snažíte prokázat.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>Zájmu
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>Nepoužívejte řetězce Magic
Při pojmenování proměnných v testování částí je důležité, pokud není důležitější, než proměnné pojmenování v produkčním kódu. Testy jednotek by neměly obsahovat řetězce Magic.

#### <a name="why"></a>Proč?

- Brání nutnosti čtenářům testu zkontrolovat kód v produkčním prostředí, aby bylo možné zjistit, co dělá tuto hodnotu jako speciální.
- Explicitně ukazuje, co se snažíte *dokázat* , a ne pokusit se o jeho *provedení*.

Řetězce Magic můžou způsobit nejasnost čtenářů vašich testů. Pokud je řetězec vyhledáný běžným způsobem, může se stát, že se pro parametr nebo návratovou hodnotu vybere určitá hodnota. To může způsobit, že se podíváme na podrobnosti implementace, ale nemusíte se zaměřit na test.

> [!TIP]
> Při psaní testů byste se měli zaměřit na co nejvíc záměrů. V případě řetězců Magic je dobrým přístupem přiřadit tyto hodnoty konstantám.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>Zájmu
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>Vyhnout se logice v testech
Při psaní testů jednotek vyhnout se ručnímu zřetězení řetězců a logickým podmínkám, jako například,,, `if` `while` `for` `switch` atd.

#### <a name="why"></a>Proč?

- Menší šance na zavedení chyby uvnitř testů.
- Zaměřte se na konečný výsledek místo podrobností implementace.

Když zavedete logiku do sady testů, šance na to, že dojde k chybě, se výrazně zvyšuje. Poslední místo, kde chcete najít chybu, je v rámci sady testů. Měli byste mít vysokou úroveň spolehlivosti, kterou testy fungují, jinak je nebudete důvěřovat. Testy, kterým nedůvěřujete, nezadávají žádnou hodnotu. Pokud se test nezdaří, chcete mít smysl, že něco je ve skutečnosti chybné s vaším kódem a že jej nelze ignorovat.

> [!TIP]
> Pokud se logika v testu jeví jako nenevyhnutelná, zvažte rozdělení testu na dva nebo více různých testů.

#### <a name="bad"></a>Chybně:
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>Zájmu
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>Preferovat pomocné metody nastavení a rozboru
Pokud pro testy požadujete podobný objekt nebo stav, preferovat pomocnou metodu než využití atributů Setup a rozboru, pokud existují.

#### <a name="why"></a>Proč?

- Při čtení testů došlo k méně nejasnostem, protože veškerý kód je viditelný v rámci každého testu.
- Menší pravděpodobnost nastavení pro daný test je příliš velká nebo příliš malá.
- Menší šance na stav sdílení mezi testy, které mezi nimi vytváří nežádoucí závislosti.

V rozhraních testování částí `Setup` je volána před každou a každou jednotkovou zkouškou v rámci sady testů. I když se některý z nich může zobrazit jako užitečný nástroj, obvykle končí na bloated a těžko čte testy. Každý test bude mít k dispozici různé požadavky, aby bylo možné spustit test a začít. Bohužel `Setup` vynutí, abyste pro každý test používali přesně stejné požadavky.

> [!NOTE]
> xUnit odebral SetUp i rozboru od verze 2. x

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>Zájmu
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>Vyhněte se několika kontrolním výrazům
Při psaní testů se pokuste zahrnout pouze jeden kontrolní výraz na test. Mezi běžné přístupy k použití pouze jednoho vyhodnocení patří:

- Vytvořte samostatný test pro každý kontrolní výraz.
- Použijte parametrizované testy.

#### <a name="why"></a>Proč?

- Pokud jeden kontrolní výraz selže, následné kontrolní výrazy nebudou vyhodnoceny.
- Zajistíte, že ve svých testech neuplatňujete více případů.
- Poskytuje celý obrázek jako důvod selhání testů.

Při zavedení více kontrolních výrazů do testovacího případu není zaručeno, že budou provedeny všechny kontrolní výrazy. Ve většině rozhraních testování částí se po selhání kontrolního výrazu v testu jednotky automaticky považují testy pokračování za neúspěšné. To může být matoucí, protože funkce, které skutečně fungují, se budou zobrazovat jako neúspěšné.

> [!NOTE]
> Běžnou výjimkou z tohoto pravidla je při uplatnění na objekt. V tomto případě je všeobecně přijatelné mít více kontrolních výrazů proti každé vlastnosti, aby bylo zajištěno, že objekt je ve stavu, ve kterém očekáváte.

#### <a name="bad"></a>Chybně:
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>Zájmu
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>Ověřit soukromé metody pomocí veřejných metod testování částí
Ve většině případů by nemělo být nutné testovat soukromou metodu. Soukromé metody jsou podrobné informace o implementaci. Tímto způsobem si můžete představit: soukromé metody nikdy neexistují v izolaci. V určitém okamžiku se jedná o veřejnou metodu, která volá soukromou metodu jako součást její implementace. To, co byste měli dbát, je konečný výsledek veřejné metody, která volá do privátního.

Vezměte v úvahu následující případ:

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

První reakce může být začít psát test pro `TrimInput` , protože chcete zajistit, aby metoda fungovala podle očekávání. Je však možné, že je zcela možné `ParseLogLine` manipulovat `sanitizedInput` takovým způsobem, že neočekáváte, vygenerování testu proti nevýhodám `TrimInput` .

Skutečný test by měl být proveden proti veřejné metodě `ParseLogLine` , protože to je to, co byste měli v konečném případě zajímat.

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

S tímto pohledem, pokud vidíte soukromou metodu, vyhledejte veřejnou metodu a zapište testy proti této metodě. Vzhledem k tomu, že soukromá metoda vrátí očekávaný výsledek, neznamená to, že systém, který nakonec volá privátní metodu, používá výsledek správně.

### <a name="stub-static-references"></a>Statické odkazy na zástupné procedury
Jedním ze zásad testování částí je, že musí mít plnou kontrolu nad testovaným systémem. To může být problematické, pokud výrobní kód zahrnuje volání statických odkazů (např. `DateTime.Now` ). Vezměte v úvahu následující kód:

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

Jak může být tento kód testován jednotkou? Můžete vyzkoušet přístup jako

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

Bohužel rychle zjistíte, že existuje několik problémů s vašimi testy.

- Pokud je testovací sada spuštěna v úterý, druhý test projde, ale první test se nezdaří.
- Pokud je testovací sada spuštěna v jakémkoli jiném dni, bude první test úspěšný, ale druhý test selže.

Chcete-li tyto problémy vyřešit, budete muset uvést do svého produkčního kódu *spojku* . Jedním z možností je zabalit kód, který je třeba ovládat v rozhraní a mít kód produkčního prostředí závislý na tomto rozhraní.

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

Vaše sada testů se teď bude

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

Sada testů nyní má úplnou kontrolu nad `DateTime.Now` a může při volání metody do této metody zástupné procedury jakékoli hodnoty.
