---
title: Konzolová aplikace
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 4324b25daa253b3d2446955ad9ca57c2f0294f0c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851018"
---
# <a name="console-application"></a>Konzolová aplikace

V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce. Naučíte se:

- Základní informace o rozhraní příkazového řádku .NET Core (CLI)
- Struktura C# konzolové aplikace
- I/O konzoly
- Základy vstupně-výstupních rozhraní API souborů v .NET
- Základy asynchronního programování založeného na úlohách v .NET

Vytvoříte aplikaci, která přečte textový soubor, a vrátí obsah tohoto textového souboru do konzoly. Výstup do konzoly je TEMP, aby odpovídal čtení, které nahlasuje. Tempo můžete zrychlit nebo zpomalit stisknutím klávesy < (menší než) nebo > (větší než).

V tomto kurzu máte spoustu funkcí. Pojďme je sestavit jednou po jednom.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač, aby běžel .NET Core. Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) . Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.
Budete muset nainstalovat svůj oblíbený editor kódu.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Zajistěte, aby byl aktuální adresář. Zadejte příkaz `dotnet new console` na příkazovém řádku. Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".

Než začnete s úpravami, Projděte si postup spuštění jednoduché aplikace Hello World. Po vytvoření aplikace zadejte `dotnet restore` do příkazového řádku. Tento příkaz spustí proces obnovení balíčku NuGet. NuGet je správce balíčků .NET. Tento příkaz stáhne všechny chybějící závislosti pro váš projekt. Vzhledem k tomu, že se jedná o nový projekt, není zavedena žádná závislost, takže první spuštění stáhne rozhraní .NET Core Framework. Po provedení tohoto počátečního kroku budete muset spustit `dotnet restore` jenom při přidávání nových závislých balíčků nebo při aktualizaci verzí jakékoli závislosti.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po obnovení balíčků spustíte `dotnet build`. Tím se spustí sestavovací modul a vytvoří se spustitelný soubor aplikace. Nakonec můžete `dotnet run` spustit aplikaci.

Jednoduchý Hello World kód aplikace je v Program.cs. Otevřete tento soubor ve svém oblíbeném textovém editoru. Chystáme se udělat první změny.
V horní části souboru se podívejte na příkaz using:

```csharp
using System;
```

Tento příkaz instruuje kompilátor, že všechny typy z `System` oboru názvů jsou v oboru. Podobně jako u jiných objektů orientovaných na objekty, C# které jste pravděpodobně použili, používá obory názvů k uspořádání typů. Tento program Hello World není jiný. Můžete vidět, že program je uzavřen v oboru názvů s názvem na základě názvu aktuálního adresáře. Pro účely tohoto kurzu změňte název oboru názvů na `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Čtení a vracení souboru se souborem

