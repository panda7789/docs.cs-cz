---
title: Interaktivní možnosti F#
description: 'Další informace o možnostech příkazového řádku F # interaktivní, nepodporuje fsi.exe.'
ms.date: 05/16/2016
ms.openlocfilehash: a461dd0eeff2de3d15e557ba37138fbd62ca43ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565802"
---
# <a name="f-interactive-options"></a>Interaktivní možnosti F#

> [!NOTE]
Tento článek popisuje aktuálně prostředí jenom pro Windows.  Bude přepsán.

Toto téma popisuje možnosti příkazového řádku F # interaktivní, nepodporuje `fsi.exe`. F # interaktivní přijímá řadu stejné možnosti příkazového řádku jako kompilátor jazyka F #, ale také přijímá některé další možnosti.

## <a name="using-f-interactive-for-scripting"></a>Pomocí F # interaktivní pro skriptování
F # interaktivní, `fsi.exe`, může být spuštěn interaktivně, nebo může být spuštěn z příkazového řádku spustit skript. Syntaxe příkazového řádku je

```
> fsi.exe [options] [ script-file [arguments] ]
```

Přípona souboru pro soubory skriptu F # je `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tabulka interaktivní možnosti F #
Následující tabulka shrnuje možnosti podporované F # interaktivní. Tyto možnosti můžete nastavit na příkazovém řádku nebo pomocí prostředí Visual Studio IDE. Chcete-li nastavit tyto možnosti v prostředí Visual Studio IDE, otevřete **nástroje** nabídce vyberte možnost **možnosti...** , pak rozbalte **nástroje F #** uzel a vyberte možnost **F # interaktivní**.

Kde seznamy se zobrazují v F # interaktivní možnost argumenty, seznamu elementů oddělených středníky (`;`).

|Možnost|Popis|
|------|-----------|
|**--**|Používá se udělit pokyny F # interaktivní považovat za zbývající argumenty argumenty příkazového řádku F # program nebo skript, kterým můžete přistupovat v kódu pomocí seznamu **fsi.CommandLineArgs**.|
|**--checked**[**+**&#124;**-**]|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**codepage –:&lt;int&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--consolecolors**[**+**&#124;**-**]|Výstupy upozornění a chybové zprávy v barev.|
|**--crossoptimize**[**+**&#124;**-**]|Povolit nebo zakázat optimalizace cross-module.|
|**--debug**[**+**&#124;**-**]<br /><br />**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**úplné**&#124;**pdbonly**&#124;**přenosné**&#124;**embedded**]|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--definovat:&lt;řetězec&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--deterministic**[**+**&#124;**-**]|Vytváří deterministickou sestavení (včetně verze modulu GUID a časové razítko).|
|**--exec**|Dá pokyn, F # interaktivní ukončíte po načtení souborů nebo spuštění souboru skriptu zadána na příkazovém řádku.|
|**fullpaths –**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--gui**[**+**&#124;**-**]|Povolí nebo zakáže smyčky událostí Windows Forms. Výchozí hodnota je povoleno.|
|**– Nápověda**<br /><br />**-?**|Slouží k zobrazení syntaxe příkazového řádku a stručný popis jednotlivých možností.|
|**--lib:&lt;seznamu složek&gt;**<br /><br />**-I:&lt;seznamu složek&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--načíst:&lt;filename&gt;**|Kompilovaný kód zadaná zdrojová při spuštění a načte kompilované konstrukce F # do relace. Pokud cílový zdroj obsahuje skriptování direktivy, jako **#use** nebo **#load**, pak musíte použít **– použít** nebo **#use** místo **– načíst** nebo **#load**.|
|**mlcompatibility –**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--noframework**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md)|
|**--nologo**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**nowarn –:&lt;seznam upozornění&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--optimize**[**+**&#124;**-**]|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**preferreduilang –:&lt;jazyk&gt;**| Určuje název jazykové verze jazyka upřednostňované výstup (například es-ES, ja-JP). |
|**--quiet**|Potlačit F # interaktivní na výstup do **stdout** datového proudu.|
|**--quotations-debug**|Určuje, že by měl pro výrazy, které jsou odvozeny od uvozovek literály F # a reflektován definice vygenerované velmi ladicí informace. Informace o ladění se přidá do vlastní atributy uzlu stromu výraz F #. V tématu [Code uvozovky](code-quotations.md) a [Expr.CustomAttributes –](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124;**-**]|Povolit nebo zakázat dokončování pomocí tabulátorů v interaktivním režimu.|
|**--reference:&lt;filename&gt;**<br /><br />**-r:&lt;filename&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--shadowcopyreferences**[**+**&#124;**-**]|Zabraňuje odkazy z zamykají F # interaktivní proces.|
|**--simpleresolution**|Přeloží odkazy na sestavení pomocí pravidel založených na adresář, nikoli MSBuild řešení.|
|**tailcalls –**[**+**&#124;**-**]|Povolí nebo zakáže použití pokyn IL tail, což způsobí, že rámce zásobníku znovu použije pro rekurzivní funkce tail. Tato možnost je povolená ve výchozím nastavení.|
|**--targetprofile:&lt;řetězec&gt;**|Určuje cílový framework profil tohoto sestavení. Platné hodnoty jsou mscorlib, netcore nebo monikerů netstandard.  Výchozí hodnota je mscorlib.|
|**--použít:&lt;filename&gt;**|Informuje překladač použít daný soubor při spuštění jako počáteční vstup.|
|**--utf8output**|Stejné jako možnost fsc.exe kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--Upozornit:&lt;úroveň upozornění&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|Stejné jako **fsc.exe** – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).|

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----|-----------|
|[Možnosti kompilátoru](compiler-options.md)|Popisuje možnosti příkazového řádku, které jsou k dispozici pro kompilátor F # **fsc.exe**.|
