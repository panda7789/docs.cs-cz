---
title: Začínáme s nástrojem F# v Visual Studio Code
description: Naučte se používat F# s Visual Studio Code a sadou modulů plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: baaa87207122cfe314972aee5dfaf8a41de2c394
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629979"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Začínáme s nástrojem F# v Visual Studio Code

Můžete psát F# v [Visual Studio Code](https://code.visualstudio.com) s modulem [Plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) a získat tak skvělé prostředí integrovaného vývojového prostředí (IDE) pro více platforem pomocí technologie IntelliSense a refaktoringu kódu Basic. Další informace o modulu plug-in najdete na [Ionide.IO](http://ionide.io) .

Chcete-li začít, ujistěte se, že máte [ F# a modul plug-in Ionide správně nainstalován](install-fsharp.md#install-f-with-visual-studio-code).

> [!NOTE]
> Ionide vygeneruje .NET Framework F# projekty, nikoli dotnet Core, což může mít problémy s kompatibilitou pro více platforem. Pokud pracujete v systému **Linux** nebo **OSX**, jednodušší způsob, jak začít, je použít [nástroje příkazového řádku](get-started-command-line.md).

## <a name="creating-your-first-project-with-ionide"></a>Vytvoření prvního projektu pomocí Ionide

Chcete-li vytvořit F# nový projekt, otevřete Visual Studio Code v nové složce (můžete si ho pojmenovat podle vaší věci).

V dalším kroku otevřete paletu příkazů (**zobrazit > paleta příkazů**) a zadejte následující:

```
> F# new project
```

Používá se v projektu [zfalšovat](https://github.com/fsharp-editing/Forge) .

> [!NOTE]
> Pokud nevidíte možnosti šablony, zkuste aktualizace šablon spustit pomocí následujícího příkazu v paletě příkazů: `>F#: Refresh Project Templates`.

VyberteF#: Nový projekt "pomocí možnosti **ENTER** Tím přejdete k dalšímu kroku, který je určen pro výběr šablony projektu.

Vyberte šablonu a stiskněte klávesu **ENTER.** `classlib`

Pak vyberte adresář, ve kterém se má projekt vytvořit. Pokud ponecháte pole prázdné, použije se aktuální adresář.

Nakonec pojmenujte projekt v posledním kroku. F#pro názvy projektů používá [velká písmena jazyka Pascal](http://c2.com/cgi/wiki?PascalCase) . Tento článek používá `ClassLibraryDemo` název. Až zadáte název, který chcete pro svůj projekt, stiskněte klávesu **ENTER**.

Pokud jste postupovali podle předchozího kroku, měli byste na levé straně získat Visual Studio Code pracovní prostor, aby se zobrazila následující:

1. Samotný F# projekt pod `ClassLibraryDemo` složkou.
2. Správná adresářová struktura pro přidávání balíčků prostřednictvím [`Paket`](https://fsprojects.github.io/Paket/).
3. Skript sestavení pro různé platformy s [`FAKE`](https://fsharp.github.io/FAKE/).
4. `paket.exe` Spustitelný soubor, který dokáže načíst balíčky a vyřešit závislosti.
5. `.gitignore` Soubor, pokud chcete přidat tento projekt do správy zdrojového kódu založeného na Gitu.

## <a name="writing-some-code"></a>Psaní kódu

Otevřete složku *ClassLibraryDemo* .  Měli byste vidět následující soubory:

1. `ClassLibraryDemo.fs`, F# implementační soubor s definovanou třídou.
2. `ClassLibraryDemo.fsproj`, soubor F# projektu použitý k sestavení tohoto projektu.
3. `Script.fsx`, soubor F# skriptu, který načte zdrojový soubor.
4. `paket.references`, soubor paket, který určuje závislosti projektu.

Otevřete `Script.fsx`a na konci tohoto kódu přidejte následující kód:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Tato funkce převede slovo na formu [prasečí Latin](https://en.wikipedia.org/wiki/Pig_Latin). Dalším krokem je vyhodnotit ho pomocí F# Interactive (fsi).

Zvýrazněte celou funkci (měla by být 11 řádků dlouhá). Až se zvýrazní, podržte klávesu **ALT** a stiskněte **ENTER**. Všimněte si, že se zobrazí okno zobrazené níže a mělo by to vypadat nějak takto:

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
> Jak jste si všimli, řádky v FSI se ukončí s `;;`. Důvodem je to, že FSI umožňuje zadat více řádků. `;;` Na konci umožňuje FSI informace o tom, kdy byl kód dokončen.

## <a name="explaining-the-code"></a>Vysvětlení kódu

Pokud si nejste jistí, co kód skutečně dělá, tady je krok za krokem.

Jak vidíte, `toPigLatin` je funkce, která jako svůj vstup přebírá slovo, a převede ho na reprezentaci tohoto slova v latince. Tato pravidla jsou následující:

Pokud první znak ve slově začíná znakem samohlásky, přidejte na konec slova "yay". Pokud nezačíná znakem samohlásky, přesuňte tento první znak na konec slova a přidejte do něj "Ay".

Možná jste si všimli, že v FSI máte následující:

```fsharp
val toPigLatin : word:string -> string
```

Jedná se o funkci, která přijímá `string` jako vstup (označovaný `word`), a vrátí jinou `string`. `toPigLatin` To se označuje jako [Signatura typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část klíče F# , která je základem pro porozumění F# kódu. Všimněte si také, že najedete myší na funkci v Visual Studio Code.

V těle funkce si všimnete dvou různých částí:

1. Vnitřní funkce, která je `isVowel`volána, která určuje, zda daný znak`c`() je znak samohlásky pomocí kontroly, zda odpovídá jednomu ze zadaných vzorů přes [porovnávání vzorů](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) Výraz, který kontroluje, zda je první znak samohlásky, a vytvoří vrácenou hodnotu ze vstupních znaků na základě toho, zda byl první znak samohláskou nebo nikoli:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Tok `toPigLatin` je tedy:

Zkontroluje, jestli je první znak vstupního slova samohláskou. Pokud je, připojte k konci slova "yay". V opačném případě přesuňte tento první znak na konec slova a přidejte do něj "Ay".

K dispozici je jedno konečné oznámení: neexistuje žádná explicitní instrukce pro návrat z funkce, na rozdíl od mnoha dalších jazyků. Důvodem je, F# že je založen na výrazu a poslední výraz v těle funkce je návratová hodnota. Vzhledem `if..then..else` k tomu, že se jedná o výraz, `then` bude v závislosti na vstupní hodnotě `else` vrácen text bloku nebo tělo bloku.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Přesunutí kódu skriptu do implementačního souboru

Předchozí části tohoto článku ukázaly běžný první krok při psaní F# kódu: zápis počáteční funkce a interaktivní spuštění pomocí FSI. To se označuje jako vývoj řízený REPL, kde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) představuje "Read-Evaluate-Print Loop". Je to skvělý způsob, jak experimentovat s funkčnostmi, dokud nebudete mít nějakou práci.

Dalším krokem v REPLém vývojovém prostředí F# je přesun pracovního kódu do implementačního souboru. Poté může být zkompilován F# kompilátorem do sestavení, které lze spustit.

Začněte tím, že `ClassLibraryDemo.fs`otevřete.  Všimněte si, že v něm už je nějaký kód. Pokračujte a odstraňte definici třídy, ale zajistěte, aby byla [`namespace`](../language-reference/namespaces.md) deklarace ponechána v horní části.

V dalším kroku vytvořte nový [`module`](../language-reference/modules.md) `PigLatin` a zkopírujte `toPigLatin` do něj funkci, jako například:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Dále znovu otevřete `Script.fsx` soubor a odstraňte celou `toPigLatin` funkci, ale nezapomeňte v souboru zachovat následující dva řádky:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

Vyberte oba řádky textu a stisknutím kombinace kláves ALT + ENTER tyto řádky v FSI spusťte. Načte obsah knihovny latince pro vepřové soubory do procesu FSI a `open` `ClassLibraryDemo` oboru názvů, abyste měli přístup k této funkci.

Dále v okně FSI zavolejte funkci s `PigLatin` modulem, který jste definovali dříve:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Nástup! Dostanete stejné výsledky jako předtím, ale nyní se načtou z F# implementačního souboru. Hlavní rozdíl je v tom, F# že zdrojové soubory jsou zkompilovány do sestavení, které lze provést kdekoli, nikoli pouze v FSI.

## <a name="summary"></a>Souhrn

V tomto článku jste se naučili:

1. Jak nastavit Visual Studio Code pomocí Ionide.
2. Jak vytvořit svůj první F# projekt pomocí Ionide.
3. Jak použít F# skriptování k zápisu první F# funkce v Ionide a její následné spuštění v FSI.
4. Postup migrace kódu skriptu na F# zdroj a následné volání tohoto kódu z FSI.

Nyní můžete pomocí Visual Studio Code a Ionide zapisovat mnohem F# více kódu.

## <a name="troubleshooting"></a>Poradce při potížích

Tady je několik způsobů, jak můžete řešit některé problémy, se kterými se můžete setkat:

1. Chcete-li získat funkce pro úpravu kódu Ionide, F# je třeba uložit soubory na disk a do složky, která je otevřena v pracovním prostoru Visual Studio Code.
2. Pokud jste provedli změny v systému nebo nastavili požadavky Ionide Visual Studio Code otevřít, restartujte Visual Studio Code.
3. Ověřte, zda můžete použít F# kompilátor a F# interaktivní z příkazového řádku bez plně kvalifikované cesty. To `fsc` lze provést zadáním příkazu do příkazového řádku pro F# kompilátor `fsi` a nebo `fsharpi` pro Visual F# Tools on Windows a mono v systému Mac/Linux v uvedeném pořadí.
4. Pokud máte v adresářích projektu neplatné znaky, Ionide nemusí fungovat.  Pokud se jedná o tento případ, přejmenujte adresáře projektu.
5. Pokud žádný z příkazů Ionide nefunguje, zkontrolujte [Visual Studio Code vazby](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) klíčů a podívejte se, jestli je nepřepisujete havárií.
6. Pokud je Ionide na vašem počítači poškozená a žádná z výše uvedených nevyřešila váš problém, zkuste `ionide-fsharp` odebrat adresář na počítači a znovu sadu modulů plug-in.

Ionide je open source projekt sestavený a spravovaný členy F# komunity. Oznamte prosím problémy a nebojte se přispět [na Ionide-VSCode: Úložiště](https://github.com/ionide/ionide-vscode-fsharp)GitHub FSharp

Pokud máte problém se sestavou, postupujte podle [pokynů pro získání protokolů, které se mají použít při hlášení problému](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Můžete si také vyžádat další pomoc od vývojářů Ionide a F# komunity v [kanálu gitteru Ionide](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Další postup

Chcete-li získat F# Další informace o funkcích jazyka, Projděte si [část F# ](../tour.md).