První funkcí, kterou je třeba přidat, je možnost číst textový soubor a zobrazit celý tento text v konzole. Nejprve přidáme textový soubor. Zkopírujte soubor [sampleQuotes. txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z úložiště GitHub pro tuto [ukázku](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu. Tato akce bude sloužit jako skript pro vaši aplikaci. Pokud chcete získat informace o tom, jak stáhnout ukázkovou aplikaci pro toto téma, přečtěte si pokyny v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) .

Dále do `Program` třídy přidejte následující metodu (hned `Main` pod metodu):

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

Rozhraní je definováno <xref:System.Collections.Generic> v oboru názvů. <xref:System.Collections.Generic.IEnumerable%601> Třída je definována <xref:System.IO> v oboru názvů. <xref:System.IO.File>

Tato metoda je speciální typ C# metody označované jako *Metoda iterátoru*. Metody enumerátoru vracejí sekvence, které jsou vyhodnocovány laxně vytvářená. To znamená, že každá položka v sekvenci je vygenerována tak, jak je požadována kódem, který spotřebovává sekvenci. Metody enumerátoru jsou metody, které obsahují jeden [`yield return`](../language-reference/keywords/yield.md) nebo více příkazů. Objekt vrácený `ReadFrom` metodou obsahuje kód pro vygenerování každé položky v sekvenci. V tomto příkladu zahrnuje čtení dalšího řádku textu ze zdrojového souboru a vrácení tohoto řetězce. Pokaždé, když volající kód požádá o další položku z sekvence, kód přečte další řádek textu ze souboru a vrátí jej. Když je soubor kompletně načtený, sekvence indikuje, že nejsou k dispozici žádné další položky.

Existují dva další C# prvky syntaxe, které mohou být pro vás nové. [`using`](../language-reference/keywords/using-statement.md) Příkaz v této metodě spravuje čištění prostředků. Proměnná, která je inicializována v `using` příkazu (`reader`v tomto <xref:System.IDisposable> příkladu), musí implementovat rozhraní. Toto rozhraní definuje jedinou metodu `Dispose`, která by měla být volána, když má být prostředek uvolněn. Kompilátor vygeneruje toto volání, když provádění dosáhne uzavírací závorce `using` příkazu. Kód generovaný kompilátorem zajišťuje uvolnění prostředku i v případě, že je vyvolána výjimka z kódu v bloku definovaném příkazem using.

Proměnná je definována `var` pomocí klíčového slova. `reader` [`var`](../language-reference/keywords/var.md)definuje *implicitní typovou lokální proměnnou*. To znamená, že typ proměnné je určen typem pro čas kompilace objektu přiřazeného k proměnné. Zde je návratová hodnota z <xref:System.IO.File.OpenText(System.String)> metody, což <xref:System.IO.StreamReader> je objekt.

Teď naplníme kód, abychom si mohli přečíst soubor v `Main` metodě:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Spusťte program (pomocí `dotnet run`) a můžete zobrazit všechny vytištěné řádky do konzoly.

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

Dále je nutné upravit způsob, jakým se vybírají řádky souboru, a po zápisu každého slova přidat prodlevu. Nahraďte `Main` příkaz v metodě následujícím blokem: `Console.WriteLine(line)`

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

Třída je v oboru názvů, takže je nutné přidat tento `using` příkaz na začátek souboru: <xref:System.Threading.Tasks> <xref:System.Threading.Tasks.Task>

```csharp
using System.Threading.Tasks;
```

Spusťte ukázku a podívejte se na výstup. Nyní se vytisknou všechna jednotlivá slova následovaná zpožděním 200 ms. Zobrazený výstup však ukazuje některé problémy, protože zdrojový textový soubor obsahuje několik řádků, které mají více než 80 znaků bez zalomení řádku. To může být obtížné číst, zatímco se posunuje. To se dá snadno opravit. Pouze budete sledovat délku každého řádku a vygenerujete nový řádek vždy, když délka řádku dosáhne určité prahové hodnoty. Deklarovat místní proměnnou za deklarací `words` `ReadFrom` v metodě, která obsahuje délku řádku:

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

V tomto posledním kroku přidáte kód pro asynchronní zápis výstupu do jedné úlohy a zároveň spustíte jiný úkol pro čtení vstupu od uživatele, pokud chtějí zrychlit nebo zpomalit zobrazení textu, nebo ukončit zobrazování textu. V tomto případě je to několik kroků a na konci budete mít k dispozici všechny potřebné aktualizace.
Prvním krokem je vytvořit asynchronní <xref:System.Threading.Tasks.Task> návratovou metodu, která představuje kód, který jste dosud vytvořili pro čtení a zobrazení souboru.

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

Všimnete si dvou změn. Nejprve v těle metody namísto volání <xref:System.Threading.Tasks.Task.Wait> synchronního čekání na dokončení úlohy `await` používá tato verze klíčové slovo. K tomu je nutné přidat `async` modifikátor do podpisu metody. Tato metoda vrátí `Task`. Všimněte si, že neexistují žádné návratové příkazy `Task` , které vracejí objekt. Místo toho `await` je objektvytvořenpomocíkódu,kterýkompilátorgenerujepři`Task` použití operátoru. Můžete si představit, že tato metoda vrátí, když dosáhne `await`. Vrácená `Task` zpráva znamená, že práce nebyla dokončena.
Metoda pokračuje, až se dokončí očekávaný úkol. Když se provede dokončení, vrátí `Task` se na to, že se dokončilo.
Volání kódu může sledovat, že `Task` bylo vráceno, aby bylo možné určit, kdy bylo dokončeno.

Tuto novou metodu můžete zavolat v `Main` metodě:

```csharp
ShowTeleprompter().Wait();
```

Zde v `Main`nástroji kód asynchronně čeká. Místo synchronního čekání `await` , pokud je to možné, byste měli použít operátor. Ale v `Main` metodě konzolové aplikace nemůžete `await` použít operátor. To by vedlo k ukončení aplikace před dokončením všech úloh.

> [!NOTE]
> Pokud používáte C# 7,1 nebo novější, můžete vytvořit konzolové aplikace s [ `async` `Main` metodou](../whats-new/csharp-7-1.md#async-main).

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

Tím se vytvoří výraz lambda, který reprezentuje <xref:System.Action> delegáta, který přečte klíč z konzoly, a upraví místní proměnnou představující zpoždění, když uživatel stiskne klávesu ' < ' (menší než) nebo ' > ' (větší než). Metoda Delegate se dokončí, když uživatel stiskne klávesy X nebo x, které uživateli umožňují zastavit zobrazování textu kdykoli.
Tato metoda používá <xref:System.Console.ReadKey> k blokování a čekání, až uživatel stiskne klávesu.

K dokončení této funkce je nutné vytvořit novou `async Task` návratovou metodu, která spustí obě tyto úlohy (`GetInput` a `ShowTeleprompter`), a také spravovat sdílená data mezi těmito dvěma úkoly.

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

Tuto třídu vložte do nového souboru a vložte tuto třídu do `TeleprompterConsole` oboru názvů, jak je uvedeno výše. Budete také muset přidat `using static` příkaz, abyste mohli odkazovat na `Min` metody a `Max` bez názvů ohraničující třídy nebo oboru názvů. [`using static`](../language-reference/keywords/using-static.md) Příkaz naimportuje metody z jedné třídy. To je v kontrastu s `using` příkazy použitými do tohoto bodu, které importovaly všechny třídy z oboru názvů.

```csharp
using static System.Math;
```

Dále je nutné aktualizovat `ShowTeleprompter` metody a `GetInput` pro použití nového `config` objektu. Napsat jednu finální `Task` metodu `async` vrácení, která spustí úlohy a ukončí po dokončení první úlohy:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Jednou z metod je <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> toto volání. Tím se vytvoří `Task` , který se dokončí, jakmile se dokončí libovolný úkol v seznamu argumentů.

Dále je nutné aktualizovat `ShowTeleprompter` metody a `GetInput` pro použití `config` objektu pro zpoždění:

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

Tato nová verze `ShowTeleprompter` volá novou metodu `TeleprompterConfig` ve třídě. Nyní je třeba aktualizovat `Main` volání `RunTeleprompter` na místo `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Závěr

V tomto kurzu jste si ukázali, kolik funkcí kolem C# jazyka a knihoven .NET Core souvisí s prací v konzolových aplikacích.
Na základě těchto znalostí můžete prozkoumat další informace o jazyce a třídách, které jsou zde zavedeny. Seznámili jste se se základy pro vstupně-výstupní operace se soubory a konzolou, blokování a neblokování použití asynchronního programování založeného na úlohách C# , prohlídku C# jazyka a způsobu uspořádání programů a rozhraní příkazového řádku .NET Core a nástroje.

Další informace o vstupně-výstupních operacích souborů najdete v tématu [vstupně-výstupní operace se soubory a datovým proudem](../../standard/io/index.md) . Další informace o modelu asynchronního programování používaném v tomto kurzu naleznete v tématu [asynchronní programování založené na úlohách](../..//standard/parallel-programming/task-based-asynchronous-programming.md) a v tématu věnovaném [asynchronnímu programování](../async.md) .
