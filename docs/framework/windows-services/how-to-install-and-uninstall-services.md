---
title: 'Postupy: Instalace a odinstalace služeb Windows'
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
ms.openlocfilehash: 0119fee443aafd1d4215260d2cf42cec9f7eba74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914078"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="a655a-102">Postupy: Instalace a odinstalace služeb Windows</span><span class="sxs-lookup"><span data-stu-id="a655a-102">How to: Install and uninstall Windows services</span></span>
<span data-ttu-id="a655a-103">Pokud vytváříte službu Windows s použitím rozhraní .NET Framework, můžete rychle nainstalovat aplikaci služby pomocí [ *InstallUtil.exe* ](../tools/installutil-exe-installer-tool.md) nástroj příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a655a-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility.</span></span> <span data-ttu-id="a655a-104">Vývojáři, kteří chtějí vydání služby Windows, které mohou uživatelé nainstalovat a odinstalovat používali InstallShield.</span><span class="sxs-lookup"><span data-stu-id="a655a-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="a655a-105">Další informace najdete v tématu [vytvoření instalačního balíčku (Windows klient)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span><span class="sxs-lookup"><span data-stu-id="a655a-105">For more information, see [Create an installer package (Windows client)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>
  
> [!WARNING]
>  <span data-ttu-id="a655a-106">Pokud chcete z počítače odinstalovat službu, není postupujte podle kroků v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="a655a-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="a655a-107">Místo toho zjistit službu nainstalované balíčky, které program nebo software a pak zvolte **aplikace** v nastavení k odinstalaci tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="a655a-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="a655a-108">Všimněte si, že mnoho služeb jsou nedílnou součástí Windows; Pokud je odstraníte, může způsobit nestabilitu systému.</span><span class="sxs-lookup"><span data-stu-id="a655a-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="a655a-109">Pokud chcete použít kroky v tomto článku, musíte nejprve přidat instalační program služby do služby Windows.</span><span class="sxs-lookup"><span data-stu-id="a655a-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="a655a-110">Další informace najdete v tématu [názorný postup: Vytvoření aplikace služby Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a655a-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="a655a-111">Projekty služeb Windows nelze spustit přímo z vývojového prostředí sady Visual Studio stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="a655a-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="a655a-112">Předtím, než spustíte projekt, je nutné nainstalovat službu v projektu.</span><span class="sxs-lookup"><span data-stu-id="a655a-112">Before you can run the project, you must install the service in the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="a655a-113">Můžete použít **Průzkumníka serveru** k ověření, že jste nainstalována nebo odinstalována vaší služby.</span><span class="sxs-lookup"><span data-stu-id="a655a-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="a655a-114">Další informace najdete v tématu [použití Průzkumníku serveru v sadě Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="a655a-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>
  
### <a name="install-your-service-manually"></a><span data-ttu-id="a655a-115">Ruční instalace služby</span><span class="sxs-lookup"><span data-stu-id="a655a-115">Install your service manually</span></span>  
  
1. <span data-ttu-id="a655a-116">Z **Start** nabídku, vyberte **sady Visual Studio \< *verze* >**  adresář a potom vyberte **Developer Command Prompt pro VS \< *verze*>**.</span><span class="sxs-lookup"><span data-stu-id="a655a-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>
  
     <span data-ttu-id="a655a-117">Zobrazí se příkazový řádek pro vývojáře pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a655a-117">The Developer Command Prompt for Visual Studio appears.</span></span> 
  
2. <span data-ttu-id="a655a-118">Přístup k adresáři, kde se nachází zkompilovaný spustitelný soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="a655a-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3. <span data-ttu-id="a655a-119">Spustit *InstallUtil.exe* příkazovém řádku s projektem spustitelného souboru jako parametr:</span><span class="sxs-lookup"><span data-stu-id="a655a-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```console
    installutil <yourproject>.exe  
    ```  

     <span data-ttu-id="a655a-120">Pokud používáte Developer Command Prompt pro sadu Visual Studio *InstallUtil.exe* by měly být v systémové cestě.</span><span class="sxs-lookup"><span data-stu-id="a655a-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="a655a-121">V opačném případě můžete přidat do cesty nebo použijte plně kvalifikovanou cestu k vyvolání jeho.</span><span class="sxs-lookup"><span data-stu-id="a655a-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="a655a-122">Tento nástroj je nainstalován pomocí rozhraní .NET Framework v *% WINDIR%\Microsoft.NET\Framework[64]\\< framework_version >*.</span><span class="sxs-lookup"><span data-stu-id="a655a-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version>*.</span></span>
     
     <span data-ttu-id="a655a-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a655a-123">For example:</span></span>
     - <span data-ttu-id="a655a-124">Pro 32bitové verze rozhraní .NET Framework 4 nebo 4.5 nebo novější, pokud je váš instalační adresář Windows *C:\Windows*, výchozí cesta je *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="a655a-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="a655a-125">Pro 64bitové verze rozhraní .NET Framework 4 nebo 4.5 nebo novější, výchozí cesta je *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="a655a-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>
  
### <a name="uninstall-your-service-manually"></a><span data-ttu-id="a655a-126">Ruční odinstalování služby</span><span class="sxs-lookup"><span data-stu-id="a655a-126">Uninstall your service manually</span></span>  
  
1. <span data-ttu-id="a655a-127">Z **Start** nabídku, vyberte **sady Visual Studio \< *verze* >**  adresář a potom vyberte **Developer Command Prompt pro VS \< *verze*>**.</span><span class="sxs-lookup"><span data-stu-id="a655a-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>
  
     <span data-ttu-id="a655a-128">Zobrazí se příkazový řádek pro vývojáře pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a655a-128">The Developer Command Prompt for Visual Studio appears.</span></span>  
  
2. <span data-ttu-id="a655a-129">Spustit *InstallUtil.exe* z příkazového řádku s výstupy projektu jako parametr:</span><span class="sxs-lookup"><span data-stu-id="a655a-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>  
  
    ```console  
    installutil /u <yourproject>.exe  
    ```  
  
3. <span data-ttu-id="a655a-130">Služba může být v registru po odstranění spustitelný soubor pro službu.</span><span class="sxs-lookup"><span data-stu-id="a655a-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="a655a-131">Pokud je to tento případ, použijte příkaz [sc delete](/windows-server/administration/windows-commands/sc-delete) pro odebrání položky služby z registru.</span><span class="sxs-lookup"><span data-stu-id="a655a-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a655a-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a655a-132">See also</span></span>

- [<span data-ttu-id="a655a-133">Úvod do aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="a655a-133">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="a655a-134">Postupy: Vytvoření služeb Windows</span><span class="sxs-lookup"><span data-stu-id="a655a-134">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="a655a-135">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="a655a-135">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="a655a-136">InstallUtil.exe (instalační nástroj)</span><span class="sxs-lookup"><span data-stu-id="a655a-136">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
