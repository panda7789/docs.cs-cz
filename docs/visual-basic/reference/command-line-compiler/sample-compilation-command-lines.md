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
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="e1825-102">Příkazové řádky ukázkové kompilace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1825-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="e1825-103">Jako alternativu k kompilování [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programy z uvnitř [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], můžete zkompilovat z příkazového řádku k vytvoření souborů spustitelný soubor (.exe) nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="e1825-103">As an alternative to compiling [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs from within [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="e1825-104">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Podporuje kompletní sadu možností, které ovládají vstupní a výstupní soubory, sestavení a ladění a preprocesor – možnosti kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e1825-104">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="e1825-105">Každá možnost je k dispozici ve dvou formách zaměňovat: `-option` a `/option`.</span><span class="sxs-lookup"><span data-stu-id="e1825-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="e1825-106">Tato dokumentace se zobrazí pouze `-option` formuláře.</span><span class="sxs-lookup"><span data-stu-id="e1825-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="e1825-107">Následující tabulka uvádí některé ukázkové příkazové řádky, které můžete upravit pro vlastní použití.</span><span class="sxs-lookup"><span data-stu-id="e1825-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="e1825-108">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="e1825-108">To</span></span>|<span data-ttu-id="e1825-109">Použití</span><span class="sxs-lookup"><span data-stu-id="e1825-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="e1825-110">Kompilace File.vb a vytvořit File.exe</span><span class="sxs-lookup"><span data-stu-id="e1825-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="e1825-111">Kompilace File.vb a vytvoření souboru File.dll</span><span class="sxs-lookup"><span data-stu-id="e1825-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="e1825-112">Kompilace File.vb a vytvořit My.exe</span><span class="sxs-lookup"><span data-stu-id="e1825-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="e1825-113">Všechny zkompilovat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory v aktuálním adresáři s optimalizace a `DEBUG` symbol definované, který vytvořil File2.exe</span><span class="sxs-lookup"><span data-stu-id="e1825-113">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="e1825-114">Všechny zkompilovat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory v aktuálním adresáři, který vytvořil ladicí verze File2.dll pro ladění bez zobrazování logo nebo upozornění</span><span class="sxs-lookup"><span data-stu-id="e1825-114">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="e1825-115">Všechny zkompilovat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory v aktuálním adresáři na Something.dll</span><span class="sxs-lookup"><span data-stu-id="e1825-115">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
 <span data-ttu-id="e1825-116">Při kompilaci z příkazového řádku, musí být explicitně uvedena Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] běhové knihovny prostřednictvím `-reference` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="e1825-116">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] run-time library through the `-reference` compiler option.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="e1825-117">Při sestavování projektu pomocí prostředí Visual Studio IDE, můžete zobrazit informace o přidruženého **Vbc –** s jeho – možnosti kompilátoru v okně výstupu.</span><span class="sxs-lookup"><span data-stu-id="e1825-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="e1825-118">Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a poté nastavte **výstup sestavení projektu MSBuild podrobností** k **normální** nebo vyšší úrovni podrobností.</span><span class="sxs-lookup"><span data-stu-id="e1825-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="e1825-119">Další informace najdete v tématu [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="e1825-119">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1825-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1825-120">See Also</span></span>  
 [<span data-ttu-id="e1825-121">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="e1825-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e1825-122">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="e1825-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
