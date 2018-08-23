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
ms.openlocfilehash: 4c95074190419dd3e984c7659ede917b83b97f08
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752326"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="686cc-102">Developer Command Prompt pro sadu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="686cc-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="686cc-103">Developer Command Prompt pro sadu Visual Studio automaticky nastaví proměnné prostředí, které vám umožní snadno používat nástroje rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="686cc-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span>

> [!div class="button"]
[<span data-ttu-id="686cc-104">Stáhněte si Visual Studio</span><span class="sxs-lookup"><span data-stu-id="686cc-104">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="686cc-105">Vyhledání příkazového řádku na vašem počítači</span><span class="sxs-lookup"><span data-stu-id="686cc-105">Searching for the command prompt on your machine</span></span>

<span data-ttu-id="686cc-106">Můžete mít více příkazových řádků, v závislosti na verzi sady Visual Studio a všech dodatečných sad SDK si nainstalujete.</span><span class="sxs-lookup"><span data-stu-id="686cc-106">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="686cc-107">Například 64bitové verze sady Visual Studio poskytují 32bitové a 64bitové verze příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="686cc-107">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="686cc-108">(32bitové a 64bitové verze Většina nástrojů jsou stejné, ale u několika nástrojů měnit konkrétní 32bitové a 64bitové prostředí) Pokud tyto kroky nefungují, můžete zkusit [ručně vyhledávání souborů na svém počítači](#manually-locating-the-files-on-your-machine) nebo [spuštění z příkazového řádku v sadě Visual Studio](#running-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="686cc-108">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locating the files on your machine](#manually-locating-the-files-on-your-machine) or [Running the command prompt from inside Visual Studio](#running-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="686cc-109">V systému Windows 10</span><span class="sxs-lookup"><span data-stu-id="686cc-109">In Windows 10</span></span>

1. <span data-ttu-id="686cc-110">Do vyhledávacího pole na hlavním panelu, začněte psát název nástroje, jako například `dev` nebo `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="686cc-110">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="686cc-111">Tím se zobrazí seznam nainstalovaných aplikací, které odpovídají vaší vyhledávací vzory.</span><span class="sxs-lookup"><span data-stu-id="686cc-111">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="686cc-112">Pokud hledáte různých příkazového řádku, zkuste zadat jinou hledaný termín, jako `prompt`.</span><span class="sxs-lookup"><span data-stu-id="686cc-112">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="686cc-113">Zvolte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="686cc-113">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="686cc-114">Ve Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="686cc-114">In Windows 8.1</span></span>

1. <span data-ttu-id="686cc-115">Přejděte na **Start** obrazovku stisknutím klávesy s logem Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici pro příklad.</span><span class="sxs-lookup"><span data-stu-id="686cc-115">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="686cc-116">Na **Start** obrazovky, stiskněte klávesu `CTRL + TAB` otevřít **aplikace** seznamu a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="686cc-116">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="686cc-117">Zobrazí seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazové řádky.</span><span class="sxs-lookup"><span data-stu-id="686cc-117">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="686cc-118">Zvolte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="686cc-118">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="686cc-119">V systému Windows 8</span><span class="sxs-lookup"><span data-stu-id="686cc-119">In Windows 8</span></span>

1. <span data-ttu-id="686cc-120">Přejděte na **Start** obrazovku stisknutím klávesy s logem Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici pro příklad.</span><span class="sxs-lookup"><span data-stu-id="686cc-120">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="686cc-121">Na **Start** obrazovky, stiskněte klávesu s logem Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="686cc-121">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="686cc-122">Zvolte **aplikace zobrazit** ikony v dolní části obrazovky a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="686cc-122">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="686cc-123">Zobrazí seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazové řádky.</span><span class="sxs-lookup"><span data-stu-id="686cc-123">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="686cc-124">Zvolte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="686cc-124">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="686cc-125">Ve Windows 7</span><span class="sxs-lookup"><span data-stu-id="686cc-125">In Windows 7</span></span>

1. <span data-ttu-id="686cc-126">Zvolte **Start**, rozbalte **všechny programy**a potom rozbalte **sady Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="686cc-126">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="686cc-127">V závislosti na verzi sady Visual Studio jste nainstalovali, zvolte **Visual Studio Tools**, **příkazový řádek sady Visual Studio**, nebo na příkazovém řádku, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="686cc-127">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="686cc-128">Pokud máte jiné sady SDK nainstalované, jako [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), mohou vidět další příkazové řádky pro ARM, x 86 nebo x64 architektury.</span><span class="sxs-lookup"><span data-stu-id="686cc-128">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="686cc-129">V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.</span><span class="sxs-lookup"><span data-stu-id="686cc-129">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="686cc-130">Ruční nalezení souborů v počítači</span><span class="sxs-lookup"><span data-stu-id="686cc-130">Manually locate the files on your machine</span></span>

<span data-ttu-id="686cc-131">Obvykle, klávesové zkratky pro příkaz vyzve k instalaci jsou umístěny na **nabídky Start** složka pro sadu Visual Studio, jako je například nástroje Studio 2017\Visual C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="686cc-131">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="686cc-132">Ale pokud z nějakého důvodu není vyhledávání pro příkazový řádek přinést očekávané výsledky, můžete zkusit ruční nalezení klávesovou zkratku na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="686cc-132">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="686cc-133">Zkuste vyhledat název souboru příkazového řádku, jako například *VsDevCmd.bat*, nebo přejděte do složky nástrojů, jako je například C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (cesta změny podle vašeho Vizuálu Umístění sady Studio verze, vydání a instalace).</span><span class="sxs-lookup"><span data-stu-id="686cc-133">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="686cc-134">Příkaz spustit příkazový řádek v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="686cc-134">Run command prompt from inside Visual Studio</span></span>

<span data-ttu-id="686cc-135">Pro snadnější přístup, můžete přidat příkazový řádek sady Visual Studio pro vývojáře, nebo jiné příkazového řádku **nástroje** nabídky v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="686cc-135">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="686cc-136">Zpřístupnění nástroje, přidejte ho do seznam externích nástrojů.</span><span class="sxs-lookup"><span data-stu-id="686cc-136">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="686cc-137">Tady jsou kroky:</span><span class="sxs-lookup"><span data-stu-id="686cc-137">Here are the steps:</span></span>

1. <span data-ttu-id="686cc-138">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="686cc-138">Open Visual Studio.</span></span>

2. <span data-ttu-id="686cc-139">Vyberte **nástroje** nabídky a klikněte na tlačítko **externích nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="686cc-139">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="686cc-140">Na **externích nástrojů** dialogového okna zvolte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="686cc-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="686cc-141">Zobrazí se nová položka.</span><span class="sxs-lookup"><span data-stu-id="686cc-141">A new entry appears.</span></span>

4. <span data-ttu-id="686cc-142">Zadejte **Title** pro novou položku nabídky, jako `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="686cc-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="686cc-143">V **příkaz** zadejte soubor, který chcete spustit, jako například `%comspec%` nebo `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="686cc-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="686cc-144">V **argumenty** pole, zadejte, kam chcete najít konkrétní příkazového řádku, který chcete použít jako `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Tento příkaz spustí příkazový řádek vývojáře, který je nainstalován se sadou Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="686cc-144">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="686cc-145">Změňte tuto hodnotu podle umístěním verze, vydání a instalace sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="686cc-145">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="686cc-146">Zvolte hodnotu **výchozí adresář** pole, jako například **adresáře projektu**.</span><span class="sxs-lookup"><span data-stu-id="686cc-146">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="686cc-147">Zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="686cc-147">Choose the **OK** button.</span></span>

   <span data-ttu-id="686cc-148">Přidat novou položku nabídky, a dostanete příkazový řádek z **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="686cc-148">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="686cc-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="686cc-149">See also</span></span>

- [<span data-ttu-id="686cc-150">Nástroje</span><span class="sxs-lookup"><span data-stu-id="686cc-150">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="686cc-151">Správa externích nástrojů</span><span class="sxs-lookup"><span data-stu-id="686cc-151">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
