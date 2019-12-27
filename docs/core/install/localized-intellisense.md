---
title: Nainstalovat lokalizované soubory IntelliSense
description: Naučte se, jak nastavit vývojový počítač tak, aby používal lokalizované soubory IntelliSense pro projekty .NET Core v sadě Visual Studio.
author: mairaw
ms.author: mairaw
ms.date: 12/18/2019
ms.openlocfilehash: 98d75544ab853e75c175dd2919991b250cfaa3b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443475"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="859be-103">Jak nainstalovat lokalizované soubory IntelliSense pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="859be-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="859be-104">[IntelliSense](/visualstudio/ide/using-intellisense) je podpora dokončování kódu, která je k dispozici v různých integrovaných vývojových prostředích (IDES), jako je například Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="859be-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="859be-105">Ve výchozím nastavení, když vyvíjíte projekty .NET Core, sada SDK obsahuje pouze anglické verze souborů technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="859be-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="859be-106">Tento článek vysvětluje:</span><span class="sxs-lookup"><span data-stu-id="859be-106">This article explains:</span></span>

- <span data-ttu-id="859be-107">Jak nainstalovat lokalizované verze těchto souborů.</span><span class="sxs-lookup"><span data-stu-id="859be-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="859be-108">Jak změnit instalaci sady Visual Studio tak, aby používala jiný jazyk.</span><span class="sxs-lookup"><span data-stu-id="859be-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="859be-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="859be-109">Prerequisites</span></span>

