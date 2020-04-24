---
title: Sestavení z příkazového řádku
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: c7219c0497bb87f0cc44f27229eaf25f9b3eebce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344796"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="4dbd7-102">Sestavení z příkazového řádku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dbd7-102">Building from the Command Line (Visual Basic)</span></span>

<span data-ttu-id="4dbd7-103">Visual Basic projekt se skládá z jednoho nebo více samostatných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="4dbd7-104">Během procesu známého jako kompilace jsou tyto soubory společně umístěny do jednoho balíčku – jeden spustitelný soubor, který lze spustit jako aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>

<span data-ttu-id="4dbd7-105">Visual Basic poskytuje kompilátor příkazového řádku jako alternativu k kompilování programů z integrovaného vývojového prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="4dbd7-106">Kompilátor příkazového řádku je určený pro situace, kdy nevyžadujete úplnou sadu funkcí v rozhraní IDE – například při použití nebo psaní počítačů s omezeným systémovou pamětí nebo prostorem úložiště.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>

<span data-ttu-id="4dbd7-107">Chcete-li kompilovat zdrojové soubory z integrovaného vývojového prostředí sady Visual Studio, v nabídce **sestavení** klikněte na příkaz **sestavit** .</span><span class="sxs-lookup"><span data-stu-id="4dbd7-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>

> [!TIP]
> <span data-ttu-id="4dbd7-108">Při sestavování souborů projektu pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio můžete zobrazit informace o přidruženém příkazu **Vbc** a jeho přepínačích v okně výstup.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="4dbd7-109">Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavte a spusťte](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a pak nastavte **Podrobnosti výstupu sestavení projektu MSBuild** na **normální** nebo vyšší úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="4dbd7-110">Další informace najdete v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span><span class="sxs-lookup"><span data-stu-id="4dbd7-110">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>

<span data-ttu-id="4dbd7-111">Soubory projektu (. vbproj) můžete kompilovat na příkazovém řádku pomocí nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="4dbd7-112">Další informace naleznete v tématu [Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference) a [Návod: použití nástroje MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="4dbd7-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4dbd7-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4dbd7-113">In This Section</span></span>

<span data-ttu-id="4dbd7-114">[Postupy: volání kompilátoru příkazového řádku](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span><span class="sxs-lookup"><span data-stu-id="4dbd7-114">[How to: Invoke the Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span></span>\
<span data-ttu-id="4dbd7-115">Popisuje, jak vyvolat kompilátor příkazového řádku v příkazovém řádku systému MS-DOS nebo z konkrétního podadresáře.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>

<span data-ttu-id="4dbd7-116">[Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="4dbd7-116">[Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>\
<span data-ttu-id="4dbd7-117">Poskytuje seznam ukázkových příkazových řádků, které můžete upravit pro vlastní použití.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-117">Provides a list of sample command lines that you can modify for your own use.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4dbd7-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4dbd7-118">Related Sections</span></span>

<span data-ttu-id="4dbd7-119">[Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="4dbd7-119">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>\
<span data-ttu-id="4dbd7-120">Obsahuje seznam možností kompilátoru uspořádaných podle abecedy nebo podle účelu.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>

<span data-ttu-id="4dbd7-121">[Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="4dbd7-121">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>\
<span data-ttu-id="4dbd7-122">Popisuje, jak zkompilovat konkrétní oddíly kódu.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-122">Describes how to compile particular sections of code.</span></span>

<span data-ttu-id="4dbd7-123">[Sestavování a čištění projektů a řešení v aplikaci Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="4dbd7-123">[Building and Cleaning Projects and Solutions in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span></span>\
<span data-ttu-id="4dbd7-124">Popisuje, jak uspořádat, co bude zahrnuto v různých sestaveních, zvolit vlastnosti projektu a zajistit, aby se projekty vytvořily ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4dbd7-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
