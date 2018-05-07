---
title: Konzolová aplikace
description: V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: bae03c9ae02f2888b1b70617ca712ef7927e9dce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="console-application"></a>Konzolová aplikace

V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#. Naučíte:

- Základy .NET Core rozhraní příkazového řádku (CLI)
- Struktura konzolovou aplikaci C#
- Konzole vstupně-výstupních operací
- Základní informace o rozhraní API pro vstupně-výstupních souborů v rozhraní .NET
- Základy založený na úlohách asynchronní programování v rozhraní .NET

Budete sestavit aplikaci, která čte textový soubor a vrátí je obsah na konzole tohoto textového souboru. Výstup do konzoly je pracovníky tak, aby odpovídaly nahlas jeho čtení. Můžete urychlit nebo zpomalit rychlost stisknutím ' <' nebo ' >' klíče.

V tomto kurzu je celá řada funkcí. Umožňuje vytvořit, je po jednom.

## <a name="prerequisites"></a>Požadavky

Budete potřebovat k nastavení vašeho počítače ke spuštění .NET Core. Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky. Tuto aplikaci můžete spustit v systému Windows, Linux, systému macOS nebo v kontejner Docker.
Budete muset nainstalovat editor vaše oblíbené kódu.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Nastavit aktuální adresář. Zadejte příkaz `dotnet new console` na příkazovém řádku. Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".

Než začnete, provádění změn, přejděte přes kroky a spusťte tak jednoduchou aplikaci Hello World. Po vytvoření aplikace, zadejte `dotnet restore` na příkazovém řádku. Tento příkaz spustí proces obnovení balíčku NuGet. NuGet je Správce balíčků .NET. Tento příkaz stáhne všechny chybějící závislosti pro váš projekt. Toto je nový projekt, žádné závislosti na místě, se tak během prvního spuštění stáhnou rozhraní .NET Core. Po provedení tohoto kroku počáteční se jenom musíte spustit `dotnet restore` při přidání nové závislé balíčky nebo aktualizace verze všechny svoje závislosti.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po obnovení balíčků, můžete spustit `dotnet build`. To provede modul sestavení a vytvoří spustitelný soubor aplikace. Nakonec spuštěním `dotnet run` spusťte aplikaci.

Jednoduchý kód aplikace Hello World je v souboru Program.cs. Otevřete tento soubor se svém oblíbeném textovém editoru. Jsme naše první změny.
V horní části souboru, najdete v části pomocí příkazu:

```csharp
using System;
```

Tento příkaz informuje kompilátor všechny typy z `System` obor názvů jsou v oboru. Podobně jako ostatní objektově orientované jazyky, které možná zneužil C# používá obory názvů organizovat typy. Tento program Hello World se neliší. Uvidíte, že je program uzavřena v oboru názvů s názvem na základě názvu aktuálního adresáře. V tomto kurzu, změňte název oboru názvů `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Čtení a zobrazování souboru

