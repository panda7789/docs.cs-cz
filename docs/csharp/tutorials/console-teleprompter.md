---
title: Konzolová aplikace
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 921c8fc7824bdb48f08e4d9f5a276bf2284f8a17
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714606"
---
# <a name="console-app"></a>Konzolová aplikace

V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce. Dozvíte se:

- Základní informace o rozhraní příkazového řádku .NET Core (CLI)
- Struktura C# konzolové aplikace
- I/O konzoly
- Základy vstupně-výstupních rozhraní API souborů v .NET
- Základy asynchronního programování založeného na úlohách v .NET

Vytvoříte aplikaci, která přečte textový soubor, a vrátí obsah tohoto textového souboru do konzoly. Výstup do konzoly je TEMP, aby odpovídal čtení, které nahlasuje. Tempo můžete zrychlit nebo zpomalit stisknutím klávesy < (menší než) nebo > (větší než).

V tomto kurzu máte spoustu funkcí. Pojďme je sestavit jednou po jednom.

## <a name="prerequisites"></a>Požadavky

- Nastavte počítač tak, aby běžel .NET Core. Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) . Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.

- Nainstalujte svůj oblíbený editor kódu.

## <a name="create-the-app"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Zajistěte, aby byl aktuální adresář. Do příkazového řádku zadejte příkaz `dotnet new console`. Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".

Než začnete s úpravami, Projděte si postup spuštění jednoduché aplikace Hello World. Po vytvoření aplikace zadejte do příkazového řádku `dotnet restore`. Tento příkaz spustí proces obnovení balíčku NuGet. NuGet je správce balíčků .NET. Tento příkaz stáhne všechny chybějící závislosti pro váš projekt. Vzhledem k tomu, že se jedná o nový projekt, není zavedena žádná závislost, takže první spuštění stáhne rozhraní .NET Core Framework. Po provedení tohoto počátečního kroku budete muset spouštět `dotnet restore` jenom při přidávání nových závislých balíčků nebo při aktualizaci verzí jakékoli závislosti.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po obnovení balíčků spustíte `dotnet build`. Tím se spustí sestavovací modul a vytvoří se spustitelný soubor aplikace. Nakonec vykonáte `dotnet run` ke spuštění aplikace.

Jednoduchý Hello World kód aplikace je v Program.cs. Otevřete tento soubor ve svém oblíbeném textovém editoru. Chystáme se udělat první změny. V horní části souboru se podívejte na příkaz using:

```csharp
using System;
```

Tento příkaz instruuje kompilátor, že všechny typy z oboru názvů `System` jsou v oboru. Podobně jako u jiných objektů orientovaných na objekty, C# které jste pravděpodobně použili, používá obory názvů k uspořádání typů. Tento program Hello World není jiný. Můžete vidět, že program je uzavřen v oboru názvů s názvem na základě názvu aktuálního adresáře. Pro účely tohoto kurzu změňte název oboru názvů na `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Čtení a vracení souboru se souborem

