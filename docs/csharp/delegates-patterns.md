---
title: Obecné vzory pro delegáty
description: Další informace o běžných vzorcích pro použití delegátů v kódu, abyste se vyhnuli silnému spojení mezi součástmi.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 22ab88e5b139381e3a8921baa20df035f1405146
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399663"
---
# <a name="common-patterns-for-delegates"></a>Obecné vzory pro delegáty

[Předchozí](delegates-strongly-typed.md)

Delegáti poskytují mechanismus, který umožňuje návrhy softwaru zahrnující minimální párování mezi součástmi.

Jeden vynikající příklad pro tento druh designu je LINQ. Vzor výrazu dotazu LINQ závisí na delegátech pro všechny jeho funkce. Vezměme si tento jednoduchý příklad:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Tím se vyfiltruje posloupnost čísel pouze na čísla menší než hodnota 10.
Metoda `Where` používá delegáta, který určuje, které prvky sekvence předat filtr. Při vytváření dotazu LINQ zadáte implementaci delegáta pro tento konkrétní účel.

Prototyp metody Kde je:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

Tento příklad se opakuje se všemi metodami, které jsou součástí LINQ. Všechny spoléhají na delegáty pro kód, který spravuje konkrétní dotaz. Tento návrhový vzor rozhraní API je velmi výkonný, který se učí a rozumí.

Tento jednoduchý příklad ukazuje, jak delegáti vyžadují velmi málo párování mezi součástmi. Není nutné vytvořit třídu, která je odvozena z určité základní třídy. Není nutné implementovat konkrétní rozhraní.
Jediným požadavkem je poskytnout implementaci jedné metody, která je pro daný úkol zásadní.

## <a name="building-your-own-components-with-delegates"></a>Vytváření vlastních komponent s delegáty

Budeme stavět na tomto příkladu vytvořením komponenty pomocí návrhu, který závisí na delegátech.

Pojďme definovat součást, která by mohla být použita pro zprávy protokolu ve velkém systému. Součásti knihovny lze použít v mnoha různých prostředích, na různých platformách. Existuje mnoho běžných funkcí v součásti, která spravuje protokoly. Bude muset přijímat zprávy z libovolné součásti v systému. Tyto zprávy budou mít různé priority, které může základní součást spravovat. Zprávy by měly mít časová razítka v konečné archivované podobě. Pro pokročilejší scénáře můžete filtrovat zprávy podle zdrojové součásti.

Existuje jeden aspekt funkce, která se bude často měnit: kde jsou zprávy zapsány. V některých prostředích mohou být zapsány do konzoly chyb. V jiných soubor. Mezi další možnosti patří úložiště databáze, protokoly událostí operačního systému nebo jiné úložiště dokumentů.

Existují také kombinace výstupu, které mohou být použity v různých scénářích. Můžete chtít psát zprávy do konzoly a do souboru.

Návrh založený na delegátech poskytne velkou flexibilitu a usnadní podporu mechanismů úložiště, které mohou být přidány v budoucnu.

V rámci tohoto návrhu primární součást protokolu může být nevirtuální, dokonce zapečetěné třídy. Chcete-li zapisovat zprávy na různá paměťová média, můžete připojit libovolnou sadu delegátů. Integrovaná podpora pro delegáty vícesměrového vysílání usnadňuje podporu scénářů, kde zprávy musí být zapsány do více umístění (soubor a konzola).

## <a name="a-first-implementation"></a>První implementace

Začněme malé: počáteční implementace bude přijímat nové zprávy a psát je pomocí libovolného připojeného delegáta. Můžete začít s jedním delegátem, který zapisuje zprávy do konzoly.

