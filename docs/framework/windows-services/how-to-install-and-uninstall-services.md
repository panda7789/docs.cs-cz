---
title: "Postupy: Instalace a odinstalace služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 1fcbc8e7a84b16d244561e0cd69f8661236e63de
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-and-uninstall-services"></a><span data-ttu-id="4daf2-102">Postupy: Instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="4daf2-102">How to: Install and Uninstall Services</span></span>
<span data-ttu-id="4daf2-103">Pokud vyvíjíte služby systému Windows s použitím rozhraní .NET Framework, můžete rychle nainstalovat aplikace služby pomocí nástroje příkazového řádku, který volá InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="4daf2-103">If you’re developing a Windows Service by using the .NET Framework, you can quickly install your service application by using a command-line utility called InstallUtil.exe.</span></span> <span data-ttu-id="4daf2-104">Pokud jste vývojář kdo chce verzi služby systému Windows, uživatelé můžou instalovat a odinstalovat jste měli využívají novou technologii.</span><span class="sxs-lookup"><span data-stu-id="4daf2-104">If you’re a developer who wants to release a Windows Service that users can install and uninstall  you should use InstallShield.</span></span> <span data-ttu-id="4daf2-105">V tématu [nasazení Instalační služby systému Windows](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span><span class="sxs-lookup"><span data-stu-id="4daf2-105">See [Windows Installer Deployment](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4daf2-106">Pokud chcete odinstalovat službu z počítače, není postupujte podle kroků v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="4daf2-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="4daf2-107">Místo toho zjistit balíčky, které program nebo software nainstaloval službu a potom vyberte **přidat nebo odebrat programy** v Ovládacích panelech odinstalujte tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="4daf2-107">Instead, find out which program or software package installed the service, and then choose **Add/Remove Programs** in Control Panel to uninstall that program.</span></span> <span data-ttu-id="4daf2-108">Všimněte si, že mnoho služeb jsou nedílnou součástí systému Windows. Pokud je odstraníte, může dojít k nestabilitě systému.</span><span class="sxs-lookup"><span data-stu-id="4daf2-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="4daf2-109">Chcete-li použít kroky v tomto článku, musíte nejprve přidat instalační program služby k službě systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4daf2-109">In order to use the steps in this article, you first need to add a service installer to your Windows Service.</span></span> <span data-ttu-id="4daf2-110">V tématu [návod: vytváření Windows aplikace v Návrháři součástí služby](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="4daf2-110">See [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="4daf2-111">Projekty služby systému Windows nemůže spustit přímo z vývojovém prostředí sady Visual Studio stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="4daf2-111">Windows Service projects cannot be run directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="4daf2-112">Je to proto, že před spuštěním projektu, musí být nainstalovaná služba v projektu.</span><span class="sxs-lookup"><span data-stu-id="4daf2-112">This is because the service in the project must be installed before you can run the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="4daf2-113">Můžete spustit **Průzkumníka serveru** a ověřte, že služby byla nainstalována nebo odinstalována.</span><span class="sxs-lookup"><span data-stu-id="4daf2-113">You can launch **Server Explorer** and verify that your service has been installed or uninstalled.</span></span> <span data-ttu-id="4daf2-114">Další informace najdete v tématu Postupy: přístup a inicializaci Průzkumníka databáze Průzkumníka serveru.</span><span class="sxs-lookup"><span data-stu-id="4daf2-114">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
### <a name="to-install-your-service-manually"></a><span data-ttu-id="4daf2-115">Ruční instalace služby</span><span class="sxs-lookup"><span data-stu-id="4daf2-115">To install your service manually</span></span>  
  
1.  <span data-ttu-id="4daf2-116">V systému Windows **spustit** nabídky nebo **spustit** obrazovky, zvolte **Visual Studio** , **nástroje sady Visual Studio**, **vývojáře Příkazový řádek**.</span><span class="sxs-lookup"><span data-stu-id="4daf2-116">On the Windows **Start** menu or **Start** screen, choose **Visual Studio** , **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="4daf2-117">Zobrazí se příkazový řádek sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4daf2-117">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="4daf2-118">Přístup k adresáři, kde je umístěn kompilované spustitelný soubor vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="4daf2-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="4daf2-119">InstallUtil.exe spusťte z příkazového řádku s spustitelný soubor vašeho projektu jako parametr:</span><span class="sxs-lookup"><span data-stu-id="4daf2-119">Run InstallUtil.exe from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     <span data-ttu-id="4daf2-120">Pokud používáte příkazového řádku Visual Studia, InstallUtil.exe by měla být na cestě k systému souborů.</span><span class="sxs-lookup"><span data-stu-id="4daf2-120">If you’re using the Visual Studio command prompt, InstallUtil.exe should be on the system path.</span></span> <span data-ttu-id="4daf2-121">Pokud ne, přidejte do cesty, nebo použijte plně kvalifikovanou cestu k vyvolání ho.</span><span class="sxs-lookup"><span data-stu-id="4daf2-121">If not, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="4daf2-122">Tento nástroj je nainstalovaný s rozhraním .NET Framework, a jeho cestu `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span><span class="sxs-lookup"><span data-stu-id="4daf2-122">This tool is installed with the .NET Framework, and its path is `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span></span> <span data-ttu-id="4daf2-123">Například pro 32bitovou verzi rozhraní .NET Framework 4 nebo 4.5. \*, pokud váš instalační adresář Windows je C:\Windows, cesta je `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="4daf2-123">For example, for the 32-bit version of the .NET Framework 4 or 4.5.\*, if your Windows installation directory is C:\Windows, the path is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span> <span data-ttu-id="4daf2-124">Pro 64bitové verze rozhraní .NET Framework 4 nebo 4.5. \*, výchozí cesta je `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="4daf2-124">For the 64-bit version of the .NET Framework 4 or 4.5.\*, the default path is `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span></span>  
  
### <a name="to-uninstall-your-service-manually"></a><span data-ttu-id="4daf2-125">Chcete-li ručně odinstalovat služby</span><span class="sxs-lookup"><span data-stu-id="4daf2-125">To uninstall your service manually</span></span>  
  
1.  <span data-ttu-id="4daf2-126">V systému Windows **spustit** nabídky nebo **spustit** obrazovky, zvolte **Visual Studio**, **nástroje sady Visual Studio**, **vývojáře Příkazový řádek**.</span><span class="sxs-lookup"><span data-stu-id="4daf2-126">On the Windows **Start** menu or **Start** screen, choose **Visual Studio**, **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="4daf2-127">Zobrazí se příkazový řádek sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4daf2-127">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="4daf2-128">InstallUtil.exe spusťte z příkazového řádku s výstupem vašeho projektu jako parametr:</span><span class="sxs-lookup"><span data-stu-id="4daf2-128">Run InstallUtil.exe from the command prompt with your project's output as a parameter:</span></span>  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  <span data-ttu-id="4daf2-129">V některých případech po odstranění je spustitelný soubor pro službu, službu může být v registru.</span><span class="sxs-lookup"><span data-stu-id="4daf2-129">Sometimes, after the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="4daf2-130">V takovém případě použijte příkaz [sc delete](http://technet.microsoft.com/library/cc742045.aspx) pro odebrání položky pro službu z registru.</span><span class="sxs-lookup"><span data-stu-id="4daf2-130">In that case, use the command [sc delete](http://technet.microsoft.com/library/cc742045.aspx) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4daf2-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="4daf2-131">See Also</span></span>  
 [<span data-ttu-id="4daf2-132">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="4daf2-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="4daf2-133">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="4daf2-133">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="4daf2-134">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="4daf2-134">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="4daf2-135">Installutil.exe (instalační nástroj)</span><span class="sxs-lookup"><span data-stu-id="4daf2-135">Installutil.exe (Installer Tool)</span></span>](../../../docs/framework/tools/installutil-exe-installer-tool.md)
