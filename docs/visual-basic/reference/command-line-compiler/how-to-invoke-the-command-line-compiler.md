---
title: "Postupy: Volání kompilátoru příkazového řádku (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c69860ede5620272e67bde435e6e6fa08cc81bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="f1e57-102">Postupy: Volání kompilátoru příkazového řádku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1e57-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="f1e57-103">Kompilátor příkazového řádku můžete vyvolat zadáním názvu jeho spustitelného souboru do příkazového řádku, také známé jako v systému MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="f1e57-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="f1e57-104">Pokud kompilujete z výchozího příkazového řádku systému Windows, musíte zadat plně kvalifikovanou cestu ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="f1e57-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="f1e57-105">Pokud chcete přepsat toto výchozí chování, můžete použít [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] příkazový řádek, nebo upravit proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="f1e57-105">To override this default behavior, you can either use the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt, or modify the PATH environment variable.</span></span> <span data-ttu-id="f1e57-106">Oba umožňují zkompilovat z libovolného adresáře jednoduše zadáním názvu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f1e57-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a><span data-ttu-id="f1e57-107">K volání kompilátoru pomocí příkazového řádku Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f1e57-107">To invoke the compiler using the Visual Studio Command Prompt</span></span>  
  
1.  <span data-ttu-id="f1e57-108">Otevřete složku programu nástroje sady Visual Studio v rámci skupiny pro program Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1e57-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="f1e57-109">Můžete použít [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] příkazového řádku pro přístup do kompilátoru z libovolného adresáře na počítači, pokud je nainstalovaná sada Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1e57-109">You can use the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="f1e57-110">Vyvolání [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f1e57-110">Invoke the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt.</span></span>  
  
4.  <span data-ttu-id="f1e57-111">Na příkazovém řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="f1e57-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="f1e57-112">Například, pokud jste uložili vašeho zdrojového kódu v adresář s názvem `SourceFiles`, by otevřete příkazový řádek a zadejte `cd SourceFiles` tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="f1e57-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="f1e57-113">Pokud adresář obsahoval zdrojový soubor s názvem `Source.vb`, může ho zkompilovat zadáním `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="f1e57-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="f1e57-114">Chcete-li nastavit proměnné prostředí PATH kompilátoru příkazového řádku pro Windows</span><span class="sxs-lookup"><span data-stu-id="f1e57-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="f1e57-115">Pomocí funkce Windows Search najít Vbc.exe na váš místní disk.</span><span class="sxs-lookup"><span data-stu-id="f1e57-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="f1e57-116">Přesný název adresáře, kde je umístěný kompilátor závisí na umístění adresáře systému Windows a verzi "Instalace rozhraní .NET Framework".</span><span class="sxs-lookup"><span data-stu-id="f1e57-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="f1e57-117">Pokud máte více než jedna verze "nainstalováno rozhraní .NET Framework", musíte určit, kterou verzi má použít (obvykle nejnovější verzi).</span><span class="sxs-lookup"><span data-stu-id="f1e57-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="f1e57-118">Z vaší **spustit** nabídky, klikněte pravým tlačítkem na **Můj počítač**a potom klikněte na **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="f1e57-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="f1e57-119">Klikněte **Upřesnit** a pak klikněte **proměnné prostředí**.</span><span class="sxs-lookup"><span data-stu-id="f1e57-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="f1e57-120">V **systému** proměnné podokně, vyberte **cesta** ze seznamu a klikněte na tlačítko **upravit**.</span><span class="sxs-lookup"><span data-stu-id="f1e57-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="f1e57-121">V **upravit systému** proměnné dialogu, přesuňte kurzor na konec řetězec v **hodnota proměnné** pole a zadejte středníkem (;) a název úplné directory nalezen v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="f1e57-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="f1e57-122">Klikněte na tlačítko **OK** potvrďte provedené úpravy a zavřete dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="f1e57-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="f1e57-123">Po provedení změny proměnné prostředí PATH, můžete spustit [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru na příkazovém řádku Windows z libovolného adresáře v počítači.</span><span class="sxs-lookup"><span data-stu-id="f1e57-123">After you change the PATH environment variable, you can run the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="f1e57-124">K volání kompilátoru pomocí příkazového řádku systému Windows</span><span class="sxs-lookup"><span data-stu-id="f1e57-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="f1e57-125">Z **spustit** nabídky, klikněte na **Příslušenství** složku a potom otevřete **příkazového řádku Windows**.</span><span class="sxs-lookup"><span data-stu-id="f1e57-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="f1e57-126">Na příkazovém řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="f1e57-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="f1e57-127">Například, pokud jste uložili vašeho zdrojového kódu v adresář s názvem `SourceFiles`, by otevřete příkazový řádek a zadejte `cd SourceFiles` tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="f1e57-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="f1e57-128">Pokud adresář obsahoval zdrojový soubor s názvem `Source.vb`, může ho zkompilovat zadáním `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="f1e57-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e57-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1e57-129">See Also</span></span>  
 [<span data-ttu-id="f1e57-130">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="f1e57-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f1e57-131">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="f1e57-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
