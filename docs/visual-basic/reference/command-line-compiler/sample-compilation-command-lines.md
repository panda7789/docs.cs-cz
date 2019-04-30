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
ms.openlocfilehash: 0771ed41d6c58ce7cc98435b405f5819e45393db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916757"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Příkazové řádky ukázkové kompilace (Visual Basic)
Jako alternativu ke kompilaci programů jazyka Visual Basic v sadě Visual Studio můžete zkompilovat z příkazového řádku k vytvoření souborů spustitelný soubor (.exe) nebo dynamická knihovna (.dll).  
  
 Kompilátor příkazového řádku jazyka Visual Basic podporuje kompletní sadu možností, které řídí vstup a výstup souborů, sestavení a ladění a možnosti preprocesoru. Každá možnost je k dispozici ve dvou formách zaměnitelné: `-option` a `/option`. Tato dokumentace se zobrazí pouze `-option` formuláře.  
  
 Následující tabulka uvádí některé ukázkové příkazové řádky, které můžete upravit pro vlastní použití.  
  
|Chcete-li|Použití|  
|--------|---------|  
|Kompilace File.vb a vytvořit File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|Kompilace File.vb a vytvořit soubor.dll|`vbc -target:library File.vb`|  
|Kompilace File.vb a vytvořit My.exe|`vbc -out:My.exe File.vb`|  
|Kompilace File.vb a vytvořit knihovnu a odkaz na sestavení s názvem soubor.dll|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Zkompilovat všechny soubory jazyka Visual Basic v aktuálním adresáři s optimalizací na a `DEBUG` symbol definovaný, vytváření File2.exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Zkompilovat všechny soubory jazyka Visual Basic do aktuálního adresáře, vytváření verzí ladění File2.dll pro ladění bez zobrazení loga nebo upozornění|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Zkompilovat všechny soubory jazyka Visual Basic v aktuálním adresáři Something.dll|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  Při vytváření projektu pomocí rozhraní IDE sady Visual Studio můžete zobrazit informace o přidružené **Vbc –** příkaz s jeho možnosti kompilátoru v okně výstup. Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a pak nastavte **podrobnosti výstupu sestavení projektu nástroje MSBuild** k **normální** nebo vyšší úroveň podrobností.   
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
