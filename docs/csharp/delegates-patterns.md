---
title: Obecné vzory pro delegáty
description: Další informace o běžných vzorů pro použití delegátů v kódu, aby silné párování mezi komponentami vaší.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: ea0e0b7af361b76c4b46b0a180e07b44c1fa07e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095695"
---
# <a name="common-patterns-for-delegates"></a>Obecné vzory pro delegáty

[Předchozí](delegates-strongly-typed.md)

Delegáti poskytují mechanismus, který umožňuje software návrhů týkajících se minimální párování mezi komponentami.

Jedním z příkladů vynikající pro tento druh návrhu je LINQ. Vzor výrazu dotazu LINQ spoléhá na delegáty pro všechny jeho funkce. Vezměte v úvahu tomto jednoduchém příkladu:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Tím se vyfiltrují posloupnost čísel pouze ty menší než hodnota 10.
`Where` Metoda používá delegáta, který určuje, které prvky pořadí předání filtru. Když vytvoříte dotaz LINQ, je třeba zadat implementace delegáta pro tento konkrétní účel.

Prototyp, kde Metoda je:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

V tomto příkladu se opakuje se všechny metody, které jsou součástí LINQ. Všechny spoléhají na delegáty pro kód, který spravuje konkrétní dotaz. Tento vzor návrhu rozhraní API je velmi efektivní informace a pochopení.

Tento jednoduchý příklad ukazuje, jak delegáti vyžadovat velmi málo párování mezi komponentami. Není nutné vytvořit třídu, která je odvozena z určité základní třídy. Není nutné provádět konkrétní rozhraní.
Jediným požadavkem je k dispozici implementace metod, které je zásadní pro daný úkol.

## <a name="building-your-own-components-with-delegates"></a>Vytváření vlastních komponent pomocí delegátů

Vytvořme v tomto příkladu tak, že vytvoříte komponenty pomocí návrh, který závisí na delegáty.

Umožňuje definovat komponentu, která se dá použít pro zprávy protokolu v rozsáhlém systému. Knihovna komponent lze použít v mnoha různých prostředích na více různých platformách. Existuje mnoho běžných funkcí v komponentě, která spravuje protokoly. Bude je nutné přijmout zprávy z libovolné součásti v systému. Tyto zprávy budou mít různé priority, které můžete spravovat součásti core. Zprávy by měl mít časové razítko v jejich poslední archivované formuláře. Pro pokročilejší scénáře může filtrovat zprávy zdrojovou součástí.

Existuje jeden aspekt funkce, která se často změní: kde zprávy prošly. V některých prostředích může být zapsána do konzoly chyby. V jiných případech souboru. Další možnosti zahrnují úložiště databáze, protokoly událostí operačního systému nebo jiné úložiště dokumentů.

Existují také kombinace různých typů výstup, který může použít v různých scénářích. Můžete chtít zápis zpráv do konzoly a do souboru.

Architekturu založenou na delegáty se poskytují velkou flexibilitu a usnadňují Podpora úložiště mechanismy, které lze přidat v budoucnosti.

U tohoto návrhu může být primární protokolu součásti nevirtuální, dokonce i zapečetěné třídy. Můžete připojit v žádné sadě delegátů k zápisu zprávy do různých úložných médií. Integrované podpory pro vícesměroví delegáti usnadňuje podporu scénáře, ve kterém musí být zprávy zapisovány do víc umístění (soubor a konzoly).

## <a name="a-first-implementation"></a>První provedení

Pojďme začít v malém: počáteční implementace bude přijímat nové zprávy a zapíše je použití žádné připojené delegáta. Můžete začít s jeden delegáta, který zapisuje zprávy do konzoly.

