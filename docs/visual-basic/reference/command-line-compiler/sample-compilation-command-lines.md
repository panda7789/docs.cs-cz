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
ms.openlocfilehash: 27a20a5a3525353ffbced729b8ac9c98b3e48fc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350844"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="47076-102">Příkazové řádky ukázkové kompilace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47076-102">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="47076-103">Jako alternativu k kompilování Visual Basicch programů v rámci sady Visual Studio můžete kompilovat z příkazového řádku a vytvářet spustitelné soubory (. exe) nebo soubory dynamické knihovny (. dll).</span><span class="sxs-lookup"><span data-stu-id="47076-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="47076-104">Kompilátor příkazového řádku Visual Basic podporuje úplnou sadu možností, které ovládají vstupní a výstupní soubory, sestavení a možnosti ladění a preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="47076-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="47076-105">Každá možnost je k dispozici ve dvou vzájemně zaměnitelné formě: `-option` a `/option`.</span><span class="sxs-lookup"><span data-stu-id="47076-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="47076-106">Tato dokumentace obsahuje pouze formulář `-option`.</span><span class="sxs-lookup"><span data-stu-id="47076-106">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="47076-107">V následující tabulce jsou uvedeny některé ukázkové příkazové řádky, které můžete upravit pro vlastní použití.</span><span class="sxs-lookup"><span data-stu-id="47076-107">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="47076-108">Pro</span><span class="sxs-lookup"><span data-stu-id="47076-108">To</span></span>|<span data-ttu-id="47076-109">Použití</span><span class="sxs-lookup"><span data-stu-id="47076-109">Use</span></span>|
|--------|---------|
|<span data-ttu-id="47076-110">Zkompiluje soubor. vb a vytvoří soubor. exe.</span><span class="sxs-lookup"><span data-stu-id="47076-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="47076-111">Zkompilujte soubor. vb a vytvořte soubor. dll.</span><span class="sxs-lookup"><span data-stu-id="47076-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="47076-112">Zkompilujte soubor. vb a vytvořte my. exe.</span><span class="sxs-lookup"><span data-stu-id="47076-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="47076-113">Zkompilujte soubor. vb a vytvořte knihovnu a referenční sestavení s názvem File. dll.</span><span class="sxs-lookup"><span data-stu-id="47076-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="47076-114">Zkompilovat všechny soubory Visual Basic v aktuálním adresáři s optimalizací na a `DEBUG` definovaným symbolem a vyprodukováním souboru Soubor2. exe</span><span class="sxs-lookup"><span data-stu-id="47076-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="47076-115">Zkompiluje všechny Visual Basic soubory v aktuálním adresáři a vyprodukuje ladicí verzi souboru Soubor2. dll bez zobrazení loga nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="47076-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="47076-116">Zkompilovat všechny soubory Visual Basic v aktuálním adresáři do souboru něco. dll</span><span class="sxs-lookup"><span data-stu-id="47076-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="47076-117">Při sestavování projektu pomocí integrovaného vývojového prostředí sady Visual Studio můžete zobrazit informace o přidruženém příkazu **Vbc** s možnostmi kompilátoru v okně výstup.</span><span class="sxs-lookup"><span data-stu-id="47076-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="47076-118">Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavte a spusťte](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a pak nastavte **Podrobnosti výstupu sestavení projektu MSBuild** na **normální** nebo vyšší úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="47076-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="47076-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47076-119">See also</span></span>

- [<span data-ttu-id="47076-120">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="47076-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="47076-121">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="47076-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
