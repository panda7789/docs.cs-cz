---
title: Konzolová aplikace
description: V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 9255ad9b1fefc828e767fb8e6ccc62b2eaf23fd6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183617"
---
# <a name="console-application"></a>Konzolová aplikace

V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core. Získáte informace:

- Základní informace o .NET Core rozhraní příkazového řádku (CLI)
- Struktura konzolovou aplikaci C#
- Konzola vstupně-výstupních operací
- Základní informace o souboru vstupně-výstupní operace rozhraní API v .NET
- Základní informace o úkolově orientovanou asynchronní programování v rozhraní .NET

Vytvoříte aplikaci, která čte textový soubor a vrátí obsah tohoto souboru text do konzoly. Výstup na konzole je tempem tak, aby odpovídala jeho nahlas. Můžete urychlit nebo zpomalit rychlost stisknutím klávesy ' <' (méně než) nebo ">" (větší) klíče.

Existuje mnoho funkcí v tomto kurzu. Vytvořme je jeden po druhém.

## <a name="prerequisites"></a>Požadavky

Budete potřebovat k nastavení vašeho počítače ke spuštění .NET Core. Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky. Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Dockeru.
Bude potřeba nainstalovat váš oblíbený editor kódu.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Ujistěte se, že do aktuálního adresáře. Zadejte příkaz `dotnet new console` příkazového řádku. Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".

Než začnete, úpravy, Podívejme se kroky ke spuštění jednoduché aplikace Hello World. Po vytvoření aplikace, zadejte `dotnet restore` příkazového řádku. Tento příkaz spustí proces obnovení balíčku NuGet. Správce balíčků NuGet je Správce balíčků .NET. Tento příkaz načte všechny chybějící závislosti pro váš projekt. Toto je nový projekt, závislosti nejsou v místě, tak při prvním spuštění se stáhnout .NET Core framework. Po provedení tohoto kroku počáteční je pouze potřeba spustit `dotnet restore` při přidání nové závislé balíčky nebo aktualizace verze závislosti.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po obnovení balíčků, spustíte `dotnet build`. To spustí modul sestavení a vytvoří spustitelný soubor aplikace. Nakonec spuštěním `dotnet run` ke spuštění aplikace.

Kód jednoduché aplikace Hello World je všechny v souboru Program.cs. Otevřete tento soubor v oblíbeném textovém editoru. Jsme naši první změny.
V horní části souboru, najdete v článku using – příkaz:

```csharp
using System;
```

Tento příkaz sděluje kompilátoru, že všechny typy `System` obor názvů jsou v oboru. Jako objektově orientované jazyků, které jste mohli použít C# používá obory názvů pro uspořádání typů. Tento program Hello World se nijak neliší. Uvidíte, že je program uzavřeny v oboru názvů s názvem na základě názvu aktuálního adresáře. Pro účely tohoto kurzu Změníme název oboru názvů `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Čtení a zobrazování souboru

