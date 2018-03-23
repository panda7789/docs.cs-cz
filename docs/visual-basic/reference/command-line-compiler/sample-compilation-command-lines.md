---
title: Příkazové řádky ukázkové kompilace (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7c3fac318e05c5e3d6fb9dd7117cac70ead03dc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Příkazové řádky ukázkové kompilace (Visual Basic)
Jako alternativu k kompilování [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programy z uvnitř [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], můžete zkompilovat z příkazového řádku k vytvoření souborů spustitelný soubor (.exe) nebo dynamická knihovna (DLL).  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Podporuje kompletní sadu možností, které ovládají vstupní a výstupní soubory, sestavení a ladění a preprocesor – možnosti kompilátoru příkazového řádku. Každá možnost je k dispozici ve dvou formách zaměňovat: `-option` a `/option`. Tato dokumentace se zobrazí pouze `-option` formuláře.  
  
 Následující tabulka uvádí některé ukázkové příkazové řádky, které můžete upravit pro vlastní použití.  
  
|Chcete-li|Použití|  
|--------|---------|  
|Kompilace File.vb a vytvořit File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|Kompilace File.vb a vytvoření souboru File.dll|`vbc -target:library File.vb`|  
|Kompilace File.vb a vytvořit My.exe|`vbc -out:My.exe File.vb`|  
|Všechny zkompilovat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory v aktuálním adresáři s optimalizace a `DEBUG` symbol definované, který vytvořil File2.exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Všechny zkompilovat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory v aktuálním adresáři, který vytvořil ladicí verze File2.dll pro ladění bez zobrazování logo nebo upozornění|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Všechny zkompilovat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory v aktuálním adresáři na Something.dll|`vbc -target:library -out:Something.dll *.vb`|  
  
 Při kompilaci z příkazového řádku, musí být explicitně uvedena Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] běhové knihovny prostřednictvím `-reference` – možnost kompilátoru.  
  
> [!TIP]
>  Při sestavování projektu pomocí prostředí Visual Studio IDE, můžete zobrazit informace o přidruženého **Vbc –** s jeho – možnosti kompilátoru v okně výstupu. Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a poté nastavte **výstup sestavení projektu MSBuild podrobností** k **normální** nebo vyšší úrovni podrobností. Další informace najdete v tématu [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
