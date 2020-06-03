---
title: Konzolová aplikace
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v jazyce C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 06affa01b67edeea09088834cf131adb55650bbb
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794660"
---
# <a name="console-app"></a>Konzolová aplikace

V tomto kurzu se naučíte řadou funkcí v .NET Core a v jazyce C#. Naučíte se:

- Základy .NET Core CLI
- Struktura konzolové aplikace v jazyce C#
- I/O konzoly
- Základy vstupně-výstupních rozhraní API souborů v .NET
- Základy asynchronního programování založeného na úlohách v .NET

Vytvoříte aplikaci, která přečte textový soubor, a vrátí obsah tohoto textového souboru do konzoly. Výstup do konzoly je TEMP, aby odpovídal čtení, které nahlasuje. Tempo můžete zrychlit nebo zpomalit stisknutím klávesy < (menší než) nebo > (větší než).

V tomto kurzu máte spoustu funkcí. Pojďme je sestavit jednou po jednom.

## <a name="prerequisites"></a>Požadavky

- Nastavte počítač tak, aby běžel .NET Core. Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) . Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.

- Nainstalujte svůj oblíbený editor kódu.

## <a name="create-the-app"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Zajistěte, aby byl aktuální adresář. Zadejte příkaz `dotnet new console` na příkazovém řádku. Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".

Než začnete s úpravami, Projděte si postup spuštění jednoduché aplikace Hello World. Po vytvoření aplikace zadejte do `dotnet restore` příkazového řádku. Tento příkaz spustí proces obnovení balíčku NuGet. NuGet je správce balíčků .NET. Tento příkaz stáhne všechny chybějící závislosti pro váš projekt. Vzhledem k tomu, že se jedná o nový projekt, není zavedena žádná závislost, takže první spuštění stáhne rozhraní .NET Core Framework. Po provedení tohoto počátečního kroku budete muset spustit jenom `dotnet restore` při přidávání nových závislých balíčků nebo při aktualizaci verzí jakékoli závislosti.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po obnovení balíčků spustíte `dotnet build` . Tím se spustí sestavovací modul a vytvoří se spustitelný soubor aplikace. Nakonec můžete spustit `dotnet run` aplikaci.

Jednoduchý Hello World kód aplikace je v Program.cs. Otevřete tento soubor ve svém oblíbeném textovém editoru. Chystáme se udělat první změny. V horní části souboru se podívejte na příkaz using:

```csharp
using System;
```

Tento příkaz instruuje kompilátor, že všechny typy z `System` oboru názvů jsou v oboru. Podobně jako u jiných objektů orientovaných na objekty, které jste pravděpodobně použili, jazyk C# používá obory názvů k uspořádání typů. Tento program Hello World není jiný. Můžete vidět, že program je uzavřen v oboru názvů s názvem na základě názvu aktuálního adresáře. Pro účely tohoto kurzu změňte název oboru názvů na `TeleprompterConsole` :

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Čtení a vracení souboru se souborem

