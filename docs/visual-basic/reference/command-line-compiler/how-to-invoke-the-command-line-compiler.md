---
title: 'Postupy: Volání kompilátoru příkazového řádku'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 3b34ebba68c9c9b2a8335822d0ffaef2a9b06d7c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344263"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="c69a2-102">Postupy: Volání kompilátoru příkazového řádku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c69a2-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="c69a2-103">Kompilátor příkazového řádku můžete vyvolat zadáním názvu spustitelného souboru do příkazového řádku, který se označuje také jako příkazový řádek MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="c69a2-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="c69a2-104">Pokud kompilujete z výchozího příkazového řádku systému Windows, je nutné zadat plně kvalifikovanou cestu ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="c69a2-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="c69a2-105">Chcete-li přepsat toto výchozí chování, můžete buď použít Developer Command Prompt pro Visual Studio, nebo upravit proměnnou prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="c69a2-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="c69a2-106">Obě umožňují kompilovat z libovolného adresáře pouhým zadáním názvu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c69a2-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="c69a2-107">Volání kompilátoru pomocí Developer Command Prompt pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c69a2-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="c69a2-108">Otevřete složku Visual Studio Tools program ve skupině Microsoft Visual Studio programu.</span><span class="sxs-lookup"><span data-stu-id="c69a2-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="c69a2-109">Pokud je nainstalována aplikace Visual Studio, můžete použít Developer Command Prompt pro Visual Studio k přístupu k kompilátoru z libovolného adresáře na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="c69a2-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="c69a2-110">Vyvolejte Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c69a2-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="c69a2-111">Do příkazového řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="c69a2-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="c69a2-112">Pokud jste například uložili zdrojový kód do adresáře s názvem `SourceFiles`, otevřete příkazový řádek a zadejte `cd SourceFiles` příkaz pro změnu do tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="c69a2-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="c69a2-113">Pokud adresář obsahoval zdrojový soubor s názvem `Source.vb`, můžete ho zkompilovat zadáním. `vbc.exe Source.vb`</span><span class="sxs-lookup"><span data-stu-id="c69a2-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="c69a2-114">Nastavení proměnné prostředí PATH na kompilátor příkazového řádku systému Windows</span><span class="sxs-lookup"><span data-stu-id="c69a2-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="c69a2-115">K vyhledání Vbc. exe na místním disku použijte funkci Windows Search.</span><span class="sxs-lookup"><span data-stu-id="c69a2-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="c69a2-116">Přesný název adresáře, ve kterém je kompilátor umístěný, závisí na umístění adresáře systému Windows a ve verzi nainstalovaného ".NET Framework".</span><span class="sxs-lookup"><span data-stu-id="c69a2-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="c69a2-117">Pokud máte nainstalovanou více než jednu verzi .NET Framework, musíte určit, která verze se má použít (obvykle nejnovější verze).</span><span class="sxs-lookup"><span data-stu-id="c69a2-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="c69a2-118">V nabídce **Start** klikněte pravým tlačítkem myši na položku **Tento počítač**a potom v místní nabídce klikněte na příkaz **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="c69a2-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="c69a2-119">Klikněte na kartu **Upřesnit** a pak klikněte na **proměnné prostředí**.</span><span class="sxs-lookup"><span data-stu-id="c69a2-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="c69a2-120">V podokně **systémové** proměnné vyberte v seznamu možnost **cesta** a klikněte na **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="c69a2-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="c69a2-121">V dialogovém okně **upravit systémovou** proměnnou přesuňte kurzor na konec řetězce v poli **hodnota proměnné** a zadejte středník (;) Následuje úplný název adresáře, který byl nalezen v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="c69a2-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="c69a2-122">Kliknutím na tlačítko **OK** potvrďte provedené úpravy a zavřete dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="c69a2-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="c69a2-123">Po změně proměnné prostředí PATH můžete spustit kompilátor Visual Basic v příkazovém řádku systému Windows z libovolného adresáře v počítači.</span><span class="sxs-lookup"><span data-stu-id="c69a2-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="c69a2-124">Vyvolání kompilátoru pomocí příkazového řádku systému Windows</span><span class="sxs-lookup"><span data-stu-id="c69a2-124">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="c69a2-125">V nabídce **Start** klikněte na složku **příslušenství** a pak otevřete **příkazový řádek systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="c69a2-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="c69a2-126">Do příkazového řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="c69a2-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="c69a2-127">Pokud jste například uložili zdrojový kód do adresáře s názvem `SourceFiles`, otevřete příkazový řádek a zadejte `cd SourceFiles` příkaz pro změnu do tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="c69a2-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="c69a2-128">Pokud adresář obsahoval zdrojový soubor s názvem `Source.vb`, můžete ho zkompilovat zadáním. `vbc.exe Source.vb`</span><span class="sxs-lookup"><span data-stu-id="c69a2-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c69a2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c69a2-129">See also</span></span>

- [<span data-ttu-id="c69a2-130">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="c69a2-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c69a2-131">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="c69a2-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
