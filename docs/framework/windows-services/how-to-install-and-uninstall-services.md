---
title: 'Postupy: instalace a odinstalace služeb systému Windows'
description: Viz jak nainstalovat a odinstalovat služby systému Windows. Pokud vyvíjíte službu systému Windows s rozhraním .NET, můžete použít InstallUtil.exe nebo PowerShell.
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
ms.openlocfilehash: 5597043bb1c5af05f5f3633cba6ee6e6de1c52c1
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925602"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="f463f-104">Postupy: instalace a odinstalace služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="f463f-104">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="f463f-105">Pokud vyvíjíte službu pro Windows s .NET Framework, můžete rychle nainstalovat aplikaci služby pomocí nástroje příkazového řádku [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) nebo [PowerShellu](/powershell/scripting/overview).</span><span class="sxs-lookup"><span data-stu-id="f463f-105">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="f463f-106">Vývojáři, kteří chtějí uvolnit službu systému Windows, kterou mohou uživatelé instalovat a odinstalovat, by měli používat program InstallShield.</span><span class="sxs-lookup"><span data-stu-id="f463f-106">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="f463f-107">Další informace najdete v tématu [Vytvoření instalačního balíčku (Desktop Windows)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="f463f-107">For more information, see [Create an installer package (Windows desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

> [!WARNING]
> <span data-ttu-id="f463f-108">Pokud chcete odinstalovat službu z počítače, neprovádějte postup v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="f463f-108">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="f463f-109">Místo toho Zjistěte, který program nebo softwarový balíček službu nainstaloval, a pak zvolte možnost **aplikace** v nastavení pro odinstalaci tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="f463f-109">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="f463f-110">Všimněte si, že mnoho služeb je nedílnou součástí Windows. Pokud je odstraníte, může to způsobit nestabilitu systému.</span><span class="sxs-lookup"><span data-stu-id="f463f-110">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="f463f-111">Chcete-li použít kroky v tomto článku, musíte nejprve přidat do služby systému Windows Instalační program služby.</span><span class="sxs-lookup"><span data-stu-id="f463f-111">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="f463f-112">Další informace najdete v tématu [Návod: Vytvoření aplikace služby systému Windows](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="f463f-112">For more information, see [Walkthrough: Creating a Windows service app](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="f463f-113">Nemůžete spustit projekty služby Windows přímo z vývojového prostředí sady Visual Studio stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="f463f-113">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="f463f-114">Předtím, než můžete spustit projekt, je nutné nainstalovat službu do projektu.</span><span class="sxs-lookup"><span data-stu-id="f463f-114">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="f463f-115">Pomocí **Průzkumník serveru** můžete ověřit, že jste nainstalovali nebo odinstalovali vaši službu.</span><span class="sxs-lookup"><span data-stu-id="f463f-115">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="f463f-116">Další informace najdete v tématu [Jak používat Průzkumník serveru v aplikaci Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f463f-116">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="f463f-117">Ruční instalace služby pomocí nástroje InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="f463f-117">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="f463f-118">V nabídce **Start** vyberte adresář sady \*\*Visual Studio \<*version*> \*\* a potom vyberte \*\*Developer Command Prompt pro vs \<*version*> \*\*.</span><span class="sxs-lookup"><span data-stu-id="f463f-118">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="f463f-119">Zobrazí se Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f463f-119">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="f463f-120">Přejděte do adresáře, kde se nachází kompilovaný spustitelný soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="f463f-120">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="f463f-121">Spusťte *InstallUtil.exe* z příkazového řádku se spustitelným souborem projektu jako parametr:</span><span class="sxs-lookup"><span data-stu-id="f463f-121">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="f463f-122">Pokud používáte Developer Command Prompt pro Visual Studio, *InstallUtil.exe* by měla být v systémové cestě.</span><span class="sxs-lookup"><span data-stu-id="f463f-122">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="f463f-123">V opačném případě ji můžete přidat do cesty nebo použít úplnou cestu k jejímu vyvolání.</span><span class="sxs-lookup"><span data-stu-id="f463f-123">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="f463f-124">Tento nástroj se instaluje s .NET Framework v \*%windir%\Microsoft.NET\Framework [64] \\<framework_version \> \*.</span><span class="sxs-lookup"><span data-stu-id="f463f-124">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="f463f-125">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f463f-125">For example:</span></span>
     - <span data-ttu-id="f463f-126">Pro 32 verze .NET Framework 4 nebo 4,5 a novější, pokud je instalační adresář systému Windows *C:\Windows*, je výchozí cesta *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="f463f-126">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="f463f-127">Pro 64 verze .NET Framework 4 nebo 4,5 a novější je výchozí cesta *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="f463f-127">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="f463f-128">Ruční odinstalace služby pomocí nástroje InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="f463f-128">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="f463f-129">V nabídce **Start** vyberte adresář sady \*\*Visual Studio \<*version*> \*\* a potom vyberte \*\*Developer Command Prompt pro vs \<*version*> \*\*.</span><span class="sxs-lookup"><span data-stu-id="f463f-129">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="f463f-130">Zobrazí se Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f463f-130">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="f463f-131">Spusťte *InstallUtil.exe* z příkazového řádku s výstupem projektu jako parametr:</span><span class="sxs-lookup"><span data-stu-id="f463f-131">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="f463f-132">Po odstranění spustitelného souboru pro službu může být služba v registru stále k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f463f-132">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="f463f-133">V takovém případě pomocí příkazu [sc delete](/windows-server/administration/windows-commands/sc-delete) odeberte položku služby z registru.</span><span class="sxs-lookup"><span data-stu-id="f463f-133">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="f463f-134">Ruční instalace služby pomocí PowerShellu</span><span class="sxs-lookup"><span data-stu-id="f463f-134">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="f463f-135">V nabídce **Start** vyberte adresář **Windows PowerShell** a pak vyberte **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f463f-135">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="f463f-136">Přejděte do adresáře, kde se nachází kompilovaný spustitelný soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="f463f-136">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="f463f-137">Spusťte rutinu [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) s výstupem vašeho projektu a názvem služby jako parametry:</span><span class="sxs-lookup"><span data-stu-id="f463f-137">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="f463f-138">Ruční odinstalace služby pomocí PowerShellu</span><span class="sxs-lookup"><span data-stu-id="f463f-138">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="f463f-139">V nabídce **Start** vyberte adresář **Windows PowerShell** a pak vyberte **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f463f-139">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="f463f-140">Spusťte rutinu [**remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) s názvem vaší služby jako parametr:</span><span class="sxs-lookup"><span data-stu-id="f463f-140">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="f463f-141">Po odstranění spustitelného souboru pro službu může být služba v registru stále k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f463f-141">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="f463f-142">V takovém případě pomocí příkazu [sc delete](/windows-server/administration/windows-commands/sc-delete) odeberte položku služby z registru.</span><span class="sxs-lookup"><span data-stu-id="f463f-142">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="f463f-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="f463f-143">See also</span></span>

- [<span data-ttu-id="f463f-144">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="f463f-144">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="f463f-145">Postupy: vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="f463f-145">How to: Create Windows services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="f463f-146">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="f463f-146">How to: Add installers to your service application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="f463f-147">Installutil.exe (instalační nástroj)</span><span class="sxs-lookup"><span data-stu-id="f463f-147">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
