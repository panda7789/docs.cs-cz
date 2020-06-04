---
title: Příkazové řádky ukázkové kompilace
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 496627d3b77b0382ae7d15c8225a6fbd41f1db73
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403119"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Příkazové řádky ukázkové kompilace (Visual Basic)

Jako alternativu k kompilování Visual Basicch programů v rámci sady Visual Studio můžete kompilovat z příkazového řádku a vytvářet spustitelné soubory (. exe) nebo soubory dynamické knihovny (. dll).

Kompilátor příkazového řádku Visual Basic podporuje úplnou sadu možností, které ovládají vstupní a výstupní soubory, sestavení a možnosti ladění a preprocesoru. Každá možnost je k dispozici ve dvou vzájemně zaměnitelné formě: `-option` a `/option` . Tato dokumentace obsahuje pouze `-option` formulář.

V následující tabulce jsou uvedeny některé ukázkové příkazové řádky, které můžete upravit pro vlastní použití.

|Akce|Použití|
|--------|---------|
|Zkompiluje soubor. vb a vytvoří soubor. exe.|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|Zkompilujte soubor. vb a vytvořte soubor. dll.|`vbc -target:library File.vb`|
|Zkompilujte soubor. vb a vytvořte my. exe.|`vbc -out:My.exe File.vb`|
|Zkompilujte soubor. vb a vytvořte knihovnu a referenční sestavení s názvem File. dll.|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Zkompilovat všechny soubory Visual Basic v aktuálním adresáři s optimalizací na a `DEBUG` definovaným symbolem a vyrábět soubor Soubor2. exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|Zkompiluje všechny Visual Basic soubory v aktuálním adresáři a vyprodukuje ladicí verzi souboru Soubor2. dll bez zobrazení loga nebo upozornění.|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|Zkompilovat všechny soubory Visual Basic v aktuálním adresáři do souboru něco. dll|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> Při sestavování projektu pomocí integrovaného vývojového prostředí sady Visual Studio můžete zobrazit informace o přidruženém příkazu **Vbc** s možnostmi kompilátoru v okně výstup. Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavte a spusťte](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a pak nastavte **Podrobnosti výstupu sestavení projektu MSBuild** na **normální** nebo vyšší úroveň podrobností.

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Podmíněná kompilace](../../programming-guide/program-structure/conditional-compilation.md)
