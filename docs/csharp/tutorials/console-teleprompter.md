---
title: Konzolová aplikace
description: Tento kurz vás naučí řadu funkcí v .NET Core a jazyk C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 09ce36e7a61f576dc4449976ce676701dc57c9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76921120"
---
# <a name="console-app"></a>Konzolová aplikace

Tento kurz vás naučí řadu funkcí v .NET Core a jazyk C#. Co se dozvíte:

- Základy rozhraní příkazového příkazu .NET Core
- Struktura aplikace konzoly Jazyka C#
- Vstupně-to-v konzole
- Základy rozhraní API vstupně-nosných souborů v rozhraní .NET
- Základy asynchronního programování založeného na úlohách v rozhraní .NET

Vytvoříte aplikaci, která přečte textový soubor a vrátí obsah tohoto textového souboru do konzoly. Výstup do konzoly je přecházel tak, aby odpovídal jeho hlasitému čtení. Tempo můžete zrychlit nebo zpomalit stisknutím kláves "<" (menší než) nebo ">" (větší než).

Existuje mnoho funkcí v tomto tutoriálu. Postavíme je jeden po druhém.

## <a name="prerequisites"></a>Požadavky

- Nastavte počítač tak, aby spouštěl .NET Core. Pokyny k instalaci naleznete na stránce [ke stažení jádra .NET.](https://dotnet.microsoft.com/download) Tuto aplikaci můžete spustit ve Windows, Linuxu, macOS nebo v kontejneru Dockeru.

- Nainstalujte si svůj oblíbený editor kódu.

## <a name="create-the-app"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Ať je to aktuální adresář. Zadejte `dotnet new console` příkaz na příkazovém řádku. Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".

Než začnete provádět úpravy, pojďme projít kroky ke spuštění jednoduché aplikace Hello World. Po vytvoření aplikace `dotnet restore` zadejte příkaz na příkazovém řádku. Tento příkaz spustí proces obnovení balíčku NuGet. NuGet je správce balíčků .NET. Tento příkaz stáhne všechny chybějící závislosti pro váš projekt. Vzhledem k tomu, že se jedná o nový projekt, žádná ze závislostí není na místě, takže první spuštění stáhne rozhraní .NET Core framework. Po tomto počátečním kroku budete `dotnet restore` muset spustit pouze při přidání nových závislých balíčků nebo aktualizaci verzí některé z vašich závislostí.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po obnovení balíčků spustíte `dotnet build`. To spustí modul sestavení a vytvoří spustitelný soubor aplikace. Nakonec spustit `dotnet run` spuštění aplikace.

Jednoduchý kód aplikace Hello World je vše v Program.cs. Otevřete tento soubor pomocí oblíbeného textového editoru. Chystáme se udělat první změny. V horní části souboru, viz using prohlášení:

```csharp
using System;
```

Tento příkaz říká kompilátoru, `System` že všechny typy z oboru názvů jsou v oboru. Stejně jako ostatní objektově orientované jazyky, které jste použili, c# používá obory názvů k uspořádání typů. Tento program Hello World se nijak neliší. Můžete vidět, že program je uzavřen v oboru názvů s názvem založeným na názvu aktuálního adresáře. V tomto kurzu změníme název oboru názvů `TeleprompterConsole`na :

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Čtení a ozvěna souboru

První funkcí, kterou chcete přidat, je možnost číst textový soubor a zobrazit veškerý text do konzoly. Nejprve přidáme textový soubor. Zkopírujte soubor [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z úložiště GitHub pro tuto [ukázku](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu. To bude sloužit jako skript pro vaši aplikaci. Pokud chcete informace o tom, jak stáhnout ukázkovou aplikaci pro toto téma, přečtěte si pokyny v tématu [Ukázky a výukové lekce.](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)

Dále přidejte následující metodu ve `Program` své `Main` třídě (přímo pod metodu):

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

Tato metoda používá typy ze dvou nových oborů názvů. Aby se toto zkompilovalo, budete muset na začátek souboru přidat následující dva řádky:

```csharp
using System.Collections.Generic;
using System.IO;
```

Rozhraní <xref:System.Collections.Generic.IEnumerable%601> je definováno <xref:System.Collections.Generic> v oboru názvů. Třída <xref:System.IO.File> je definována <xref:System.IO> v oboru názvů.

Tato metoda je zvláštní typ metody Jazyka C# nazývaný *metodou Iterátor*. Metody výčtu vracejí sekvence, které jsou vyhodnocovány líně. To znamená, že každá položka v pořadí je generována tak, jak je požadována kódem, který tuto sekvenci spotřebovává. Metody výčtu jsou metody, které [`yield return`](../language-reference/keywords/yield.md) obsahují jeden nebo více příkazů. Objekt vrácený `ReadFrom` metodou obsahuje kód pro generování každé položky v sekvenci. V tomto příkladu, který zahrnuje čtení dalšího řádku textu ze zdrojového souboru a vrácení tohoto řetězce. Pokaždé, když volající kód požaduje další položku z sekvence, kód přečte další řádek textu ze souboru a vrátí jej. Když je soubor zcela přečten, sekvence označuje, že neexistují žádné další položky.

Existují dva další prvky syntaxe jazyka C#, které mohou být pro vás nové. Příkaz [`using`](../language-reference/keywords/using-statement.md) v této metodě spravuje vyčištění prostředků. Proměnná, která je `using` inicializována v příkazu (`reader`, v tomto příkladu) musí implementovat <xref:System.IDisposable> rozhraní. Toto rozhraní definuje jednu metodu , `Dispose`která by měla být volána, když by měl být prostředek uvolněn. Kompilátor generuje toto volání při spuštění dosáhne `using` uzavírací složená závorka příkazu. Kód generovaný kompilátorem zajišťuje, že prostředek je uvolněna i v případě, že je vyvolána výjimka z kódu v bloku definované using prohlášení.

Proměnná `reader` je definována pomocí klíčového `var` slova. [`var`](../language-reference/keywords/var.md)definuje *implicitně zadali místní proměnné*. To znamená, že typ proměnné je určen typem kompilace objektu přiřazeného proměnné. Zde je vrácená hodnota <xref:System.IO.File.OpenText(System.String)> z metody, <xref:System.IO.StreamReader> která je objekt.

Nyní vyplníme kód a přečteme `Main` soubor v metodě:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Spusťte program `dotnet run`(pomocí) a uvidíte všechny linky vytištěné na konzoli.

## <a name="adding-delays-and-formatting-output"></a>Přidání zpoždění a formátování výstupu

To, co máte, je zobrazeno příliš rychle na to, abyste to bylo nahlas. Nyní je třeba přidat zpoždění ve výstupu. Při spuštění budete vytvářet některé základní kód, který umožňuje asynchronní zpracování. Nicméně, tyto první kroky budou následovat několik anti-vzory. Anti-vzory jsou zdůrazněny v komentářích při přidávání kódu a kód bude aktualizován v pozdějších krocích.

V této části jsou dva kroky. Nejprve aktualizujete metodu iterátoru, abyste vrátili jednotlivá slova namísto celých řádků. To je hotovo s těmito úpravami. Nahraďte `yield return line;` příkaz následujícím kódem:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Dále je třeba upravit způsob, jakým spotřebováváte řádky souboru, a přidat zpoždění po napsání každého slova. Nahraďte `Console.WriteLine(line)` příkaz `Main` v metodě následujícím blokem:

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

Třída <xref:System.Threading.Tasks.Task> je v <xref:System.Threading.Tasks> oboru názvů, takže je `using` třeba přidat tento příkaz v horní části souboru:

```csharp
using System.Threading.Tasks;
```

Spusťte ukázku a zkontrolujte výstup. Nyní je vytištěno každé slovo, následované zpožděním 200 ms. Zobrazený výstup však zobrazuje některé problémy, protože zdrojový textový soubor má několik řádků, které mají více než 80 znaků bez zalomení řádku. To může být těžké číst, zatímco je to rolování. To se dá snadno napravit. Budete jen sledovat délku každého řádku a generovat nový řádek vždy, když délka řádku dosáhne určité prahové hodnoty. Deklarujte místní proměnnou po deklaraci `words` v metodě, `ReadFrom` která obsahuje délku řádku:

```csharp
var lineLength = 0;
```

Potom přidejte následující kód `yield return word + " ";` za příkaz (před uzavírací složenou závorku):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Spusťte ukázku a budete moci číst nahlas v předem nakonfigurovaném tempu.

## <a name="async-tasks"></a>Asynchronní úlohy

V tomto posledním kroku přidáte kód pro zápis výstupu asynchronně v jedné úloze, a zároveň spuštění jiné úlohy pro čtení vstupu od uživatele, pokud chtějí urychlit nebo zpomalit zobrazení textu nebo úplně zastavit zobrazení textu. To má několik kroků v něm a na konci, budete mít všechny aktualizace, které potřebujete. Prvním krokem je vytvoření asynchronní <xref:System.Threading.Tasks.Task> návratové metody, která představuje kód, který jste dosud vytvořili ke čtení a zobrazení souboru.

Přidejte tuto `Program` metodu do třídy (je `Main` převzata z těla vaší metody):

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

Všimněte si dvou změn. Nejprve v těle metody, namísto <xref:System.Threading.Tasks.Task.Wait> volání synchronně čekat na dokončení úkolu, tato `await` verze používá klíčové slovo. Chcete-li to provést, musíte `async` přidat modifikátor k podpisu metody. Tato metoda `Task`vrátí . Všimněte si, že neexistují `Task` žádné návratové příkazy, které vrátí objekt. Místo toho `Task` je tento objekt vytvořen kódem, který `await` kompilátor generuje při použití operátoru. Můžete si představit, že tato metoda `await`vrátí, když dosáhne . Vrácené `Task` označuje, že práce nebyla dokončena. Metoda pokračuje po dokončení očekávané úlohy. Po dokončení, vrácené `Task` označuje, že je dokončena.
Volající kód můžete `Task` sledovat, který se vrátil k určení, kdy byl dokončen.

Tuto novou metodu můžete `Main` volat ve vaší metodě:

```csharp
ShowTeleprompter().Wait();
```

Zde v `Main`, kód synchronně čekat. Měli byste `await` použít operátor namísto synchronního čekání, kdykoli je to možné. Ale v metodě konzolové `Main` aplikace nelze `await` použít operátor. To by mělo za následek ukončení aplikace před dokončením všech úkolů.

> [!NOTE]
> Pokud používáte C# 7.1 nebo novější, [ `async` `Main` ](../whats-new/csharp-7-1.md#async-main)můžete vytvořit konzolové aplikace s metodou .

Dále je třeba napsat druhou asynchronní metodu číst z konzoly a sledovat '<' (menší než), '>' (větší než) a 'X' nebo 'x' klíče. Zde je metoda, kterou přidáte pro tento úkol:

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

Tím se vytvoří výraz lambda představující <xref:System.Action> delegáta, který přečte klíč z konzoly a upraví místní proměnnou představující zpoždění, když uživatel stiskne klávesy "<" (menší než) nebo ">" (větší než). Metoda delegáta se dokončí, když uživatel stiskne klávesy "X" nebo 'x', které uživateli umožňují kdykoli zastavit zobrazení textu. Tato metoda <xref:System.Console.ReadKey> používá k zablokování a čekání na uživatele stisknout klávesu.

Chcete-li dokončit tuto funkci, `async Task` je třeba vytvořit novou metodu`GetInput` `ShowTeleprompter`vrácení, která spustí oba tyto úkoly ( a ) a také spravuje sdílená data mezi těmito dvěma úkoly.

Je čas vytvořit třídu, která může zpracovávat sdílená data mezi těmito dvěma úkoly. Tato třída obsahuje dvě veřejné vlastnosti: `Done` zpoždění a příznak označující, že soubor byl zcela přečten:

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

Vložte tuto třídu do nového souboru `TeleprompterConsole` a uzavřete ji do oboru názvů, jak je uvedeno výše. Budete také muset přidat `using static` příkaz, takže můžete `Min` odkazovat na metody a `Max` bez ohraničujících názvů tříd nebo oborů názvů. Příkaz [`using static`](../language-reference/keywords/using-static.md) importuje metody z jedné třídy. To je v `using` rozporu s příkazy používané až do tohoto okamžiku, které importovaly všechny třídy z oboru názvů.

```csharp
using static System.Math;
```

Dále je třeba aktualizovat `ShowTeleprompter` `GetInput` metody a pro `config` použití nového objektu. Napište `Task` jednu `async` konečnou metodu vrácení, abyste zahájili oba úkoly a ukončili po dokončení prvního úkolu:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Jedna nová metoda je <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> zde volání. To vytvoří, `Task` který dokončí, jakmile některý z úkolů v seznamu argumentů dokončí.

Dále je třeba aktualizovat `ShowTeleprompter` a `GetInput` metody pro `config` použití objektu pro zpoždění:

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

Tato nová `ShowTeleprompter` verze volá novou `TeleprompterConfig` metodu ve třídě. Nyní je třeba `Main` aktualizovat `RunTeleprompter` volání `ShowTeleprompter`namísto:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Závěr

Tento kurz vám ukázal řadu funkcí kolem jazyka C# a knihoven .NET Core souvisejících s prací v konzolových aplikacích. Můžete stavět na těchto znalostech, abyste prozkoumali více o jazyce a třídách zde zavedených. Viděli jste základy vstupně-amp;v. souboru a konzoly, blokování a neblokující použití asynchronního programování založeného na úlohách, prohlídku jazyka C# a uspořádání programů jazyka C# a rozhraní PŘÍKAZOVÉHO PŘÍKAZU .NET Core.

Další informace o vstupně-já souborů najdete v tématu [Soubor a vstupně-tovišti](../../standard/io/index.md) datových proudů. Další informace o asynchronním programovacím modelu použitém v tomto kurzu naleznete v tématu [Asynchronní programování založené na úlohách](../..//standard/parallel-programming/task-based-asynchronous-programming.md) a v tématu [asynchronního programování.](../async.md)
