---
title: Nainstalovat lokalizované soubory IntelliSense
description: Naučte se, jak nastavit vývojový počítač tak, aby používal lokalizované soubory IntelliSense pro projekty .NET Core v sadě Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157710"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="64de6-103">Jak nainstalovat lokalizované soubory IntelliSense pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="64de6-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="64de6-104">[IntelliSense](/visualstudio/ide/using-intellisense) je podpora dokončování kódu, která je k dispozici v různých integrovaných vývojových prostředích (IDES), jako je například Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64de6-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="64de6-105">Ve výchozím nastavení, když vyvíjíte projekty .NET Core, sada SDK obsahuje pouze anglické verze souborů technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="64de6-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="64de6-106">Tento článek vysvětluje:</span><span class="sxs-lookup"><span data-stu-id="64de6-106">This article explains:</span></span>

- <span data-ttu-id="64de6-107">Jak nainstalovat lokalizované verze těchto souborů.</span><span class="sxs-lookup"><span data-stu-id="64de6-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="64de6-108">Jak změnit instalaci sady Visual Studio tak, aby používala jiný jazyk.</span><span class="sxs-lookup"><span data-stu-id="64de6-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="64de6-109">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="64de6-109">Prerequisites</span></span>

- <span data-ttu-id="64de6-110">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="64de6-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="64de6-111">[Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="64de6-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="64de6-112">Stažení a instalace lokalizovaných souborů IntelliSense</span><span class="sxs-lookup"><span data-stu-id="64de6-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64de6-113">Tento postup vyžaduje, abyste měli oprávnění správce ke kopírování souborů IntelliSense do instalační složky .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64de6-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="64de6-114">Přejít na stránku [stáhnout soubory IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense) .</span><span class="sxs-lookup"><span data-stu-id="64de6-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="64de6-115">Stáhněte si soubor IntelliSense pro jazyk a verzi, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="64de6-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="64de6-116">Extrahujte obsah souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="64de6-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="64de6-117">Přejděte do složky .NET Core IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="64de6-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="64de6-118">Přejděte do instalační složky rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64de6-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="64de6-119">Ve výchozím nastavení je to pod *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="64de6-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="64de6-120">Vyberte sadu SDK, pro kterou chcete technologii IntelliSense nainstalovat, a přejděte k související cestě.</span><span class="sxs-lookup"><span data-stu-id="64de6-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="64de6-121">Máte následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="64de6-121">You have the following options:</span></span>

      | <span data-ttu-id="64de6-122">Typ sady SDK</span><span class="sxs-lookup"><span data-stu-id="64de6-122">SDK type</span></span>        | <span data-ttu-id="64de6-123">Cesta</span><span class="sxs-lookup"><span data-stu-id="64de6-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="64de6-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="64de6-124">.NET Core</span></span>       | <span data-ttu-id="64de6-125">*Microsoft. NETCore. app. ref*</span><span class="sxs-lookup"><span data-stu-id="64de6-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="64de6-126">Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="64de6-126">Windows Desktop</span></span> | <span data-ttu-id="64de6-127">*Microsoft. WindowsDesktop. app. ref*</span><span class="sxs-lookup"><span data-stu-id="64de6-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="64de6-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="64de6-128">.NET Standard</span></span>   | <span data-ttu-id="64de6-129">*NETStandard. Library. ref*</span><span class="sxs-lookup"><span data-stu-id="64de6-129">*NETStandard.Library.Ref*</span></span>          |

   1. <span data-ttu-id="64de6-130">Přejděte do verze, pro kterou chcete nainstalovat lokalizovanou technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="64de6-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="64de6-131">Například *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="64de6-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="64de6-132">Otevřete složku *ref* .</span><span class="sxs-lookup"><span data-stu-id="64de6-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="64de6-133">Otevřete složku moniker.</span><span class="sxs-lookup"><span data-stu-id="64de6-133">Open the moniker folder.</span></span> <span data-ttu-id="64de6-134">Například *netcoreapp 3.1*.</span><span class="sxs-lookup"><span data-stu-id="64de6-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="64de6-135">Úplná cesta, na kterou byste chtěli přejít, by tak vypadala podobně jako *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="64de6-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="64de6-136">Vytvořte podsložku ve složce moniker, kterou jste právě otevřeli.</span><span class="sxs-lookup"><span data-stu-id="64de6-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="64de6-137">Název složky určuje, který jazyk chcete použít.</span><span class="sxs-lookup"><span data-stu-id="64de6-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="64de6-138">Následující tabulka uvádí různé možnosti:</span><span class="sxs-lookup"><span data-stu-id="64de6-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="64de6-139">Jazyk</span><span class="sxs-lookup"><span data-stu-id="64de6-139">Language</span></span>              | <span data-ttu-id="64de6-140">Název složky</span><span class="sxs-lookup"><span data-stu-id="64de6-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="64de6-141">Brazilská portugalština</span><span class="sxs-lookup"><span data-stu-id="64de6-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="64de6-142">*pt – br*</span><span class="sxs-lookup"><span data-stu-id="64de6-142">*pt-br*</span></span>     |
   | <span data-ttu-id="64de6-143">Čínština (zjednodušená)</span><span class="sxs-lookup"><span data-stu-id="64de6-143">Chinese (simplified)</span></span>  | <span data-ttu-id="64de6-144">*zh – Hans*</span><span class="sxs-lookup"><span data-stu-id="64de6-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="64de6-145">Čínština (tradiční)</span><span class="sxs-lookup"><span data-stu-id="64de6-145">Chinese (traditional)</span></span> | <span data-ttu-id="64de6-146">*zh – Hant*</span><span class="sxs-lookup"><span data-stu-id="64de6-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="64de6-147">Francouzština</span><span class="sxs-lookup"><span data-stu-id="64de6-147">French</span></span>                | <span data-ttu-id="64de6-148">*FR*</span><span class="sxs-lookup"><span data-stu-id="64de6-148">*fr*</span></span>        |
   | <span data-ttu-id="64de6-149">Němčina</span><span class="sxs-lookup"><span data-stu-id="64de6-149">German</span></span>                | <span data-ttu-id="64de6-150">*&*</span><span class="sxs-lookup"><span data-stu-id="64de6-150">*de*</span></span>        |
   | <span data-ttu-id="64de6-151">Italština</span><span class="sxs-lookup"><span data-stu-id="64de6-151">Italian</span></span>               | <span data-ttu-id="64de6-152">*její*</span><span class="sxs-lookup"><span data-stu-id="64de6-152">*it*</span></span>        |
   | <span data-ttu-id="64de6-153">Japonština</span><span class="sxs-lookup"><span data-stu-id="64de6-153">Japanese</span></span>              | <span data-ttu-id="64de6-154">*dža*</span><span class="sxs-lookup"><span data-stu-id="64de6-154">*ja*</span></span>        |
   | <span data-ttu-id="64de6-155">Korejština</span><span class="sxs-lookup"><span data-stu-id="64de6-155">Korean</span></span>                | <span data-ttu-id="64de6-156">*Ko*</span><span class="sxs-lookup"><span data-stu-id="64de6-156">*ko*</span></span>        |
   | <span data-ttu-id="64de6-157">Ruština</span><span class="sxs-lookup"><span data-stu-id="64de6-157">Russian</span></span>               | <span data-ttu-id="64de6-158">*ru*</span><span class="sxs-lookup"><span data-stu-id="64de6-158">*ru*</span></span>        |
   | <span data-ttu-id="64de6-159">Španělština</span><span class="sxs-lookup"><span data-stu-id="64de6-159">Spanish</span></span>               | <span data-ttu-id="64de6-160">*jednomu*</span><span class="sxs-lookup"><span data-stu-id="64de6-160">*es*</span></span>        |

