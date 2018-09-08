---
title: 'Postupy: Instalace a odinstalace služeb'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
manager: douge
ms.openlocfilehash: 9d8e84280b5821f8d8df36694198bd85fb8470d4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44175832"
---
# <a name="how-to-install-and-uninstall-services"></a><span data-ttu-id="0cbb9-102">Postupy: Instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="0cbb9-102">How to: Install and Uninstall Services</span></span>
<span data-ttu-id="0cbb9-103">Vyvíjíte služby Windows s použitím rozhraní .NET Framework, můžete rychle nainstalovat aplikaci služby pomocí nástroje příkazového řádku InstallUtil.exe volána.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-103">If you’re developing a Windows Service by using the .NET Framework, you can quickly install your service application by using a command-line utility called InstallUtil.exe.</span></span> <span data-ttu-id="0cbb9-104">Pokud jste vývojář, kdo chce vydání služby Windows, mohou uživatelé nainstalovat a odinstalovat jste používali InstallShield.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-104">If you’re a developer who wants to release a Windows Service that users can install and uninstall  you should use InstallShield.</span></span> <span data-ttu-id="0cbb9-105">Zobrazit [nasazení Instalační služby systému Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span><span class="sxs-lookup"><span data-stu-id="0cbb9-105">See [Windows Installer Deployment](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0cbb9-106">Pokud chcete z počítače odinstalovat službu, není postupujte podle kroků v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="0cbb9-107">Místo toho zjistit službu nainstalované balíčky, které program nebo software a pak zvolte **přidat nebo odebrat programy** v Ovládacích panelech odinstalujte tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-107">Instead, find out which program or software package installed the service, and then choose **Add/Remove Programs** in Control Panel to uninstall that program.</span></span> <span data-ttu-id="0cbb9-108">Všimněte si, že mnoho služeb jsou nedílnou součástí Windows; Pokud je odstraníte, může způsobit nestabilitu systému.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="0cbb9-109">Chcete-li použít postup v tomto článku, musíte nejprve přidat instalační program služby do služby Windows.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-109">In order to use the steps in this article, you first need to add a service installer to your Windows Service.</span></span> <span data-ttu-id="0cbb9-110">Zobrazit [návod: vytváření Windows aplikace v Návrháři součástí služby](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="0cbb9-110">See [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="0cbb9-111">Projekty služeb Windows nelze spustit přímo z vývojového prostředí sady Visual Studio stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-111">Windows Service projects cannot be run directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="0cbb9-112">Je to proto musí být nainstalována služba v projektu, abyste mohli spustit projekt.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-112">This is because the service in the project must be installed before you can run the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="0cbb9-113">Můžete spustit **Průzkumníka serveru** a ověřte, zda má vaše služba nainstalovat nebo odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-113">You can launch **Server Explorer** and verify that your service has been installed or uninstalled.</span></span> <span data-ttu-id="0cbb9-114">Další informace najdete v tématu Postupy: přístup a inicializace Průzkumníka serveru Průzkumníka databáze.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-114">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
### <a name="to-install-your-service-manually"></a><span data-ttu-id="0cbb9-115">Ruční instalace služby</span><span class="sxs-lookup"><span data-stu-id="0cbb9-115">To install your service manually</span></span>  
  
1.  <span data-ttu-id="0cbb9-116">V Windows **Start** nabídky nebo **Start** obrazovce **sady Visual Studio** , **Visual Studio Tools**, **pro vývojáře Příkazový řádek**.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-116">On the Windows **Start** menu or **Start** screen, choose **Visual Studio** , **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="0cbb9-117">Zobrazí se příkazový řádek sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-117">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="0cbb9-118">Přístup k adresáři, kde se nachází zkompilovaný spustitelný soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="0cbb9-119">Spusťte InstallUtil.exe z příkazového řádku s projektem spustitelného souboru jako parametru:</span><span class="sxs-lookup"><span data-stu-id="0cbb9-119">Run InstallUtil.exe from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     <span data-ttu-id="0cbb9-120">Pokud používáte příkazový řádek sady Visual Studio, InstallUtil.exe by měla být v systémové cestě.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-120">If you’re using the Visual Studio command prompt, InstallUtil.exe should be on the system path.</span></span> <span data-ttu-id="0cbb9-121">Pokud ne, můžete ho přidat do cesty nebo použijte plně kvalifikovanou cestu k vyvolání ho.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-121">If not, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="0cbb9-122">Tento nástroj je nainstalován pomocí rozhraní .NET Framework a je jeho cesta `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-122">This tool is installed with the .NET Framework, and its path is `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span></span> <span data-ttu-id="0cbb9-123">Například pro 32bitovou verzi rozhraní .NET Framework 4 nebo 4.5. \*, pokud váš instalační adresář Windows C:\Windows, cesta je `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-123">For example, for the 32-bit version of the .NET Framework 4 or 4.5.\*, if your Windows installation directory is C:\Windows, the path is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span> <span data-ttu-id="0cbb9-124">Pro 64bitové verze rozhraní .NET Framework 4 nebo 4.5. \*, výchozí cesta je `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-124">For the 64-bit version of the .NET Framework 4 or 4.5.\*, the default path is `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span></span>  
  
### <a name="to-uninstall-your-service-manually"></a><span data-ttu-id="0cbb9-125">Ruční odinstalování služby</span><span class="sxs-lookup"><span data-stu-id="0cbb9-125">To uninstall your service manually</span></span>  
  
1.  <span data-ttu-id="0cbb9-126">V Windows **Start** nabídky nebo **Start** obrazovce **sady Visual Studio**, **Visual Studio Tools**, **pro vývojáře Příkazový řádek**.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-126">On the Windows **Start** menu or **Start** screen, choose **Visual Studio**, **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="0cbb9-127">Zobrazí se příkazový řádek sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-127">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="0cbb9-128">Spusťte InstallUtil.exe z příkazového řádku s výstupy projektu jako parametr:</span><span class="sxs-lookup"><span data-stu-id="0cbb9-128">Run InstallUtil.exe from the command prompt with your project's output as a parameter:</span></span>  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  <span data-ttu-id="0cbb9-129">V některých případech po odstranění spustitelný soubor pro službu služby může být v registru.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-129">Sometimes, after the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="0cbb9-130">V takovém případě použijte příkaz [sc delete](https://technet.microsoft.com/library/cc742045.aspx) pro odebrání položky služby z registru.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-130">In that case, use the command [sc delete](https://technet.microsoft.com/library/cc742045.aspx) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cbb9-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cbb9-131">See Also</span></span>  
 [<span data-ttu-id="0cbb9-132">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="0cbb9-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="0cbb9-133">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="0cbb9-133">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="0cbb9-134">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="0cbb9-134">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="0cbb9-135">Installutil.exe (instalační nástroj)</span><span class="sxs-lookup"><span data-stu-id="0cbb9-135">Installutil.exe (Installer Tool)</span></span>](../../../docs/framework/tools/installutil-exe-installer-tool.md)
