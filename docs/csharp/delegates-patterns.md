---
title: Obecné vzory pro delegáty
description: Přečtěte si o běžných vzorech pro používání delegátů ve vašem kódu, abyste zabránili silnému propojení mezi vašimi komponentami.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 40e6ced7337e32d6e9b67b12a15ad7e03a77c4b6
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239869"
---
# <a name="common-patterns-for-delegates"></a>Obecné vzory pro delegáty

[Předchozí](delegates-strongly-typed.md)

Delegáti poskytují mechanismus, který umožňuje vytvářet návrhy softwaru zahrnující minimální propojení mezi komponentami.

Jedním z skvělých příkladů tohoto druhu návrhu je LINQ. Vzor výrazu dotazu LINQ spoléhá na delegáty všech jeho funkcí. Vezměte v úvahu tento jednoduchý příklad:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Tím se vyfiltruje posloupnost čísel jenom na hodnoty, které jsou menší než hodnota 10.
Metoda `Where` používá delegáta, který určuje, které prvky sekvence předejte filtru. Když vytvoříte dotaz LINQ, zadáváte implementaci delegáta pro tento konkrétní účel.

Prototyp pro metodu WHERE je:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

Tento příklad se opakuje se všemi metodami, které jsou součástí LINQ. Všichni spoléhají na delegáty pro kód, který spravuje konkrétní dotaz. Tento vzor návrhu rozhraní API je velmi výkonným, abyste se dozvěděli a pochopili.

Tento jednoduchý příklad ukazuje, jak Delegáti vyžadují velmi malé propojení mezi komponentami. Nemusíte vytvářet třídu, která je odvozena z konkrétní základní třídy. Nemusíte implementovat konkrétní rozhraní.
Jediným požadavkem je poskytnout implementaci jedné metody, která je pro úkol zásadní.

## <a name="building-your-own-components-with-delegates"></a>Vytváření vlastních komponent s delegáty

Pojďme tento příklad sestavit vytvořením komponenty pomocí návrhu, který spoléhá na delegáty.

Pojďme definovat komponentu, která se dá použít pro zprávy protokolu ve velkém systému. Komponenty knihovny lze v mnoha různých prostředích použít na více různých platformách. Komponenta, která spravuje protokoly, obsahuje spoustu běžných funkcí. Bude muset přijímat zprávy ze všech součástí systému. Tyto zprávy budou mít různé priority, které může základní komponenta spravovat. Zprávy by měly mít v konečném archivovaném formuláři časová razítka. V případě pokročilejších scénářů můžete zprávy filtrovat pomocí zdrojové součásti.

K dispozici je jeden aspekt funkce, která se bude často měnit: kde se zapisují zprávy. V některých prostředích se můžou zapisovat do chybové konzoly. V ostatních souborech soubor. Mezi další možnosti patří úložiště databáze, protokoly událostí operačního systému nebo jiné úložiště dokumentů.

Existují také kombinace výstupů, které mohou být používány v různých scénářích. Můžete chtít napsat zprávy do konzoly a do souboru.

Návrh založený na delegátech poskytne značnou flexibilitu a usnadňuje podporu mechanismů úložiště, které mohou být přidány do budoucna.

V rámci tohoto návrhu může být primární součástí protokolu nevirtuální, sudá i zapečetěná třída. Můžete připojit libovolnou sadu delegátů a zapsat zprávy na jiná úložná média. Integrovaná podpora pro delegáty vícesměrového vysílání usnadňuje podporu scénářů, ve kterých je nutné zapsat zprávy do více umístění (soubor a konzolu).

## <a name="a-first-implementation"></a>První implementace

Pojďme začít malým: počáteční implementace přijme nové zprávy a zapíše je pomocí kteréhokoli připojeného delegáta. Můžete začít s jedním delegátem, který zapisuje zprávy do konzoly.