První funkce přidání je schopnost čtení z textového souboru a zobrazí tento text do konzoly. Nejprve přidáme do textového souboru. Kopírovat [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) soubor z úložiště GitHub pro tuto [ukázka](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře vašeho projektu. To bude sloužit jako skript pro vaši aplikaci. Pokud chcete informace o tom, jak stáhnout ukázkovou aplikaci pro toto téma, postupujte podle pokynů v [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) tématu.

V dalším kroku přidejte následující metodu do vaší `Program` třídy (přímo pod `Main` metoda):

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

Tato metoda používá typy z dva nové obory názvů. Pro tuto kompilaci je potřeba na začátek souboru přidejte následující dva řádky:

```csharp
using System.Collections.Generic;
using System.IO;
```

<xref:System.Collections.Generic.IEnumerable%601> Rozhraní je definováno v <xref:System.Collections.Generic> oboru názvů. <xref:System.IO.File> Třída je definována v <xref:System.IO> oboru názvů.

Tato metoda je speciální typ jazyka C# metodu s názvem *metody iterátoru*. Enumerátor metody vrací sekvence, které jsou vyhodnocovány laxně. To znamená, že každá položka v sekvenci se vygeneruje, jak to požadoval kód využívání sekvence. Enumerátor metody jsou metody, které obsahují jeden nebo více [ `yield return` ](../language-reference/keywords/yield.md) příkazy. Objekt vrácený rutinou `ReadFrom` metoda obsahuje kód pro vygenerování každé položky v sekvenci. V tomto příkladu, který zahrnuje čtení Zalamovat text ze zdrojového souboru a vrátí tento řetězec. Pokaždé, když volající kód požadavků na další položku z řady, kód načte Zalamovat text ze souboru a vrátí jej. Pokud soubor je zcela čtení, sekvence označuje, že neexistují žádné další položky.

Existují dva další C# prvky syntaxe, které mohou být pro vás nová. [ `using` ](../language-reference/keywords/using-statement.md) Příkaz v této metodě spravuje vyčištění prostředků. Proměnné, která je inicializována v `using` – příkaz (`reader`, v tomto příkladu), musí implementovat <xref:System.IDisposable> rozhraní. Toto rozhraní definuje jedinou metodu `Dispose`, která by měla být volána při prostředku by měly být vydány. Kompilátor generuje toto volání, když spuštění dosáhne složené závorce `using` příkazu. Kód generovaný kompilátorem zajistí, že prostředek je uvolněn i v případě, že dojde k výjimce z kódu v bloku určené na pomocí příkazu.

`reader` Proměnné definované `var` – klíčové slovo. [`var`](../language-reference/keywords/var.md) definuje *implicitně typované lokální proměnné*. To znamená, že typ proměnné je určen podle typu za kompilace objektu přiřazena k proměnné. Tady, který je návratová hodnota z <xref:System.IO.File.OpenText(System.String)> metodu, která je <xref:System.IO.StreamReader> objektu.

Teď Pojďme vyplnit kód ke čtení souboru v `Main` metody:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Spusťte program (pomocí `dotnet run`) a zobrazí se každý jednotlivý řádek tisknout do konzoly.

## <a name="adding-delays-and-formatting-output"></a>Přidávání zpoždění a formátování výstupu

Je nutné se zobrazí příliš rychle k nahlas. Teď budete muset přidat zpoždění ve výstupu. Když začnete, budete mít sestavování, některé základní kód, který umožňuje asynchronní zpracování. První postup se postupujte podle několika antimodely. Antimodely jsou uvedli v komentářích jako přidat kód a kód bude aktualizován v dalších krocích.

Existují dva kroky k této sekci. Nejprve budete aktualizovat metodu iterátoru k vrácení jednoho slova místo celé řádky. Který se provádí s těmito úpravami. Nahradit `yield return line;` příkaz následujícím kódem:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Dále je třeba upravit, jak využívat řádky souboru a přidání zpoždění po zápisu všech slov. Nahradit `Console.WriteLine(line)` výroky `Main` metodu s následující blok:

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

<xref:System.Threading.Tasks.Task> Hodina může začít <xref:System.Threading.Tasks> obor názvů, takže je třeba ho přidat `using` příkazu v horní části souboru:

```csharp
using System.Threading.Tasks;
```

Spusťte ukázku a podívejte se ve výstupu. Teď je vytištěna každý jednoho slova, za nímž následuje zpožděním 200 ms. Ale zobrazené výstup ukazuje některé problémy, protože text souboru zdroje má několik řádků, které mají více než 80 znaků bez konce řádku. Může být obtížné číst, zatímco je posouvání. To je snadno to vyřešíme. Stejně budete udržovat přehled o délce každý řádek a generovat nový řádek pokaždé, když se dosáhne určité prahové hodnoty délky řádku. Deklarujte místní proměnné po deklaraci `words` v `ReadFrom` metodu, která obsahuje délky řádku:

```csharp
var lineLength = 0;
```

Potom přidejte následující kód za `yield return word + " ";` – příkaz (před pravou složenou závorku):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Spusťte ukázku a budete moct rychlost čtení na její předem nakonfigurovaná tempu.

## <a name="async-tasks"></a>Úloh s modifikátorem Async

V tomto posledním kroku budete přidejte kód pro zápis výstupu asynchronně v jednom úkolu, při vstupu od uživatele, pokud je to vyžadováno pro urychlení nebo zpomalit zobrazení textu také běží jiné úlohy ke čtení nebo úplně zastavit zobrazení textu. Tato akce nemá několika krocích a do konce, budete mít všechny aktualizace, které potřebujete.
Prvním krokem je vytvoření asynchronní <xref:System.Threading.Tasks.Task> vrací metoda, která představuje kód zatím jste vytvořili pro čtení a zobrazení souboru.

Přidejte tuto metodu za účelem vaše `Program` třídy (je převzata z těla vaše `Main` metoda):

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

Můžete si všimnout dvou změn. První v těle metody, namísto volání metody <xref:System.Threading.Tasks.Task.Wait> synchronně čekat na dokončení úlohy, používá tato verze `await` – klíčové slovo. Abyste to mohli udělat, budete muset přidat `async` modifikátor do podpisu metody. Tato metoda vrátí hodnotu `Task`. Všimněte si, že neexistují žádné návratové příkazy, které vracejí `Task` objektu. Místo toho, který `Task` kódem, vygeneruje kompilátor při použití je vytvořen objekt `await` operátor. Představte si, že tato metoda vrátí při dosažení `await`. Vrácený `Task` označuje, že práce nebyla dokončena.
Metoda obnoví při dokončení očekávané úlohy. Když po provedení do konce, vrácený `Task` označuje, že je dokončeno.
Volání kódu můžete sledovat, která vrátila `Task` k určení, kdy bude uvolňování dokončeno.

Tato nová metoda může volat v vaše `Main` metody:

```csharp
ShowTeleprompter().Wait();
```

Tady v `Main`, kód synchronně čekání. Měli byste použít `await` operátor místo synchronním čekání, kdykoli je to možné. Ale v konzolové aplikaci `Main` metodu, nelze použít `await` operátor. Bude výsledkem ukončení aplikace předtím, než se dokončí všechny úlohy.

> [!NOTE]
> Pokud používáte C# 7.1 nebo novější, můžete vytvořit konzolové aplikace s [ `async` `Main` metoda](../whats-new/csharp-7-1.md#async-main).

Dále je třeba zadat druhý asynchronní metodu ke čtení z konzoly a podívejte se ' <' (méně než), ">" (větší) a "X" nebo "x" klíče. Tady je pro tuto úlohu, které přidáte metodu:

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
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

Tím se vytvoří pro reprezentaci výrazu lambda <xref:System.Action> delegáta, který čte klíč z konzoly a upravuje místní proměnnou představující zpoždění, když uživatel stiskne ' <' (méně než) nebo ">" (větší) klíče. Metody delegáta dokončí, když uživatel stiskne "X" nebo "x" klíče, které uživateli umožní zastavit zobrazení textu v každém okamžiku.
Tato metoda používá <xref:System.Console.ReadKey> blokovat a čekat, uživatel ke stisknutí klávesy.

Dokončete tuto funkci je potřeba vytvořit nový `async Task` vrací metoda, která spustí oba z těchto úloh (`GetInput` a `ShowTeleprompter`) a také spravuje sdílených dat mezi těmito dvěma úkoly.

Je čas vytvořit třídu, která dokáže zpracovat sdílených dat mezi těmito dvěma úkoly. Tato třída obsahuje dvě veřejné vlastnosti: zpoždění a příznak `Done` k označení zcela čtení souboru:

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

Vložit tuto třídu do nového souboru a použijte tuto třídu v `TeleprompterConsole` obor názvů, jak je znázorněno výše. Také budete muset přidat `using static` příkaz tak, aby můžete odkazovat `Min` a `Max` metody bez nadřazené třídy nebo oboru názvů. A [ `using static` ](../language-reference/keywords/using-static.md) příkaz importuje metody z jedné třídy. To je rozdíl od s `using` do této chvíle používat příkazy, které jste importovali všechny třídy z oboru názvů.

```csharp
using static System.Math;
```

Jiné, která je nová funkce jazyk je [ `lock` ](../language-reference/keywords/lock-statement.md) příkazu. Tento příkaz zajistí, že pouze jedno vlákno může být v kódu v daném okamžiku. Pokud jedno vlákno je v uzamčeném části, ostatní vlákna třeba vyčkat na dokončení první vlákno pro ukončení tohoto oddílu. `lock` Příkaz používá objekt, který chrání zamknout oddíl. Tato třída se řídí standardní idiom uzamknout privátní objekt ve třídě.

V dalším kroku je potřeba aktualizovat `ShowTeleprompter` a `GetInput` metod používaných nové `config` objektu. Zápis jeden konečný `Task` vrácení `async` metoda obě úlohy spuštění a ukončení po dokončení první úlohy:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Je zde jeden novou metodu <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> volání. Který vytváří `Task` , který dokončí, jakmile se dokončí všechny úlohy ve svém seznamu argumentů.

Dále je třeba oba aktualizovat `ShowTeleprompter` a `GetInput` metod používaných `config` objekt pro zpoždění:

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
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

Tato nová verze `ShowTeleprompter` volá novou metodu `TeleprompterConfig` třídy. Teď, budete muset aktualizovat `Main` volat `RunTeleprompter` místo `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Závěr

Tento kurz vám ukázal, že jste celou řadu funkcí jazyka C# a knihovny .NET Core týkající se práce v konzolových aplikacích.
Můžete sestavit s bližším prozkoumáváním jazyka a tříd sem zavedl tyto znalosti. Jste se seznámili se základy souborové služby a konzoly vstupně-výstupních operací, blokujících a neblokujících použití asynchronní programování založené na úlohách, prohlídka jazyka C# a jak jsou uspořádány programy jazyka C# a rozhraní příkazového řádku .NET Core a nástroje.

Další informace o vstupně-výstupní operace souboru, najdete v článku [Souborová služba a vstupně-výstupní operace Stream](../../standard/io/index.md) tématu. Další informace o asynchronní programovací model použitý v tomto kurzu, najdete v článku [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) tématu a [asynchronní programování](../async.md) tématu.
