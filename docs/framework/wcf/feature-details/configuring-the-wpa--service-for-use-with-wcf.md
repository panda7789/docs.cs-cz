---
title: Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 5533393f759408002b83ba8ff485ba8229e921dd
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964635"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="a8d46-102">Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a8d46-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="a8d46-103">Toto téma popisuje kroky potřebné k nastavení aktivační služby procesů systému Windows (označované také jako WAS) ve Windows Vista na hostování služeb Windows Communication Foundation (WCF), které nekomunikují přes síťové protokoly HTTP.</span><span class="sxs-lookup"><span data-stu-id="a8d46-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="a8d46-104">Následující části popisují kroky pro tuto konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="a8d46-104">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="a8d46-105">Nainstalujte (nebo potvrďte instalaci produktu) požadované komponenty aktivace WCF.</span><span class="sxs-lookup"><span data-stu-id="a8d46-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="a8d46-106">Vytvořte lokalitu s použitím vazeb síťových protokolů, které chcete použít, nebo přidejte novou vazbu protokolu k existující lokalitě.</span><span class="sxs-lookup"><span data-stu-id="a8d46-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="a8d46-107">Vytvořte aplikaci pro hostování služeb a povolte, aby tato aplikace používala požadované síťové protokoly.</span><span class="sxs-lookup"><span data-stu-id="a8d46-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="a8d46-108">Sestavte službu WCF, která zveřejňuje koncový bod jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="a8d46-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="a8d46-109">Konfigurace lokality s vazbami jiného typu než HTTP</span><span class="sxs-lookup"><span data-stu-id="a8d46-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="a8d46-110">Chcete-li použít vazbu jiného typu než HTTP s nástrojem, musí být vazba webu přidána do konfigurace WAS.</span><span class="sxs-lookup"><span data-stu-id="a8d46-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="a8d46-111">Úložiště konfigurace pro byl soubor applicationHost. config, který se nachází v adresáři%windir%\system32\inetsrv\config.</span><span class="sxs-lookup"><span data-stu-id="a8d46-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="a8d46-112">Toto úložiště konfigurace sdílí i služba IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="a8d46-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="a8d46-113">applicationHost. config je textový soubor XML, který lze otevřít pomocí standardního textového editoru (například Poznámkový blok).</span><span class="sxs-lookup"><span data-stu-id="a8d46-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="a8d46-114">Konfigurační nástroj příkazového řádku IIS 7,0 (Appcmd. exe) je ale upřednostňovaným způsobem, jak přidat vazby jiných než HTTP lokalit.</span><span class="sxs-lookup"><span data-stu-id="a8d46-114">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="a8d46-115">Následující příkaz přidá k výchozímu webovému serveru vazbu sítě NET. TCP pomocí nástroje Appcmd. exe (Tento příkaz je zadaný jako jeden řádek).</span><span class="sxs-lookup"><span data-stu-id="a8d46-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="a8d46-116">Tento příkaz přidá novou vazbu NET. TCP na výchozí web přidáním řádku uvedeného níže do souboru applicationHost. config.</span><span class="sxs-lookup"><span data-stu-id="a8d46-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="a8d46-117">Povolení používání jiných protokolů než HTTP</span><span class="sxs-lookup"><span data-stu-id="a8d46-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="a8d46-118">Můžete povolit nebo zakázat jednotlivé sítě protocolsat na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8d46-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="a8d46-119">Následující příkaz ukazuje, jak povolit protokoly HTTP i NET. TCP pro aplikaci, která běží v `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="a8d46-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="a8d46-120">Seznam povolených protokolů lze také nastavit v \<applicationDefaults > elementu konfigurace XML webu uloženého v souboru ApplicationHost. config.</span><span class="sxs-lookup"><span data-stu-id="a8d46-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="a8d46-121">Následující kód XML z souboru applicationHost. config ukazuje lokalitu, která je vázaná na protokoly HTTP i non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="a8d46-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="a8d46-122">Další konfigurace požadovaná pro podporu jiných protokolů než HTTP se nazývá s komentáři.</span><span class="sxs-lookup"><span data-stu-id="a8d46-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
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
  
 <span data-ttu-id="a8d46-123">Pokud se pokusíte aktivovat službu pomocí nástroje pro aktivaci jiným způsobem než HTTP a nejste nainstalovali a nakonfigurovali jste, může se zobrazit následující chyba:</span><span class="sxs-lookup"><span data-stu-id="a8d46-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="a8d46-124">Pokud se zobrazí tato chyba, zajistěte, aby byla správně nainstalovaná a nakonfigurovaná aktivace bez protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a8d46-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="a8d46-125">Další informace najdete v tématu [Postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="a8d46-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="a8d46-126">Vytvoření služby WCF, která se používá pro aktivaci bez protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="a8d46-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="a8d46-127">Po provedení kroků k instalaci a nakonfigurování (viz [Postup: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)) konfigurace služby, která se má použít pro aktivaci, je podobná konfiguraci služby hostované ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="a8d46-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="a8d46-128">Podrobné pokyny k vytvoření aktivované služby WCF najdete v tématu [How to: Host a služba WCF v](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)nástroji.</span><span class="sxs-lookup"><span data-stu-id="a8d46-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d46-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8d46-129">See also</span></span>

- [<span data-ttu-id="a8d46-130">Hostování v Aktivační službě procesů systému Windows</span><span class="sxs-lookup"><span data-stu-id="a8d46-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- <span data-ttu-id="a8d46-131">[Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a8d46-131">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
