---
title: Developer Command Prompt pro Visual Studio
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
ms.openlocfilehash: 59af252967a18eca858035fb0a3465d909734ddf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044731"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="7d307-102">Developer Command Prompt pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7d307-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="7d307-103">Developer Command Prompt pro Visual Studio vám umožní snadněji používat nástroje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d307-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="7d307-104">Jedná se o příkazový řádek, který automaticky nastaví konkrétní proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="7d307-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
> [<span data-ttu-id="7d307-105">Stáhnout Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7d307-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="7d307-106">Hledání příkazového řádku na svém počítači</span><span class="sxs-lookup"><span data-stu-id="7d307-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="7d307-107">V závislosti na verzi sady Visual Studio a všech dalších sadách SDK, které jste nainstalovali, můžete mít více příkazových výzev.</span><span class="sxs-lookup"><span data-stu-id="7d307-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="7d307-108">Například 64bitové verze sady Visual Studio poskytují 32bitové a 64bitové verze příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7d307-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="7d307-109">(32 a 64 verze většiny nástrojů jsou stejné, ale některé nástroje mění konkrétní možnosti pro 32-bitové 64 a 16bitové prostředí.) Pokud následující postup nefunguje, můžete zkusit [soubory ručně vyhledat na](#manually-locate-the-files-on-your-machine) počítači nebo [Spustit příkazový řádek z aplikace Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="7d307-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="7d307-110">Ve Windows 10</span><span class="sxs-lookup"><span data-stu-id="7d307-110">In Windows 10</span></span>

1. <span data-ttu-id="7d307-111">Do vyhledávacího pole na hlavním panelu začněte psát název nástroje, například `dev` nebo. `developer command prompt`</span><span class="sxs-lookup"><span data-stu-id="7d307-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="7d307-112">Tím se zobrazí seznam nainstalovaných aplikací, které odpovídají vašemu vzoru hledání.</span><span class="sxs-lookup"><span data-stu-id="7d307-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="7d307-113">Pokud hledáte jiný příkazový řádek, zkuste zadat jiný hledaný výraz, jako je například `prompt`.</span><span class="sxs-lookup"><span data-stu-id="7d307-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="7d307-114">Vyberte **Developer Command Prompt pro Visual Studio** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="7d307-114">Choose the **Developer Command Prompt for Visual Studio** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="7d307-115">V Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="7d307-115">In Windows 8.1</span></span>

1. <span data-ttu-id="7d307-116">Kliknutím![na klávesu s logem Windows na klávesnici na obrazovce Start přejdete na **úvodní** obrazovku.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="7d307-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="7d307-117">například na klávesnici.</span><span class="sxs-lookup"><span data-stu-id="7d307-117">on your keyboard for example.</span></span>

2. <span data-ttu-id="7d307-118">Na obrazovce **Start** **stiskněte klávesu** **CTRL**+a otevřete seznam **aplikace** a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="7d307-118">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="7d307-119">Tím se zobrazí seznam, který obsahuje všechny nainstalované příkazy sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d307-119">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="7d307-120">Vyberte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="7d307-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="7d307-121">V systému Windows 8</span><span class="sxs-lookup"><span data-stu-id="7d307-121">In Windows 8</span></span>

1. <span data-ttu-id="7d307-122">Kliknutím![na klávesu s logem Windows na klávesnici na obrazovce Start přejdete na **úvodní** obrazovku.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="7d307-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="7d307-123">například na klávesnici.</span><span class="sxs-lookup"><span data-stu-id="7d307-123">on your keyboard for example.</span></span>

2. <span data-ttu-id="7d307-124">Na obrazovce **Start** stiskněte klávesu s ![logem Windows na klávesu s logem Windows na klávesnici.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="7d307-124">On the **Start** screen, press the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="7d307-125">`+ Z`.</span><span class="sxs-lookup"><span data-stu-id="7d307-125">`+ Z`.</span></span>

3. <span data-ttu-id="7d307-126">V dolní části obrazovky zvolte ikonu **zobrazení aplikace** a pak zadejte `V`.</span><span class="sxs-lookup"><span data-stu-id="7d307-126">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="7d307-127">Tím se zobrazí seznam, který obsahuje všechny nainstalované příkazy sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d307-127">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="7d307-128">Vyberte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).</span><span class="sxs-lookup"><span data-stu-id="7d307-128">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="7d307-129">V systému Windows 7</span><span class="sxs-lookup"><span data-stu-id="7d307-129">In Windows 7</span></span>

1. <span data-ttu-id="7d307-130">Klikněte na tlačítko **Start**, rozbalte položku **všechny programy**a poté rozbalte položku **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7d307-130">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="7d307-131">V závislosti na verzi sady Visual Studio, kterou jste nainstalovali, vyberte možnost **Visual Studio Tools**, **příkazový řádek sady Visual Studio**nebo příkazový řádek, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="7d307-131">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="7d307-132">Pokud máte nainstalované jiné sady SDK, jako je například [Sada Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), může se zobrazit další příkazová výzva pro architektury ARM, x86 nebo x64.</span><span class="sxs-lookup"><span data-stu-id="7d307-132">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="7d307-133">V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.</span><span class="sxs-lookup"><span data-stu-id="7d307-133">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="7d307-134">Ručně vyhledat soubory na počítači</span><span class="sxs-lookup"><span data-stu-id="7d307-134">Manually locate the files on your machine</span></span>

<span data-ttu-id="7d307-135">Zkratky pro příkazy, které jste nainstalovali, se obvykle nacházejí ve složce **nabídky Start** pro Visual Studio, například v C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="7d307-135">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="7d307-136">Ale z nějakého důvodu hledání příkazového řádku nepřinese očekávané výsledky, můžete zkusit zástupce na svém počítači najít ručně.</span><span class="sxs-lookup"><span data-stu-id="7d307-136">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="7d307-137">Zkuste vyhledat název souboru příkazového řádku, například *VsDevCmd. bat*, nebo přejít do složky Tools, jako je C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (cesta se mění podle verze sady Visual Studio, edice). a umístění instalace).</span><span class="sxs-lookup"><span data-stu-id="7d307-137">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="7d307-138">Spuštění příkazového řádku v rámci sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7d307-138">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="7d307-139">Pro snazší přístup můžete přidat Developer Command Prompt sady Visual Studio nebo jakýkoli jiný příkazový řádek do nabídky **nástroje** v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d307-139">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="7d307-140">Aby byl nástroj dostupný, přidejte ho do seznamu externích nástrojů.</span><span class="sxs-lookup"><span data-stu-id="7d307-140">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="7d307-141">Postup je následující:</span><span class="sxs-lookup"><span data-stu-id="7d307-141">Here are the steps:</span></span>

1. <span data-ttu-id="7d307-142">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d307-142">Open Visual Studio.</span></span>

2. <span data-ttu-id="7d307-143">Vyberte nabídku **nástroje** a pak zvolte **externí nástroje**.</span><span class="sxs-lookup"><span data-stu-id="7d307-143">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="7d307-144">V dialogovém okně **externí nástroje** klikněte na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="7d307-144">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="7d307-145">Zobrazí se nová položka.</span><span class="sxs-lookup"><span data-stu-id="7d307-145">A new entry appears.</span></span>

4. <span data-ttu-id="7d307-146">Zadejte **název** nové položky nabídky, například `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="7d307-146">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="7d307-147">Do pole **příkaz** zadejte soubor, který chcete spustit, například `%comspec%` nebo. `C:\Windows\System32\cmd.exe`</span><span class="sxs-lookup"><span data-stu-id="7d307-147">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="7d307-148">V poli **argumenty** určete, kde se má najít konkrétní příkazový řádek, který chcete použít `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Tento příkaz spustí Developer Command Prompt, který je nainstalován se sadou Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="7d307-148">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="7d307-149">Změňte tuto hodnotu podle vaší verze, edice a umístění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d307-149">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="7d307-150">Vyberte hodnotu pro počáteční pole **adresáře** , jako je například **adresář projektu**.</span><span class="sxs-lookup"><span data-stu-id="7d307-150">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="7d307-151">Zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7d307-151">Choose the **OK** button.</span></span>

   <span data-ttu-id="7d307-152">Nová položka nabídky se přidá a k příkazovému řádku můžete získat přístup z nabídky **nástroje** .</span><span class="sxs-lookup"><span data-stu-id="7d307-152">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Položka nabídky příkazového řádku v aplikaci Visual Studio](./media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="7d307-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d307-154">See also</span></span>

- [<span data-ttu-id="7d307-155">Nástroje</span><span class="sxs-lookup"><span data-stu-id="7d307-155">Tools</span></span>](index.md)
- [<span data-ttu-id="7d307-156">Správa externích nástrojů</span><span class="sxs-lookup"><span data-stu-id="7d307-156">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
