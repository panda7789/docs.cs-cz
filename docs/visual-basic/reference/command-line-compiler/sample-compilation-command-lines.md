---
title: Příkazové řádky ukázkové kompilace (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b0f1fc1d269801efdbf2e89d10679dc8159851f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653660"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Příkazové řádky ukázkové kompilace (Visual Basic)
Jako alternativu k kompilace jazyka Visual Basic programů z v sadě Visual Studio můžete zkompilovat z příkazového řádku k vytvoření souborů spustitelný soubor (.exe) nebo dynamická knihovna (DLL).  
  
 Visual Basic – kompilátor příkazového řádku podporuje úplnou sadu možností, které řídí vstup a výstup souborů, sestavení a ladění a preprocesoru možnosti. Každá možnost je k dispozici ve dvou formách zaměňovat: `-option` a `/option`. Tato dokumentace se zobrazí pouze `-option` formuláře.  
  
 Následující tabulka uvádí některé ukázkové příkazové řádky, které můžete upravit pro vlastní použití.  
  
|Chcete-li|Použití|  
|--------|---------|  
|Kompilace File.vb a vytvořit File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|Kompilace File.vb a vytvoření souboru File.dll|`vbc -target:library File.vb`|  
|Kompilace File.vb a vytvořit My.exe|`vbc -out:My.exe File.vb`|  
|Kompilace File.vb a vytvořte knihovnu a referenční sestavení s názvem souboru File.dll|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Kompilaci všech souborů jazyka Visual Basic v aktuálním adresáři, s optimalizací na a `DEBUG` symbol definované, který vytvořil File2.exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Kompilaci všech souborů jazyka Visual Basic v aktuálním adresáři, který vytvořil ladicí verze File2.dll pro ladění bez zobrazování logo nebo upozornění|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Všechny soubory jazyka Visual Basic v aktuálním adresáři na Something.dll kompilace|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  Při sestavování projektu pomocí prostředí Visual Studio IDE, můžete zobrazit informace o přidruženého **Vbc –** s jeho – možnosti kompilátoru v okně výstupu. Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a poté nastavte **výstup sestavení projektu MSBuild podrobností** k **normální** nebo vyšší úrovni podrobností.   
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
