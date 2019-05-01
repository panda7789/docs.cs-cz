---
title: Interaktivní možnosti F#
description: Další informace o možnostech příkazového řádku podporované F# Interactive, fsi.exe.
ms.date: 05/16/2016
ms.openlocfilehash: cca1ef6671878acb1b837d6590139d5de7b7167d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996798"
---
# <a name="f-interactive-options"></a>Interaktivní možnosti F#

> [!NOTE]
> Tento článek popisuje aktuálně prostředí jenom pro Windows.  Bude přepsán.

Toto téma popisuje možnosti příkazového řádku podporované F# Interactive `fsi.exe`. F#Interactive přijímá mnoho stejných možností příkazového řádku, jako F# kompilátoru, ale přijímá také některé další možnosti.

## <a name="using-f-interactive-for-scripting"></a>Pomocí F# Interactive pro skriptování
F#Interaktivní, `fsi.exe`, lze spustit interaktivně nebo může být spuštěn z příkazového řádku pro spuštění skriptu. Syntaxe příkazového řádku

```
> fsi.exe [options] [ script-file [arguments] ]
```

Přípona souboru pro F# soubory skriptu je `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tabulka F# interaktivní možnosti
Následující tabulka shrnuje možnosti podporované F# interaktivní. Tyto možnosti můžete nastavit na příkazovém řádku nebo pomocí integrovaného vývojového prostředí sady Visual Studio. Chcete-li nastavit tyto možnosti v integrovaném vývojovém prostředí sady Visual Studio, otevřete **nástroje** příkaz **možnosti...** , potom rozbalte  **F# nástroje** uzel a vyberte možnost  **F# interaktivní**.

Kde se zobrazí seznamy v F# interaktivní možnost argumenty, prvky seznamu jsou odděleny středníky (`;`).

|Možnost|Popis|
|------|-----------|
|**--**|Slouží k informování F# interaktivní zpracovat zbývající argumenty jako argumenty příkazového řádku F# program nebo skript, kterým můžete přistupovat v kódu pomocí seznamu **fsi.CommandLineArgs**.|
|**--checked**[**+**&#124;**-**]|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**-codepage:&lt;int&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--consolecolors**[**+**&#124;**-**]|Výstupy upozornění a chybové zprávy barvou.|
|**--crossoptimize**[**+**&#124;**-**]|Povolí nebo zakáže optimalizace mezi moduly.|
|**--debug**[**+**&#124;**-**]<br /><br />**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**úplné**&#124;**pdbonly**&#124;**přenosné**&#124;**vložený**]|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--definovat:&lt;řetězec&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--deterministic**[**+**&#124;**-**]|Vytvoří deterministické sestavení (včetně GUID verze modulu a časového razítka).|
|**--exec**|Dává pokyn F# interactive k ukončení po načtení souborů nebo spuštění souboru skriptu, který je uveden v příkazovém řádku.|
|**--fullpaths**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--gui**[**+**&#124;**-**]|Povolí nebo zakáže smyčku událostí Windows Forms. Výchozí hodnota je povolená.|
|**--help**<br /><br />**-?**|Slouží k zobrazení syntaxe příkazového řádku a stručný popis jednotlivých možností.|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;seznam složek&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--načíst:&lt;název souboru&gt;**|Kompiluje kód daného zdroje při spuštění a načtení zkompilovaný F# vytvoří do relace. Pokud zdroj cíle obsahuje skriptovací direktivy, jako **#use** nebo **#load**, pak je třeba použít **– použijte** nebo **#use** místo **– načíst** nebo **#load**.|
|**--mlcompatibility**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--noframework**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md)|
|**--nologo**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--nowarn:&lt;warning-list&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--optimize**[**+**&#124;**-**]|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**-preferreduilang:&lt;lang&gt;**| Určuje název upřednostňovaného výstupního jazyka jazykové verze (například es-ES, ja-JP). |
|**--quiet**|Potlačit F# interaktivní výstupního **stdout** datového proudu.|
|**--quotations-debug**|Určuje, že by pro výrazy, které jsou odvozeny z vyzařovaného dodatečné informace o ladění F# literály citace nezahrnou a reflektovaných definic. Informace o ladění se přidá do vlastní atributy F# uzel stromu výrazu. Zobrazit [nabídky kódu](code-quotations.md) a [Expr.CustomAttributes –](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124;**-**]|Povolit nebo zakázat doplňování tabulátorů v interaktivním režimu.|
|**--reference:&lt;filename&gt;**<br /><br />**-r:&lt;název souboru&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--shadowcopyreferences**[**+**&#124;**-**]|Znemožňuje zamknutí podle referencí F# interaktivní proces.|
|**--simpleresolution**|Překládá odkazy na sestavení pomocí pravidel založených na adresáři spíše než pomocí rozlišení MSBuild.|
|**--tailcalls**[**+**&#124;**-**]|Povolí nebo zakáže použití instrukce IL chvostu, což způsobí opětovné použití pro rekurzivní funkce chvostu rámce zásobníku. Tato možnost je povolená ve výchozím nastavení.|
|**--targetprofile:&lt;řetězec&gt;**|Určuje profil cílového rozhraní tohoto sestavení. Platné hodnoty jsou mscorlib, netcore nebo netstandard.  Výchozí je mscorlib.|
|**– použijte:&lt;název souboru&gt;**|Říká překladači, aby použil zadaný soubor při spuštění jako počáteční vstup.|
|**--utf8output**|Stejná jako možnost kompilátoru fsc.exe. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--warn:&lt;warning-level&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Možnosti kompilátoru](compiler-options.md)|Popisuje možnosti příkazového řádku, které jsou k dispozici pro F# kompilátoru, **fsc.exe**.|
