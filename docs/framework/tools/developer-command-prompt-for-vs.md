---
title: Příkazový řádek vývojáře pro sadu Visual Studio
ms.date: 06/18/2018
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
ms.openlocfilehash: 8e64facffd4face929b28d660ffd5210f127c3bd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315222"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="05c8c-102">Příkazový řádek vývojáře pro sadu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="05c8c-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="05c8c-103">Příkazový řádek vývojáře pro sadu Visual Studio automaticky nastaví proměnné prostředí, které vám umožní snadno používat nástroje rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="05c8c-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="05c8c-104">Do příkazového řádku vývojáře se instaluje s plná nebo komunity edice sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05c8c-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="05c8c-105">Není nainstalovaná verze Express sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05c8c-105">It isn't installed with the Express versions of Visual Studio.</span></span>

> [!div class="button"]
[<span data-ttu-id="05c8c-106">Stáhněte si Visual Studio</span><span class="sxs-lookup"><span data-stu-id="05c8c-106">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="05c8c-107">Hledání příkazového řádku na počítači</span><span class="sxs-lookup"><span data-stu-id="05c8c-107">Searching for the Command Prompt on your machine</span></span>

<span data-ttu-id="05c8c-108">Může se zobrazit mnoho okna příkazového řádku, v závislosti na verzi sady Visual Studio a všechny další sady SDK jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="05c8c-108">You may see many command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="05c8c-109">Například 64bitové verze sady Visual Studio poskytují 32bitové a 64bitové verze příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="05c8c-109">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="05c8c-110">(32bitové a 64bitové verze Většina nástrojů jsou stejné, ale několik nástrojů změnit konkrétní prostředí 32bitové a 64bitové verze.) Pokud tyto kroky nefungují, můžete zkusit [ručně vyhledávání souborů v počítači](#manually-locating-the-files-on-your-machine) nebo [spuštěním příkazu příkazový řádek v sadě Visual Studio](#running-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="05c8c-110">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locating the files on your machine](#manually-locating-the-files-on-your-machine) or [Running command prompt from inside Visual Studio](#running-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="05c8c-111">Ve Windows 10</span><span class="sxs-lookup"><span data-stu-id="05c8c-111">In Windows 10</span></span>

1. <span data-ttu-id="05c8c-112">Do vyhledávacího pole na hlavním panelu, začněte psát název nástroje, jako například `dev` nebo `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="05c8c-112">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="05c8c-113">Tím zobrazíte seznam nainstalovaných aplikací, které odpovídají parametry vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="05c8c-113">This brings a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="05c8c-114">Pokud hledáte jiný příkazový řádek, zkuste zadat jiný hledaný termín, jako `prompt`.</span><span class="sxs-lookup"><span data-stu-id="05c8c-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="05c8c-115">Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).</span><span class="sxs-lookup"><span data-stu-id="05c8c-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="05c8c-116">Ve Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="05c8c-116">In Windows 8.1</span></span>

1. <span data-ttu-id="05c8c-117">Přejděte na **spustit** obrazovky, stisknutím klávesy s logem Windows ![s logem Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.</span><span class="sxs-lookup"><span data-stu-id="05c8c-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="05c8c-118">Na **spustit** obrazovky, stiskněte `CTRL + TAB` otevřete **aplikace** seznamu a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="05c8c-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="05c8c-119">Tím zobrazíte seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="05c8c-119">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="05c8c-120">Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).</span><span class="sxs-lookup"><span data-stu-id="05c8c-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="05c8c-121">Ve Windows 8</span><span class="sxs-lookup"><span data-stu-id="05c8c-121">In Windows 8</span></span>

1. <span data-ttu-id="05c8c-122">Přejděte na **spustit** obrazovky, stisknutím klávesy s logem Windows ![s logem Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.</span><span class="sxs-lookup"><span data-stu-id="05c8c-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="05c8c-123">Na **spustit** obrazovky, stiskněte klávesu s logem Windows ![s logem Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="05c8c-123">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="05c8c-124">Vyberte **zobrazení aplikace** ikona v dolní části obrazovky a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="05c8c-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="05c8c-125">Tím zobrazíte seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="05c8c-125">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="05c8c-126">Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).</span><span class="sxs-lookup"><span data-stu-id="05c8c-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="05c8c-127">Ve Windows 7</span><span class="sxs-lookup"><span data-stu-id="05c8c-127">In Windows 7</span></span>

1. <span data-ttu-id="05c8c-128">Zvolte **spustit**, rozbalte položku **všechny programy**a potom rozbalte **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="05c8c-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="05c8c-129">V závislosti na verzi sady Visual Studio, které jste nainstalovali, zvolte **nástroje sady Visual Studio**, **Visual Studio – příkazový řádek**, nebo na příkazovém řádku, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="05c8c-129">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="05c8c-130">Pokud máte dalších sadách SDK nainstalovat, jako [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive) nainstalován, mohou se zobrazit další příkaz vyzve k zadání ARM, x 86 nebo x64 architektury.</span><span class="sxs-lookup"><span data-stu-id="05c8c-130">If you have other SDKs installed such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="05c8c-131">V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.</span><span class="sxs-lookup"><span data-stu-id="05c8c-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="05c8c-132">Ručně vyhledávání souborů v počítači</span><span class="sxs-lookup"><span data-stu-id="05c8c-132">Manually locating the files on your machine</span></span>

<span data-ttu-id="05c8c-133">Obvykle jsou umístěny zástupce pro vás příkaz požádá jste nainstalovali na **nabídce Start** složku pro sadu Visual Studio, například v nástroji Studio 2017\Visual C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05c8c-133">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="05c8c-134">Ale pokud z nějakého důvodu není vyhledávání pro příkazový řádek přineste očekávané výsledky, můžete zkusit ruční nalezení zástupce na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="05c8c-134">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="05c8c-135">Zkuste vyhledat název souboru příkazového řádku, jako například *VsDevCmd.bat*, nebo přejděte do složky nástroje, například C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (cesta změny podle vaší Visual Studio verze, vydání a instalace umístění).</span><span class="sxs-lookup"><span data-stu-id="05c8c-135">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="05c8c-136">Spuštění příkazu příkazový řádek v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="05c8c-136">Running command prompt from inside Visual Studio</span></span>

<span data-ttu-id="05c8c-137">Pro snadnější přístup můžete přidat příkazového řádku vývojáře Visual Studio nebo jiné příkazového řádku nabídky Nástroje v sadě Visual Studio, přidáním do seznamu externí nástroje.</span><span class="sxs-lookup"><span data-stu-id="05c8c-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="05c8c-138">Toto je, jak můžete provést, který:</span><span class="sxs-lookup"><span data-stu-id="05c8c-138">This is how you can accomplish that:</span></span>

1. <span data-ttu-id="05c8c-139">Otevřete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05c8c-139">Open Visual Studio.</span></span>

2. <span data-ttu-id="05c8c-140">Vyberte **nástroje** nabídky a zvolte **externích nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="05c8c-140">Select the **Tools** menu and choose **External Tools**.</span></span>

3. <span data-ttu-id="05c8c-141">Na **externích nástrojů** dialogovém okně vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="05c8c-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="05c8c-142">Nová položka.</span><span class="sxs-lookup"><span data-stu-id="05c8c-142">A new entry appears.</span></span>

4. <span data-ttu-id="05c8c-143">Zadejte **název** pro novou položku nabídky jako `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="05c8c-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="05c8c-144">V **příkaz** pole, zadejte soubor, který chcete spustit jako `%comspec%` nebo `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="05c8c-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="05c8c-145">V **argumenty** pole, zadejte, kam chcete najít konkrétní příkazového řádku, kterou chcete použít jako `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Tento příkaz spustí příkazový řádek vývojáře, který je nainstalován pomocí Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="05c8c-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="05c8c-146">Změňte tuto hodnotu podle vašeho umístění verze, vydání a instalace sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05c8c-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="05c8c-147">Vyberte hodnotu pro **directory počáteční** pole, jako **adresáři projektu**.</span><span class="sxs-lookup"><span data-stu-id="05c8c-147">Choose a value for the **Initial directory** field such as **Project Directory**.</span></span>

8. <span data-ttu-id="05c8c-148">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="05c8c-148">Choose the **OK** button.</span></span>

<span data-ttu-id="05c8c-149">Poté při přidání nové položky nabídky a dostanete příkazového řádku **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="05c8c-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="05c8c-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05c8c-150">See also</span></span>

 [<span data-ttu-id="05c8c-151">Nástroje</span><span class="sxs-lookup"><span data-stu-id="05c8c-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="05c8c-152">Správa externích nástrojů</span><span class="sxs-lookup"><span data-stu-id="05c8c-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)  
