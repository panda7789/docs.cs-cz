---
title: 'Postupy: Volání kompilátoru příkazového řádku (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: d2d193f8c3d483ff87fe719919982e8c3473ec0b
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221840"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="c19e2-102">Postupy: Volání kompilátoru příkazového řádku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c19e2-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="c19e2-103">Kompilátor příkazového řádku můžete vyvolat zadáním názvu jeho spustitelného souboru do příkazového řádku, označované také jako příkazový.</span><span class="sxs-lookup"><span data-stu-id="c19e2-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="c19e2-104">Pokud kompilujete z výchozího příkazového řádku Windows, je nutné zadat úplnou cestu ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="c19e2-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="c19e2-105">Chcete-li přepsat toto výchozí chování, můžete použít příkazový řádek pro vývojáře pro sadu Visual Studio nebo upravit proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="c19e2-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="c19e2-106">Umožňují z libovolného adresáře kompilovat pouze zadáním názvu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c19e2-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="c19e2-107">K vyvolání kompilátoru pomocí příkazového řádku pro vývojáře pro sadu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c19e2-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>  
  
1.  <span data-ttu-id="c19e2-108">Otevřete složku program Visual Studio Tools v rámci skupiny pro program Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c19e2-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="c19e2-109">Developer Command Prompt pro sadu Visual Studio můžete použít pro přístup k kompilátor z libovolného adresáře v počítači, pokud je nainstalována aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c19e2-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="c19e2-110">Vyvolání Developer Command Prompt pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c19e2-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>  
  
4.  <span data-ttu-id="c19e2-111">Na příkazovém řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="c19e2-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="c19e2-112">Například, pokud váš zdrojový kód jste uložili v adresáři s názvem `SourceFiles`, by otevřete příkazový řádek a zadejte `cd SourceFiles` pro přechod do této složky.</span><span class="sxs-lookup"><span data-stu-id="c19e2-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="c19e2-113">Pokud adresář obsahuje zdrojový soubor s názvem `Source.vb`, může zkompilovat jej tak, že zadáte `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="c19e2-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="c19e2-114">Chcete-li nastavit proměnné prostředí PATH v kompilátoru pro příkazový řádek Windows</span><span class="sxs-lookup"><span data-stu-id="c19e2-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="c19e2-115">Pomocí funkce Windows Search hledání Vbc.exe na místním disku.</span><span class="sxs-lookup"><span data-stu-id="c19e2-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="c19e2-116">Přesný název adresáře, kde je umístěn kompilátor závisí na umístění adresáře Windows a verzí "nainstalováno rozhraní .NET Framework".</span><span class="sxs-lookup"><span data-stu-id="c19e2-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="c19e2-117">Pokud máte více než jednu verzi "Instalace rozhraní .NET Framework", musíte určit, která verze se má použít (obvykle na nejnovější verzi).</span><span class="sxs-lookup"><span data-stu-id="c19e2-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="c19e2-118">Z vaší **Start** nabídky, klikněte pravým tlačítkem na **tento počítač**a potom klikněte na tlačítko **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="c19e2-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="c19e2-119">Klikněte na tlačítko **Upřesnit** kartu a potom klikněte na tlačítko **proměnné prostředí**.</span><span class="sxs-lookup"><span data-stu-id="c19e2-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="c19e2-120">V **systému** podokno proměnných, vyberte **cesta** ze seznamu a klikněte na tlačítko **upravit**.</span><span class="sxs-lookup"><span data-stu-id="c19e2-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="c19e2-121">V **upravit systému** proměnné dialogové okno, přesuňte kurzor na konec řetězce **hodnotu proměnné** pole a zadejte středníkem (;) za nímž následuje název úplné adresáře v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="c19e2-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="c19e2-122">Klikněte na tlačítko **OK** potvrzení úprav a zavřete dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="c19e2-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="c19e2-123">Po změně proměnné prostředí PATH, můžete spustit kompilátor jazyka Visual Basic v příkazovém řádku Windows z libovolného adresáře v počítači.</span><span class="sxs-lookup"><span data-stu-id="c19e2-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="c19e2-124">K volání kompilátoru příkazového řádku Windows</span><span class="sxs-lookup"><span data-stu-id="c19e2-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="c19e2-125">Z **Start** nabídky, klikněte na **Příslušenství** složku a pak otevřete **příkazový řádek Windows**.</span><span class="sxs-lookup"><span data-stu-id="c19e2-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="c19e2-126">Na příkazovém řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="c19e2-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="c19e2-127">Například, pokud váš zdrojový kód jste uložili v adresáři s názvem `SourceFiles`, by otevřete příkazový řádek a zadejte `cd SourceFiles` pro přechod do této složky.</span><span class="sxs-lookup"><span data-stu-id="c19e2-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="c19e2-128">Pokud adresář obsahuje zdrojový soubor s názvem `Source.vb`, může zkompilovat jej tak, že zadáte `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="c19e2-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c19e2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c19e2-129">See Also</span></span>  
 [<span data-ttu-id="c19e2-130">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19e2-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c19e2-131">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="c19e2-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