První funkcí, kterou je třeba přidat, je možnost číst textový soubor a zobrazit celý tento text v konzole. Nejprve přidáme textový soubor. Zkopírujte soubor [sampleQuotes. txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z úložiště GitHub pro tuto [ukázku](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu. Tato akce bude sloužit jako skript pro vaši aplikaci. Pokud chcete získat informace o tom, jak stáhnout ukázkovou aplikaci pro toto téma, přečtěte si pokyny v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) .

Dále přidejte následující metodu do třídy `Program` (přímo pod `Main` metodu):

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

Rozhraní <xref:System.Collections.Generic.IEnumerable%601> je definováno v oboru názvů <xref:System.Collections.Generic>. Třída <xref:System.IO.File> je definována v oboru názvů <xref:System.IO>.

Tato metoda je speciální typ C# metody označované jako *Metoda iterátoru*. Metody enumerátoru vracejí sekvence, které jsou vyhodnocovány laxně vytvářená. To znamená, že každá položka v sekvenci je vygenerována tak, jak je požadována kódem, který spotřebovává sekvenci. Metody enumerátoru jsou metody, které obsahují jeden nebo více příkazů [`yield return`](../language-reference/keywords/yield.md) . Objekt vrácený metodou `ReadFrom` obsahuje kód pro vygenerování každé položky v sekvenci. V tomto příkladu zahrnuje čtení dalšího řádku textu ze zdrojového souboru a vrácení tohoto řetězce. Pokaždé, když volající kód požádá o další položku z sekvence, kód přečte další řádek textu ze souboru a vrátí jej. Když je soubor kompletně načtený, sekvence indikuje, že nejsou k dispozici žádné další položky.

Existují dva další C# prvky syntaxe, které mohou být pro vás nové. Příkaz [`using`](../language-reference/keywords/using-statement.md) v této metodě spravuje čištění prostředků. Proměnná, která je inicializována v příkazu `using` (`reader`v tomto příkladu), musí implementovat rozhraní <xref:System.IDisposable>. Toto rozhraní definuje jedinou metodu, `Dispose`, která by měla být volána, když by měl být prostředek uvolněn. Kompilátor vygeneruje toto volání, když provádění dosáhne uzavírací složené závorky příkazu `using`. Kód generovaný kompilátorem zajišťuje uvolnění prostředku i v případě, že je vyvolána výjimka z kódu v bloku definovaném příkazem using.

Proměnná `reader` je definována pomocí klíčového slova `var`. [`var`](../language-reference/keywords/var.md) definuje *implicitní typovou místní proměnnou*. To znamená, že typ proměnné je určen typem pro čas kompilace objektu přiřazeného k proměnné. Zde je návratová hodnota z metody <xref:System.IO.File.OpenText(System.String)>, což je objekt <xref:System.IO.StreamReader>.

Nyní vyplníme kód pro čtení souboru v metodě `Main`:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Spusťte program (pomocí `dotnet run`) a uvidíte všechny vytištěné řádky do konzoly.

## <a name="adding-delays-and-formatting-output"></a>Přidání zpoždění a formátování výstupu

To, co je ještě daleko příliš rychlé pro čtení nahlasu. Nyní je třeba přidat prodlevy ve výstupu. Při spuštění budete tvořit část základního kódu, který umožňuje asynchronní zpracování. Tyto první kroky se ale budou řídit několika anti vzory. Anti-patterny jsou v komentářích při přidávání kódu ukázány a kód se aktualizuje v pozdějších krocích.

Tato část obsahuje dva kroky. Nejprve aktualizujte metodu iterátoru tak, aby vracela jednoduchá slova namísto celých řádků. To se provádí s těmito úpravami. Nahraďte příkaz `yield return line;` následujícím kódem:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Dále je nutné upravit způsob, jakým se vybírají řádky souboru, a po zápisu každého slova přidat prodlevu. Nahraďte příkaz `Console.WriteLine(line)` v metodě `Main` následujícím blokem:

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

Třída <xref:System.Threading.Tasks.Task> je v oboru názvů <xref:System.Threading.Tasks>, takže je nutné přidat tento `using` příkaz do horní části souboru:

```csharp
using System.Threading.Tasks;
```

Spusťte ukázku a podívejte se na výstup. Nyní se vytisknou všechna jednotlivá slova následovaná zpožděním 200 ms. Zobrazený výstup však ukazuje některé problémy, protože zdrojový textový soubor obsahuje několik řádků, které mají více než 80 znaků bez zalomení řádku. To může být obtížné číst, zatímco se posunuje. To se dá snadno opravit. Pouze budete sledovat délku každého řádku a vygenerujete nový řádek vždy, když délka řádku dosáhne určité prahové hodnoty. Deklarovat místní proměnnou po deklaraci `words` v metodě `ReadFrom`, která obsahuje délku řádku:

```csharp
var lineLength = 0;
```

Poté přidejte následující kód za příkaz `yield return word + " ";` (před pravou závorku):

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

V tomto posledním kroku přidáte kód pro asynchronní zápis výstupu do jedné úlohy a zároveň spustíte jiný úkol pro čtení vstupu od uživatele, pokud chtějí zrychlit nebo zpomalit zobrazení textu, nebo ukončit zobrazování textu. V tomto případě je to několik kroků a na konci budete mít k dispozici všechny potřebné aktualizace. Prvním krokem je vytvoření metody, která vrací asynchronní <xref:System.Threading.Tasks.Task>, která představuje kód, který jste dosud vytvořili pro čtení a zobrazení souboru.

Přidejte tuto metodu do třídy `Program` (je pořízena z těla vaší `Main` metody):

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

Všimnete si dvou změn. Nejprve v těle metody namísto volání <xref:System.Threading.Tasks.Task.Wait> k synchronnímu čekání na dokončení úlohy používá tato verze klíčové slovo `await`. K tomu je nutné přidat modifikátor `async` k podpisu metody. Tato metoda vrací `Task`. Všimněte si, že neexistují žádné návratové příkazy, které vracejí objekt `Task`. Místo toho je objekt `Task` vytvořen pomocí kódu, který kompilátor generuje při použití operátoru `await`. Můžete si představit, že tato metoda vrátí, když dosáhne `await`. Vrácený `Task` značí, že práce nebyla dokončena. Metoda pokračuje, až se dokončí očekávaný úkol. Když se provede dokončení, vrátí `Task`, že je to hotové.
Volání kódu může monitorovat, který vrátil `Task` k určení, kdy byl dokončen.

Tuto novou metodu můžete zavolat v metodě `Main`:

```csharp
ShowTeleprompter().Wait();
```

Zde v `Main`kód asynchronně čeká. Místo synchronního čekání vždy, když je to možné, byste měli použít operátor `await`. Ale v metodě `Main` konzolové aplikace nemůžete použít operátor `await`. To by vedlo k ukončení aplikace před dokončením všech úloh.

> [!NOTE]
> Pokud používáte C# 7,1 nebo novější, můžete vytvořit konzolové aplikace pomocí [metody`async` `Main`](../whats-new/csharp-7-1.md#async-main).

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

Tím se vytvoří výraz lambda, který představuje delegáta <xref:System.Action>, který přečte klíč z konzoly, a upraví místní proměnnou představující zpoždění, když uživatel stiskne klávesu < (menší než) nebo ' > ' (větší než). Metoda Delegate se dokončí, když uživatel stiskne klávesy X nebo x, které uživateli umožňují zastavit zobrazování textu kdykoli. Tato metoda používá <xref:System.Console.ReadKey> k blokování a čekání na stisknutí klávesy uživatelem.

Chcete-li tuto funkci dokončit, je nutné vytvořit novou `async Task` vracející metodu, která spustí obě tyto úlohy (`GetInput` a `ShowTeleprompter`), a také spravovat sdílená data mezi těmito dvěma úkoly.

Je čas vytvořit třídu, která může zpracovávat sdílená data mezi těmito dvěma úkoly. Tato třída obsahuje dvě veřejné vlastnosti: zpoždění a příznak `Done` k označení toho, že soubor byl zcela načten:

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

Tuto třídu vložte do nového souboru a vložte tuto třídu do oboru názvů `TeleprompterConsole`, jak je uvedeno výše. Také je nutné přidat příkaz `using static`, aby bylo možné odkazovat na metody `Min` a `Max` bez ohraničujících názvů třídy nebo oboru názvů. Příkaz [`using static`](../language-reference/keywords/using-static.md) importuje metody z jedné třídy. To je v kontrastu s příkazy `using` použitými do tohoto bodu, které importovaly všechny třídy z oboru názvů.

```csharp
using static System.Math;
```

Dále je nutné aktualizovat `ShowTeleprompter` a `GetInput` metody pro použití nového objektu `config`. Napsat jednu finální `Task` vracející `async` metodu, která spustí úlohy a ukončí po dokončení první úlohy:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Jednou z nových metod je <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> volání. Tím se vytvoří `Task`, který skončí hned po dokončení všech úkolů v seznamu argumentů.

Dál je potřeba aktualizovat `ShowTeleprompter` i `GetInput` metody tak, aby pro zpoždění používaly objekt `config`:

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

Tato nová verze `ShowTeleprompter` volá novou metodu ve třídě `TeleprompterConfig`. Teď je potřeba aktualizovat `Main` pro volání `RunTeleprompter` namísto `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Závěr

V tomto kurzu jste si ukázali, kolik funkcí kolem C# jazyka a knihoven .NET Core souvisí s prací v konzolových aplikacích. Na základě těchto znalostí můžete prozkoumat další informace o jazyce a třídách, které jsou zde zavedeny. Seznámili jste se se základy pro vstupně-výstupní operace se soubory a konzolou, blokování a neblokování použití asynchronního programování založeného na úlohách C# , prohlídku C# jazyka a způsobu uspořádání programů a rozhraní příkazového řádku .NET Core a nástroje.

Další informace o vstupně-výstupních operacích souborů najdete v tématu [vstupně-výstupní operace se soubory a datovým proudem](../../standard/io/index.md) . Další informace o modelu asynchronního programování používaném v tomto kurzu naleznete v tématu [asynchronní programování založené na úlohách](../..//standard/parallel-programming/task-based-asynchronous-programming.md) a v tématu věnovaném [asynchronnímu programování](../async.md) .
