---
title: Osvědčené postupy pro zápis testů jednotek
description: Přečtěte si osvědčené postupy pro zápis testů jednotek, které kvalitu kódu a odolnost pro projekty .NET Core a .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.custom: seodec18
ms.openlocfilehash: 812b89ff163c9d39a658f817495ac12616c28f6f
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836250"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a>Testování osvědčených postupů pomocí .NET Core a .NET Standard

Existuje mnoho výhod zápis testů jednotek; pomáhají s regrese, poskytují dokumentaci a usnadňují dobrý návrh. Obtížné číst a křehký jednotkové testy lze však způsobí zmatek v vašeho základu kódu. Tento článek popisuje některé osvědčené postupy týkající se návrhu testů jednotek pro projekty .NET Core a .NET Standard.

V této příručce se dozvíte některé osvědčené postupy při psaní testů jednotek se testy odolné a snadno pochopitelná.

Podle [Jan Reese](https://reese.dev) se zvláštními k [Roy Osherove](http://osherove.com/)

## <a name="why-unit-test"></a>Proč pro testování částí?

### <a name="less-time-performing-functional-tests"></a>Méně času provádění funkční testy
Funkční testy jsou nákladné. Obvykle zahrnují pouhému spuštění aplikace a provádění posloupnosti kroků, které můžete (nebo někomu jinému), musíte provést, chcete-li ověřit, že očekávané chování. Tyto kroky nemusí být vždy známá testerovi, což znamená, že budou muset kontaktovat někomu více-li hlubší znalosti v oblasti za účelem provádění testu. Vlastní testování může trvat sekund pro jednoduché změny nebo minut, než větší změny. A konečně tento proces opakuje pro každé změny provedené v systému.

Testy jednotek, na druhé straně, trvat milisekund, můžete spustit stisknutím tlačítka a nevyžadují žádnou znalost systému ve velkém. Určuje, jestli test projde nebo selže záleží nástroje test runner, ne jednotlivec.

### <a name="protection-against-regression"></a>Ochrana proti regrese
Vady regrese jsou chyby, které se zavedly při změně do aplikace. Je běžné pro testery, nejen otestovat jejich novou funkci, ale také funkce, které existovaly předem za účelem ověření, které dřív implementovaná funkce fungují i podle očekávání.

S testováním částí je možné spustit znovu vaše celou sadu testů po každém sestavení nebo dokonce i po změně řádku kódu. Díky tomu získáte jistotu, že váš nový kód nedojde k poškození stávajících funkcí.

### <a name="executable-documentation"></a>Spustitelný soubor dokumentace
Nemusí být vždy zřejmé čemu konkrétní metody nebo chování dané určité vstup. Vám může položte si otázku: Jak tato metoda chovat když překročím je prázdný řetězec? Hodnota Null?

Pokud máte sadu dobře pojmenované jednotkové testy, měli být schopni jasně vysvětlit očekávaný výstup pro daný vstup každého testu. Kromě toho by měl být schopen ověřit, že ve skutečnosti funguje.

### <a name="less-coupled-code"></a>Méně propojených kódu
Pokud kód je úzce svázány, může být obtížné testování částí. Bez vytvoření testů jednotek pro kód, který píšete, může být méně zřejmé párování.

Psaní testů pro váš kód bude přirozeně oddělit váš kód, protože by byla obtížnější testovat jinak.

## <a name="characteristics-of-a-good-unit-test"></a>Vlastnosti dobré Jednotkový test
- **Rychlé**. Není, až po zralé projekty tisícovky rozhraní testování částí. Testy jednotek by měla trvat velmi málo času spuštění. Milisekundy.
- **Izolované**. Testování částí jsou samostatný, můžete spustit v izolaci a nemají žádné závislosti na jakýkoli vnější faktory, jako je systém souborů nebo databáze.
- **Opakovatelné**. Testování částí by měl být konzistentní s jeho výsledky, to znamená, vždy vrátí stejného výsledku Pokud něco mezi spuštění nelze změnit.
- **Kontroluje se svým**. Test by měl být dokáže automaticky rozpoznat, pokud byl úspěšný, nebo bez zásahu člověka.
- **Včasné**. Testování částí, neměla by mít Neproporcionální změna dlouhou dobu pro zápis ve srovnání s testovaný kód. Pokud zjistíte testování kódu, přičemž velké množství času ve srovnání s psaní kódu, zvažte návrh, který je víc možností intenzivního testování.

## <a name="lets-speak-the-same-language"></a>Můžeme mluvit stejný jazyk
Termín *napodobení* je bohužel chybná, když mluvíme o testování. Definuje následující nejběžnější typy *napodobenin* při psaní testů jednotek:

*Falešné* – phishing je obecný termín, který slouží k popisu zástupnou proceduru nebo mock objektu. Zda je zástupná procedura nebo model závisí na kontextu, ve kterém se používá. Tak jinými slovy, phishing může být zástupnou proceduru nebo model.

*Napodobení* -mock objektu je objekt falešné v systému, která určuje, zda má testování částí úspěšný nebo neúspěšný. Model vychází phishing dokud je uplatněna proti.

*Zástupná procedura* -zástupná procedura představuje může ovládat nahrazení existujícího závislosti (nebo spolupracovníka) v systému. Pomocí zástupné procedury můžete otestovat váš kód se schématy závislost přímo. Ve výchozím nastavení phishing začíná jako zástupná procedura.

Vezměte v úvahu následující fragment kódu:

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

To může být příklad zástupné procedury jsou označovány jako model. V takovém případě je zástupná procedura. Už se v pořadí, jako prostředky, abyste mohli vytvořit instanci jen předání `Purchase` (testovaného systému). Název `MockOrder` je také velmi matoucí, protože znovu, pořadí, není model.

Lepším řešením by

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Při přejmenování třídy, která se `FakeOrder`provedené třídy mnohem více obecný, třída může sloužit jako model nebo zástupné procedury. Podle toho, co je lepší pro testovací případ. Ve výše uvedeném příkladu `FakeOrder` slouží jako zástupné procedury. Nepoužíváte `FakeOrder` v libovolné formě během vyhodnocení. `FakeOrder` právě se předal `Purchase` vyhovět jejich požadavkům konstruktoru třídy.

Pokud chcete použít ho jako model, to můžeme asi takhle nějak.

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

V takovém případě se kontroluje vlastnosti phishing (uplatnění u ní), takže ve výše uvedeném fragmentu kódu `mockOrder` je model.

> [!IMPORTANT]
> Je důležité získat Tato terminologie správné. Při volání vaše zástupné procedury "mocks", jinými vývojáři se chystáte vytvořit false předpoklady o vašich představ.

Hlavní mít na paměti mocks oproti zástupné procedury je, že mocks jsou stejné jako zástupné procedury, ale vyhodnocení proti mock objektu, že není kontrolní výraz proti zástupnou proceduru.

## <a name="best-practices"></a>Osvědčené postupy

### <a name="naming-your-tests"></a>Názvy testů
Název testu by měla obsahovat tři části:
- Název metody testování.
- Scénář, ve které je právě testováno.
- Očekávané chování při vyvolání scénář.

#### <a name="why"></a>Proč?
- Standardy pro vytváření názvů jsou důležité, protože explicitně vyjadřují záměr testu.

Testy se více než jen zajistit váš kód funguje, také poskytují dokumentaci. Jenom podle sady testů jednotek, je třeba možnost odvodit chování kódu bez i postupného prohlížení samotný kód. Navíc když dojde k selhání testů, zobrazí se přesně scénáře, které nebudou vyhovovat vašim požadavkům.

#### <a name="bad"></a>Špatné:
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>Uspořádání testů
**Uspořádat, fungovat, vyhodnocení** je běžný vzor při testování částí. Jak již název napovídá, se skládá ze tří hlavních akcí:
- *Uspořádat* objektů, vytváření a jejich nastavení podle potřeby.
- *ACT* na objekt.
- *Assert –* , který je podle očekávání.

#### <a name="why"></a>Proč?
- Jasně odděluje, co je právě testováno z *uspořádat* a *vyhodnocení* kroky.
- Menší pravděpodobnost kombinovat výrazy s kódem "Akce".

Čitelnost je jedním z nejdůležitějších aspektů při psaní testu. Každá z těchto akcí v rámci testu oddělení jasně zvýrazněte závislosti, které vyžaduje pro volání kódu, jak se váš kód volá a co se snažíte uplatnit. Může být možné kombinovat několik kroků a zmenšete velikost vašeho testu, primární cílem je čitelnost test co nejrychleji.

#### <a name="bad"></a>Špatné:
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>Zápis minimálně předávání testů
Vstup pro použití v testu jednotek by měl být nejjednodušší možný ověří chování, které právě testujete.

#### <a name="why"></a>Proč?
- Testy se stanou odolnější vůči budoucím změnám v základu kódu.
- Blíže k testování chování nad implementací.

Testy, které obsahují další informace, než se požaduje projde testem mají vyšší riziko zavlečení chyby do testu a mohl provádět záměr testovacího méně jasné. Při psaní testů chcete zaměřit na chování. Nastavení dalších vlastností u modelů nebo pomocí nenulové hodnoty, pokud není vyžadována, pouze nesnižuje co se pokoušíte prokázat, že.

#### <a name="bad"></a>Špatné:
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>Vyhněte se magic řetězce
Názvy proměnných v jednotce testů je jako důležité, pokud není mnohem důležitější než názvů proměnných v produkčním kódu. Testy jednotek by neměla obsahovat magic řetězce.

#### <a name="why"></a>Proč?
- Zabraňuje potřebu čtecí modul testu ke kontrole produkčního kódu. Pokud chcete zjistit, co dělá hodnota speciální.
- Explicitně ukazuje, co se pokoušíte *prokázat* namísto pokusu o *dosáhnout*.

Magický řetězce může způsobit zmatení čtečku testy. Pokud řetězec vypadá neobvyklého, mohou divit, proč byla vybrána určitou hodnotu pro parametr nebo návratovou hodnotu. Může to vést je se na ně podívat podrobnosti implementace, místo zaměření na test.

> [!TIP] 
> Při psaní testů, bychom se měli snažit co nejvíce záměr nejvíce express. V případě magic řetězce je dobrý přístup přiřadit tyto hodnoty konstant.

#### <a name="bad"></a>Špatné:
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>Vyhněte se logika v testech
Při zápisu jednotky testů Vyhněte se řetězení řetězců ruční a logické podmínky, jako například `if`, `while`, `for`, `switch`atd.

#### <a name="why"></a>Proč?
- Menší pravděpodobnost zavést chybu v rámci testů.
- Zaměřte se na konečný výsledek, spíše než podrobnosti implementace.

Když zavádíte logiky do testovací sady, výrazně zvyšuje riziko zavlečení chybu do něj. Poslední místo, které chcete najít chybu se do testovací sady. Byste měli mít vysoký stupeň spolehnout, že testy pracovat, jinak jim nebude důvěřovat. Testy, které nepovažujete za důvěryhodný, se neposkytuje žádnou hodnotu. Pokud test selže, budete chtít mít pocit, že je ve skutečnosti chyba s kódem a že nelze ignorovat.

> [!TIP]
> Logika v testu zdá se, že nevyhnutelné, vezměte v úvahu test rozdělení do dvou nebo více různých testy.

#### <a name="bad"></a>Špatné:
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>Preferovat pomocné metody pro nastavení a jejich vyřazování z provozu
Pokud požadujete podobných objektu nebo stav testů, raději metodu helper než využitím atributy instalační program a jejich vyřazování z provozu, pokud existují.

#### <a name="why"></a>Proč?
- Méně nedorozumění při čtení testů od veškerý kód je viditelná z v rámci každého testu.
- Menší pravděpodobnost, že nastavení příliš mnoho nebo příliš málo pro daný test.
- Menší riziko sdílení stavu mezi testů, které vytvoří nechtěné závislosti mezi nimi.

V jednotce testování rozhraní, `Setup` je volána před testováním jednotky každého v rámci vaší sady testů. Zatímco některé to vidí jako užitečný nástroj, obvykle ukončí si vede na opakovaném a těžko čitelný testy. Každý test obvykle má jiné požadavky zajistí test rychle zprovoznit. Bohužel `Setup` vynutí použití přesně stejné požadavky pro každý test.

> [!NOTE] 
> xUnit odebral instalační program a jejich vyřazování z provozu od verze 2.x

#### <a name="bad"></a>Špatné:
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>Vyhněte se více nepodmíněné výrazy
Při psaní testů, zkuste obsahovat jenom jeden kontrolní výraz na test. Běžné způsoby používání pouze jeden výraz patří:
- Vytvoření samostatné testu pro každý kontrolní výraz.
- Parametrizované testy použijte.

#### <a name="why"></a>Proč?
- Pokud selže jeden kontrolní výraz nebude vyhodnocen následné nepodmíněné výrazy.
- Zajišťuje, že v testech nejsou uplatnění více případů.
- Poskytuje celého obrázku, proč jsou neúspěšné testy. 

Při zavedení více nepodmíněné výrazy do testovacího případu, to není zaručeno, že všechny aplikace nepodmíněné výrazy se provést. Ve většině rozhraní testování částí jakmile kontrolní výraz selže v testování částí, řízení testy jsou automaticky považovány za docházet k selháním. To může být matoucí, tak, jak funkce, které skutečně funguje, bude zobrazovat jako selhání.

> [!NOTE]
> Běžné výjimky tohoto pravidla je po uplatnění proti objektu. V takovém případě je obecně přijatelné mít více nepodmíněné výrazy pro každou vlastnost zajistit objekt je ve stavu, který očekáváte, že bude v.

#### <a name="bad"></a>Špatné:
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>Lepší:
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>Ověření privátní metody testování veřejné metody jednotky
Ve většině případů by neměl být potřeba testovat privátní metodu. Privátní metody jsou podrobnosti implementace. Můžete si ho představit tímto způsobem: privátní metody nikdy existovat v izolaci. V určitém okamžiku se chystají se protilehlé veřejnou metodu, která volá metodu privátní jako součást jeho implementace. By měl postaral o je konečný výsledek veřejnou metodu, která volá do privátní objektu. 

Zvažte následující případ

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = trimInput(input);
    return sanitizedInput;
}

