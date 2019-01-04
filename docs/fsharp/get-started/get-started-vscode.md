---
title: Začínáme s F# ve Visual Studio Code
description: Další informace o použití F# s Visual Studio Code a Ionide suite modulu plug-in.
ms.date: 12/23/2018
ms.openlocfilehash: 34802551bf4e34abb5aa0130643f32dbce68f1b2
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029551"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Začínáme s F# ve Visual Studio Code

Můžete napsat F# v [Visual Studio Code](https://code.visualstudio.com) s [modulu plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) zobrazíte skvělé prostředí integrované vývojové prostředí (IDE) napříč platformami, základní technologie IntelliSense a základní kód refaktoring. Navštivte [Ionide.io](http://ionide.io) získat další informace o modulu plug-in.

Pokud chcete začít, ujistěte se, že máte [ F# a modul plug-in Ionide správně nainstalovaný](install-fsharp.md#install-f-with-visual-studio-code).

## <a name="creating-your-first-project-with-ionide"></a>Vytvoření prvního projektu s Ionide

Chcete-li vytvořit nový F# projektu, otevřete Visual Studio Code v nové složce (můžete ji nazvat cokoli, co chcete).

Dále otevřete paletu příkazů (**zobrazení > paletu příkazů**) a zadejte následující údaje:

```
> F# new project
```

Toto využívá k tomu [FORGE](https://github.com/fsharp-editing/Forge) projektu.

> [!NOTE]
> Pokud nevidíte šablonu možnosti, zkuste aktualizovat šablony spuštěním následujícího příkazu v paletu příkazů: `>F#: Refresh Project Templates`.

Vyberte "F#: Nový projekt"tím, že kliknete **Enter**. Tím přejdete k dalšímu kroku, který je pro výběr šablony projektu.

Vyberte si `classlib` šablony a stiskněte klávesu **Enter**.

V dalším kroku vyberte adresář pro vytvoření projektu v. Pokud necháte prázdné, použije aktuální adresář.

A konečně pojmenujte svůj projekt v posledním kroku. F#používá [pascalcase](http://c2.com/cgi/wiki?PascalCase) pro názvy projektů. Tento článek používá `ClassLibraryDemo` jako název. Jakmile zadáte název, který chcete pro váš projekt, stiskněte **Enter**.

Pokud jste postupovali podle předchozího kroku, měli byste získat Visual Studio Code pracovního prostoru na levé straně se zobrazí s následujícími možnostmi:

1. F# Samotný projekt pod ní `ClassLibraryDemo` složky.
2. Správnou adresářovou strukturu pro přidávání balíčků prostřednictvím [ `Paket` ](https://fsprojects.github.io/Paket/).
3. Různé platformy sestavení skript s [ `FAKE` ](https://fsharp.github.io/FAKE/).
4. `paket.exe` Spustitelný soubor, který lze načíst balíčky a vyřešení závislostí pro vás.
5. A `.gitignore` souboru, pokud chcete přidat tento projekt do správy verzí z Gitu.

## <a name="writing-some-code"></a>Psaním kódu

Otevřít *ClassLibraryDemo* složky.  Zobrazí se následující soubory:

1. `ClassLibraryDemo.fs`, F# implementační soubor s třídou definované.
2. `ClassLibraryDemo.fsproj`, F# soubor projektu používá k vytváření buildu tohoto projektu.
3. `Script.fsx`, F# soubor skriptu, který načte zdrojového souboru.
4. `paket.references`, stáhnout soubor, který určuje závislosti projektu.

Otevřít `Script.fsx`a přidejte následující kód na konci ho:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Tato funkce převede do formy slovo [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin). Dalším krokem je vyhodnotit pomocí F# interaktivní (soubor FSI).

Zvýrazněte celý – funkce (musí být dlouhý 11 řádky). Jakmile je zvýrazněn, podržte **Alt** klíče a přístupů **Enter**. Všimněte si níže překryvné okno a měl by se zobrazit, přibližně takto:

![Příklad F# interaktivní výstup s Ionide](media/getting-started-vscode/vscode-fsi.png)

To provedl tři věci:

1. Jeho spuštění procesu FSI.
2. Kód, který jste zvýraznili se odesílají prostřednictvím procesu FSI.
3. Proces FSI vyhodnotí kód, který jste odeslali přes.

Vzhledem k tomu, že byl odeslán přes [funkce](../language-reference/functions/index.md), můžete nyní volat tuto funkci s FSI! V interaktivním okně zadejte následující příkaz:

```fsharp
toPigLatin "banana";;
```

Měli byste vidět následující výsledek:

```fsharp
val it : string = "ananabay"
```

Teď vyzkoušíme s samohláskou jako první písmeno. Zadejte následující příkaz:

```fsharp
toPigLatin "apple";;
```

Měli byste vidět následující výsledek:

```fsharp
val it : string = "appleyay"
```

Zdá se, že funkce fungovat podle očekávání. Blahopřejeme, jste napsali první F# funkce v aplikaci Visual Studio Code a vyhodnotit s FSI!

> [!NOTE]
> Protože jste si všimli, se ukončují vstupující FSI `;;`. Je to proto, že soubor FSI umožňuje zadat více řádků. `;;` Na konci umožňuje FSI vědět, kdy je dokončena kód.

## <a name="explaining-the-code"></a>Vysvětlení kódu

Pokud si nejste jisti, co kód skutečně dělají, tady je krok za krokem.

Jak je vidět, `toPigLatin` je funkce, která přebírá slova jako vstup a převede ho na Pig Latin reprezentace toto slovo. Pravidla pro to jsou následující:

Pokud první znak v slovo začíná samohláskou, přidáte na konec slovo "yay". Pokud se nespustí s samohláskou přesunout prvním znaku na konci slovo a "ay" přidejte do ní.

Možná jste si všimli v FSI následující kroky:

```fsharp
val toPigLatin : word:string -> string
```

Uvádí, že to `toPigLatin` je funkce, která přijímá `string` jako vstup (volá `word`) a vrátí jiný `string`. To se označuje jako [podpis typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část F# , který je klíčem k pochopení F# kódu. Můžete také všimnout to Pokud najedete myší na funkci v aplikaci Visual Studio Code.

V těle funkce můžete si všimnout dvou samostatných částí:

1. Vnitřní funkci nazvanou `isVowel`, který určuje, zda daný znak (`c`) je samohláskou kontrolou, jestli odpovídá jednomu ze vzorů poskytnutý prostřednictvím [porovnávání vzorů](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Výraz, který zkontroluje, jestli je první znak samohláskou a konstrukcí návratová hodnota ze vstupních znaků na základě-li první znak byla samohláskou nebo ne:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Tok `toPigLatin` je takto:

Zkontrolujte, jestli je první znak slova vstupní samohláskou. Pokud se jedná, připojte na konci slovo "yay". V opačném případě přesunout prvním znaku na konci slovo a přidejte do ní "ay".

Existuje jedna poslední věc, Všimněte si, že o tomto: neexistuje žádná explicitní instrukce k vrácení z funkce, na rozdíl od mnoha jiných jazycích tam. Důvodem je, že F# je založené na výrazu, a je návratová hodnota posledního výrazu v těle funkce. Protože `if..then..else` je samotný výraz text `then` bloku nebo textu `else` bloku se vrátí v závislosti na vstupní hodnota.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Přesunutí kódu skriptu do souboru implementace

Předchozích částech tohoto článku jsme vám ukázali běžné prvním krokem při psaní F# kódu: psaní počáteční funkce a interaktivní spuštění pomocí FSI. To se označuje jako vývoj řízený REPL, kde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) zastupuje "Čtení-vyhodnocení-Print smyčka". To je skvělý způsob, jak experimentovat s funkcemi, dokud máte něco, co funguje.

Dalším krokem v vývoj řízený REPL je chcete přesunout pracovní kód do F# implementační soubor. To může být poté zkompilován pomocí F# kompilátoru do sestavení, které mohou být provedeny.

Pokud chcete začít, otevřete `ClassLibraryDemo.fs`.  Můžete si všimnout, že nějaký kód je již existuje. Pokračujte a odstranit definici třídy, ale ponechte [ `namespace` ](../language-reference/namespaces.md) deklarace v horní části.

Dále vytvořte novou [ `module` ](../language-reference/modules.md) volá `PigLatin` a zkopírujte `toPigLatin` funkce do něj takto:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Dále otevřete `Script.fsx` soubor znovu a odstranit celý `toPigLatin` fungovat, ale ujistěte se, aby následující dva řádky v souboru:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```
Vyberte obě čáry text a stisknutím kláves Alt + Enter pro spuštění ve FSI tyto řádky. Obsah knihovny Pig Latin tyto se načtou do procesu FSI a `open` `ClassLibraryDemo` obor názvů, abyste měli přístup k funkcím.

Pak v okně FSI zavolejte funkci s `PigLatin` modul, který jste definovali dříve:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Úspěch! Zobrazí stejné výsledky jako předtím, ale teď načíst ze F# implementační soubor. Hlavní rozdíl spočívá v tom, který F# zdrojové soubory jsou zkompilovány do sestavení, které lze spustit kdekoli, ne jenom v FSI.

## <a name="summary"></a>Souhrn

V tomto článku jste zjistili:

1. Jak nastavit službu Visual Studio Code s Ionide.
2. Jak vytvořit první F# projekt s Ionide.
3. Jak používat F# skriptování pro zápis první F# fungovat v Ionide a proveďte jej v FSI.
4. Jak migrovat kód skriptu do F# zdroje a pak vyvolejte tento kód z FSI.

Jste teď umožňuje psát spoustu dalších věcí F# programování s využitím Visual Studio Code a Ionide.

## <a name="troubleshooting"></a>Poradce při potížích

Tady je několik způsobů, jak je řešit určité problémy, které můžete narazit na:

1. Chcete-li získat funkce Ionide, pro úpravu kódu vašeho F# soubory musí být uloženo na disk a ve složce, která je otevřena v pracovním prostoru Visual Studio Code.
2. Pokud jste provedené změny v systému nebo nainstalované požadavky Ionide pomocí Visual Studio Code, otevřít, restartujte Visual Studio Code.
3. Zkontrolujte, zda můžete použít F# kompilátoru a F# interaktivní z příkazového řádku bez plně kvalifikované cesty. To lze provést zadáním `fsc` v příkazový řádek, F# kompilátoru, a `fsi` nebo `fsharpi` vizuálu F# nástroje na Windows a Mono na Mac/Linux, v uvedeném pořadí.
4. Pokud vaše adresáře projektu obsahuje neplatné znaky, Ionide nemusí fungovat.  Přejmenování adresáře vašeho projektu, pokud tomu tak.
5. Pokud žádný z příkazů Ionide práci, zkontrolujte vaše [klávesové zkratky pro Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) zobrazíte, pokud jste už je přepsání náhodná.
6. Pokud Ionide nefunguje na vašem počítači a žádná z výše uvedených vyřešil potíže, zkuste odebrat `ionide-fsharp` adresáře v počítači a znovu nainstalujte modul plug-in.

Ionide je projekt open source integrované a udržován členy F# komunity. Naleznete hlaste problémy a Nebojte se přispět na [Ionide VSCode: Úložiště FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).

Pokud máte potíže do sestavy, postupujte prosím podle [pokyny pro získání protokolů pro použití při hlášení](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Můžete také požádat o další pomoc od vývojářů Ionide a F# komunitou v [Ionide Gitteru kanál](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Další kroky

Další informace o F# a funkcí jazyka, podívejte se na [prohlídka F# ](../tour.md).
