---
title: 'Postupy: Instalace a konfigurace aktivačních komponent WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: cd792c2c26898cd3dfd7b52d865fa83636c426eb
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253970"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="1811d-102">Postupy: Instalace a konfigurace aktivačních komponent WCF</span><span class="sxs-lookup"><span data-stu-id="1811d-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="1811d-103">Toto téma popisuje kroky potřebné k nastavení služby Aktivace procesu Windows (WAS) na [!INCLUDE[wv](../../../../includes/wv-md.md)] k hostování Windows Communication Foundation (WCF) služby, které nekomunikují přes protokol HTTP síťových protokolů.</span><span class="sxs-lookup"><span data-stu-id="1811d-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="1811d-104">Následující oddíly popisují kroky pro tuto konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="1811d-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="1811d-105">Nainstalovat (nebo potvrďte instalaci) aktivačních komponent WCF.</span><span class="sxs-lookup"><span data-stu-id="1811d-105">Install (or confirm the installation of) the WCF activation components.</span></span>  
  
-   <span data-ttu-id="1811d-106">Konfigurace WAS pro podporu protokolu jiným protokolem než HTTP.</span><span class="sxs-lookup"><span data-stu-id="1811d-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="1811d-107">Následující postup umožňuje konfiguraci [!INCLUDE[wv](../../../../includes/wv-md.md)] pro Aktivace protokolem TCP.</span><span class="sxs-lookup"><span data-stu-id="1811d-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="1811d-108">Po instalaci a konfiguraci služby WAS, naleznete v tématu [postupy: hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) postupy k vytvoření služby WCF, který zpřístupňuje koncový bod jiným protokolem než HTTP, která používá WAS.</span><span class="sxs-lookup"><span data-stu-id="1811d-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="1811d-109">Chcete-li nainstalovat jiným protokolem než HTTP aktivačních komponent WCF</span><span class="sxs-lookup"><span data-stu-id="1811d-109">To install the WCF non-HTTP activation components</span></span>  
  
1.  <span data-ttu-id="1811d-110">Klikněte na tlačítko **Start** tlačítko a pak klikněte na tlačítko **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="1811d-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="1811d-111">Klikněte na tlačítko **programy**a potom klikněte na tlačítko **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="1811d-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="1811d-112">Na **úlohy** nabídky, klikněte na tlačítko **Windows zapnout nebo vypnout funkce**.</span><span class="sxs-lookup"><span data-stu-id="1811d-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4.  <span data-ttu-id="1811d-113">Najít [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] uzlu, vyberte a pak ji rozbalte.</span><span class="sxs-lookup"><span data-stu-id="1811d-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5.  <span data-ttu-id="1811d-114">Vyberte **aktivačních komponent WCF jiným protokolem než Http** pole a uložení nastavení.</span><span class="sxs-lookup"><span data-stu-id="1811d-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="1811d-115">Konfigurace WAS pro podporu Aktivace protokolem TCP</span><span class="sxs-lookup"><span data-stu-id="1811d-115">To configure the WAS to support TCP activation</span></span>  
  
1.  <span data-ttu-id="1811d-116">Kvůli podpoře aktivace net.tcp, musíte ji nejdřív svázat výchozí webový server k portu net.tcp.</span><span class="sxs-lookup"><span data-stu-id="1811d-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="1811d-117">Můžete to provést pomocí Appcmd.exe, která se instaluje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] sada nástrojů pro správu.</span><span class="sxs-lookup"><span data-stu-id="1811d-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="1811d-118">V okně příkazového řádku na úrovni správce spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="1811d-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1811d-119">Tento příkaz je jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="1811d-119">This command is a single line of text.</span></span> <span data-ttu-id="1811d-120">Tento příkaz přidá vazbu webu net.tcp výchozí webový server naslouchá na portu TCP 808 s názvem hostitele.</span><span class="sxs-lookup"><span data-stu-id="1811d-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2.  <span data-ttu-id="1811d-121">Přestože všechny aplikace v rámci lokality sdílejí společné vazby net.tcp, každá aplikace můžete povolit podporu net.tcp jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="1811d-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="1811d-122">Pokud chcete povolit net.tcp pro aplikaci, spusťte následující příkaz z příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="1811d-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1811d-123">Tento příkaz je jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="1811d-123">This command is a single line of text.</span></span> <span data-ttu-id="1811d-124">Tento příkaz povolí /\<*aplikace WCF*> aplikace přistupovat pomocí obou `http://localhost/<WCF Application>` a `net.tcp://localhost/<WCF Application>`.</span><span class="sxs-lookup"><span data-stu-id="1811d-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>
  
     <span data-ttu-id="1811d-125">Odeberte net.tcp vazby webu, kterou jste přidali pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="1811d-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="1811d-126">V zájmu usnadnění práce následující dva kroky jsou implementovány v dávkovém souboru volá RemoveNetTcpSiteBinding.cmd nachází v adresáři ukázkové.</span><span class="sxs-lookup"><span data-stu-id="1811d-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="1811d-127">Odeberte net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu v okně příkazového řádku úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="1811d-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="1811d-128">Tento příkaz je jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="1811d-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="1811d-129">Odeberte vazbu webu net.tcp spuštěním následujícího příkazu v okně příkazového řádku se zvýšenými oprávněními:</span><span class="sxs-lookup"><span data-stu-id="1811d-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="1811d-130">Tento příkaz je jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="1811d-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="1811d-131">Chcete-li odebrat ze seznamu povolených protokolů net.tcp</span><span class="sxs-lookup"><span data-stu-id="1811d-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1.  <span data-ttu-id="1811d-132">Chcete-li odebrat ze seznamu povolených protokolů net.tcp, spusťte následující příkaz v okně příkazového řádku úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="1811d-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1811d-133">Tento příkaz je jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="1811d-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="1811d-134">Chcete-li odebrat vazbu webu net.tcp</span><span class="sxs-lookup"><span data-stu-id="1811d-134">To remove the net.tcp site binding</span></span>  
  
1.  <span data-ttu-id="1811d-135">Odeberte lokalitu net.tcp vazby spusťte následující příkaz v okně příkazového řádku úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="1811d-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1811d-136">Tento příkaz je jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="1811d-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1811d-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="1811d-137">See Also</span></span>  
 [<span data-ttu-id="1811d-138">Aktivace protokolu TCP</span><span class="sxs-lookup"><span data-stu-id="1811d-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="1811d-139">Aktivace služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="1811d-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [<span data-ttu-id="1811d-140">Aktivace pojmenovaného kanálu</span><span class="sxs-lookup"><span data-stu-id="1811d-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [<span data-ttu-id="1811d-141">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="1811d-141">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