private string trimInput(string input)
{
    return input.Trim();
}
```

Aby vám začali psát test může být první reakci `trimInput` proto, abyste měli jistotu, že metoda funguje podle očekávání. Je však šíři, který `ParseLogLine` manipuluje `sanitizedInput` takovým způsobem, který nepočítáte, testují splnění vykreslování `trimInput` zbytečné. 

Skutečný test by mělo být provedeno proti veřejnou metodu protilehlé `ParseLogLine` protože to je, co vám by nakonec záleží. 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

Pomocí této základní vlastností viru Pokud se zobrazí privátní metodu, Najít veřejnou metodu a zápis testování proti dané metody. Pouze z důvodu privátní metoda vrátí očekávaný výsledek, neznamená, že systém, který nakonec volá metodu privátní používá výsledek správně.

### <a name="stub-static-references"></a>Zástupná procedura statických odkazů.
Jedním z principů testování částí je, že musí mít úplnou kontrolu nad testovaného systému. To může být problematické, pokud je produkční kód obsahuje volání statických odkazů (třeba `DateTime.Now`). Uvažujme následující kód

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

Jak tento kód může být lze testování částí? Zkuste přístup, jako

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

Bohužel se rychle dobré si uvědomit, že existuje několik problémů s testy. 

- Pokud sadu testů je spuštěn úterý, druhý test bude úspěšný, ale první test se nezdaří.
- Pokud sadu testů je spuštěn na libovolný den, bude první test úspěšný, ale druhý test se nezdaří.

K řešení těchto problémů, je potřeba zavést *švu* do produkčního kódu. Jedním z přístupů je zabalit kód, který je potřeba řídit v rozhraní a produkční kód závisí na tomto rozhraní.

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

Teď bude vaše testovací sada

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

Nyní sada testů má plnou kontrolu nad `DateTime.Now` a můžete se zakázaným inzerováním libovolnou hodnotu při volání do metody.