- <span data-ttu-id="859be-110">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="859be-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="859be-111">[Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="859be-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="859be-112">Stažení a instalace lokalizovaných souborů IntelliSense</span><span class="sxs-lookup"><span data-stu-id="859be-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="859be-113">Tento postup vyžaduje, abyste měli oprávnění správce ke kopírování souborů IntelliSense do instalační složky .NET Core.</span><span class="sxs-lookup"><span data-stu-id="859be-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="859be-114">Přejít na stránku [stáhnout soubory IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense) .</span><span class="sxs-lookup"><span data-stu-id="859be-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="859be-115">Stáhněte si soubor IntelliSense pro jazyk a verzi, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="859be-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="859be-116">Extrahujte obsah souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="859be-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="859be-117">Přejděte do instalační složky rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="859be-117">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="859be-118">Ve výchozím nastavení je to pod *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="859be-118">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>

   - <span data-ttu-id="859be-119">Vyberte sadu SDK, pro kterou chcete technologii IntelliSense nainstalovat, a přejděte k související cestě.</span><span class="sxs-lookup"><span data-stu-id="859be-119">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="859be-120">Máte následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="859be-120">You have the following options:</span></span>

      | <span data-ttu-id="859be-121">Typ sady SDK</span><span class="sxs-lookup"><span data-stu-id="859be-121">SDK type</span></span>        | <span data-ttu-id="859be-122">Cesta</span><span class="sxs-lookup"><span data-stu-id="859be-122">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="859be-123">.NET Core</span><span class="sxs-lookup"><span data-stu-id="859be-123">.NET Core</span></span>       | <span data-ttu-id="859be-124">*Microsoft. NETCore. app. ref*</span><span class="sxs-lookup"><span data-stu-id="859be-124">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="859be-125">Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="859be-125">Windows Desktop</span></span> | <span data-ttu-id="859be-126">*Microsoft. WindowsDesktop. app. ref*</span><span class="sxs-lookup"><span data-stu-id="859be-126">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="859be-127">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="859be-127">.NET Standard</span></span>   | <span data-ttu-id="859be-128">*NETStandard. Library. ref*</span><span class="sxs-lookup"><span data-stu-id="859be-128">*NETStandard.Library.Ref*</span></span>          |
   
   - <span data-ttu-id="859be-129">Přejděte do verze, pro kterou chcete nainstalovat lokalizovanou technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="859be-129">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="859be-130">Například *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="859be-130">For example, *3.1.0*.</span></span>
   - <span data-ttu-id="859be-131">Otevřete složku *ref* .</span><span class="sxs-lookup"><span data-stu-id="859be-131">Open the *ref* folder.</span></span>
   - <span data-ttu-id="859be-132">Otevřete složku moniker.</span><span class="sxs-lookup"><span data-stu-id="859be-132">Open the moniker folder.</span></span> <span data-ttu-id="859be-133">Například *netcoreapp 3.1*.</span><span class="sxs-lookup"><span data-stu-id="859be-133">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="859be-134">Úplná cesta, na kterou byste chtěli přejít, by tak vypadala podobně jako *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="859be-134">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="859be-135">Vytvořte podsložku ve složce moniker, kterou jste právě otevřeli.</span><span class="sxs-lookup"><span data-stu-id="859be-135">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="859be-136">Název složky určuje, který jazyk chcete použít.</span><span class="sxs-lookup"><span data-stu-id="859be-136">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="859be-137">Následující tabulka uvádí různé možnosti:</span><span class="sxs-lookup"><span data-stu-id="859be-137">The following table specifies the different options:</span></span>

   | <span data-ttu-id="859be-138">Jazyk</span><span class="sxs-lookup"><span data-stu-id="859be-138">Language</span></span>              | <span data-ttu-id="859be-139">Název složky</span><span class="sxs-lookup"><span data-stu-id="859be-139">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="859be-140">Brazilská portugalština</span><span class="sxs-lookup"><span data-stu-id="859be-140">Brazilian Portuguese</span></span>  | <span data-ttu-id="859be-141">*pt – br*</span><span class="sxs-lookup"><span data-stu-id="859be-141">*pt-br*</span></span>     |
   | <span data-ttu-id="859be-142">Čínština (zjednodušená)</span><span class="sxs-lookup"><span data-stu-id="859be-142">Chinese (simplified)</span></span>  | <span data-ttu-id="859be-143">*zh – Hans*</span><span class="sxs-lookup"><span data-stu-id="859be-143">*zh-hans*</span></span>   |
   | <span data-ttu-id="859be-144">Čínština (tradiční)</span><span class="sxs-lookup"><span data-stu-id="859be-144">Chinese (traditional)</span></span> | <span data-ttu-id="859be-145">*zh – Hant*</span><span class="sxs-lookup"><span data-stu-id="859be-145">*zh-hant*</span></span>   |
   | <span data-ttu-id="859be-146">Francouzština</span><span class="sxs-lookup"><span data-stu-id="859be-146">French</span></span>                | <span data-ttu-id="859be-147">*FR*</span><span class="sxs-lookup"><span data-stu-id="859be-147">*fr*</span></span>        |
   | <span data-ttu-id="859be-148">Němčina</span><span class="sxs-lookup"><span data-stu-id="859be-148">German</span></span>                | <span data-ttu-id="859be-149">*&*</span><span class="sxs-lookup"><span data-stu-id="859be-149">*de*</span></span>        |
   | <span data-ttu-id="859be-150">Italština</span><span class="sxs-lookup"><span data-stu-id="859be-150">Italian</span></span>               | <span data-ttu-id="859be-151">*její*</span><span class="sxs-lookup"><span data-stu-id="859be-151">*it*</span></span>        |
   | <span data-ttu-id="859be-152">Japonština</span><span class="sxs-lookup"><span data-stu-id="859be-152">Japanese</span></span>              | <span data-ttu-id="859be-153">*dža*</span><span class="sxs-lookup"><span data-stu-id="859be-153">*ja*</span></span>        |
   | <span data-ttu-id="859be-154">Korejština</span><span class="sxs-lookup"><span data-stu-id="859be-154">Korean</span></span>                | <span data-ttu-id="859be-155">*Ko*</span><span class="sxs-lookup"><span data-stu-id="859be-155">*ko*</span></span>        |
   | <span data-ttu-id="859be-156">Ruština</span><span class="sxs-lookup"><span data-stu-id="859be-156">Russian</span></span>               | <span data-ttu-id="859be-157">*ru*</span><span class="sxs-lookup"><span data-stu-id="859be-157">*ru*</span></span>        |
   | <span data-ttu-id="859be-158">Španělština</span><span class="sxs-lookup"><span data-stu-id="859be-158">Spanish</span></span>               | <span data-ttu-id="859be-159">*jednomu*</span><span class="sxs-lookup"><span data-stu-id="859be-159">*es*</span></span>        |

1. <span data-ttu-id="859be-160">Zkopírujte soubory *. XML* , které jste extrahovali v kroku 3, do této nové složky.</span><span class="sxs-lookup"><span data-stu-id="859be-160">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="859be-161">Soubory *. XML* jsou rozdělené podle složek sady SDK, proto je zkopírujte do odpovídajícího SDK, kterou jste zvolili v kroku 4.</span><span class="sxs-lookup"><span data-stu-id="859be-161">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="859be-162">Změnit jazyk sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="859be-162">Modify Visual Studio language</span></span>

<span data-ttu-id="859be-163">Aby sada Visual Studio používala pro technologii IntelliSense jiný jazyk, nainstalujte příslušnou jazykovou sadu.</span><span class="sxs-lookup"><span data-stu-id="859be-163">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="859be-164">To lze provést v [průběhu instalace](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) nebo později úpravou instalace sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="859be-164">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="859be-165">Pokud již sadu Visual Studio nakonfigurovali pro zvolený jazyk, bude instalace technologie IntelliSense připravena.</span><span class="sxs-lookup"><span data-stu-id="859be-165">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="859be-166">Nainstalovat jazykovou sadu</span><span class="sxs-lookup"><span data-stu-id="859be-166">Install the language pack</span></span>