[!code-csharp[LoggerImplementation](../../samples/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

Statická třída výše je nejjednodušší věcí, které může fungovat. Musíme napsat jednu implementaci pro metodu, která zapisuje zprávy do konzoly: 

[!code-csharp[LogToConsole](../../samples/csharp/delegates-and-events/Program.cs#LogToConsole "A Console logger.")]

Nakonec je třeba připojení delegáta pomocí připojení k WriteMessage delegáta deklarovaného v protokolovacího nástroje:

[!code-csharp[ConnectDelegate](../../samples/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Postupy

Naše ukázka zatím je docela jednoduché, ale stále ukazuje některé důležité pokyny pro návrhů týkajících se delegátů.

Použití delegáta typy definované v rámci jádra usnadňuje uživatelům pracovat s delegáty. Není nutné definovat nové typy a není potřeba další typy delegátů nové, specializované vývojářům, kteří používají knihovny.

Rozhraní používá se jako minimální a je to možné nejpružnější: Pokud chcete vytvořit nový protokolovací nástroj výstupu, musíte vytvořit jednu metodu. Tato metoda může být statickou metodu nebo metodu instance. Může mít přístup.

## <a name="formatting-output"></a>Formátování výstupu

Vytvoříme tato první verze bit robustnější a poté spusťte vytváření jiných mechanismů protokolování.

V dalším kroku přidáme několik argumentů `LogMessage()` metodu tak, aby vaše třída protokolu vytváří více strukturovaných zprávy:

[!code-csharp[Severity](../../samples/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

V dalším kroku vytvoříme využívání, která `Severity` výstupní argument pro filtrování zpráv, které se odesílají do protokolu. 

[!code-csharp[FinalLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Postupy

Protokolování infrastruktury jsme přidali nové funkce. Protože komponenta protokolovacího nástroje je velmi volně propojené na každý použitý mechanizmus výstupu a je možné přidat tyto nové funkce bez jakéhokoli dopadu na kód implementace delegáta protokolovacího nástroje.

Jak vám pokračujte v sestavování to, uvidíte Další příklady, jak tento volné párování umožňuje větší flexibilitu při aktualizaci části webu bez uložení změn do jiných umístění. Ve skutečnosti ve větší aplikace, třídy výstupu protokolovacího nástroje může být v jiném sestavení a dokonce ani je třeba znovu sestavit.

## <a name="building-a-second-output-engine"></a>Druhý modul výstupu sestavení

Součást protokolu pochází spolu dobře. Přidejme jeden další modul výstupu, který zaznamenává zprávy do souboru. Bude jím zapojí o něco víc modul výstupu. Je třída, která zapouzdřuje operací se soubory a zajišťuje, že soubor je vždy uzavřen, po každém zápisu. Který zajistí, že všechna data vyprazdňuje na disk po vygenerování každé zprávy.

Tady je tento soubor na základě protokolovacího nástroje:

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Po vytvoření této třídy, můžete vytvořit jeho instanci a připojování jeho LogMessage – metoda komponenta protokolovacího nástroje:

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Tyto dvě se vzájemně nevylučují. Můžete připojit obě metody protokolu a vygenerování zprávy do konzoly a do souboru:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

Později dokonce i ve stejné aplikaci, můžete odebrat jeden delegátů bez problémů v systému:

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a>Postupy

Nyní že jste přidali Druhá obslužná rutina výstup pro protokolování subsystémů.
Tohle vyžaduje trochu další infrastrukturu pro podporu správně systému souborů. Delegát je metoda instance. Je také privátní metodu.
Není nutné většího usnadnění, protože infrastruktura delegáta se můžete připojit delegáty.

Za druhé návrh delegáta umožňuje více metod výstupu bez nějaký zvláštní kód. Není nutné žádnou další infrastrukturu pro podporu více metod výstupu sestavení. Jednoduše stanou jinou metodu na seznamu vyvolání.

Věnujte zvláštní pozornost kód v souboru protokolování metoda výstupu. Ujistěte se, že nevyvolá žádné výjimky je kódován. Když to není vždy nezbytně nutné, je vhodné. Pokud některou z metod delegáta vyvolá výjimku, nebude vyvolána zbývající delegáty, které jsou pro vyvolání.

Jako poslední Poznámka protokolovacího nástroje souboru musí spravovat její prostředky otevírání a zavírání souboru v každé zprávě protokolu. Můžete se rozhodnout ho nechat otevřené a implementovat rozhraní IDisposable a zavřete soubor, když se dokončí.
Některé z metod má své výhody a nevýhody. Obě vytváří o trochu výkonnější párování mezi třídami.

Žádný kód ve třídě protokolovací nástroj se musel být aktualizované kvůli podpoře obou scénářích.

## <a name="handling-null-delegates"></a>Zpracování Null delegátů

A konečně můžeme aktualizovat LogMessage – metoda tak, aby je robustní pro případy, pokud žádný výstup mechanismus, který je vybrána. Aktuální implementace vyvolá výjimku `NullReferenceException` při `WriteMessage` delegát nemá seznam vyvolání připojen.
Návrh, který při byly připojeny žádné metody tiše pokračovat možná dáte přednost. Je to snadné použití null podmíněného operátoru v kombinaci s `Delegate.Invoke()` metody:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Podmíněný operátor s hodnotou null (`?.`) při zkratům levý operand (`WriteMessage` v tomto případě) má hodnotu null, což znamená, že k zaznamenání zprávy nejsou provedeny žádné pokusy.

Nebude `Invoke()` metody uvedené v dokumentaci k `System.Delegate` nebo `System.MulticastDelegate`. Kompilátor generuje bezpečnost typů `Invoke` typ deklarovat delegáta metodu pro všechny. V tomto příkladu to znamená, že `Invoke` přebírá jediný `string` argument, a má typ vrácené hodnoty void.

## <a name="summary-of-practices"></a>Přehled postupů

Už víte, začátku protokolu komponentu, která by mohla být rozšířena s další uživatelé vytvářející obsah a další funkce. Pomocí delegátů v návrhu jsou velmi volně propojené těchto různých komponent. To poskytuje několik výhod. Je velmi snadné vytvořit nový výstup mechanismy a připojte je k systému. Tyto mechanismy stačí jenom jedna metoda: metoda, která zapíše zprávu protokolu. Je návrh, který je velmi odolné, když se přidají nové funkce. Smlouva vyžaduje se pro všechny zapisovače je implementovat jednu metodu. Tato metoda může být statickou metodu nebo metodu instance. To může být veřejný, privátní nebo jiné právní přístup.

Třída protokolovacího nástroje mohli libovolný počet rozšíření nebo změny bez vnášení nejnovější změny. Stejně jako všechny třídy nelze upravit veřejné rozhraní API bez riziko rozbíjející změny. Ale protože párování mezi protokolovací nástroj a všechny moduly pro výstup je pouze prostřednictvím delegáta, necháváte žádné jiné typy (jako je rozhraní nebo základní třídy). Vazba je co nejmenší.

[Next](events-overview.md)
