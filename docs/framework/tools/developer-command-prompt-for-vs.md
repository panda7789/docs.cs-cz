---
title: Developer Command Prompt pro sadu Visual Studio
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20dc7caa9e4c3e023bf2848b1dd8c63a9b94a01b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170006"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="50dc5-102">Developer Command Prompt pro sadu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="50dc5-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="50dc5-103">Developer Command Prompt pro sadu Visual Studio umožňuje snadno používat nástroje rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50dc5-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="50dc5-104">Je příkazový řádek, který automaticky nastavuje určité proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="50dc5-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
[<span data-ttu-id="50dc5-105">Stáhněte si Visual Studio</span><span class="sxs-lookup"><span data-stu-id="50dc5-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="50dc5-106">Hledat příkazový řádek na svém počítači</span><span class="sxs-lookup"><span data-stu-id="50dc5-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="50dc5-107">Můžete mít více příkazových řádků, v závislosti na verzi sady Visual Studio a všech dodatečných sad SDK si nainstalujete.</span><span class="sxs-lookup"><span data-stu-id="50dc5-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="50dc5-108">Například 64bitové verze sady Visual Studio poskytují 32bitové a 64bitové verze příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="50dc5-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="50dc5-109">(32bitové a 64bitové verze Většina nástrojů jsou stejné, ale u několika nástrojů měnit konkrétní 32bitové a 64bitové prostředí) Pokud tyto kroky nefungují, můžete zkusit [ručně vyhledat soubory na svém počítači](#manually-locate-the-files-on-your-machine) nebo [spustit z příkazového řádku v sadě Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="50dc5-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="50dc5-110">V systému Windows 10</span><span class="sxs-lookup"><span data-stu-id="50dc5-110">In Windows 10</span></span>

1. <span data-ttu-id="50dc5-111">Do vyhledávacího pole na hlavním panelu, začněte psát název nástroje, jako například `dev` nebo `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="50dc5-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="50dc5-112">Tím se zobrazí seznam nainstalovaných aplikací, které odpovídají vaší vyhledávací vzory.</span><span class="sxs-lookup"><span data-stu-id="50dc5-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="50dc5-113">Pokud hledáte různých příkazového řádku, zkuste zadat jinou hledaný termín, jako `prompt`.</span><span class="sxs-lookup"><span data-stu-id="50dc5-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="50dc5-114">Zvolte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="50dc5-114">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="50dc5-115">Ve Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="50dc5-115">In Windows 8.1</span></span>

1. <span data-ttu-id="50dc5-116">Přejděte na **Start** obrazovku stisknutím klávesy s logem Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici pro příklad.</span><span class="sxs-lookup"><span data-stu-id="50dc5-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="50dc5-117">Na **Start** obrazovky, stiskněte klávesu **Ctrl**+**kartu** otevřít **aplikace** seznamu a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="50dc5-117">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="50dc5-118">Zobrazí seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazové řádky.</span><span class="sxs-lookup"><span data-stu-id="50dc5-118">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="50dc5-119">Zvolte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="50dc5-119">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="50dc5-120">V systému Windows 8</span><span class="sxs-lookup"><span data-stu-id="50dc5-120">In Windows 8</span></span>

1. <span data-ttu-id="50dc5-121">Přejděte na **Start** obrazovku stisknutím klávesy s logem Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici pro příklad.</span><span class="sxs-lookup"><span data-stu-id="50dc5-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="50dc5-122">Na **Start** obrazovky, stiskněte klávesu s logem Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="50dc5-122">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="50dc5-123">Zvolte **aplikace zobrazit** ikony v dolní části obrazovky a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="50dc5-123">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="50dc5-124">Zobrazí seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazové řádky.</span><span class="sxs-lookup"><span data-stu-id="50dc5-124">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="50dc5-125">Zvolte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="50dc5-125">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="50dc5-126">Ve Windows 7</span><span class="sxs-lookup"><span data-stu-id="50dc5-126">In Windows 7</span></span>

1. <span data-ttu-id="50dc5-127">Zvolte **Start**, rozbalte **všechny programy**a potom rozbalte **sady Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="50dc5-127">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="50dc5-128">V závislosti na verzi sady Visual Studio jste nainstalovali, zvolte **Visual Studio Tools**, **příkazový řádek sady Visual Studio**, nebo na příkazovém řádku, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="50dc5-128">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="50dc5-129">Pokud máte jiné sady SDK nainstalované, jako [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), mohou vidět další příkazové řádky pro ARM, x 86 nebo x64 architektury.</span><span class="sxs-lookup"><span data-stu-id="50dc5-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="50dc5-130">V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.</span><span class="sxs-lookup"><span data-stu-id="50dc5-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="50dc5-131">Ruční nalezení souborů v počítači</span><span class="sxs-lookup"><span data-stu-id="50dc5-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="50dc5-132">Obvykle, klávesové zkratky pro příkaz vyzve k instalaci jsou umístěny na **nabídky Start** složka pro sadu Visual Studio, jako je například nástroje Studio 2017\Visual C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50dc5-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="50dc5-133">Ale pokud z nějakého důvodu není vyhledávání pro příkazový řádek přinést očekávané výsledky, můžete zkusit ruční nalezení klávesovou zkratku na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="50dc5-133">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="50dc5-134">Zkuste vyhledat název souboru příkazového řádku, jako například *VsDevCmd.bat*, nebo přejděte do složky nástrojů, jako je například C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (cesta změny podle vašeho Vizuálu Umístění sady Studio verze, vydání a instalace).</span><span class="sxs-lookup"><span data-stu-id="50dc5-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="50dc5-135">Spusťte z příkazového řádku v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="50dc5-135">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="50dc5-136">Pro snadnější přístup, můžete přidat příkazový řádek sady Visual Studio pro vývojáře, nebo jiné příkazového řádku **nástroje** nabídky v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50dc5-136">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="50dc5-137">Zpřístupnění nástroje, přidejte ho do seznam externích nástrojů.</span><span class="sxs-lookup"><span data-stu-id="50dc5-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="50dc5-138">Tady jsou kroky:</span><span class="sxs-lookup"><span data-stu-id="50dc5-138">Here are the steps:</span></span>

1. <span data-ttu-id="50dc5-139">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50dc5-139">Open Visual Studio.</span></span>

2. <span data-ttu-id="50dc5-140">Vyberte **nástroje** nabídky a klikněte na tlačítko **externích nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="50dc5-140">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="50dc5-141">Na **externích nástrojů** dialogového okna zvolte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="50dc5-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="50dc5-142">Zobrazí se nová položka.</span><span class="sxs-lookup"><span data-stu-id="50dc5-142">A new entry appears.</span></span>

4. <span data-ttu-id="50dc5-143">Zadejte **Title** pro novou položku nabídky, jako `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="50dc5-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="50dc5-144">V **příkaz** zadejte soubor, který chcete spustit, jako například `%comspec%` nebo `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="50dc5-144">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="50dc5-145">V **argumenty** pole, zadejte, kam chcete najít konkrétní příkazového řádku, který chcete použít jako `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Tento příkaz spustí příkazový řádek vývojáře, který je nainstalován se sadou Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="50dc5-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="50dc5-146">Změňte tuto hodnotu podle umístěním verze, vydání a instalace sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50dc5-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="50dc5-147">Zvolte hodnotu **výchozí adresář** pole, jako například **adresáře projektu**.</span><span class="sxs-lookup"><span data-stu-id="50dc5-147">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="50dc5-148">Zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="50dc5-148">Choose the **OK** button.</span></span>

   <span data-ttu-id="50dc5-149">Přidat novou položku nabídky, a dostanete příkazový řádek z **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="50dc5-149">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Položka nabídky příkazového řádku v sadě Visual Studio](media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="50dc5-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50dc5-151">See also</span></span>

- [<span data-ttu-id="50dc5-152">Nástroje</span><span class="sxs-lookup"><span data-stu-id="50dc5-152">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="50dc5-153">Správa externích nástrojů</span><span class="sxs-lookup"><span data-stu-id="50dc5-153">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
