---
title: Příkazový řádek pro vývojáře pro Visual Studio
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715853"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="41858-102">Příkazový řádek pro vývojáře pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="41858-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="41858-103">Příkazový řádek pro vývojáře pro visual studio umožňuje snadněji používat nástroje rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41858-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="41858-104">Jedná se o příkazový řádek, který automaticky nastaví specifické proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="41858-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="41858-105">Po otevření příkazového řádku pro vývojáře můžete zadat příkazy `clrver`pro nástroje rozhraní [.NET Framework,](index.md) například `ildasm` nebo .</span><span class="sxs-lookup"><span data-stu-id="41858-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="41858-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41858-106">Prerequisites</span></span>

- [<span data-ttu-id="41858-107">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="41858-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="41858-108">Hledání příkazového řádku v počítači</span><span class="sxs-lookup"><span data-stu-id="41858-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="41858-109">V závislosti na verzi sady Visual Studio a dalších nainstalovaných sadách SDK a úlohách můžete mít k dispozici více příkazů.</span><span class="sxs-lookup"><span data-stu-id="41858-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="41858-110">Pokud následující kroky nefungují, můžete zkusit [ručně vyhledat soubory v počítači](#manually-locate-the-files-on-your-machine) nebo spustit [příkazový řádek z aplikace Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="41858-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="41858-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="41858-111">Windows 10</span></span>

1. <span data-ttu-id="41858-112">Na klávesnici vyberte **Spustit** ![klávesu s logem Windows.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="41858-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="41858-113">a přejděte na písmeno **V**.</span><span class="sxs-lookup"><span data-stu-id="41858-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="41858-114">Rozbalte složku **Visual Studio 2019.**</span><span class="sxs-lookup"><span data-stu-id="41858-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="41858-115">Zvolte **Příkazový řádek pro vývojáře pro VS 2019** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="41858-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="41858-116">Případně můžete začít psát název příkazového řádku do vyhledávacího pole na hlavním panelu a vybrat požadovaný výsledek, protože seznam výsledků začne zobrazovat shody hledání.</span><span class="sxs-lookup"><span data-stu-id="41858-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Animovaný gif zobrazující chování vyhledávání ve Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="41858-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="41858-118">Windows 8.1</span></span>

1. <span data-ttu-id="41858-119">Přejděte na **úvodní** obrazovku stisknutím klávesy ![s logem Windows windows na klávesnici.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="41858-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="41858-120">na klávesnici.</span><span class="sxs-lookup"><span data-stu-id="41858-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="41858-121">Na **úvodní** obrazovce otevřete stisknutím **klávesy Ctrl**+**kartu** **a** stiskněte **klávesu V**. Tím se zobrazí seznam, který obsahuje všechny nainstalované příkazové příkazy sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41858-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="41858-122">Zvolte **Příkazový řádek pro vývojáře pro VS 2019** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="41858-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="41858-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="41858-123">Windows 7</span></span>

1. <span data-ttu-id="41858-124">Zvolte **Spustit** a potom rozbalte **položku Všechny programy**.</span><span class="sxs-lookup"><span data-stu-id="41858-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="41858-125">Zvolte **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt pro VS 2019**nebo příkazový řádek, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="41858-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Nabídka Start systému Windows 7 se zvýrazněným příkazovým řádekm](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="41858-127">Pokud máte nainstalované jiné sady SDK, například [sady Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), mohou se zobrazit další příkazové příkazové příkazy.</span><span class="sxs-lookup"><span data-stu-id="41858-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="41858-128">V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.</span><span class="sxs-lookup"><span data-stu-id="41858-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="41858-129">Ruční vyhledání souborů v počítači</span><span class="sxs-lookup"><span data-stu-id="41858-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="41858-130">Zástupci nainstalovaných příkazových příkazů jsou obvykle umístěny ve složce **Nabídka Start** pro sadu Visual Studio, například v *%ProgramData%\Microsoft\Windows\Nabídka Start\Programy\Visual Studio 2019\Visual Studio Tools*.</span><span class="sxs-lookup"><span data-stu-id="41858-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="41858-131">Pokud však hledání příkazového řádku z nějakého důvodu nevede k očekávaným výsledkům, můžete se pokusit zástupce v počítači vyhledat ručně.</span><span class="sxs-lookup"><span data-stu-id="41858-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="41858-132">Zkuste vyhledat název souboru příkazového řádku, například *VsDevCmd.bat*, nebo přejděte do složky Nástroje, například *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (změna cesty podle verze, edice a umístění instalace sady Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="41858-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="41858-133">Spuštění příkazového řádku z aplikace Visual Studio</span><span class="sxs-lookup"><span data-stu-id="41858-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="41858-134">Pro snadnější přístup můžete přidat příkazový řádek pro vývojáře nebo jakýkoli jiný příkazový řádek do nabídky Nástroje v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41858-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="41858-135">Chcete-li nástroj zpřístupnit, přidejte jej do seznamu externích nástrojů.</span><span class="sxs-lookup"><span data-stu-id="41858-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="41858-136">Postup je následující:</span><span class="sxs-lookup"><span data-stu-id="41858-136">Here are the steps:</span></span>

1. <span data-ttu-id="41858-137">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41858-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="41858-138">V počátečním okně zvolte **Pokračovat bez kódu**.</span><span class="sxs-lookup"><span data-stu-id="41858-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="41858-139">Na řádku nabídek zvolte **Nástroje externínástroje** > **External Tools**.</span><span class="sxs-lookup"><span data-stu-id="41858-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="41858-140">V dialogovém okně **Externí nástroje** zvolte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="41858-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="41858-141">Zobrazí se nová položka.</span><span class="sxs-lookup"><span data-stu-id="41858-141">A new entry appears.</span></span>

1. <span data-ttu-id="41858-142">Zadejte **název** nové položky `Command Prompt`nabídky, například .</span><span class="sxs-lookup"><span data-stu-id="41858-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="41858-143">V poli **Příkaz** zadejte soubor, který chcete `%comspec%` `C:\Windows\System32\cmd.exe`spustit, například nebo .</span><span class="sxs-lookup"><span data-stu-id="41858-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="41858-144">V poli **Argumenty** určete, kde najít konkrétní příkazový řádek, který chcete použít, například `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span><span class="sxs-lookup"><span data-stu-id="41858-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="41858-145">Tento příkaz spustí příkazový řádek pro vývojáře, který je nainstalovaný v komunitě Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="41858-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="41858-146">Změňte tuto hodnotu podle verze, edice a umístění instalace sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41858-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="41858-147">V poli **Počáteční adresář** zadejte adresář, ve kterém bude příkazový řádek spouštěn.</span><span class="sxs-lookup"><span data-stu-id="41858-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="41858-148">Zvolte hodnotu, například **Adresář projektu,** výběrem šipky vedle pole.</span><span class="sxs-lookup"><span data-stu-id="41858-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="41858-149">Zvolte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="41858-149">Choose the **OK** button.</span></span>

   ![Dialogové okno Externí nástroje s vyplněnými hodnotami polí.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="41858-151">Nová položka nabídky je přidána a přístup k příkazovému řádku můžete získat z nabídky Nástroje.</span><span class="sxs-lookup"><span data-stu-id="41858-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Položka nabídky příkazového řádku v sadě Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="41858-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="41858-153">See also</span></span>

- [<span data-ttu-id="41858-154">.NET Framework – nástroje</span><span class="sxs-lookup"><span data-stu-id="41858-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="41858-155">Správa externích nástrojů</span><span class="sxs-lookup"><span data-stu-id="41858-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="41858-156">Použití sady nástrojů Microsoft C++ z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="41858-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