[!code-csharp[LoggerImplementation](../../samples/snippets/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

Statická třída výše je nejjednodušší věc, která může fungovat. Musíme napsat jedinou implementaci pro metodu, která zapisuje zprávy do konzoly:

[!code-csharp[LogToConsole](../../samples/snippets/csharp/delegates-and-events/LoggingMethods.cs#LogToConsole "A Console logger.")]

Nakonec je třeba připojit delegáta připojením k writemessage delegát deklarované v protokolování:

[!code-csharp[ConnectDelegate](../../samples/snippets/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Postupy

Náš vzorek zatím je poměrně jednoduchý, ale stále ukazuje některé důležité pokyny pro návrhy zahrnující delegáty.

Použití typů delegátů definovaných v základní rámci usnadňuje uživatelům práci s delegáty. Nemusíte definovat nové typy a vývojáři, kteří používají vaši knihovnu, se nemusí učit nové specializované typy delegátů.

Použitá rozhraní jsou co nejmenší a co nejflexibilnější: Chcete-li vytvořit nový výstupní protokol, musíte vytvořit jednu metodu. Tato metoda může být statickou metodou nebo metodou instance. Může mít jakýkoliv přístup.

## <a name="formatting-output"></a>Formátování výstupu

Udělejme tuto první verzi trochu robustnější a pak začněte vytvářet další mechanismy protokolování.

Dále přidáme několik argumentů k `LogMessage()` metodě tak, aby vaše třída protokolu vytvořila strukturovanější zprávy:

[!code-csharp[Severity](../../samples/snippets/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

Dále využijte tento `Severity` argument k filtrování zpráv, které jsou odesílány do výstupu protokolu.

[!code-csharp[FinalLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Postupy

Do infrastruktury protokolování jste přidali nové funkce. Vzhledem k tomu, že součást protokolování je velmi volně spojena s libovolným výstupním mechanismem, tyto nové funkce lze přidat bez dopadu na některý z kódu implementujícího delegáta protokolování.

Při vytváření tohoto stavu uvidíte další příklady toho, jak tato volná spojka umožňuje větší flexibilitu při aktualizaci částí webu bez jakýchkoli změn v jiných umístěních. Ve skutečnosti ve větší aplikaci, výstupní třídy protokolování může být v jiném sestavení a ani není nutné znovu sestavit.

## <a name="building-a-second-output-engine"></a>Vytvoření druhého výstupního modulu

Složka Log přichází dobře. Přidáme ještě jeden výstupní modul, který zaznamenává zprávy do souboru. To bude o něco více zapojený chod motoru. Bude to třída, která zapouzdřuje operace se soubory a zajišťuje, že soubor je vždy uzavřen po každém zápisu. Tím zajistíte, že všechna data jsou vyprázdněna na disk po vygenerování každé zprávy.

Zde je, že soubor založený logger:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Po vytvoření této třídy, můžete vytvořit instanci a připojí jeho LogMessage metoda logger komponenty:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Tihle dva se vzájemně nevylučují. Můžete připojit metody protokolu a generovat zprávy ke konzole a souboru:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LoggingMethods.LogToConsole; // LoggingMethods is the static class we utilized earlier
```

Později, i ve stejné aplikaci, můžete odebrat jeden z delegátů bez dalších problémů do systému:

```csharp
Logger.WriteMessage -= LoggingMethods.LogToConsole;
```

## <a name="practices"></a>Postupy

Nyní jste přidali druhou výstupní obslužnou rutinu pro podsystém protokolování.
Ten potřebuje trochu více infrastruktury pro správnou podporu systému souborů. Delegát je metoda instance. Je to také soukromá metoda.
Není třeba větší dostupnost, protože infrastruktura delegáta může připojit delegáty.

Za druhé návrh založený na delegáta umožňuje více výstupních metod bez dalšího kódu. Není nutné vytvářet žádné další infrastruktury pro podporu více výstupních metod. Jednoduše se stávají další metodou na seznamu vyvolání.

Věnujte zvláštní pozornost kódu v metodě výstupu protokolování souborů. Je kódován zajistit, že nevyvolá žádné výjimky. I když to není vždy nezbytně nutné, je to často dobrá praxe. Pokud některá z metod delegáta vyvolá výjimku, zbývající delegáti, které jsou na vyvolání nebude vyvolána.

Jako poslední poznámka musí protokolování souborů spravovat své prostředky otevřením a zavřením souboru v každé zprávě protokolu. Můžete se rozhodnout ponechat soubor otevřený a implementovat IDisposable k zavření souboru po dokončení.
Každá metoda má své výhody a nevýhody. Oba vytvořit trochu více spojení mezi třídami.

Žádný kód ve třídě Logger by bylo nutné aktualizovat, aby bylo možné podporovat oba scénáře.

## <a name="handling-null-delegates"></a>Zpracování nulových delegátů

Nakonec pojďme aktualizovat LogMessage metoda tak, aby je robustní pro ty případy, kdy je vybrán žádný výstupní mechanismus. Aktuální implementace vyvolá, `NullReferenceException` když `WriteMessage` delegát nemá seznam vyvolání připojen.
Můžete dát přednost návrhu, který tiše pokračuje, když nebyly připojeny žádné metody. To je snadné pomocí operátoru podmíněné `Delegate.Invoke()` null v kombinaci s metodou:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Operátor null podmíněné (`?.`) zkratuje,`WriteMessage` když je levý operand ( v tomto případě) null, což znamená, že není proveden žádný pokus o protokolování zprávy.

Nenajdete metodu `Invoke()` uvedenou v dokumentaci pro `System.Delegate` nebo `System.MulticastDelegate`. Kompilátor generuje typ `Invoke` ovou bezpečnou metodu pro všechny deklarované typy delegátů. V tomto příkladu `Invoke` to `string` znamená, že má jeden argument a má prázdný návratový typ.

## <a name="summary-of-practices"></a>Shrnutí postupů

Viděli jste začátky součásti protokolu, která by mohla být rozšířena s jinými autory a dalšími funkcemi. Pomocí delegátů v návrhu jsou tyto různé součásti velmi volně spojeny. To poskytuje několik výhod. Je velmi snadné vytvořit nové výstupní mechanismy a připojit je k systému. Tyto další mechanismy potřebují pouze jednu metodu: metodu, která zapisuje zprávu protokolu. Je to design, který je velmi odolný, když jsou přidány nové funkce. Smlouva požadovaná pro všechny zapisovatel je implementovat jednu metodu. Tato metoda může být statickou metodu nebo metodu instance. Může to být veřejný, soukromý nebo jakýkoli jiný legální přístup.

Logger třída může provádět libovolný počet vylepšení nebo změny bez zavedení narušující změny. Stejně jako všechny třídy nelze upravit veřejné rozhraní API bez rizika porušení změn. Ale protože spojení mezi protokolování a všechny výstupní motory je pouze prostřednictvím delegáta, žádné jiné typy (jako rozhraní nebo základní třídy) jsou zapojeny. Spojka je co nejmenší.

[Další](events-overview.md)