První funkce přidání je možnost čtení z textového souboru a zobrazit všechny tento text do konzoly. Nejprve přidejme do textového souboru. Kopírování [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) soubor z úložiště GitHub pro tento [ukázka](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu. To bude sloužit jako skript pro vaši aplikaci. Pokud vás zajímají informace o tom, jak stáhnout ukázkové aplikace pro toto téma, postupujte podle pokynů v [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) tématu.

Dál přidejte následující metodu v vaše `Program` – třída (přímo pod `Main` metoda):

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

Tato metoda používá typů z dva nové obory názvů. Tento postup můžete zkompilovat budete potřebovat na začátek souboru přidejte následující dva řádky:

```csharp
using System.Collections.Generic;
using System.IO;
```

<xref:System.Collections.Generic.IEnumerable%601> Rozhraní je definováno v <xref:System.Collections.Generic> oboru názvů. <xref:System.IO.File> Třída definovaná v <xref:System.IO> oboru názvů.

Tato metoda je zvláštní druh C# metodu s názvem *Iterator – metoda*. Vrátí enumerátor metody pořadí, které se vyhodnocují líné. To znamená, že každá položka v pořadí se vygeneruje, jak vyžádala kód využívání sekvenci. Enumerátor metody jsou metody, které obsahují jednu nebo více [ `yield return` ](../language-reference/keywords/yield.md) příkazy. Objekt vrácený `ReadFrom` metoda obsahuje kód pro generování každou položku v pořadí. V tomto příkladu, který zahrnuje čtení na další řádek textu ze zdrojového souboru a vrácení tento řetězec. Pokaždé, když kód volání požadavků na další položku z řady, kód čte na další řádek textu ze souboru a vrátí ji. Při soubor je zcela přečíst, sekvenci označuje, že neexistují žádné další položky.

Existují dva další C# syntaxe prvky, které může být pro vás nový. [ `using` ](../language-reference/keywords/using-statement.md) Příkaz v této metodě spravuje vyčištění prostředků. Proměnné, která je v inicializovat `using` – příkaz (`reader`, v tomto příkladu) musí implementovat <xref:System.IDisposable> rozhraní. Toto rozhraní definuje jedinou metodu `Dispose`, která by měla být volána, když prostředek by měly být uvolněny. Kompilátor generuje tohoto volání při provádění dosáhne složená závorka `using` příkaz. Kód generované kompilátorem zajistí, že prostředek vydání i v případě, že je vyvolána výjimka z kódu v bloku definované na pomocí příkazu.

`reader` Proměnná je definována pomocí `var` – klíčové slovo. [`var`](../language-reference/keywords/var.md) definuje *implicitně typované lokální proměnné*. To znamená, že typ proměnné je určen podle typu kompilaci objektu přiřazenou proměnné. Tady, který je vrácená hodnota z <xref:System.IO.File.OpenText(System.String)> metoda, která je <xref:System.IO.StreamReader> objektu.

Nyní Pojďme zadejte kód pro čtení tohoto souboru v `Main` metoda:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Spusťte program (pomocí `dotnet run`) a zobrazí se všechny řádky, vytisknout ke konzole.

## <a name="adding-delays-and-formatting-output"></a>Přidávání zpoždění a formátování výstupu

Je nutné se zobrazuje příliš rychlé pro čtení. Teď je potřeba přidat zpoždění ve výstupu. Když začnete, budete se vytváření, některé základní kód, který umožňuje asynchronní zpracování. První takto bude postupujte podle několik proti vzory. Proti vzory jsou zdůraznit v komentářích přidejte kód a kód bude aktualizován v dalších krocích.

Existují dva kroky v této části. Nejprve budete aktualizovat metodu iterator vrátit jednoho slova místo celé řádky. Která se provádí s tyto úpravy. Nahraďte `yield return line;` příkaz následujícím kódem:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Dále musíte upravit jak využívat řádky souboru a přidejte zpoždění po napsání jednotlivých slov. Nahraďte `Console.WriteLine(line)` příkaz v `Main` metoda s následující blok:

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<xref:System.Threading.Tasks.Task> Třída je v <xref:System.Threading.Tasks> obor názvů, takže budete muset přidat `using` příkaz v horní části souboru:

```csharp
using System.Threading.Tasks;
```

Ukázku spustit a zkontrolujte výstup. Nyní je vytištěno každý jednoho slova, za nímž následuje zpožděním 200 ms. Ale zobrazených výstup zobrazuje některé problémy, protože zdroj textového souboru má několik řádků, které mají více než 80 znaků bez konec řádku. Který může být těžko čitelný, když je posouvání pomocí. To je snadno opravit. Budete právě udržování přehledu o délce každého řádku a vygenerovat nový řádek vždy, když délka řádku dosáhne určité prahovou hodnotu. Deklarujte místní proměnné po deklaraci `words` v `ReadFrom` metoda, která obsahuje délka řádku:

```csharp
var lineLength = 0;
```

Pak přidejte následující kód po `yield return word + " ";` (než pravé složené závorce):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Ukázku spustit, a budete moct nahlas přečíst v její předem nakonfigurovaná rychle.

## <a name="async-tasks"></a>Úloh s modifikátorem Async

V tomto posledním kroku přidáte kód pro zápis výstupu asynchronně v jedné úloze při také spuštěna jiná úloha číst vstupní od uživatele, pokud chtějí zrychlit nebo zpomalit zobrazení textu. To má několik kroků a na konci, budete mít všechny aktualizace, které potřebujete.
Prvním krokem je vytvoření asynchronní <xref:System.Threading.Tasks.Task> vrácení metoda, která představuje kód, pokud jste vytvořili pro čtení a zobrazit soubor.

Přidejte tuto metodu za účelem vaše `Program` – třída (jsou převzaty z textu vaší `Main` metoda):

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

Můžete si všimnout dvou změny. První v těle metody, namísto volání <xref:System.Threading.Tasks.Task.Wait> synchronně počkat na dokončení úlohy, používá tato verze `await` – klíčové slovo. Aby bylo možné provést, je nutné přidat `async` modifikátor k označení metody. Tato metoda vrátí hodnotu `Task`. Všimněte si, že neexistují žádné návratový příkazy, které vracejí `Task` objektu. Místo toho, který `Task` objekt se vytvoří v kódu kompilátor vygeneruje při použití `await` operátor. Představte si, že tato metoda vrátí při dosažení `await`. Vrácený `Task` znamená, že práce nebyl dokončen.
Metoda obnoví při dokončení awaited úlohy. Když se provedla k dokončení, vrácený `Task` označuje, že je kompletní.
Volání kódu můžete monitorovat vrácená `Task` k určení, kdy byla dokončena.

Tato nová metoda můžete volat vaší `Main` metoda:

```csharp
ShowTeleprompter().Wait();
```

Zde v `Main`, kód synchronně čekání. Měli byste použít `await` operátor místo abyste čekali synchronně, kdykoli je to možné. Ale v konzolové aplikaci `Main` metodu, nemůžete použít `await` operátor. Může se stát, který by způsobilo ukončení aplikace před všechny úkoly dokončí.

> [!NOTE]
> Pokud používáte C# 7.1 nebo novější, můžete vytvořit konzolové aplikace s [ `async` `Main` metoda](../whats-new/csharp-7-1.md#async-main).

Potom budete muset napsat druhé asynchronní metody pro čtení z konzoly a sledovat ' <' a ' >' klíče. Tady je metoda, které přidáte pro tuto úlohu:

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

Tím se vytvoří výrazu lambda představují <xref:System.Action> delegáta, který čte klíč z konzoly a upravuje místní proměnné představující zpoždění při stisknutí ' <' nebo ' >' klíče. Tato metoda používá <xref:System.Console.ReadKey> blokovat a čekat, uživatel ke stisknutí klávesy.

Chcete-li dokončit tuto funkci, je potřeba vytvořit novou `async Task` vrácení metoda, která spustí obě tyto úlohy (`GetInput` a `ShowTeleprompter`) a také spravuje sdílených dat mezi těmito dvěma úkoly.

Je čas vytvořit třídu, která dokáže zpracovat sdílených dat mezi těmito dvěma úkoly. Tato třída obsahuje dvě veřejné vlastnosti: zpoždění a příznak `Done` k označení úplně čtení souboru:

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

Vložte nový soubor třídy a uzavřete třídy v `TeleprompterConsole` obor názvů, jak je uvedeno výše. Také budete muset přidat `using static` příkaz tak, aby můžete odkazovat `Min` a `Max` metody bez nadřazených třída nebo obor názvů. A [ `using static` ](../language-reference/keywords/using-static.md) příkaz importuje metody z jedné třídy. To je rozdíl s `using` použít v tomto okamžiku příkazů, které jste importovali všechny třídy z oboru názvů.

```csharp
using static System.Math;
```

Jiné, je nová funkce jazyka je [ `lock` ](../language-reference/keywords/lock-statement.md) příkaz. Tento příkaz zajistí, že pouze jedno vlákno mohou být v tomto kódu v daném okamžiku. Pokud jedno vlákno je v uzamčeném části, musí jiná vlákna počkejte první vlákno ukončíte této části. `lock` Příkaz používá objekt, který chrání zamknout oddíl. Tato třída pracuje standardní stylu k uzamčení soukromý objekt ve třídě.

Dále je potřeba aktualizovat `ShowTeleprompter` a `GetInput` můžete použít nové metody `config` objektu. Zápis jeden konečné `Task` vrácení `async` metoda spuštění obě úlohy a po dokončení prvního úkolu ukončit:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Je zde jeden nová metoda <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> volání. Které vytváří `Task` který dokončí při dokončení některých úkolů ve svém seznamu argumentů.

Dále je potřeba aktualizovat i `ShowTeleprompter` a `GetInput` metod používaných `config` objekt zpoždění:

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

Tuto novou verzi `ShowTeleprompter` volání do nové metody `TeleprompterConfig` třídy. Nyní, budete muset aktualizovat `Main` volat `RunTeleprompter` místo `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Závěr

Tento kurz vám ukázal, že jste celou řadu funkcí kolem jazyka C# a knihovny .NET Core týkající se práce v konzolové aplikace.
Můžete vytvořit tyto znalosti prozkoumat více o jazyce a třídy zavedené sem. Seznámili jste se základy a konzoly vstupně-výstupních operací, blokování a neblokující použití asynchronní programování založené na úlohách, prohlídka jazyka C# a jak jsou uspořádány programy C# a rozhraní příkazového řádku .NET Core a nástroje.

Další informace o vstupně-výstupní soubor najdete v tématu [souborové služby a vstupně-výstupní datový proud](../../standard/io/index.md) tématu. Další informace o asynchronní programovací model použili v tomto kurzu, najdete v článku [založený na úlohách asynchronní programování](../..//standard/parallel-programming/task-based-asynchronous-programming.md) tématu a [asynchronní programování](../async.md) tématu.