První funkcí, kterou je třeba přidat, je možnost číst textový soubor a zobrazit celý tento text v konzole. Nejprve přidáme textový soubor. Zkopírujte soubor [sampleQuotes. txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z úložiště GitHub pro tuto [ukázku](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu. Tato akce bude sloužit jako skript pro vaši aplikaci. Pokud chcete získat informace o tom, jak stáhnout ukázkovou aplikaci pro toto téma, přečtěte si pokyny v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) .

Dále do třídy přidejte následující metodu `Program` (hned pod `Main` metodu):

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

Tato metoda používá typy ze dvou nových oborů názvů. Pro zkompilování je třeba do horní části souboru přidat následující dva řádky:

```csharp
using System.Collections.Generic;
using System.IO;
```

<xref:System.Collections.Generic.IEnumerable%601>Rozhraní je definováno v <xref:System.Collections.Generic> oboru názvů. <xref:System.IO.File>Třída je definována v <xref:System.IO> oboru názvů.

Tato metoda je speciální typ metody jazyka C# s názvem *Metoda iterátoru*. Metody enumerátoru vracejí sekvence, které jsou vyhodnocovány laxně vytvářená. To znamená, že každá položka v sekvenci je vygenerována tak, jak je požadována kódem, který spotřebovává sekvenci. Metody enumerátoru jsou metody, které obsahují jeden nebo více [`yield return`](../language-reference/keywords/yield.md) příkazů. Objekt vrácený `ReadFrom` metodou obsahuje kód pro vygenerování každé položky v sekvenci. V tomto příkladu zahrnuje čtení dalšího řádku textu ze zdrojového souboru a vrácení tohoto řetězce. Pokaždé, když volající kód požádá o další položku z sekvence, kód přečte další řádek textu ze souboru a vrátí jej. Když je soubor kompletně načtený, sekvence indikuje, že nejsou k dispozici žádné další položky.

Existují dva další prvky syntaxe jazyka C#, které mohou být pro vás nové. [`using`](../language-reference/keywords/using-statement.md)Příkaz v této metodě spravuje čištění prostředků. Proměnná, která je inicializována v `using` příkazu ( `reader` v tomto příkladu), musí implementovat <xref:System.IDisposable> rozhraní. Toto rozhraní definuje jedinou metodu, `Dispose` která by měla být volána, když má být prostředek uvolněn. Kompilátor vygeneruje toto volání, když provádění dosáhne uzavírací závorce `using` příkazu. Kód generovaný kompilátorem zajišťuje uvolnění prostředku i v případě, že je vyvolána výjimka z kódu v bloku definovaném příkazem using.

`reader`Proměnná je definována pomocí `var` klíčového slova. [`var`](../language-reference/keywords/var.md)definuje *implicitní typovou lokální proměnnou*. To znamená, že typ proměnné je určen typem pro čas kompilace objektu přiřazeného k proměnné. Zde je návratová hodnota z <xref:System.IO.File.OpenText(System.String)> metody, což je <xref:System.IO.StreamReader> objekt.

Teď naplníme kód, abychom si mohli přečíst soubor v `Main` metodě:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Spusťte program (pomocí `dotnet run` ) a můžete zobrazit všechny vytištěné řádky do konzoly.

## <a name="adding-delays-and-formatting-output"></a>Přidání zpoždění a formátování výstupu

To, co je ještě daleko příliš rychlé pro čtení nahlasu. Nyní je třeba přidat prodlevy ve výstupu. Při spuštění budete tvořit část základního kódu, který umožňuje asynchronní zpracování. Tyto první kroky se ale budou řídit několika anti vzory. Anti-patterny jsou v komentářích při přidávání kódu ukázány a kód se aktualizuje v pozdějších krocích.

Tato část obsahuje dva kroky. Nejprve aktualizujte metodu iterátoru tak, aby vracela jednoduchá slova namísto celých řádků. To se provádí s těmito úpravami. Nahraďte `yield return line;` příkaz následujícím kódem:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Dále je nutné upravit způsob, jakým se vybírají řádky souboru, a po zápisu každého slova přidat prodlevu. Nahraďte `Console.WriteLine(line)` příkaz v `Main` metodě následujícím blokem:

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

<xref:System.Threading.Tasks.Task>Třída je v <xref:System.Threading.Tasks> oboru názvů, takže je nutné přidat tento `using` příkaz na začátek souboru:

```csharp
using System.Threading.Tasks;
```

Spusťte ukázku a podívejte se na výstup. Nyní se vytisknou všechna jednotlivá slova následovaná zpožděním 200 ms. Zobrazený výstup však ukazuje některé problémy, protože zdrojový textový soubor obsahuje několik řádků, které mají více než 80 znaků bez zalomení řádku. To může být obtížné číst, zatímco se posunuje. To se dá snadno opravit. Pouze budete sledovat délku každého řádku a vygenerujete nový řádek vždy, když délka řádku dosáhne určité prahové hodnoty. Deklarovat místní proměnnou za deklarací `words` v `ReadFrom` metodě, která obsahuje délku řádku:

```csharp
var lineLength = 0;
```

Poté přidejte následující kód za `yield return word + " ";` příkaz (před pravou závorku):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Spusťte ukázku a budete moct číst nahlas v jeho předem nakonfigurovaném tempu.

## <a name="async-tasks"></a>Asynchronní úlohy

V tomto posledním kroku přidáte kód pro asynchronní zápis výstupu do jedné úlohy a zároveň spustíte jiný úkol pro čtení vstupu od uživatele, pokud chtějí zrychlit nebo zpomalit zobrazení textu, nebo ukončit zobrazování textu. V tomto případě je to několik kroků a na konci budete mít k dispozici všechny potřebné aktualizace. Prvním krokem je vytvořit asynchronní <xref:System.Threading.Tasks.Task> návratovou metodu, která představuje kód, který jste dosud vytvořili pro čtení a zobrazení souboru.

Přidejte tuto metodu do `Program` třídy (ta je pořízena z těla vaší `Main` metody):

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

Všimnete si dvou změn. Nejprve v těle metody namísto volání <xref:System.Threading.Tasks.Task.Wait> synchronního čekání na dokončení úlohy používá tato verze `await` klíčové slovo. K tomu je nutné přidat `async` modifikátor do podpisu metody. Tato metoda vrátí `Task` . Všimněte si, že neexistují žádné návratové příkazy, které vracejí `Task` objekt. Místo toho `Task` je objekt vytvořen pomocí kódu, který kompilátor generuje při použití `await` operátoru. Můžete si představit, že tato metoda vrátí, když dosáhne `await` . Vrácená zpráva `Task` znamená, že práce nebyla dokončena. Metoda pokračuje, až se dokončí očekávaný úkol. Když se provede dokončení, vrátí se na to `Task` , že se dokončilo.
Volání kódu může sledovat, že bylo vráceno, aby bylo možné `Task` určit, kdy bylo dokončeno.

Tuto novou metodu můžete zavolat v `Main` metodě:

```csharp
ShowTeleprompter().Wait();
```

Zde v nástroji `Main` kód asynchronně čeká. `await`Místo synchronního čekání, pokud je to možné, byste měli použít operátor. Ale v metodě konzolové aplikace `Main` nemůžete použít `await` operátor. To by vedlo k ukončení aplikace před dokončením všech úloh.

> [!NOTE]
> Používáte-li C# 7,1 nebo novější, můžete vytvořit konzolové aplikace s [ `async` `Main` metodou](../whats-new/csharp-7-1.md#async-main).

Dále je potřeba napsat druhou asynchronní metodu pro čtení z konzoly a sledovat "<" (menší než), ">" (větší než) a "X" nebo "klíče" x ". Zde je metoda, kterou přidáte pro tuto úlohu:

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

Tím se vytvoří výraz lambda <xref:System.Action> , který reprezentuje delegáta, který přečte klíč z konzoly, a upraví místní proměnnou představující zpoždění, když uživatel stiskne klávesu ' < ' (menší než) nebo ' > ' (větší než). Metoda Delegate se dokončí, když uživatel stiskne klávesy X nebo x, které uživateli umožňují zastavit zobrazování textu kdykoli. Tato metoda používá <xref:System.Console.ReadKey> k blokování a čekání, až uživatel stiskne klávesu.

K dokončení této funkce je nutné vytvořit novou `async Task` návratovou metodu, která spustí obě tyto úlohy ( `GetInput` a `ShowTeleprompter` ), a také spravovat sdílená data mezi těmito dvěma úkoly.

Je čas vytvořit třídu, která může zpracovávat sdílená data mezi těmito dvěma úkoly. Tato třída obsahuje dvě veřejné vlastnosti: zpoždění a příznak `Done` označující, že soubor byl zcela načten:

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

Tuto třídu vložte do nového souboru a vložte tuto třídu do `TeleprompterConsole` oboru názvů, jak je uvedeno výše. Budete také muset přidat `using static` příkaz, abyste mohli odkazovat na `Min` `Max` metody a bez názvů ohraničující třídy nebo oboru názvů. [`using static`](../language-reference/keywords/using-static.md)Příkaz naimportuje metody z jedné třídy. To je v kontrastu s `using` příkazy použitými do tohoto bodu, které importovaly všechny třídy z oboru názvů.

```csharp
using static System.Math;
```

Dále je nutné aktualizovat `ShowTeleprompter` `GetInput` metody a pro použití nového `config` objektu. Napsat jednu finální `Task` `async` metodu vrácení, která spustí úlohy a ukončí po dokončení první úlohy:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Jednou z metod je toto <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> volání. Tím se vytvoří `Task` , který se dokončí, jakmile se dokončí libovolný úkol v seznamu argumentů.

Dále je nutné aktualizovat `ShowTeleprompter` `GetInput` metody a pro použití `config` objektu pro zpoždění:

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
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

Tato nová verze `ShowTeleprompter` volá novou metodu ve `TeleprompterConfig` třídě. Nyní je třeba aktualizovat `Main` volání na `RunTeleprompter` místo `ShowTeleprompter` :

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Závěr

V tomto kurzu jste si ukázali řadu funkcí pro jazyk C# a knihovny .NET Core, které souvisejí s prací v konzolových aplikacích. Na základě těchto znalostí můžete prozkoumat další informace o jazyce a třídách, které jsou zde zavedeny. Seznámili jste se se základy pro vstupně-výstupní operace se soubory a konzolou, blokování a neblokování použití asynchronního programování založeného na úlohách, prohlídka jazyka C# a způsobu uspořádání programů v jazyce C# a .NET Core CLI.

Další informace o vstupně-výstupních operacích souborů najdete v tématu [vstupně-výstupní operace se soubory a datovým proudem](../../standard/io/index.md) . Další informace o modelu asynchronního programování používaném v tomto kurzu naleznete v tématu [asynchronní programování založené na úlohách](../../standard/parallel-programming/task-based-asynchronous-programming.md) a v tématu věnovaném [asynchronnímu programování](../async.md) .
