---
title: Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 6e74c81aa26ba7f8d093b8b3ec52f19eb3519905
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216064"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="23663-102">Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="23663-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="23663-103">Toto téma popisuje kroky potřebné k nastavení služby Aktivace procesu Windows (WAS) v [!INCLUDE[wv](../../../../includes/wv-md.md)] k hostování Windows Communication Foundation (WCF) služby, které nekomunikují přes protokol HTTP síťových protokolů.</span><span class="sxs-lookup"><span data-stu-id="23663-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="23663-104">Následující oddíly popisují kroky pro tuto konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="23663-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="23663-105">Nainstalovat (nebo potvrďte instalaci) aktivačních komponent WCF vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="23663-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
-   <span data-ttu-id="23663-106">Vytvoření webu WAS se vazeb síťových protokolů, které chcete použít, nebo přidat novou vazbu protokolu o stávající web.</span><span class="sxs-lookup"><span data-stu-id="23663-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
-   <span data-ttu-id="23663-107">Vytvořte aplikaci pro hostování služeb a povolte tuto aplikaci používat požadované protokoly.</span><span class="sxs-lookup"><span data-stu-id="23663-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
-   <span data-ttu-id="23663-108">Vytvoření služby WCF, který zpřístupňuje koncový bod jiným protokolem než HTTP.</span><span class="sxs-lookup"><span data-stu-id="23663-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="23663-109">Konfigurace sítě s vazbami jiným protokolem než HTTP</span><span class="sxs-lookup"><span data-stu-id="23663-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="23663-110">Pro použití vazby jiným protokolem než HTTP s WAS, musí přidat vazbu webu do konfigurace WAS.</span><span class="sxs-lookup"><span data-stu-id="23663-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="23663-111">Konfigurace úložiště pro WAS je soubor applicationHost.config umístěný v adresáři %windir%\system32\inetsrv\config.</span><span class="sxs-lookup"><span data-stu-id="23663-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="23663-112">Tato konfigurace úložiště je sdílen WAS a IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="23663-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="23663-113">soubor applicationHost.config je textový soubor XML, který lze otevřít v libovolném standardního textového editoru (například Poznámkový blok).</span><span class="sxs-lookup"><span data-stu-id="23663-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="23663-114">Ale [!INCLUDE[iisver](../../../../includes/iisver-md.md)] preferovaný způsob, jak přidat vazby webu jiným protokolem než HTTP je nástroj příkazového řádku konfigurace (appcmd.exe).</span><span class="sxs-lookup"><span data-stu-id="23663-114">However, the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="23663-115">Následující příkaz přidá vazbu webu net.tcp výchozí webový server pomocí appcmd.exe (Tento příkaz je zadat jako jeden řádek).</span><span class="sxs-lookup"><span data-stu-id="23663-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="23663-116">Tento příkaz přidá novou vazbu net.tcp výchozí webový server tak, že přidáte řádku níže uvedeného souboru applicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="23663-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="23663-117">Povolení aplikace pro použití jiných protokolů než HTTP</span><span class="sxs-lookup"><span data-stu-id="23663-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="23663-118">Můžete povolit nebo zakázat jednotlivým síťovým protocolsat na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="23663-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="23663-119">Následující příkaz ukazuje, jak povolit protokoly HTTP i net.tcp pro aplikace, která běží v `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="23663-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="23663-120">Seznam Povolené protokoly je možné také nastavit v \<applicationDefaults > element konfigurace XML pro lokalitu uložené v souboru ApplicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="23663-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="23663-121">Následující kód XML ze souboru applicationHost.config znázorňuje lokality vázána na HTTP a jiných protokolů než HTTP.</span><span class="sxs-lookup"><span data-stu-id="23663-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="23663-122">Další konfigurace vyžadovaná pro podporu jiných protokolů než HTTP je vyznačeny pomocí komentářů.</span><span class="sxs-lookup"><span data-stu-id="23663-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile   
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging   
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults   
      applicationPool="DefaultAppPool"   
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="23663-123">Pokud při pokusu o aktivaci služby pomocí služby WAS Aktivace jiným protokolem než HTTP a ještě nainstalovaná a nakonfigurovaná služba WAS může se zobrazit následující chyba:</span><span class="sxs-lookup"><span data-stu-id="23663-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="23663-124">Pokud se zobrazí tato chyba, zkontrolujte WAS pro aktivace jiným protokolem než HTTP je nainstalován a nakonfigurován správně.</span><span class="sxs-lookup"><span data-stu-id="23663-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="23663-125">Další informace najdete v tématu [postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="23663-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="23663-126">Vytváření WCF službě, používá se pro aktivace jiným protokolem než HTTP</span><span class="sxs-lookup"><span data-stu-id="23663-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="23663-127">Jakmile provedete kroky instalace a konfigurace služby WAS (naleznete v tématu [postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), konfigurace služby WAS použít aktivace je podobné konfigurace služby, která je hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="23663-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="23663-128">Podrobné pokyny k vytvoření služby WCF aktivaci WAS, naleznete v tématu [postupy: hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="23663-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23663-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="23663-129">See Also</span></span>  
 [<span data-ttu-id="23663-130">Hostování v Aktivační službě procesů systému Windows</span><span class="sxs-lookup"><span data-stu-id="23663-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [<span data-ttu-id="23663-131">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="23663-131">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
