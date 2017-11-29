---
title: "Obecné vzory pro delegáti"
description: "Další informace o obecné vzory pro použití delegátů ve vašem kódu předejdete silné párování mezi vaší součásti."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 83214800fb997e9274cacfd1bae85ab07c4515a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="common-patterns-for-delegates"></a>Obecné vzory pro delegáti

[Předchozí](delegates-strongly-typed.md)

Delegáti poskytují mechanismus, který umožňuje návrhy softwaru zahrnující minimální párování mezi součástmi.

Příkladem vynikající pro tento typ návrhu je LINQ. Vzor výrazu dotazu LINQ spoléhá na delegáty pro všechny její funkce. Vezměte v úvahu tomto jednoduchém příkladu:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Tím se odfiltrují pořadí čísel a pouze ty menší než hodnota 10.
`Where` Metoda používá delegáta, který určuje, které prvky pořadí předat filtru. Když vytvoříte dotaz LINQ, je třeba zadat implementace delegáta pro tento konkrétní účel.

Prototyp Where je metoda:

```csharp
public static IEnumerable<TSource> Where<in TSource> (IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

V tomto příkladu se opakuje se všechny metody, které jsou součástí LINQ. Všechny spoléhají na delegáty pro kód, který spravuje specifického dotazu. Tento vzor návrhu rozhraní API je velice mocný zjišťovat a pochopit.

Tento jednoduchý příklad ukazuje, jak delegáti vyžadují velmi malé párování mezi součástmi. Nemusíte vytvořte třídu, která je odvozena z určité základní třídy. Nemusíte implementovat určité rozhraní.
Jediným požadavkem je poskytnout implementaci jednu metodu, je nezbytné, aby na prováděné úloze.

## <a name="building-your-own-components-with-delegates"></a>Vytváření vlastních součástí s delegáti

Umožňuje vytvořit v tomto příkladu vytvořením součást pomocí návrhu, které jsou závislé na delegáti.

Umožňuje definovat komponenty, která by mohly být použity zprávy protokolu ve velkých systému. Součásti knihovny může v mnoha různých prostředích, na více různých platformách. Existuje mnoho běžných funkcí v součásti, která spravuje protokoly. Může se stát, ji budou muset přijmout zprávy z libovolné součásti v systému. Tyto zprávy budou mít různé priority, které můžou spravovat součást základních. Zprávy musí mít časová razítka v jejich poslední archivovaný formuláře. Pro pokročilejší scénáře můžete vyfiltrovat zprávy zdrojovou součástí.

Neexistuje jeden aspekt funkce, která se často změní: zápis zpráv. V některých prostředích může být zapsána do konzoly chyby. V jiných případech soubor. Ostatní možnosti patří úložiště databáze, protokoly událostí operačního systému nebo jiného dokumentu úložiště.

Existují také kombinací výstupu, které lze použít v různých scénářích. Můžete pro zápis zpráv do konzoly a do souboru.

Návrh podle delegáti bude poskytovat značnou flexibilitu a usnadňují podporu úložiště mechanismy, které lze přidat v budoucnu.

V tomto návrhu může být primární protokolu součásti nevirtuálních, i zapečetěné třídy. Můžete zařadit v žádné sadě delegátů k zápisu zprávy do jiného úložiště média. Integrované podporu vícesměrového vysílání delegáti usnadňuje podporu scénáře, kde musí být zprávy zapisovány do víc umístění (soubor a konzole).

## <a name="a-first-implementation"></a>První implementace

Začněme malé: počáteční implementace přijmout nové zprávy a zapsat je pomocí všechny připojené delegáta. Můžete začít s jeden delegáta, který zapíše zpráv do konzoly.

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(string msg)
    {
        WriteMessage(msg);
    }
}
```

Statická třída výše je nejjednodušší věcí, které může fungovat. Je potřeba zapsat jediná implementace pro metody, která zapisuje zpráv do konzoly: 

```csharp
public static void LogToConsole(string message)
{
    Console.Error.WriteLine(message);
}
```

Nakonec můžete spojit delegát připojením k WriteMessage delegáta deklarovat v protokolovacího nástroje:

```csharp
Logger.WriteMessage += LogToConsole;
```

## <a name="practices"></a>Postupy

Naše ukázka, pokud je docela jednoduchá, ale stále ukazuje některé důležité pokyny pro návrhy zahrnující delegáti.

Použití delegáta typů front definovaných v rámci základní usnadňuje uživatelům pracovat s delegáty. Nemusíte definovat nové typy a vývojáře, kteří používají vaše knihovna není potřeba další typy nové, specializované delegáta.

Rozhraní používá se jako minimální a co nejpružnější: Pokud chcete vytvořit nové protokoly výstup, musíte vytvořit jednu metodu. Tato metoda může být statickou metodu nebo metody instance. Může mít žádné přístup.

## <a name="formatting-output"></a>Výstupní formátování

Můžeme zpřístupnit tento první verzi bit robustnější a poté spusťte vytváření jiným mechanismem protokolování.

V dalším kroku přidejme několik argumenty, které mají `LogMessage()` metoda tak, aby třídě protokolu vytváří více strukturovaných zprávy:

```csharp
// Logger implementation two
public enum Severity
{
    Verbose,
    Trace,
    Information,
    Warning,
    Error,
    Critical
}

public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```

