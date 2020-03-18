---
title: Instalace lokalizovaných souborů IntelliSense
description: Přečtěte si, jak nastavit vývojový počítač tak, aby používal lokalizované soubory IntelliSense pro projekty .NET Core v sadě Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157710"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="79245-103">Jak nainstalovat lokalizované soubory IntelliSense pro rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="79245-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="79245-104">[IntelliSense](/visualstudio/ide/using-intellisense) je podpora pro dokončení kódu, která je k dispozici v různých integrovaných vývojových prostředích (IDE), jako je například Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79245-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="79245-105">Ve výchozím nastavení při vývoji projektů .NET Core sada SDK obsahuje pouze anglickou verzi souborů IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="79245-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="79245-106">Tento článek vysvětluje:</span><span class="sxs-lookup"><span data-stu-id="79245-106">This article explains:</span></span>

- <span data-ttu-id="79245-107">Jak nainstalovat lokalizovanou verzi těchto souborů.</span><span class="sxs-lookup"><span data-stu-id="79245-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="79245-108">Jak upravit instalaci sady Visual Studio tak, aby používala jiný jazyk.</span><span class="sxs-lookup"><span data-stu-id="79245-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79245-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79245-109">Prerequisites</span></span>

- <span data-ttu-id="79245-110">[Sada .NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="79245-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="79245-111">[Visual Studio 2019 verze 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="79245-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="79245-112">Stažení a instalace lokalizovaných souborů IntelliSense</span><span class="sxs-lookup"><span data-stu-id="79245-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79245-113">Tento postup vyžaduje, abyste měli oprávnění správce ke kopírování souborů IntelliSense do instalační složky Jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="79245-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="79245-114">Přejděte na stránku [Stáhnout soubory IntelliSense.](https://dotnet.microsoft.com/download/dotnet-core/intellisense)</span><span class="sxs-lookup"><span data-stu-id="79245-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="79245-115">Stáhněte si soubor IntelliSense pro jazyk a verzi, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="79245-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="79245-116">Extrahujte obsah souboru zip.</span><span class="sxs-lookup"><span data-stu-id="79245-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="79245-117">Přejděte do složky .NET Core Intellisense.</span><span class="sxs-lookup"><span data-stu-id="79245-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="79245-118">Přejděte do instalační složky jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="79245-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="79245-119">Ve výchozím nastavení je v části *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="79245-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="79245-120">Zvolte, pro kterou sadu SDK chcete nainstalovat službu IntelliSense, a přejděte na přidruženou cestu.</span><span class="sxs-lookup"><span data-stu-id="79245-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="79245-121">Máte následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="79245-121">You have the following options:</span></span>

      | <span data-ttu-id="79245-122">Typ sady SDK</span><span class="sxs-lookup"><span data-stu-id="79245-122">SDK type</span></span>        | <span data-ttu-id="79245-123">Cesta</span><span class="sxs-lookup"><span data-stu-id="79245-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="79245-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="79245-124">.NET Core</span></span>       | <span data-ttu-id="79245-125">*Soubor Microsoft.NETCore.App.ref*</span><span class="sxs-lookup"><span data-stu-id="79245-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="79245-126">Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="79245-126">Windows Desktop</span></span> | <span data-ttu-id="79245-127">*Microsoft.WindowsDesktop.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="79245-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="79245-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="79245-128">.NET Standard</span></span>   | <span data-ttu-id="79245-129">*NETStandard.Library.Ref*</span><span class="sxs-lookup"><span data-stu-id="79245-129">*NETStandard.Library.Ref*</span></span>          |

   1. <span data-ttu-id="79245-130">Přejděte na verzi, pro kterou chcete nainstalovat lokalizovanou službu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="79245-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="79245-131">Například *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="79245-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="79245-132">Otevřete složku *ref.*</span><span class="sxs-lookup"><span data-stu-id="79245-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="79245-133">Otevřete složku zástupné názvy.</span><span class="sxs-lookup"><span data-stu-id="79245-133">Open the moniker folder.</span></span> <span data-ttu-id="79245-134">Například *netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="79245-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="79245-135">Úplná cesta, na kterou byste přešli, by tedy vypadala podobně jako *c:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="79245-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="79245-136">Vytvořte podsložku uvnitř složky zástupný název, kterou jste právě otevřeli.</span><span class="sxs-lookup"><span data-stu-id="79245-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="79245-137">Název složky označuje, který jazyk chcete použít.</span><span class="sxs-lookup"><span data-stu-id="79245-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="79245-138">V následující tabulce jsou uvedeny různé možnosti:</span><span class="sxs-lookup"><span data-stu-id="79245-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="79245-139">Jazyk</span><span class="sxs-lookup"><span data-stu-id="79245-139">Language</span></span>              | <span data-ttu-id="79245-140">Název složky</span><span class="sxs-lookup"><span data-stu-id="79245-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="79245-141">Brazilská portugalština</span><span class="sxs-lookup"><span data-stu-id="79245-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="79245-142">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="79245-142">*pt-br*</span></span>     |
   | <span data-ttu-id="79245-143">Čínština (zjednodušená)</span><span class="sxs-lookup"><span data-stu-id="79245-143">Chinese (simplified)</span></span>  | <span data-ttu-id="79245-144">*zh-hans*</span><span class="sxs-lookup"><span data-stu-id="79245-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="79245-145">Čínština (tradiční)</span><span class="sxs-lookup"><span data-stu-id="79245-145">Chinese (traditional)</span></span> | <span data-ttu-id="79245-146">*zh-hant*</span><span class="sxs-lookup"><span data-stu-id="79245-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="79245-147">Francouzština</span><span class="sxs-lookup"><span data-stu-id="79245-147">French</span></span>                | <span data-ttu-id="79245-148">*Fr*</span><span class="sxs-lookup"><span data-stu-id="79245-148">*fr*</span></span>        |
   | <span data-ttu-id="79245-149">Němčina</span><span class="sxs-lookup"><span data-stu-id="79245-149">German</span></span>                | <span data-ttu-id="79245-150">*De*</span><span class="sxs-lookup"><span data-stu-id="79245-150">*de*</span></span>        |
   | <span data-ttu-id="79245-151">Italština</span><span class="sxs-lookup"><span data-stu-id="79245-151">Italian</span></span>               | <span data-ttu-id="79245-152">*je to*</span><span class="sxs-lookup"><span data-stu-id="79245-152">*it*</span></span>        |
   | <span data-ttu-id="79245-153">Japonština</span><span class="sxs-lookup"><span data-stu-id="79245-153">Japanese</span></span>              | <span data-ttu-id="79245-154">*ja*</span><span class="sxs-lookup"><span data-stu-id="79245-154">*ja*</span></span>        |
   | <span data-ttu-id="79245-155">Korejština</span><span class="sxs-lookup"><span data-stu-id="79245-155">Korean</span></span>                | <span data-ttu-id="79245-156">*Ko*</span><span class="sxs-lookup"><span data-stu-id="79245-156">*ko*</span></span>        |
   | <span data-ttu-id="79245-157">Ruština</span><span class="sxs-lookup"><span data-stu-id="79245-157">Russian</span></span>               | <span data-ttu-id="79245-158">*Ru*</span><span class="sxs-lookup"><span data-stu-id="79245-158">*ru*</span></span>        |
   | <span data-ttu-id="79245-159">Španělština</span><span class="sxs-lookup"><span data-stu-id="79245-159">Spanish</span></span>               | <span data-ttu-id="79245-160">*es*</span><span class="sxs-lookup"><span data-stu-id="79245-160">*es*</span></span>        |

1. <span data-ttu-id="79245-161">Zkopírujte soubory *XML,* které jste extrahovali v kroku 3, do této nové složky.</span><span class="sxs-lookup"><span data-stu-id="79245-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="79245-162">Soubory *XML* jsou rozděleny podle složek sady SDK, takže je zkopírujte do odpovídající sady SDK, kterou jste zvolili v kroku 4.</span><span class="sxs-lookup"><span data-stu-id="79245-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="79245-163">Úprava jazyka sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79245-163">Modify Visual Studio language</span></span>

<span data-ttu-id="79245-164">Aby visual studio používalo pro technologie IntelliSense jiný jazyk, nainstalujte příslušnou jazykovou sadu.</span><span class="sxs-lookup"><span data-stu-id="79245-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="79245-165">To lze provést [během instalace](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) nebo později úpravou instalace sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79245-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="79245-166">Pokud již máte Visual Studio nakonfigurované podle jazyka podle vašeho výběru, instalace technologie IntelliSense je připravena.</span><span class="sxs-lookup"><span data-stu-id="79245-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="79245-167">Instalace jazykové sady</span><span class="sxs-lookup"><span data-stu-id="79245-167">Install the language pack</span></span>

<span data-ttu-id="79245-168">Pokud jste požadovanou jazykovou sadu během instalace nenainstalovali, aktualizujte sadu Visual Studio následujícím způsobem a nainstalujte ji:</span><span class="sxs-lookup"><span data-stu-id="79245-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79245-169">Chcete-li nainstalovat, aktualizovat nebo upravit visual studio, musíte se přihlásit pomocí účtu, který má oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="79245-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="79245-170">Další informace naleznete [v tématu Uživatelská oprávnění a Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="79245-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="79245-171">Vyhledejte instalační program sady Visual Studio v počítači.</span><span class="sxs-lookup"><span data-stu-id="79245-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="79245-172">Například v počítači se systémem Windows 10 vyberte **start**a pak přejděte na písmeno **V**, kde je uvedeno jako **Instalační služba sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79245-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Otevření Instalační služby sady Visual Studio z Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="79245-174">Instalační program sady Visual Studio najdete také v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="79245-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="79245-175">Před pokračováním bude pravděpodobně nutné aktualizovat instalační program.</span><span class="sxs-lookup"><span data-stu-id="79245-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="79245-176">Pokud ano, postupujte podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="79245-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="79245-177">V instalačním programu vyhledejte edici sady Visual Studio, do které chcete přidat jazykovou sadu, a pak zvolte **Změnit**.</span><span class="sxs-lookup"><span data-stu-id="79245-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Aktualizace nebo úprava sady Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="79245-179">Pokud tlačítko **Změnit nevidíte,** ale místo toho se zobrazí **aktualizace,** je třeba před úpravou instalace aktualizovat visual studio.</span><span class="sxs-lookup"><span data-stu-id="79245-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="79245-180">Po dokončení aktualizace by se mělo zobrazit tlačítko **Změnit.**</span><span class="sxs-lookup"><span data-stu-id="79245-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="79245-181">Na kartě **Jazykové sady** vyberte nebo zrušte výběr jazyků, které chcete nainstalovat nebo odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="79245-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Karta jazykové sady Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="79245-183">Zvolte **Změnit**.</span><span class="sxs-lookup"><span data-stu-id="79245-183">Choose **Modify**.</span></span> <span data-ttu-id="79245-184">Aktualizace se spustí.</span><span class="sxs-lookup"><span data-stu-id="79245-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="79245-185">Změna nastavení jazyka v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79245-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="79245-186">Po instalaci požadovaných jazykových sad upravte nastavení sady Visual Studio tak, aby používalo jiný jazyk:</span><span class="sxs-lookup"><span data-stu-id="79245-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="79245-187">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79245-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="79245-188">V počátečním okně zvolte **Pokračovat bez kódu**.</span><span class="sxs-lookup"><span data-stu-id="79245-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="79245-189">Na řádku nabídek vyberte**Možnosti** **nástrojů** > .</span><span class="sxs-lookup"><span data-stu-id="79245-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="79245-190">Otevře se dialogové okno Možnosti.</span><span class="sxs-lookup"><span data-stu-id="79245-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="79245-191">V uzlu **Prostředí** zvolte **Mezinárodní nastavení**.</span><span class="sxs-lookup"><span data-stu-id="79245-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="79245-192">V rozevíracím panelu **Jazyk** vyberte požadovaný jazyk.</span><span class="sxs-lookup"><span data-stu-id="79245-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="79245-193">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="79245-193">Choose **OK**.</span></span>

1. <span data-ttu-id="79245-194">Dialogové okno informuje, že je nutné restartovat visual studio pro změny se projeví.</span><span class="sxs-lookup"><span data-stu-id="79245-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="79245-195">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="79245-195">Choose **OK**.</span></span>

1. <span data-ttu-id="79245-196">Restartujte sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79245-196">Restart Visual Studio.</span></span>

<span data-ttu-id="79245-197">Poté by měl váš technologie IntelliSense fungovat očekávaným způsobem při otevření projektu .NET Core, který se zaměřuje na verzi právě nainstalovaných souborů IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="79245-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="79245-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="79245-198">See also</span></span>

- [<span data-ttu-id="79245-199">Technologie IntelliSense v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79245-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
