---
title: "Začínáme s F # v sadě Visual Studio kódu"
description: "Další informace o použití F # s Visual Studio Code a suite Ionide modulu plug-in."
keywords: "Visual f #, f #, funkční programování, .NET, Visual Studio Code vscode Ionide"
author: cartermp
ms.author: phcart
ms.date: 02/28/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: c452e791b27bc3f32e137a515011d953005344c6
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Začínáme s F # v sadě Visual Studio kódu

Můžete napsat F # [Visual Studio Code](https://code.visualstudio.com) s [modulu plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), abyste získali optimálního uživatelského prostředí IDE (Integrade vývoj Enivronment) a platformy, lightweight s IntelliSense a základní kódu refaktoring.  Navštivte [Ionide.io](http://ionide.io) Další informace o sadě modulu plug-in.

## <a name="prerequisites"></a>Požadavky

Musíte mít [nainstalovat git](https://git-scm.com/download) a k dispozici na CESTU ke zkontrolujte pomocí šablon projektu v Ionide.  Můžete ověřit, zda je správně nainstalován zadáním `git --version` v příkazovém řádku a stiskněte **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

Používá Ionide [Mono](http://www.mono-project.com).  Nejjednodušší způsob, jak nainstalovat Mono v systému macOS je prostřednictvím Homebrew.  Jednoduše zadejte do terminálu následující:

```
brew install mono
```

Je také nutné nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

V systému Linux, Ionide také používá [Mono](https://www.mono-project.com). Pokud jste na Debian a Ubuntu, můžete použít následující:

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Je také nutné nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Pokud jste v systému Windows, musíte [instalaci sady Visual Studio s podporou F #](get-started-visual-studio.md#installing-f). Tím se nainstaluje všechny komponenty potřebné k zápisu, zkompilování a spuštění kódu F #.

Je také nutné nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download/).

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a>Instalace Visual Studio Code a Ionide modulu plug-in

Můžete nainstalovat Visual Studio Code z [code.visualstudio.com](https://code.visualstudio.com) webu. Potom existují dva způsoby jak najít modul plug-in Ionide:

1. Použijte příkaz palety (Ctrl + Shift + P v systému Windows, ⌘ + Shift + P v systému macOS, Ctrl + Shift + P v systému Linux) a zadejte následující příkaz:

    ```
    >ext install Ionide
    ```

2. Klikněte na ikonu rozšíření a vyhledejte "Ionide":

    ![](media/getting-started-vscode/vscode-ext.png)

Pouze modul plug-in, které jsou potřebné pro podporu F # ve Visual Studio Code je [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Ale můžete taky nainstalovat [Ionide PHISHING](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) a získat [ZFALŠOVAT](https://fsharp.github.io/FAKE/) podporu a [Ionide Stáhnout](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) získat [Stáhnout](https://fsprojects.github.io/Paket/) podporovat. ZFALŠOVAT a stáhnout dalších F # komunity nástroje pro sestavení projektů a správu závislosti, v uvedeném pořadí.

## <a name="creating-your-first-project-with-ionide"></a>Vytvoření prvního projektu s Ionide

Pokud chcete vytvořit nový projekt F #, otevřete Visual Studio Code do nové složky (můžete pojmenovat se vám líbí).

![](media/getting-started-vscode/vscode-open-dir.png)

Dále otevřete příkaz palety (Ctrl + Shift + P v systému Windows, ⌘ + Shift + P v systému macOS, Ctrl + Shift + P v systému Linux) a zadejte následující příkaz:

```
>f#: New Project
```

To používá technologii [FORGE](https://github.com/fsharp-editing/Forge) projektu.  Měli byste vidět zhruba takhle:

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
Pokud nevidíte výše, aktualizujte šablony spuštěním následujícího příkazu v příkazu palety: `>F#: Refresh Project Templates`.

Vyberte "F #: nový projekt" zasažení **Enter**, který se dostanete k tomuto kroku:

![](media/getting-started-vscode/vscode-proj-type.png)

To bude vyberte šablonu pro konkrétní typ projektu.  Existuje zde několik možností, jako [FsLab](https://fslab.org) šablonu pro vědecké zpracování dat nebo [Suave](https://suave.io) šablonu pro webové programování.  Tento článek používá `classlib` šablony, takže zvýrazněte a stiskněte tlačítko **Enter**.  Potom bude přístup následující krok:

![](media/getting-started-vscode/vscode-new-dir.png)

To vám umožní vytvořit projekt v jiném adresáři, pokud chcete.  Necháte prázdné, teď.  Vytvoří projekt v aktuálním adresáři.  Po stisknutí klávesy **Enter**, nedostanete následující krok:

![](media/getting-started-vscode/vscode-proj-name.png)

Díky tomu můžete název projektu.  F # používá [pascalcase](http://c2.com/cgi/wiki?PascalCase) pro názvy projektů.  Tento článek používá `ClassLibraryDemo` jako název.  Po zadání názvu, který chcete pro svůj projekt, stiskněte tlačítko **Enter**.

Pokud jste postupovali podle předchozích kroků krok, měli byste obdržet Visual Studio Code pracovní prostor na levé straně a vypadat přibližně takto:

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

Tato šablona vytváří několik věcí, které budete užitečné:

1. F # projektu samostatně, pod `ClassLibraryDemo` složky.
2. Správnou adresářovou strukturu pro přidávání balíčků prostřednictvím [ `Paket` ](https://fsprojects.github.io/Paket/).
3. Napříč platformami sestavení skriptu s [ `FAKE` ](https://fsharp.github.io/FAKE/).
4. `paket.exe` Spustitelný soubor, který může načíst balíčky a vyřešení závislostí pro vás.
5. A `.gitignore` soubor, pokud chcete přidat tento projekt na základě Git zdrojového kódu.

## <a name="writing-some-code"></a>Zápis některých kódu

Otevřete *ClassLibraryDemo* složky.  Měli byste vidět následující soubory:

1. `ClassLibraryDemo.fs`, F # implementace souboru třídy definované.
2. `CassLibraryDemo.fsproj`, F # souboru projektu aplikace sloužící k vytvoření tohoto projektu.
3. `Script.fsx`, F # skript soubor který načte zdrojový soubor.
4. `paket.references`, stáhnout soubor, který určuje závislosti projektu.

Otevřete `Script.fsx`a přidejte následující kód na konci ho:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Tato funkce převede slovo forma [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).  Dalším krokem je vyhodnotit pomocí F # interaktivní (FSI).

Zvýrazněte celý funkce (by měl být dlouhý 11 řádky).  Jakmile se zvýrazní, podržte **Alt** klíče a počtu **Enter**.  Můžete si všimnout okno otevíraném níže a jeho by měl zobrazit přibližně takto:

![](media/getting-started-vscode/vscode-fsi.png)

To provedl tři věci:

1. Spuštění procesu FSI.
2. Vámi vybraný úsek zvýrazněný kód se odešlou přes FSI proces.
3. Proces FSI vyhodnotí kód, který jste odeslali přes.

Protože odeslané přes [funkce](../language-reference/functions/index.md), můžete nyní volání této funkce se FSI!  V okně interaktivní zadejte následující příkaz:

```fsharp
toPigLatin "banana";;
```

Měli byste vidět následující výsledek:

```fsharp
val it : string = "ananabay"
```

Nyní zkuste to prosím ještě s samohláskou jako první písmeno. Zadejte následující příkaz:

```fsharp
toPigLatin "apple";;
```

Měli byste vidět následující výsledek:

```fsharp
val it : string = "appleyay"
```

Zdá se, že funkce fungovat podle očekávání.  Blahopřejeme, stačí napsali první funkce F # ve Visual Studio Code a vyhodnotit s FSI.

>[!NOTE]
Protože jste si všimli, jsou řádky v FSI byla ukončena s `;;`.  To je proto FSI umožňuje zadat více řádků.  `;;` Na konci umožňuje FSI vědět, kdy je dokončena kód.

## <a name="explaining-the-code"></a>Vysvětlení kód

Pokud si nejste si jisti, co kód ve skutečnosti provádí, zde je krok za krokem.

Jak vidíte, `toPigLatin` je funkce, která přebírá slovo jako vstup a převede jej na znázornění Pig Latin tohoto slova.  Pravidla pro toto jsou následující:

Pokud první znak v slovo začíná samohláskou, přidejte na konec slovo "yay".  Pokud se nespustí, s samohláskou, přesuňte tento první znak ke konci slova a přidejte do ní "ay".

Může dojít k tomu následující FSI:

```
val toPigLatin : word:string -> string
```

To stavů, které `toPigLatin` je funkce, která přebírá `string` jako vstup (nazývá `word`) a vrátí jiné `string`.  To se označuje jako [podpis typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část F #, která je klíčem k pochopení F # – kód.  Tento postup můžete si všimnout také v Pokud najedete funkci v aplikaci Visual Studio Code.

V těle funkce můžete si všimnout dvou různých částí:

1. Vnitřní funkce, nazývá `isVowel`, která určuje, zda daného znaku (`c`) je samohláskou kontrolou, pokud odpovídá jednomu vzoru zadaný prostřednictvím [porovnávání vzorů](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Výrazu, které ověří, zda je první znak je samohláskou a vytvoří návratovou hodnotu mimo vstupní znaky na základě-li první znak byla samohláskou nebo ne:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Tok `toPigLatin` proto:

Zkontrolujte, jestli je první znak vstupní slovo samohláskou.  Je-li, připojte na konec slovo "yay".  Jinak přesuňte tento první znak ke konci slova a do ní přidejte "ay".

Neexistuje jeden konečné si všimněte o to: neexistuje žádné explicitní instrukce k návratu z funkce, na rozdíl od mnoha dalších jazycích odhlašování došlo.  Je to proto F # je založené na výrazu a poslední výrazů v těle funkce je návratovou hodnotu.  Protože `if..then..else` je sám výraz text `then` bloku nebo textu `else` bloku bude vrácen v závislosti na vstupní hodnoty.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Přesunutí kód skriptu do souboru implementace

V předchozích částech v tomto článku ukázán běžné prvním krokem při psaní kódu F #: psaní počáteční funkce a provádění interaktivně s FSI.  To se označuje jako REPL řízený vývoj, kde REPL znamená "Pro čtení vyhodnotit tiskových smyčka".  Je skvělým způsobem, jak experimentovat s funkcemi, dokud něco práce.

Dalším krokem v vývoje řízeného REPL je přesunout funkční kód do souboru implementace F #.  Ho můžete pak zkompilovat pomocí kompilátor jazyka F # do sestavení, které mohou být provedeny.

Chcete-li začít, otevřete `ClassLibraryDemo.fs`.  Můžete si všimnout, že některé kódu se již existuje.  Pokračujte a odstranit definice třídy, ale ponechte [ `namespace` ](../language-reference/namespaces.md) deklarace v horní části.

Dál vytvořte novou [ `module` ](../language-reference/modules.md) názvem `PigLatin` a zkopírujte `toPigLatin` funkce do ní takto:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Toto je jedna z mnoha způsoby, jak můžete uspořádat funkcí v F # – kód a běžný postup, pokud chcete také volání kódu z jazyka C# nebo projekty Visual Basic.

Dále otevřete `Script.fsx` znovu a odstranit celý `toPigLatin` fungovat, ale ujistěte se, aby následující dva řádky v souboru:

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

První řádek je potřeba pro FSI skriptování načíst `ClassLibraryDemo.fs`.  Druhý řádek je pro vaše pohodlí: ho vynechání je nepovinný, ale budete muset zadejte `open ClassLibraryDemo` v okně FSI Pokud chcete převést `ToPigLatin` modulu do oboru.

Potom v okně FSI volání funkce s `PigLatin` modul, který jste definovali dříve:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Úspěšné!  Stejné výsledky jako před, ale nyní načtena ze souboru implementace F #.  Hlavní rozdíl je, že jsou zdrojové soubory F # zkompilovány do sestavení, které lze spustit kdekoliv a nikoli pouze v FSI.

## <a name="summary"></a>Souhrn

V tomto článku když jste se naučili:

1. Jak nastavit Visual Studio Code s Ionide.
2. Jak vytvořit svůj první projekt F # s Ionide.
3. Jak používat F # skriptování k zápisu první funkce F # v Ionide a potom spusťte v FSI.
4. Postup migrace vašeho skriptu Chcete-li F # zdrojový kód a potom tento kód volat z FSI.

Jste nyní vybavený napsat mnohem víc kód F # pomocí sady Visual Studio Code a Ionide.

## <a name="troubleshooting"></a>Poradce při potížích

Můžete řešit určité problémy, které můžete narazit na několika způsoby:

1. Získat kód funkce Ionide úprav, měly být uloženy na disk a uvnitř složky, která je otevřený v pracovním prostoru Visual Studio Code soubory F #.
2. Pokud jste provedené změny v systému nebo nainstalované s Visual Studio Code otevřete Ionide požadavky, restartujte Visual Studio Code.
3. Zkontrolujte, že můžete kompilátor jazyka F # a F # interaktivní z příkazového řádku bez plně kvalifikovanou cestu.  To lze provést zadáním `fsc` v příkazovém řádku pro kompilátor F # a `fsi` nebo `fsharpi` pro Visual F # nástrojů v systému Windows a Mono na Mac/Linux, v uvedeném pořadí.
4. Pokud projekt adresáře obsahuje neplatné znaky, Ionide nemusí fungovat.  Pokud se jedná o tento případ, přejmenování adresáře projektu.
5. Pokud žádná z příkazy Ionide pracují, zkontrolujte vaše [klíčových vazeb Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) chcete zobrazit, pokud jste se jejich přepsání omylem odstraněný.
6. Pokud Ionide je rozděleno na váš počítač a žádná z výše má pevnou váš problém, zkuste odebrat `ionide-fsharp` adresář na váš počítač a znovu nainstalujte modul plug-in.

Ionide je opensourcový projekt vytvořené a spravují členové komunity F #.  Zkontrolujte hlášení problémů a Nebojte se přispět na [Ionide VSCode: úložiště FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).

Pokud máte potíže do sestavy, postupujte podle [pokyny pro získání protokolů vykazování problém](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Můžete také požádat o další pomoc z Ionide vývojáři a F # komunity v [Ionide Gitter kanál](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Další kroky

Další informace o F # a funkce jazyka, podívejte se na [prohlídka z F #](../tour.md).

## <a name="see-also"></a>Viz také

[Prohlídka jazyka F#](../tour.md)

[Referenční dokumentace jazyka F#](../language-reference/index.md)

[Funkce](../language-reference/functions/index.md)

[Moduly](../language-reference/modules.md)

[Obory názvů](../language-reference/namespaces.md)

[Ionide VSCode: FSharp](https://github.com/ionide/ionide-vscode-fsharp)