V dalším kroku provedeme pomocí této `Severity` výstupu argument k filtrování zprávy, které se odesílají do protokolu. 

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static Severity LogLevel {get;set;} = Severity.Warning;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        if (s < LogLevel)
            return;
            
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```
## <a name="practices"></a>Postupy

Přidali jste nové funkce protokolování infrastruktury. Vzhledem k tomu, že komponenta protokolovacího nástroje je velmi volně vázány do jakéhokoli výstupu mechanismu, mohou být přidány tyto nové funkce bez dopadu na kód implementace delegáta protokolovacího nástroje.

Jak zachovat sestavování to, zobrazí se další příklady jak tato volné párování umožňuje větší flexibilitu při aktualizaci části webu bez uložení změn do jiných umístění. Ve skutečnosti ve větší aplikaci třídy výstupu protokolovacího nástroje může být v jiném sestavení a ani je třeba znovu sestavit.

## <a name="building-a-second-output-engine"></a>Druhý modul výstup sestavení

Součásti protokolu pochází podél také. Umožňuje přidat jeden další modul výstup, který zaznamenává zprávy do souboru. Bude jím modul výstupní zapojí o něco víc. Je třída, který zapouzdřuje operací se soubory a zajišťuje, že soubor je vždy zavřel po každém zápisu. Který zajišťuje, že všechna data vyprazdňuje na disk po vygenerování každé zprávě.

Tady je tento soubor na základě protokoly:

```csharp
public class FileLogger
{
    private readonly string logPath;
    public FileLogger(string path)
    {
        logPath = path;
        Logger.WriteMessage += LogMessage;
    }
    
    public void DetachLog() => Logger.WriteMessage -= LogMessage;

    // make sure this can't throw.
    private void LogMessage(string msg)
    {
        try {
            using (var log = File.AppendText(logPath))
            {
                log.WriteLine(msg);
                log.Flush();
            }
        } catch (Exception e)
        {
            // Hmm. Not sure what to do.
            // Logging is failing...
        }
    }
}
```

Po vytvoření této třídy, můžete vytvořit jeho instanci a jeho LogMessage – metoda přiloží k komponenta protokolovacího nástroje:

```csharp
var file = new FileLogger("log.txt");
```

Tyto dva se vzájemně nevylučují. Můžete připojit obě metody protokolu a generovat zpráv do konzoly a soubor:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

Později i ve stejné aplikaci, můžete odebrat jedním z delegáty bez dalších problémů v systému:

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a>Postupy

Nyní jste přidali Druhá obslužná rutina výstup pro dílčí systém protokolování.
Tato potřebuje trochu další infrastrukturu pro správně podporu systému souborů. Delegát je metoda instance. Je také soukromá metoda.
Není nutné pro větší usnadnění, protože delegáta infrastruktury můžete připojit delegáty.

Druhý návrhu na základě delegáta umožňuje více metod výstupu bez jakékoli další kód. Nemusíte vytvářet žádné další infrastrukturu pro podporu více metod výstup. Jednoduše budou jinou metodu na seznamu vyvolání.

Věnujte zvláštní pozornost kód v souboru protokolování způsob výstupu. Je zakódované Ujistěte se, že nevyvolá jakékoli výjimky. Když to není vždy nezbytně nutné, je vhodné. Pokud některou z metod delegát vyvolá výjimku, nebude volána zbývající delegáti, které jsou pro vyvolání.

Jako poslední Poznámka protokolovacího nástroje souboru musí spravovat její prostředky otvírání a zavírání souborů v každé zprávě protokolu. Mohli byste nechat otevřený soubor a implementovat rozhraní IDisposable po dokončení zavřete soubor.
Některé z metod má své výhody a nevýhody. Jak vytvořit trochu další párování mezi třídami.

Žádný kód ve třídě protokolovacího nástroje by musela být aktualizované kvůli podpoře buď scénář.

## <a name="handling-null-delegates"></a>Zpracování Null delegáti

Nakonec umožňuje aktualizovat metodu LogMessage tak, aby se robustní pro případy, pokud je vybrána mechanismus žádný výstup. Aktuální implementace vyvolá výjimku `NullReferenceException` při `WriteMessage` delegáta nemá seznam vyvolání připojen.
Dáváte přednost tomu návrh, který pokračuje bez upozornění při byly připojeny žádné metody. Toto je snadný při použití null podmíněný operátor v kombinaci s `Delegate.Invoke()` metoda:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Podmíněný operátor s hodnotou null (`?.`) při zkratům levý operand (`WriteMessage` v tomto případě) je null, což znamená žádné pokusu o zprávu protokolu.

Nebude možné najít `Invoke()` metoda uvedeny v dokumentaci k `System.Delegate` nebo `System.MulticastDelegate`. Kompilátor generuje bezpečnost typů `Invoke` delegovat metoda pro libovolný typ deklarovaný. V tomto příkladu to znamená `Invoke` přebírá jediný `string` argument, a má typ vrácené hodnoty void.

## <a name="summary-of-practices"></a>Souhrn postupů

Seznámili jste se začátku protokolu součásti, která by mohla být rozšířena s další zapisovače a další funkce. Pomocí delegátů v návrhu jsou velmi volně vázány tyto různé součásti. To poskytuje několik výhod. Je velmi snadné vytvořit nový výstupní mechanismy a jejich připojení k systému. Tyto další mechanismy, stačí jeden metoda: metody, která zapisuje zprávy protokolu. Je k návrhu, který je velmi odolné, když se přidají nové funkce. Kontrakt potřebné pro všechny zapisovače je implementovat jednu metodu. Tato metoda může být statické nebo metodu instance. To může být veřejné, privátní nebo jiné právní přístup.

Třída protokolovacího nástroje můžete nastavit libovolný počet vylepšení nebo změny bez zavedení nejnovější změny. Podobně jako všechny třídy nelze změnit veřejné rozhraní API bez riziko nejnovější změny. Ale protože párování mezi protokolovacího nástroje a všechny moduly výstupu je pouze prostřednictvím delegáta, se podílejí žádné jiné typy (například rozhraní nebo základní třídy). Vazba je co nejmenší.

[Další](events-overview.md)
