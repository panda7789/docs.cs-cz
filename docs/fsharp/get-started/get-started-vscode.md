---
title: Začínáme s jazykem F# v editoru Visual Studio Code
description: Naučte se používat F# s Visual Studio Code a sadou modulů plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2aa62bb1afc220348f884865e55c4d7de4359b7f
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980350"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Začínáme s jazykem F# v editoru Visual Studio Code

Můžete psát F# v [Visual Studio Code](https://code.visualstudio.com) s [modulem plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) a získat tak skvělé prostředí integrovaného vývojového prostředí (IDE) pro více platforem pomocí technologie IntelliSense a refaktoringu kódu. Další informace o modulu plug-in najdete na [Ionide.IO](http://ionide.io) .

Chcete-li začít, ujistěte se, že máte [ F# a modul plug-in Ionide správně nainstalován](install-fsharp.md#install-f-with-visual-studio-code).

## <a name="create-your-first-project-with-ionide"></a>Vytvoření prvního projektu pomocí Ionide

Chcete-li vytvořit F# nový projekt, otevřete příkazový řádek a vytvořte nový projekt s .NET Core CLI:

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

Po dokončení změňte adresář na projekt a otevřete Visual Studio Code:

```console
cd FirstIonideProject
code .
```

Po načtení projektu na Visual Studio Code byste měli vidět podokno F# Průzkumník řešení na levé straně okna otevřené. To znamená, že Ionide úspěšně zavedl projekt, který jste právě vytvořili. Můžete napsat kód v editoru před tímto bodem v čase, ale jakmile k tomu dojde, všechno se načetlo.

## <a name="configure-f-interactive"></a>Konfigurovat F# interaktivní

Nejdřív zajistěte, aby bylo skriptování .NET Core výchozím skriptovacím prostředím:

1. Otevřete nastavení Visual Studio Code ( **předvolby** > **kódu** > **Nastavení**).
1. Vyhledejte termín  **F# skriptu**.
1. Klikněte na zaškrtávací políčko, které říká **FSharp: použijte skripty sady SDK**.

V současné době je to nezbytné kvůli tomu, že v .NET Framework skriptování založeném na, které nefungují s skriptováním .NET Core, se v současnosti vyžaduje, aby služba Ionide v současné době zajistila tuto zpětnou kompatibilitu. V budoucnu se skriptování .NET Core stane výchozím nastavením.

### <a name="write-your-first-script"></a>Napište svůj první skript.

Jakmile nakonfigurujete Visual Studio Code pro použití skriptování .NET Core, přejděte do zobrazení Průzkumníka v Visual Studio Code a vytvořte nový soubor. Pojmenujte ho *MyFirstScript. fsx*.

Nyní do něj přidejte následující kód:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Tato funkce převede slovo na formu [prasečí Latin](https://en.wikipedia.org/wiki/Pig_Latin). Dalším krokem je vyhodnotit ho pomocí F# Interactive (fsi).

Zvýrazněte celou funkci (měla by být 11 řádků dlouhá). Až se zvýrazní, stiskněte klávesu **ALT** a stiskněte **ENTER**. Všimněte si, že se v dolní části obrazovky zobrazí okno terminálu, které by mělo vypadat podobně jako toto:

![Příklad F# interaktivního výstupu s Ionide](./media/getting-started-vscode/vscode-fsi.png)

To mělo tři věci:

1. Spustil se proces FSI.
2. Odeslali jsme kód, který jste zvýraznili v rámci procesu FSI.
3. Proces FSI vyhodnotil kód, který jste odeslali.

Vzhledem k tomu, že jste přeposlali [funkci](../language-reference/functions/index.md), můžete tuto funkci nyní volat pomocí FSI! V interaktivním okně zadejte následující:

```fsharp
toPigLatin "banana";;
```

Měl by se zobrazit následující výsledek:

```fsharp
val it : string = "ananabay"
```

Teď zkusíme použít samohlásku jako první písmeno. Zadejte následující:

```fsharp
toPigLatin "apple";;
```

Měl by se zobrazit následující výsledek:

```fsharp
val it : string = "appleyay"
```

Zdá se, že funkce funguje podle očekávání. Gratulujeme, právě jste napsali F# svou první funkci v Visual Studio Code a vyhodnotili ji pomocí FSI!

> [!NOTE]
> Jak jste si všimli, řádky v FSI se ukončí s `;;`. Důvodem je to, že FSI umožňuje zadat více řádků. `;;` na konci umožňuje FSI ví, že je kód dokončen.

## <a name="explaining-the-code"></a>Vysvětlení kódu

Pokud si nejste jistí, co kód skutečně dělá, tady je krok za krokem.

Jak vidíte, `toPigLatin` je funkce, která jako svůj vstup přebírá slovo, a převede ho na reprezentaci tohoto slova v latince. Tato pravidla jsou následující:

Pokud první znak ve slově začíná znakem samohlásky, přidejte na konec slova "yay". Pokud nezačíná znakem samohlásky, přesuňte tento první znak na konec slova a přidejte do něj "Ay".

Možná jste si všimli, že v FSI máte následující:

```fsharp
val toPigLatin : word:string -> string
```

To uvádí, že `toPigLatin` je funkce, která přebírá `string` jako vstup (nazývaný `word`), a vrací další `string`. To se označuje jako [Signatura typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část klíče F# , která je základem pro porozumění F# kódu. Všimněte si také, že najedete myší na funkci v Visual Studio Code.

V těle funkce si všimnete dvou různých částí:

1. Vnitřní funkce označovaná jako `isVowel`, která určuje, zda daný znak (`c`) je znak samohlásky kontrolou, pokud odpovídá jednomu ze zadaných vzorů přes [porovnávání vzorů](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Výraz [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) , který kontroluje, zda je první znak samohlásky, a vytvoří vrácenou hodnotu ze vstupních znaků na základě toho, zda byl první znak samohláskou nebo nikoli:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Tok `toPigLatin` je tedy:

Zkontroluje, jestli je první znak vstupního slova samohláskou. Pokud je, připojte k konci slova "yay". V opačném případě přesuňte tento první znak na konec slova a přidejte do něj "Ay".

K dispozici je jedno konečné oznámení: v F#nástroji neexistuje žádná explicitní instrukce pro návrat z funkce. Důvodem je, F# že je založen na výrazu a poslední výraz vyhodnocený v těle funkce určuje návratovou hodnotu této funkce. Vzhledem k tomu, že `if..then..else` je sám o sobě výraz, vyhodnocování těla bloku `then` nebo tělo `else`ho bloku Určuje hodnotu vrácenou `toPigLatin` funkcí.

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>Vypnutí konzolové aplikace na prasečí generátor v latince

Předchozí části tohoto článku ukázaly běžný první krok při psaní F# kódu: zápis počáteční funkce a interaktivní spuštění pomocí FSI. To se označuje jako vývoj řízený REPL, kde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) představuje "Read-Evaluate-Print Loop". Je to skvělý způsob, jak experimentovat s funkčnostmi, dokud nebudete mít nějakou práci.

Dalším krokem v REPLém vývojovém prostředí F# je přesun pracovního kódu do implementačního souboru. Poté může být zkompilován F# kompilátorem do sestavení, které lze spustit.

Začněte tím, že otevřete soubor *program. FS* , který jste vytvořili dříve, pomocí .NET Core CLI. Všimněte si, že v něm už je nějaký kód.

Dále vytvořte nový [`module`](../language-reference/modules.md) nazvaný `PigLatin` a zkopírujte `toPigLatin` funkci, kterou jste předtím vytvořili.

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

Tento modul by měl být nad `main`ovou funkcí a pod deklarací `open System`. Pořadí deklarací v F#nástroji, takže je nutné definovat funkci před jejich voláním v souboru.

Nyní ve funkci `main` volejte funkci generátoru latince pro prase na argumenty:

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

Nyní můžete spustit konzolovou aplikaci z příkazového řádku:

```dotnetcli
dotnet run apple banana
```

A uvidíte, že výstup má stejný výsledek jako soubor skriptu, ale tentokrát jako běžící program.

## <a name="troubleshooting-ionide"></a>Řešení potíží s Ionide

Tady je několik způsobů, jak můžete řešit některé problémy, se kterými se můžete setkat:

1. Chcete-li získat funkce pro úpravu kódu Ionide, F# je třeba uložit soubory na disk a do složky, která je otevřena v pracovním prostoru Visual Studio Code.
1. Pokud jste provedli změny v systému nebo nastavili požadavky Ionide Visual Studio Code otevřít, restartujte Visual Studio Code.
1. Pokud máte v adresářích projektu neplatné znaky, Ionide nemusí fungovat.  Pokud se jedná o tento případ, přejmenujte adresáře projektu.
1. Pokud žádný z příkazů Ionide nefunguje, zkontrolujte [vazby Visual Studio Code klíčů](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) a zjistěte, jestli je nebudete mít v úmyslu přepisování.
1. Pokud je Ionide na vašem počítači poškozená a žádná z výše uvedených kroků nevyřešila váš problém, zkuste na svém počítači odebrat `ionide-fsharp` adresář a znovu sadu modulů plug-in.
1. Pokud se projekt nepovedlo načíst ( F# Průzkumník řešení to uvidí), klikněte pravým tlačítkem na tento projekt a kliknutím na **Zobrazit podrobnosti** Získejte další diagnostické informace.

Ionide je open source projekt sestavený a spravovaný členy F# komunity. Oznamte prosím problémy a nebojte se přispět v [úložišti GitHub ionide-VSCode-FSharp](https://github.com/ionide/ionide-vscode-fsharp).

Můžete si také vyžádat další pomoc od vývojářů Ionide a F# komunity v [kanálu gitteru Ionide](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Další kroky

Chcete-li získat F# Další informace o funkcích jazyka, Projděte si [část F# ](../tour.md).
