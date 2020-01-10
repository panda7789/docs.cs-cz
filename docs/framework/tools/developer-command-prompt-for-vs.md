---
title: Developer Command Prompt pro Visual Studio
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715853"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="0c056-102">Developer Command Prompt pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0c056-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="0c056-103">Developer Command Prompt pro Visual Studio vám umožní snadněji používat nástroje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c056-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="0c056-104">Jedná se o příkazový řádek, který automaticky nastaví konkrétní proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="0c056-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="0c056-105">Po otevření Developer Command Prompt můžete zadat příkazy pro [.NET Framework nástroje](index.md) , jako je například `ildasm` nebo `clrver`.</span><span class="sxs-lookup"><span data-stu-id="0c056-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0c056-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c056-106">Prerequisites</span></span>

- [<span data-ttu-id="0c056-107">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="0c056-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="0c056-108">Hledání příkazového řádku na svém počítači</span><span class="sxs-lookup"><span data-stu-id="0c056-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="0c056-109">V závislosti na verzi sady Visual Studio a všech dalších sadách SDK a úlohách, které jste nainstalovali, může být více příkazů.</span><span class="sxs-lookup"><span data-stu-id="0c056-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="0c056-110">Pokud následující kroky nefungují, můžete zkusit [soubory vyhledat ručně na svém počítači](#manually-locate-the-files-on-your-machine) nebo [Spustit příkazový řádek v rámci sady Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="0c056-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="0c056-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="0c056-111">Windows 10</span></span>

1. <span data-ttu-id="0c056-112">Na klávesnici vyberte **spustit** ![klávesu s logem Windows.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="0c056-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="0c056-113">a přejděte k písmenu **v**.</span><span class="sxs-lookup"><span data-stu-id="0c056-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="0c056-114">Rozbalte složku **Visual Studio 2019** .</span><span class="sxs-lookup"><span data-stu-id="0c056-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="0c056-115">Vyberte **Developer Command Prompt pro VS 2019** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="0c056-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="0c056-116">Alternativně můžete spustit zadání názvu příkazového řádku do vyhledávacího pole na hlavním panelu a vybrat výsledek, který chcete zobrazit v seznamu výsledků hledání.</span><span class="sxs-lookup"><span data-stu-id="0c056-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Animovaný obrázek GIF znázorňující chování hledání ve Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="0c056-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="0c056-118">Windows 8.1</span></span>

1. <span data-ttu-id="0c056-119">Na **úvodní** obrazovce stiskněte klávesu s logem Windows ![klávesu s logem Windows na klávesnici.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="0c056-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="0c056-120">například na klávesnici.</span><span class="sxs-lookup"><span data-stu-id="0c056-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="0c056-121">Na **úvodní** obrazovce stisknutím klávesy **CTRL**+**kartu** otevřete seznam **aplikace** a potom stiskněte klávesu **V**. Tím zobrazíte seznam, který obsahuje všechny nainstalované příkazy sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0c056-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="0c056-122">Vyberte **Developer Command Prompt pro VS 2019** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="0c056-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="0c056-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="0c056-123">Windows 7</span></span>

1. <span data-ttu-id="0c056-124">Zvolte **Start** a potom rozbalte **všechny programy**.</span><span class="sxs-lookup"><span data-stu-id="0c056-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="0c056-125">Vyberte možnost **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt pro vs 2019**nebo příkazový řádek, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="0c056-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Nabídka Start ve Windows 7 se zvýrazněným příkazovým řádkem](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="0c056-127">Pokud máte nainstalované jiné sady SDK, jako je například [Sada Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), může se zobrazit další příkazová výzva.</span><span class="sxs-lookup"><span data-stu-id="0c056-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="0c056-128">V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.</span><span class="sxs-lookup"><span data-stu-id="0c056-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="0c056-129">Ručně vyhledat soubory na počítači</span><span class="sxs-lookup"><span data-stu-id="0c056-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="0c056-130">Zkratky pro příkazy, které jste nainstalovali, jsou obvykle umístěny ve složce **nabídky Start** pro aplikaci Visual Studio, například v *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*.</span><span class="sxs-lookup"><span data-stu-id="0c056-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="0c056-131">Ale pokud z nějakého důvodu hledání příkazového řádku nepřinese očekávané výsledky, můžete zkusit na svém počítači ručně najít zástupce.</span><span class="sxs-lookup"><span data-stu-id="0c056-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="0c056-132">Zkuste vyhledat název souboru příkazového řádku, například *VsDevCmd. bat*, nebo přejít do složky Tools, například *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (cesta se mění podle vaší verze sady Visual Studio, edice a umístění instalace).</span><span class="sxs-lookup"><span data-stu-id="0c056-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="0c056-133">Spuštění příkazového řádku v rámci sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0c056-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="0c056-134">Pro snazší přístup můžete přidat Developer Command Prompt nebo jakýkoli jiný příkazový řádek do nabídky nástroje v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0c056-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="0c056-135">Aby byl nástroj dostupný, přidejte ho do seznamu externích nástrojů.</span><span class="sxs-lookup"><span data-stu-id="0c056-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="0c056-136">Postup je následující:</span><span class="sxs-lookup"><span data-stu-id="0c056-136">Here are the steps:</span></span>

1. <span data-ttu-id="0c056-137">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0c056-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="0c056-138">V okně Start vyberte možnost **pokračovat bez kódu**.</span><span class="sxs-lookup"><span data-stu-id="0c056-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="0c056-139">Na panelu nabídek vyberte **nástroje** > **externích nástrojích**.</span><span class="sxs-lookup"><span data-stu-id="0c056-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="0c056-140">V dialogovém okně **externí nástroje** klikněte na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="0c056-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="0c056-141">Zobrazí se nová položka.</span><span class="sxs-lookup"><span data-stu-id="0c056-141">A new entry appears.</span></span>

1. <span data-ttu-id="0c056-142">Zadejte **název** nové položky nabídky, například `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="0c056-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="0c056-143">Do pole **příkaz** zadejte soubor, který chcete spustit, například `%comspec%` nebo `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="0c056-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="0c056-144">V poli **argumenty** určete, kde se má najít konkrétní příkazový řádek, který chcete použít, například `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span><span class="sxs-lookup"><span data-stu-id="0c056-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="0c056-145">Tento příkaz spustí Developer Command Prompt, která je nainstalovaná se sadou Visual Studio 2019 Community.</span><span class="sxs-lookup"><span data-stu-id="0c056-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="0c056-146">Změňte tuto hodnotu podle vaší verze, edice a umístění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0c056-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="0c056-147">V poli **počáteční adresář** zadejte adresář, ve kterém se spustí příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="0c056-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="0c056-148">Zvolte hodnotu jako **adresář projektu** výběrem šipky vedle pole.</span><span class="sxs-lookup"><span data-stu-id="0c056-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="0c056-149">Zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0c056-149">Choose the **OK** button.</span></span>

   ![Dialog externích nástrojů s vyplněnými hodnotami pole](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="0c056-151">Nová položka nabídky se přidá a k příkazovému řádku můžete získat přístup z nabídky nástroje.</span><span class="sxs-lookup"><span data-stu-id="0c056-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Položka nabídky příkazového řádku v aplikaci Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="0c056-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c056-153">See also</span></span>

- [<span data-ttu-id="0c056-154">Nástroje .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0c056-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="0c056-155">Správa externích nástrojů</span><span class="sxs-lookup"><span data-stu-id="0c056-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="0c056-156">Použití sady nástrojů C++ Microsoft z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0c056-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
