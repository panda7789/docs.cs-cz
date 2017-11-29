---
title: "Příkazový řádek vývojáře pro sadu Visual Studio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e93a1d116ac0480c80e259ddbadbc65fd9539389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="91e44-102">Příkazový řádek vývojáře pro sadu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="91e44-102">Developer Command Prompt for Visual Studio</span></span>
<span data-ttu-id="91e44-103">Příkazový řádek vývojáře pro sadu Visual Studio automaticky nastaví proměnné prostředí, které vám umožní snadno používat nástroje rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91e44-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="91e44-104">Do příkazového řádku vývojáře se instaluje s plná nebo komunity edice sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91e44-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="91e44-105">Není nainstalovaná verze Express sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91e44-105">It is not installed with the Express versions of Visual Studio.</span></span>  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="91e44-106">Hledání příkazového řádku na počítači</span><span class="sxs-lookup"><span data-stu-id="91e44-106">Searching for the Command Prompt on your machine</span></span>  
 <span data-ttu-id="91e44-107">Může se zobrazit více příkazového řádku, v závislosti na verzi sady Visual Studio a všechny další sady SDK jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="91e44-107">You may see multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="91e44-108">Například 64bitové verze sady Visual Studio poskytují 32bitové a 64bitové verze příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="91e44-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="91e44-109">(32bitové a 64bitové verze jsou u většiny nástrojů stejné, u několika nástrojů se však 32bitové a 64bitové prostředí liší.) Pokud nejsou k dispozici níže uvedené kroky, můžete zkusit [ručně vyhledávání souborů v počítači](#alternative) nebo [spuštěním příkazu příkazový řádek v sadě Visual Studio](#visualstudio).</span><span class="sxs-lookup"><span data-stu-id="91e44-109">(The 32-bit and 64-bit versions of most tools are identical; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the steps below don't work, you can try [Manually locating the files on your machine](#alternative) or [Running command prompt from inside Visual Studio](#visualstudio).</span></span>  
  
 <span data-ttu-id="91e44-110">**Ve Windows 10**</span><span class="sxs-lookup"><span data-stu-id="91e44-110">**In Windows 10**</span></span>  
  
1.  <span data-ttu-id="91e44-111">Otevřete **spustit** nabídky, stisknutím klávesy s logem Windows ![s logem Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.</span><span class="sxs-lookup"><span data-stu-id="91e44-111">Open the **Start** menu, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="91e44-112">Na **spustit** nabídky, zadejte `dev`.</span><span class="sxs-lookup"><span data-stu-id="91e44-112">On the **Start** menu, enter `dev`.</span></span> <span data-ttu-id="91e44-113">Otevře se seznam nainstalovaných aplikací, které odpovídají parametry vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="91e44-113">This will bring a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="91e44-114">Pokud hledáte jiný příkazový řádek, zkuste zadat jiný hledaný termín, jako `prompt`.</span><span class="sxs-lookup"><span data-stu-id="91e44-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>  
  
3.  <span data-ttu-id="91e44-115">Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).</span><span class="sxs-lookup"><span data-stu-id="91e44-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="91e44-116">**Ve Windows 8.1**</span><span class="sxs-lookup"><span data-stu-id="91e44-116">**In Windows 8.1**</span></span>  
  
1.  <span data-ttu-id="91e44-117">Přejděte na **spustit** obrazovky, stisknutím klávesy s logem Windows ![s logem Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.</span><span class="sxs-lookup"><span data-stu-id="91e44-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="91e44-118">Na **spustit** obrazovky, stiskněte `CTRL + TAB` otevřete **aplikace** seznamu a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="91e44-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="91e44-119">Otevře se seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="91e44-119">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
3.  <span data-ttu-id="91e44-120">Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).</span><span class="sxs-lookup"><span data-stu-id="91e44-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="91e44-121">**Ve Windows 8**</span><span class="sxs-lookup"><span data-stu-id="91e44-121">**In Windows 8**</span></span>  
  
1.  <span data-ttu-id="91e44-122">Přejděte na **spustit** obrazovky, stisknutím klávesy s logem Windows ![s logem Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.</span><span class="sxs-lookup"><span data-stu-id="91e44-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="91e44-123">Na **spustit** obrazovky, stiskněte klávesu s logem Windows ![s logem Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="91e44-123">On the **Start** screen, press the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>  
  
3.  <span data-ttu-id="91e44-124">Vyberte **zobrazení aplikace** ikona v dolní části obrazovky a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="91e44-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="91e44-125">Otevře se seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="91e44-125">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
4.  <span data-ttu-id="91e44-126">Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).</span><span class="sxs-lookup"><span data-stu-id="91e44-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="91e44-127">**Ve Windows 7**</span><span class="sxs-lookup"><span data-stu-id="91e44-127">**In Windows 7**</span></span>  
  
