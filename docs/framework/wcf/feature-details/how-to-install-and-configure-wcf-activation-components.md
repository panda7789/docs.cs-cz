---
title: 'Postupy: Instalace a konfigurace aktivačních komponent WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: f362bd1e4a644488e85cdeca674d46ca340bde05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491745"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="f972e-102">Postupy: Instalace a konfigurace aktivačních komponent WCF</span><span class="sxs-lookup"><span data-stu-id="f972e-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="f972e-103">Toto téma popisuje kroky potřebné k nastavení aktivační služba procesů systému Windows (WAS) na [!INCLUDE[wv](../../../../includes/wv-md.md)] k hostování Windows Communication Foundation (WCF) služeb, které není komunikaci pomocí protokolu HTTP síťových protokolů.</span><span class="sxs-lookup"><span data-stu-id="f972e-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="f972e-104">Následující oddíly popisují kroky pro tuto konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="f972e-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="f972e-105">Nainstalovat (nebo potvrďte instalaci) aktivačních komponent WCF.</span><span class="sxs-lookup"><span data-stu-id="f972e-105">Install (or confirm the installation of) the WCF activation components.</span></span>  
  
-   <span data-ttu-id="f972e-106">Konfigurace WAS pro podporu protokolu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="f972e-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="f972e-107">Následující postup umožňuje konfiguraci [!INCLUDE[wv](../../../../includes/wv-md.md)] pro Aktivace protokolem TCP.</span><span class="sxs-lookup"><span data-stu-id="f972e-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="f972e-108">Po instalaci a konfiguraci služby WAS, najdete v části [postupy: hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) postupy k vytvoření služby WCF, který zveřejňuje jiným protokolem než HTTP koncový bod, který využívá WAS.</span><span class="sxs-lookup"><span data-stu-id="f972e-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="f972e-109">Chcete-li nainstalovat komponenty Aktivace jiným protokolem než HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="f972e-109">To install the WCF non-HTTP activation components</span></span>  
  
1.  <span data-ttu-id="f972e-110">Klikněte **spustit** tlačítko a potom klikněte na **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="f972e-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="f972e-111">Klikněte na tlačítko **programy**a potom klikněte na **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="f972e-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="f972e-112">Na **úlohy** nabídky, klikněte na tlačítko **Windows zapnout nebo vypnout funkce**.</span><span class="sxs-lookup"><span data-stu-id="f972e-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4.  <span data-ttu-id="f972e-113">Najít [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] uzlu, vyberte a potom rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="f972e-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5.  <span data-ttu-id="f972e-114">Vyberte **součásti Aktivace jiným protokolem než Http WCF** pole a uložte nastavení.</span><span class="sxs-lookup"><span data-stu-id="f972e-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="f972e-115">Konfigurace WAS pro podporu Aktivace protokolem TCP</span><span class="sxs-lookup"><span data-stu-id="f972e-115">To configure the WAS to support TCP activation</span></span>  
  
1.  <span data-ttu-id="f972e-116">Kvůli podpoře aktivace net.tcp, nutné ji nejdřív svázat výchozí web na net.tcp port.</span><span class="sxs-lookup"><span data-stu-id="f972e-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="f972e-117">Můžete to provést pomocí Appcmd.exe, která se instaluje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] sada nástrojů pro správu.</span><span class="sxs-lookup"><span data-stu-id="f972e-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="f972e-118">V okně příkazového řádku na úrovni správce spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="f972e-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f972e-119">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="f972e-119">This command is a single line of text.</span></span> <span data-ttu-id="f972e-120">Tento příkaz přidá vazbu net.tcp lokality na výchozí web naslouchá na portu TCP 808 s libovolným názvem hostitele.</span><span class="sxs-lookup"><span data-stu-id="f972e-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2.  <span data-ttu-id="f972e-121">Přestože všechny aplikace v rámci lokality sdílet běžné net.tcp vazbu, každá aplikace můžete povolit podporu net.tcp jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="f972e-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="f972e-122">Pokud chcete povolit net.tcp pro aplikaci, spusťte následující příkaz z příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="f972e-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f972e-123">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="f972e-123">This command is a single line of text.</span></span> <span data-ttu-id="f972e-124">Tento příkaz povolí nebo\<*aplikace WCF*> přístup k aplikaci lze pomocí obou http://localhost  */ \<aplikace WCF >* a net.tcp:// localhost nebo*\<aplikace WCF >*.</span><span class="sxs-lookup"><span data-stu-id="f972e-124">This command enables the /\<*WCF Application*> application to be accessed using both http://localhost*/\<WCF Application>* and net.tcp://localhost/*\<WCF Application>*.</span></span>  
  
     <span data-ttu-id="f972e-125">Odeberte net.tcp vazby webu, který jste přidali Tato ukázka.</span><span class="sxs-lookup"><span data-stu-id="f972e-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="f972e-126">Pro potřeby následující dva kroky jsou implementované v dávkovém souboru názvem RemoveNetTcpSiteBinding.cmd umístěný v adresáři ukázka.</span><span class="sxs-lookup"><span data-stu-id="f972e-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="f972e-127">Odeberte net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu v okně příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="f972e-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="f972e-128">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="f972e-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="f972e-129">Odeberte vazbu webu net.tcp v okno příkazového řádku se zvýšenými oprávněními spustíte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f972e-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="f972e-130">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="f972e-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="f972e-131">Chcete-li odebrat ze seznamu povolených protokolů net.tcp</span><span class="sxs-lookup"><span data-stu-id="f972e-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1.  <span data-ttu-id="f972e-132">Chcete-li odebrat net.tcp ze seznamu povolených protokolů, spusťte následující příkaz v okně příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="f972e-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f972e-133">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="f972e-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="f972e-134">Chcete-li odebrat vazby webu net.tcp</span><span class="sxs-lookup"><span data-stu-id="f972e-134">To remove the net.tcp site binding</span></span>  
  
1.  <span data-ttu-id="f972e-135">Vazba k odebrání net.tcp lokality spusťte následující příkaz v okně příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="f972e-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f972e-136">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="f972e-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f972e-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="f972e-137">See Also</span></span>  
 [<span data-ttu-id="f972e-138">Aktivace protokolu TCP</span><span class="sxs-lookup"><span data-stu-id="f972e-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="f972e-139">Aktivace služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="f972e-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [<span data-ttu-id="f972e-140">Aktivace pojmenovaného kanálu</span><span class="sxs-lookup"><span data-stu-id="f972e-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [<span data-ttu-id="f972e-141">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="f972e-141">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
