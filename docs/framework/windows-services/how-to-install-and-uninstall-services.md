---
title: 'Postup: Instalace a odinstalace služeb systému Windows'
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 8937ef8b4007253b06444e59b292395084e4df2f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607916"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="63f7f-102">Postup: Instalace a odinstalace služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="63f7f-102">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="63f7f-103">Pokud vyvíjíte službu Windows s rozhraním .NET Framework, můžete aplikaci služby rychle nainstalovat pomocí nástroje příkazového řádku [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) nebo [prostředí PowerShell](/powershell/scripting/overview).</span><span class="sxs-lookup"><span data-stu-id="63f7f-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="63f7f-104">Vývojáři, kteří chtějí uvolnit službu systému Windows, kterou mohou uživatelé nainstalovat a odinstalovat, by měli používat program InstallShield.</span><span class="sxs-lookup"><span data-stu-id="63f7f-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="63f7f-105">Další informace naleznete [v tématu Vytvoření balíčku instalačního programu (plocha systému Windows).](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)</span><span class="sxs-lookup"><span data-stu-id="63f7f-105">For more information, see [Create an installer package (Windows desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

> [!WARNING]
> <span data-ttu-id="63f7f-106">Pokud chcete odinstalovat službu z počítače, nepostupujte podle pokynů v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="63f7f-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="63f7f-107">Místo toho zjistěte, který program nebo softwarový balíček službu nainstaloval, a pak v nastavení odinstalujte tento program výběrem **možnosti Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="63f7f-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="63f7f-108">Všimněte si, že mnoho služeb jsou nedílnou součástí systému Windows; Pokud je odeberete, může dojít k nestabilitě systému.</span><span class="sxs-lookup"><span data-stu-id="63f7f-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="63f7f-109">Chcete-li použít postup uvedený v tomto článku, musíte nejprve přidat instalační službu služby do služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="63f7f-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="63f7f-110">Další informace naleznete [v tématu Návod: Vytvoření aplikace služby Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="63f7f-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="63f7f-111">Projekty služeb systému Windows nelze spustit přímo z vývojového prostředí sady Visual Studio stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="63f7f-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="63f7f-112">Před spuštěním projektu je nutné nainstalovat službu v projektu.</span><span class="sxs-lookup"><span data-stu-id="63f7f-112">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="63f7f-113">**Pomocí Průzkumníka serveru** můžete ověřit, zda jste službu nainstalovali nebo odinstalovali.</span><span class="sxs-lookup"><span data-stu-id="63f7f-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="63f7f-114">Další informace naleznete v tématu [Použití Průzkumníka serveru v sadě Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="63f7f-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="63f7f-115">Ruční instalace služby pomocí nástroje InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="63f7f-115">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="63f7f-116">V nabídce **Start** vyberte adresář \*\* \< *verze* > sady Visual Studio\*\* a pak vyberte **příkazový řádek pro vývojáře pro \< *verzi*>VS**.</span><span class="sxs-lookup"><span data-stu-id="63f7f-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="63f7f-117">Zobrazí se příkazový řádek vývojáře pro visual studio.</span><span class="sxs-lookup"><span data-stu-id="63f7f-117">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="63f7f-118">Získejte přístup k adresáři, ve kterém je umístěn zkompilovaný spustitelný soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="63f7f-118">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="63f7f-119">*Spusťte soubor InstallUtil.exe* z příkazového řádku s spustitelným souborem projektu jako parametrem:</span><span class="sxs-lookup"><span data-stu-id="63f7f-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="63f7f-120">Pokud používáte příkazový řádek pro vývojáře pro Visual Studio, *installutil.exe* by měl být na systémové cestě.</span><span class="sxs-lookup"><span data-stu-id="63f7f-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="63f7f-121">V opačném případě jej můžete přidat do cesty nebo ji vyvolat pomocí plně kvalifikované cesty.</span><span class="sxs-lookup"><span data-stu-id="63f7f-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="63f7f-122">Tento nástroj je nainstalován s rozhraním .NET Framework v *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span><span class="sxs-lookup"><span data-stu-id="63f7f-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="63f7f-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="63f7f-123">For example:</span></span>
     - <span data-ttu-id="63f7f-124">Pokud je instalační adresář systému Windows *C:\Windows,* je v 32bitové verzi rozhraní .NET Framework 4 nebo 4.5 a novějších výchozí cesta *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="63f7f-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="63f7f-125">Pro 64bitovou verzi rozhraní .NET Framework 4 nebo 4.5 a novější je výchozí cesta *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="63f7f-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="63f7f-126">Odinstalace služby ručně pomocí nástroje InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="63f7f-126">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="63f7f-127">V nabídce **Start** vyberte adresář \*\* \< *verze* > sady Visual Studio\*\* a pak vyberte **příkazový řádek pro vývojáře pro \< *verzi*>VS**.</span><span class="sxs-lookup"><span data-stu-id="63f7f-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="63f7f-128">Zobrazí se příkazový řádek vývojáře pro visual studio.</span><span class="sxs-lookup"><span data-stu-id="63f7f-128">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="63f7f-129">*Spusťte soubor InstallUtil.exe* z příkazového řádku s výstupem projektu jako parametrem:</span><span class="sxs-lookup"><span data-stu-id="63f7f-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="63f7f-130">Po odstranění spustitelného souboru služby může být služba stále přítomna v registru.</span><span class="sxs-lookup"><span data-stu-id="63f7f-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="63f7f-131">V takovém případě odeberte položku služby z registru pomocí příkazu [sc delete.](/windows-server/administration/windows-commands/sc-delete)</span><span class="sxs-lookup"><span data-stu-id="63f7f-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="63f7f-132">Ruční instalace služby pomocí PowerShellu</span><span class="sxs-lookup"><span data-stu-id="63f7f-132">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="63f7f-133">V nabídce **Start** vyberte adresář **prostředí Windows PowerShell** a pak vyberte **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="63f7f-133">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="63f7f-134">Získejte přístup k adresáři, ve kterém je umístěn zkompilovaný spustitelný soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="63f7f-134">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="63f7f-135">Spusťte rutinu [**Nové služby**](/powershell/module/microsoft.powershell.management/new-service) s výstupem projektu a názvem služby jako parametry:</span><span class="sxs-lookup"><span data-stu-id="63f7f-135">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="63f7f-136">Odinstalace služby ručně pomocí prostředí PowerShell</span><span class="sxs-lookup"><span data-stu-id="63f7f-136">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="63f7f-137">V nabídce **Start** vyberte adresář **prostředí Windows PowerShell** a pak vyberte **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="63f7f-137">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="63f7f-138">Spusťte rutinu [**Odebrat službu**](/powershell/module/microsoft.powershell.management/remove-service) s názvem služby jako parametrem:</span><span class="sxs-lookup"><span data-stu-id="63f7f-138">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="63f7f-139">Po odstranění spustitelného souboru služby může být služba stále přítomna v registru.</span><span class="sxs-lookup"><span data-stu-id="63f7f-139">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="63f7f-140">V takovém případě odeberte položku služby z registru pomocí příkazu [sc delete.](/windows-server/administration/windows-commands/sc-delete)</span><span class="sxs-lookup"><span data-stu-id="63f7f-140">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="63f7f-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="63f7f-141">See also</span></span>

- [<span data-ttu-id="63f7f-142">Úvod do aplikací služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="63f7f-142">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="63f7f-143">Postup: Vytvoření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="63f7f-143">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="63f7f-144">Postup: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="63f7f-144">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="63f7f-145">Installutil.exe (instalační nástroj)</span><span class="sxs-lookup"><span data-stu-id="63f7f-145">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