1.  <span data-ttu-id="91e44-128">Zvolte **spustit**, rozbalte položku **všechny programy**a potom rozbalte **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="91e44-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="91e44-129">V závislosti na verzi sady Visual Studio, které jste nainstalovali, zvolte **nástroje sady Visual Studio**, **Visual Studio – příkazový řádek**, nebo na příkazovém řádku, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="91e44-129">Depending on the version of Visual Studio you have installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>  
  
 <span data-ttu-id="91e44-130">Pokud máte [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) nebo [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) nainstalován, mohou se zobrazit další příkaz vyzve k zadání ARM, x 86 nebo x64 architektury.</span><span class="sxs-lookup"><span data-stu-id="91e44-130">If you have the [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) or [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="91e44-131">V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.</span><span class="sxs-lookup"><span data-stu-id="91e44-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="91e44-132">Ručně vyhledávání souborů v počítači</span><span class="sxs-lookup"><span data-stu-id="91e44-132">Manually locating the files on your machine</span></span>  
  <span data-ttu-id="91e44-133">Obvykle bude provedeno zástupce pro vás příkaz požádá jste nainstalovali na **nabídce Start** složku pro sadu Visual Studio, například C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Nástroje.</span><span class="sxs-lookup"><span data-stu-id="91e44-133">Usually, the shortcuts for the command prompts you have installed will be placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools.</span></span>    <span data-ttu-id="91e44-134">Ale pokud z nějakého důvodu není vyhledávání pro příkazový řádek yield očekávané výsledky, můžete zkusit ruční nalezení zástupce na počítači-li ji používat.</span><span class="sxs-lookup"><span data-stu-id="91e44-134">But if for some reason, searching for the command prompt doesn't yield the expected results, you can try to manually locate the shortcut on your machine in order to use it.</span></span>   <span data-ttu-id="91e44-135">Zkuste vyhledat název souboru příkazového řádku, jako je například VsDevCmd.bat nebo přejděte do složky nástroje, jako je například C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\Tools (cesta se změní podle umístění instalace a verzi vaší aplikace Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="91e44-135">Try searching for the name of the command prompt file such as VsDevCmd.bat or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools (path will change according to your Visual Studio version and installation location).</span></span>  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="91e44-136">Spuštění příkazu příkazový řádek v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="91e44-136">Running command prompt from inside Visual Studio</span></span>  
 <span data-ttu-id="91e44-137">Pro snadnější přístup můžete přidat příkazového řádku vývojáře Visual Studio nebo jiné příkazového řádku nabídky Nástroje v sadě Visual Studio, přidáním do seznamu externí nástroje.</span><span class="sxs-lookup"><span data-stu-id="91e44-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="91e44-138">Toto je, jak můžete provést, který:</span><span class="sxs-lookup"><span data-stu-id="91e44-138">This is how you can accomplish that:</span></span>  
  
1.  <span data-ttu-id="91e44-139">Otevřete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91e44-139">Open Visual Studio.</span></span>  
  
2.  <span data-ttu-id="91e44-140">Vyberte **nástroje** nabídky a zvolte **externích nástrojů...** .</span><span class="sxs-lookup"><span data-stu-id="91e44-140">Select the **Tools** menu and choose **External Tools...**.</span></span>  
  
3.  <span data-ttu-id="91e44-141">Na **externích nástrojů** dialogovém okně vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="91e44-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="91e44-142">Nová položka</span><span class="sxs-lookup"><span data-stu-id="91e44-142">A new entry appears</span></span>  
  
4.  <span data-ttu-id="91e44-143">Zadejte **název** pro novou položku nabídky jako `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="91e44-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>  
  
5.  <span data-ttu-id="91e44-144">V **příkaz** pole, zadejte soubor, který chcete spustit jako `%comspec%` nebo `C:\Windows\System32\cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="91e44-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe` .</span></span>  
  
6.  <span data-ttu-id="91e44-145">V **argumenty** pole, zadejte, kam chcete najít konkrétní příkazového řádku, kterou chcete použít jako `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (tím se spustí příkazový řádek vývojáře nainstalované s [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="91e44-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (this will launch the Developer Command Prompt installed with [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span></span> <span data-ttu-id="91e44-146">Tato hodnota je potřeba změnit podle vašeho umístění instalace a verzi sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91e44-146">This value needs to be changed according to your Visual Studio version and installation location.</span></span>  
  
7.  <span data-ttu-id="91e44-147">Vyberte hodnotu pro **directory počáteční** pole, jako **adresáři projektu** .</span><span class="sxs-lookup"><span data-stu-id="91e44-147">Choose a value for the **Initial directory** field such as **Project Directory** .</span></span>  
  
8.  <span data-ttu-id="91e44-148">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="91e44-148">Choose the **OK** button.</span></span>  
  
 <span data-ttu-id="91e44-149">Poté při přidání nové položky nabídky a dostanete příkazového řádku **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="91e44-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e44-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="91e44-150">See Also</span></span>  
 [<span data-ttu-id="91e44-151">Nástroje</span><span class="sxs-lookup"><span data-stu-id="91e44-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="91e44-152">Správa externích nástrojů</span><span class="sxs-lookup"><span data-stu-id="91e44-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