<span data-ttu-id="859be-167">Pokud jste požadovanou jazykovou sadu neinstalovali během instalace, aktualizujte sadu Visual Studio podle následujících pokynů k instalaci jazykové sady:</span><span class="sxs-lookup"><span data-stu-id="859be-167">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="859be-168">Instalovat, aktualizovat nebo upravit sadu Visual Studio, musíte se přihlásit pomocí účtu, který má oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="859be-168">To install, update, or modify Visual Studio, you must log on with an account that has administrative permissions.</span></span> <span data-ttu-id="859be-169">Další informace naleznete v tématu [uživatelská oprávnění a aplikace Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="859be-169">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="859be-170">Najdete instalační program sady Visual Studio v počítači.</span><span class="sxs-lookup"><span data-stu-id="859be-170">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="859be-171">Například v počítači se systémem Windows 10, vyberte **Start**a poté přejděte k označení **V**, kde je hodnota uvedena jako **instalační program sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="859be-171">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Otevřete Instalační program pro Visual Studio z Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="859be-173">Instalační program pro Visual Studio můžete najít také v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="859be-173">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="859be-174">Než budete pokračovat, bude pravděpodobně nutné aktualizovat instalační program.</span><span class="sxs-lookup"><span data-stu-id="859be-174">You might have to update the installer before continuing.</span></span> <span data-ttu-id="859be-175">Pokud ano, postupujte podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="859be-175">If so, follow the prompts.</span></span>

1. <span data-ttu-id="859be-176">V instalačním programu vyhledejte edici sady Visual Studio, do které chcete přidat jazykovou sadu, a pak zvolte možnost **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="859be-176">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Aktualizace nebo změna sady Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="859be-178">Pokud nevidíte tlačítko **Upravit** , ale místo toho se zobrazí **aktualizace** , budete muset Visual Studio aktualizovat předtím, než budete moct instalaci upravit.</span><span class="sxs-lookup"><span data-stu-id="859be-178">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="859be-179">Po dokončení aktualizace by se mělo zobrazit tlačítko **Upravit** .</span><span class="sxs-lookup"><span data-stu-id="859be-179">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="859be-180">Na kartě **jazykové sady** vyberte nebo zrušte výběr jazyků, které chcete nainstalovat nebo odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="859be-180">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Karta jazykové sady sady Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="859be-182">Klikněte na tlačítko **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="859be-182">Choose **Modify**.</span></span> <span data-ttu-id="859be-183">Spustí se aktualizace.</span><span class="sxs-lookup"><span data-stu-id="859be-183">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="859be-184">Úprava nastavení jazyka v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="859be-184">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="859be-185">Jakmile nainstalujete požadované jazykové sady, upravte nastavení aplikace Visual Studio tak, aby používalo jiný jazyk:</span><span class="sxs-lookup"><span data-stu-id="859be-185">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="859be-186">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="859be-186">Open Visual Studio.</span></span>

1. <span data-ttu-id="859be-187">V okně Start vyberte možnost **pokračovat bez kódu**.</span><span class="sxs-lookup"><span data-stu-id="859be-187">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="859be-188">V hlavní nabídce vyberte **nástroje** > **Možnosti**.</span><span class="sxs-lookup"><span data-stu-id="859be-188">On the main menu, select **Tools** > **Options**.</span></span> <span data-ttu-id="859be-189">Otevře se dialogové okno Možnosti.</span><span class="sxs-lookup"><span data-stu-id="859be-189">The Options dialog opens.</span></span>

1. <span data-ttu-id="859be-190">Ve složce **prostředí** vyberte možnost **mezinárodní nastavení**.</span><span class="sxs-lookup"><span data-stu-id="859be-190">Under the **Environment** folder, choose **International Settings**.</span></span>

1. <span data-ttu-id="859be-191">V rozevíracím seznamu **jazyk** vyberte požadovaný jazyk.</span><span class="sxs-lookup"><span data-stu-id="859be-191">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="859be-192">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="859be-192">Choose **OK**.</span></span> 

1. <span data-ttu-id="859be-193">Dialog vás informuje o tom, že je nutné restartovat aplikaci Visual Studio, aby se změny projevily.</span><span class="sxs-lookup"><span data-stu-id="859be-193">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="859be-194">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="859be-194">Choose **OK**.</span></span>

1. <span data-ttu-id="859be-195">Restartujte sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="859be-195">Restart Visual Studio.</span></span>

<span data-ttu-id="859be-196">Poté by měla technologie IntelliSense fungovat podle očekávání, když otevřete projekt .NET Core, který cílí na verzi souborů technologie IntelliSense, které jste právě nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="859be-196">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="859be-197">Viz také:</span><span class="sxs-lookup"><span data-stu-id="859be-197">See also</span></span>

- [<span data-ttu-id="859be-198">IntelliSense v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="859be-198">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
