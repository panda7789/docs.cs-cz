---
title: Interaktivní možnosti
description: Přečtěte si o možnostech příkazového řádku, F# které podporuje Interactive, FSI. exe.
ms.date: 05/16/2016
ms.openlocfilehash: cceb8fb50434f3525ebb2ede16e84720d10d320c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348225"
---
# <a name="f-interactive-options"></a>Interaktivní možnosti F#

> [!NOTE]
> V tomto článku se aktuálně popisuje prostředí jenom pro Windows.  Bude přepsána.

Toto téma popisuje možnosti příkazového řádku, které podporuje F# Interactive, `fsi.exe`. F#Interactive přijímá mnoho z stejných možností příkazového řádku jako F# kompilátor, ale také přijímá některé další možnosti.

## <a name="using-f-interactive-for-scripting"></a>Použití F# Interactive pro skriptování

F#Interactive, `fsi.exe`, lze spustit interaktivně nebo je lze spustit z příkazového řádku pro spuštění skriptu. Syntaxe příkazového řádku je

```console
> fsi.exe [options] [ script-file [arguments] ]
```

Přípona souboru pro F# soubory skriptu je `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tabulka F# interaktivních možností

Následující tabulka shrnuje možnosti podporované F# Interactive. Tyto možnosti lze nastavit na příkazovém řádku nebo v integrovaném vývojovém prostředí sady Visual Studio. Chcete-li nastavit tyto možnosti v integrovaném vývojovém prostředí sady Visual Studio, otevřete nabídku **nástroje** , vyberte možnost **Možnosti...** , poté rozbalte uzel  **F# nástroje** a vyberte možnost  **F# interaktivní**.

Pokud se v F# argumentech interaktivní možnosti zobrazí seznamy, prvky seznamu jsou odděleny středníky (`;`).

|Možnost|Popis|
|------|-----------|
|**--**|Slouží k tomu F# , aby bylo možné interaktivním způsobem nakládat zbývající argumenty F# jako argumenty příkazového řádku pro program nebo skript, ke kterému můžete přistupovat v kódu pomocí seznamu **FSI. CommandLineArgs –** .|
|**--checked**[ **+** &#124; **-** ]|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--codepage:&lt;int&gt;**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--consolecolors**[ **+** &#124; **-** ]|Vypíše upozornění a chybové zprávy barevně.|
|**--crossoptimize**[ **+** &#124; **-** ]|Povolí nebo zakáže optimalizace mezi moduly.|
|**--debug**[ **+** &#124; **-** ]<br /><br />**--debug:** [**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[ **+** &#124; **-** ]<br /><br />**-g:** [**Full**&#124;**pdbonlyed**&#124;&#124;**Embedded**]|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--define:&lt;řetězec&gt;**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--deterministic**[ **+** &#124; **-** ]|Vytvoří deterministické sestavení (včetně GUID verze modulu a časového razítka).|
|**--exec**|Instruuje F# interaktivní ukončení po načtení souborů nebo spuštění souboru skriptu zadaného na příkazovém řádku.|
|**--fullpaths**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--gui**[ **+** &#124; **-** ]|Povolí nebo zakáže smyčku události model Windows Forms. Výchozí hodnota je povolena.|
|**--Help**<br /><br />**-?**|Slouží k zobrazení syntaxe příkazového řádku a stručný popis jednotlivých možností.|
|**--lib:&lt;složka – seznam&gt;**<br /><br />**-I:&lt;seznam složek&gt;**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--Load:&lt;filename&gt;**|Zkompiluje daný zdrojový kód při spuštění a načte zkompilované F# konstrukce do relace. Pokud cílový zdroj obsahuje direktivy skriptování, například **#use** nebo **#load**, je nutné místo **--Load** nebo **#load**použít **--Use** nebo **#use** .|
|**--mlcompatibility**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--noframework**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace najdete v tématu [Možnosti kompilátoru](compiler-options.md) .|
|**--nologo**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--Warn:&lt;upozornění – seznam&gt;**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--optimize**[ **+** &#124; **-** ]|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--preferreduilang –:&lt;lang&gt;**| Určuje preferovaný název jazykové verze jazyka (například ES-ES, ja-JP). |
|**--quiet**|Potlačí F# výstup interaktivního výstupu do datového proudu **stdout** .|
|**--quotations-debug**|Určuje, že se mají vygenerovat dodatečné informace o ladění pro výrazy, které F# jsou odvozeny z literálů citace a reflektované definice. Informace o ladění jsou přidány do vlastních atributů uzlu stromu F# výrazu. Viz [citace kódu](code-quotations.md) a [expr. CustomAttributes –](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[ **+** &#124; **-** ]|Povolí nebo zakáže dokončování tabulátorů v interaktivním režimu.|
|**--reference:&lt;filename&gt;**<br /><br />**-r:&lt;filename&gt;**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--shadowcopyreferences**[ **+** &#124; **-** ]|Zabraňuje tomu, aby F# byly odkazy uzamčeny interaktivním procesem.|
|**--simpleresolution**|Řeší odkazy na sestavení pomocí pravidel založených na adresáři, nikoli pomocí nástroje MSBuild.|
|**--volání funkce tail**[ **+** &#124; **-** ]|Povolí nebo zakáže použití instrukcí Tail IL, což způsobí, že se rámec zásobníku znovu použije pro rekurzivní funkce tail. Tato možnost je ve výchozím nastavení povolená.|
|**--targetprofile:&lt;&gt; řetězců**|Určuje profil cílového rozhraní tohoto sestavení. Platné hodnoty jsou mscorlib, Netcore nebo netstandard.  Výchozí hodnota je mscorlib.|
|**--použijte:&lt;filename&gt;**|Říká Překladači použití daného souboru při spuštění jako počáteční vstup.|
|**--utf8output**|Stejné jako možnost kompilátoru FSC. exe. Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--Warn:&lt;&gt; úrovně upozornění**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]: **&lt;int-list&gt;**|Stejné jako možnost kompilátoru **FSC. exe** . Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).|

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Možnosti kompilátoru](compiler-options.md)|Popisuje možnosti příkazového řádku, které F# jsou k dispozici pro kompilátor, **FSC. exe**.|