1. <span data-ttu-id="64de6-161">Zkopírujte soubory *. XML* , které jste extrahovali v kroku 3, do této nové složky.</span><span class="sxs-lookup"><span data-stu-id="64de6-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="64de6-162">Soubory *. XML* jsou rozdělené podle složek sady SDK, proto je zkopírujte do odpovídajícího SDK, kterou jste zvolili v kroku 4.</span><span class="sxs-lookup"><span data-stu-id="64de6-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="64de6-163">Změnit jazyk sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="64de6-163">Modify Visual Studio language</span></span>

<span data-ttu-id="64de6-164">Aby sada Visual Studio používala pro technologii IntelliSense jiný jazyk, nainstalujte příslušnou jazykovou sadu.</span><span class="sxs-lookup"><span data-stu-id="64de6-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="64de6-165">To lze provést v [průběhu instalace](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) nebo později úpravou instalace sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64de6-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="64de6-166">Pokud již sadu Visual Studio nakonfigurovali pro zvolený jazyk, bude instalace technologie IntelliSense připravena.</span><span class="sxs-lookup"><span data-stu-id="64de6-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="64de6-167">Nainstalovat jazykovou sadu</span><span class="sxs-lookup"><span data-stu-id="64de6-167">Install the language pack</span></span>

<span data-ttu-id="64de6-168">Pokud jste požadovanou jazykovou sadu neinstalovali během instalace, aktualizujte sadu Visual Studio podle následujících pokynů k instalaci jazykové sady:</span><span class="sxs-lookup"><span data-stu-id="64de6-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64de6-169">Chcete-li nainstalovat, aktualizovat nebo upravit aplikaci Visual Studio, je nutné se přihlásit pomocí účtu, který má oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="64de6-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="64de6-170">Další informace naleznete v tématu [uživatelská oprávnění a aplikace Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="64de6-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="64de6-171">Najdete instalační program sady Visual Studio v počítači.</span><span class="sxs-lookup"><span data-stu-id="64de6-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="64de6-172">Například na počítači se systémem Windows 10 vyberte možnost **Start**a potom přejděte k písmenu **v**, kde je uveden jako **instalační program pro Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="64de6-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Otevřete Instalační program pro Visual Studio z Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="64de6-174">Instalační program pro Visual Studio můžete najít také v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="64de6-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="64de6-175">Než budete pokračovat, bude pravděpodobně nutné aktualizovat instalační program.</span><span class="sxs-lookup"><span data-stu-id="64de6-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="64de6-176">Pokud ano, postupujte podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="64de6-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="64de6-177">V instalačním programu vyhledejte edici sady Visual Studio, do které chcete přidat jazykovou sadu, a pak zvolte možnost **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="64de6-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Aktualizace nebo změna sady Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="64de6-179">Pokud nevidíte tlačítko **Upravit** , ale místo toho se zobrazí **aktualizace** , budete muset Visual Studio aktualizovat předtím, než budete moct instalaci upravit.</span><span class="sxs-lookup"><span data-stu-id="64de6-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="64de6-180">Po dokončení aktualizace by se mělo zobrazit tlačítko **Upravit** .</span><span class="sxs-lookup"><span data-stu-id="64de6-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="64de6-181">Na kartě **jazykové sady** vyberte nebo zrušte výběr jazyků, které chcete nainstalovat nebo odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="64de6-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Karta jazykové sady sady Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="64de6-183">Klikněte na tlačítko **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="64de6-183">Choose **Modify**.</span></span> <span data-ttu-id="64de6-184">Spustí se aktualizace.</span><span class="sxs-lookup"><span data-stu-id="64de6-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="64de6-185">Úprava nastavení jazyka v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="64de6-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="64de6-186">Jakmile nainstalujete požadované jazykové sady, upravte nastavení aplikace Visual Studio tak, aby používalo jiný jazyk:</span><span class="sxs-lookup"><span data-stu-id="64de6-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="64de6-187">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64de6-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="64de6-188">V okně Start vyberte možnost **pokračovat bez kódu**.</span><span class="sxs-lookup"><span data-stu-id="64de6-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="64de6-189">Na panelu nabídek vyberte možnost **nástroje** > **Možnosti**.</span><span class="sxs-lookup"><span data-stu-id="64de6-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="64de6-190">Otevře se dialogové okno Možnosti.</span><span class="sxs-lookup"><span data-stu-id="64de6-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="64de6-191">V uzlu **prostředí** vyberte možnost **mezinárodní nastavení**.</span><span class="sxs-lookup"><span data-stu-id="64de6-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="64de6-192">V rozevíracím seznamu **jazyk** vyberte požadovaný jazyk.</span><span class="sxs-lookup"><span data-stu-id="64de6-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="64de6-193">Zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="64de6-193">Choose **OK**.</span></span>

1. <span data-ttu-id="64de6-194">Dialog vás informuje o tom, že je nutné restartovat aplikaci Visual Studio, aby se změny projevily.</span><span class="sxs-lookup"><span data-stu-id="64de6-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="64de6-195">Zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="64de6-195">Choose **OK**.</span></span>

1. <span data-ttu-id="64de6-196">Restartujte sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64de6-196">Restart Visual Studio.</span></span>

<span data-ttu-id="64de6-197">Poté by měla technologie IntelliSense fungovat podle očekávání, když otevřete projekt .NET Core, který cílí na verzi souborů technologie IntelliSense, které jste právě nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="64de6-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="64de6-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="64de6-198">See also</span></span>

- [<span data-ttu-id="64de6-199">IntelliSense v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="64de6-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