[!code-csharp[LoggerImplementation](../../samples/snippets/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

Výše uvedená statická třída je nejjednodušší věc, která může fungovat. Musíme napsat jednu implementaci pro metodu, která zapisuje zprávy do konzoly: 

[!code-csharp[LogToConsole](../../samples/snippets/csharp/delegates-and-events/LoggingMethods.cs#LogToConsole "A Console logger.")]

Nakonec musíte připojit delegáta tak, že ho připojíte k delegátovi WriteMessage deklarovanému v protokolovacím nástroji:

[!code-csharp[ConnectDelegate](../../samples/snippets/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Způsobů

Naše ukázka je tak poměrně jednoduchá, ale stále předvádí některé důležité pokyny pro návrhy zahrnující delegáty.

Použití typů delegátů definovaných v rozhraní Core usnadňuje uživatelům práci s delegáty. Nemusíte definovat nové typy a vývojáři, kteří používají vaši knihovnu, nemusejí učit nové, specializované typy delegátů.

Použitá rozhraní jsou co nejmenší a co nejpružnější: pro vytvoření nového výstupního protokolovacího nástroje je nutné vytvořit jednu metodu. Tato metoda může být statickou metodou nebo metodou instance. Může mít jakýkoliv přístup.

## <a name="formatting-output"></a>Formátování výstupu

Pojďme tuto první verzi udělat trochu robustnější a pak začít vytvářet další mechanismy protokolování.

Nyní přidáme do metody `LogMessage()` několik argumentů, aby vaše třída protokolu vytvořila více strukturovaných zpráv:

[!code-csharp[Severity](../../samples/snippets/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

Teď využijeme tento argument `Severity` k filtrování zpráv, které se odesílají do výstupu protokolu. 

[!code-csharp[FinalLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Způsobů

Do infrastruktury protokolování jste přidali nové funkce. Vzhledem k tomu, že komponenta protokolovacího nástroje je velmi volně spojená s jakýmkoliv výstupním mechanismem, je možné tyto nové funkce přidat bez dopadu na žádný kód implementující delegáta protokolovacího nástroje.

V takovém případě se zobrazí další příklady toho, jak toto volné spojení umožňuje větší flexibilitu při aktualizaci částí webu bez jakýchkoli změn v jiných umístěních. Ve skutečnosti může být ve větší aplikaci výstupní třídy protokolovacího nástroje v jiném sestavení a ještě není nutné je znovu sestavit.

## <a name="building-a-second-output-engine"></a>Vytvoření druhého výstupního modulu

Komponenta log je také k disjetí. Pojďme přidat další výstupní modul, který bude protokolovat zprávy do souboru. To bude poněkud více součástí výstupního stroje. Bude to třída, která zapouzdřuje operace se soubory a zajistí, že se soubor vždy zavře po každém zápisu. Tím zajistíte, že všechna data budou po vygenerování každé zprávy vyprázdněna na disk.

Tady je tento protokolovací nástroj založený na souboru:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Po vytvoření této třídy je možné ji vytvořit a připojit její metodu LogMessage – k součásti protokolovacího nástroje:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Tyto dvě se vzájemně nevylučují. Můžete připojit obě metody protokolu a generovat zprávy do konzoly a souboru:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LoggingMethods.LogToConsole; // LoggingMethods is the static class we utilized earlier
```

Později i ve stejné aplikaci můžete odebrat jednoho z delegátů bez jakýchkoli dalších problémů systému:

```csharp
Logger.WriteMessage -= LoggingMethods.LogToConsole;
```

## <a name="practices"></a>Způsobů

Nyní jste přidali druhou obslužnou rutinu výstupu pro dílčí systém protokolování.
Tato jedna z nich potřebuje trochu větší infrastrukturu, aby správně podporovala systém souborů. Delegát je metoda instance. Je to také soukromá metoda.
Není potřeba mít větší přístupnost, protože delegát může připojit delegáty.

Za druhé, návrh založený na delegátech umožňuje více metod výstupu bez dalšího kódu. Nemusíte vytvářet žádnou další infrastrukturu pro podporu více metod výstupu. Jednoduše se v seznamu vyvolání stanou jinou metodou.

Věnujte zvláštní pozornost kódu v metodě pro výstup protokolování souborů. Je kódována, aby se zajistilo, že nevyvolá žádné výjimky. I když to není vždy naprosto nezbytné, často je to dobrý postup. Pokud některá z metod delegáta vyvolá výjimku, zbývající delegáti, kteří jsou při vyvolání, nebudou vyvoláni.

Jako poslední Poznámka musí protokolovací nástroj souboru spravovat jeho prostředky otevřením a zavřením souboru v každé zprávě protokolu. Můžete zvolit, že soubor zůstane otevřený a implementuje IDisposable pro zavření souboru po dokončení.
Kterákoli z metod má své výhody a nevýhody. Obě třídy vytvoří trochu větší propojení mezi třídami.

Žádný kód ve třídě protokolovacího nástroje by se neměl aktualizovat, aby podporoval buď scénář.

## <a name="handling-null-delegates"></a>Manipulace s delegáty s hodnotou null

Nakonec aktualizujeme metodu LogMessage – tak, aby byla robustní pro případy, kdy není vybraný žádný výstupní mechanismus. Aktuální implementace vyvolá `NullReferenceException`, když delegát `WriteMessage` nemá připojen seznam volání.
Můžete preferovat návrh, který Tichy pokračuje, i když nebyly připojeny žádné metody. To je snadné pomocí podmíněného operátoru null kombinovaného s `Delegate.Invoke()` metodou:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Pokud levý operand (`WriteMessage` v tomto případě) má hodnotu null, znamená to, že se nepokusí o protokolování zprávy, což znamená, že došlo k nedostatku podmíněného operátoru (`?.`).

Nenajdete tu metodu `Invoke()` uvedenou v dokumentaci pro `System.Delegate` nebo `System.MulticastDelegate`. Kompilátor generuje metodu bezpečného `Invoke` typu pro jakýkoli deklarovaný typ delegáta. V tomto příkladu to znamená, že `Invoke` přebírá jeden `string` argument a má návratový typ void.

## <a name="summary-of-practices"></a>Přehled postupů

Viděli jste začátek komponenty protokolu, kterou je možné rozšířit o jiné moduly pro zápis a další funkce. Použití delegátů v návrhu těchto různých komponent je velmi volně připojeno. To přináší několik výhod. Je velmi snadné vytvořit nové výstupní mechanismy a připojit je k systému. Tyto další mechanismy potřebují jenom jednu metodu: metoda, která zapisuje zprávu protokolu. Je to návrh, který je velmi odolný při přidávání nových funkcí. Kontraktem vyžadovaným pro jakýkoliv zapisovač je implementace jedné metody. Tato metoda může být statickou metodou nebo metodou instance. Může to být veřejné, privátní nebo jakýkoli jiný právní přístup.

Třída protokolovacího nástroje může provádět libovolný počet vylepšení nebo změn bez nutnosti zavádět zásadní změny. Stejně jako u libovolné třídy nemůžete změnit veřejné rozhraní API bez rizika zásadních změn. Vzhledem k tomu, že propojení mezi protokolovacím modulem a všemi výstupními moduly je pouze prostřednictvím delegáta, nejsou zapojeny žádné další typy (jako rozhraní nebo základní třídy). Spojení je co nejmenší.

[Next](events-overview.md)
