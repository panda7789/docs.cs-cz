---
title: Ukázka konfigurace
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 87afeb0c562254e0f4cf6a85946a765a740c79ec
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990069"
---
# <a name="configuration-sample"></a><span data-ttu-id="f8b34-102">Ukázka konfigurace</span><span class="sxs-lookup"><span data-stu-id="f8b34-102">Configuration Sample</span></span>
<span data-ttu-id="f8b34-103">Tato ukázka demonstruje použití konfiguračního souboru k tomu, aby služba byla zjistitelná.</span><span class="sxs-lookup"><span data-stu-id="f8b34-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8b34-104">Tato ukázka implementuje zjišťování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f8b34-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="f8b34-105">Ukázku, která implementuje zjišťování v kódu, naleznete v tématu [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f8b34-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f8b34-106">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="f8b34-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f8b34-107">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f8b34-107">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f8b34-108">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="f8b34-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8b34-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f8b34-109">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="f8b34-110">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="f8b34-110">Service Configuration</span></span>  
 <span data-ttu-id="f8b34-111">Konfigurační soubor v této ukázce ukazuje dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="f8b34-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="f8b34-112">Zajištění zjistitelnosti služby na úrovni Standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="f8b34-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="f8b34-113">Úprava informací týkajících se zjišťování pro koncový bod aplikace služby a úpravu některých nastavení týkajících se zjišťování na standardním koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="f8b34-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="f8b34-114">Chcete-li povolit zjišťování, je nutné provést několik změn v konfiguračním souboru aplikace pro tuto službu:</span><span class="sxs-lookup"><span data-stu-id="f8b34-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="f8b34-115">Koncový bod zjišťování musí být přidán do `<service>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f8b34-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="f8b34-116">Toto je standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f8b34-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="f8b34-117">Toto je systémový koncový bod, který modul runtime přidruží ke službě zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f8b34-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="f8b34-118">Služba zjišťování naslouchá zprávám v tomto koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="f8b34-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="f8b34-119">Do části se přidá `<serviceDiscovery>`chování `<serviceBehaviors>` .</span><span class="sxs-lookup"><span data-stu-id="f8b34-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="f8b34-120">To umožňuje, aby se služba zjistila za běhu a používala koncový bod zjišťování, který se dřív `Probe` uvedl `Resolve` pro naslouchání zjišťování a zpráv.</span><span class="sxs-lookup"><span data-stu-id="f8b34-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="f8b34-121">S těmito dvěma dodatky je služba zjistitelná v zadaném koncovém bodu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f8b34-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="f8b34-122">Následující fragment kódu konfigurace ukazuje službu s koncovým bodem aplikace a uživatelem definovaným koncovým bodem zjišťování:</span><span class="sxs-lookup"><span data-stu-id="f8b34-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"   
                    kind="udpDiscoveryEndpoint"   
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 <span data-ttu-id="f8b34-123">Pokud chcete využít oznámení, budete muset přidat koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="f8b34-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="f8b34-124">Uděláte to tak, že upravíte konfigurační soubor, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f8b34-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="f8b34-125">Přidání koncového bodu oznámení do chování služby zjišťování vytvoří pro službu výchozího klienta oznámení.</span><span class="sxs-lookup"><span data-stu-id="f8b34-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="f8b34-126">To zaručuje, že služba při otevření a uzavření služby pošle online a offline oznámení.</span><span class="sxs-lookup"><span data-stu-id="f8b34-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="f8b34-127">Tento konfigurační soubor překračuje jenom tyto jednoduché kroky úpravou dalšího chování.</span><span class="sxs-lookup"><span data-stu-id="f8b34-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="f8b34-128">Informace související se zjišťováním je možné řídit pomocí konkrétních koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f8b34-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="f8b34-129">To znamená, že uživatel může řídit, jestli se může koncový bod zjistit, a uživatel může tento koncový bod označit <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> pomocí a vlastní metadata XML.</span><span class="sxs-lookup"><span data-stu-id="f8b34-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="f8b34-130">K tomu musí uživatel přidat `behaviorConfiguration` vlastnost do koncového bodu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f8b34-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="f8b34-131">V tomto případě je do koncového bodu aplikace přidána následující vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f8b34-131">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="f8b34-132">Nyní lze prostřednictvím elementu konfigurace chování řídit atributy související se zjišťováním.</span><span class="sxs-lookup"><span data-stu-id="f8b34-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="f8b34-133">V tomto případě se do koncového bodu aplikace přidají dva obory.</span><span class="sxs-lookup"><span data-stu-id="f8b34-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
```  
  
 <span data-ttu-id="f8b34-134">Další informace o oborech najdete v tématu [vyhledání a kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="f8b34-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="f8b34-135">Můžete také řídit konkrétní podrobnosti koncového bodu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f8b34-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="f8b34-136">To se provádí prostřednictvím <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="f8b34-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="f8b34-137">V této ukázce je upravena verze používaného protokolu a také přidání `maxResponseDelay` atributu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f8b34-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="f8b34-138">Následuje úplný konfigurační soubor použitý v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="f8b34-138">The following is the complete configuration file used in this example:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->            
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a><span data-ttu-id="f8b34-139">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="f8b34-139">Client Configuration</span></span>  
 <span data-ttu-id="f8b34-140">V konfiguračním souboru aplikace pro klienta `standardEndpoint` je typ `dynamicEndpoint` použit k využití zjišťování, jak je znázorněno v následujícím fragmentu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f8b34-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 <span data-ttu-id="f8b34-141">Když klient používá `dynamicEndpoint`, modul runtime provádí zjišťování automaticky.</span><span class="sxs-lookup"><span data-stu-id="f8b34-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="f8b34-142">Během zjišťování se používají různá nastavení, jako jsou ta definovaná v `discoveryClientSettings` části, která určuje typ koncového bodu zjišťování, který se má použít:</span><span class="sxs-lookup"><span data-stu-id="f8b34-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="f8b34-143">Kritéria hledání používaná k hledání služeb:</span><span class="sxs-lookup"><span data-stu-id="f8b34-143">The find criteria used to search for services:</span></span>  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 <span data-ttu-id="f8b34-144">Tato ukázka rozšiřuje tuto funkci a upraví <xref:System.ServiceModel.Discovery.FindCriteria> používaného klienta a také některé vlastnosti standardu `updDiscoveryEndpoint` používaného pro zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f8b34-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="f8b34-145">Jsou upraveny tak, aby používaly obor a `scopeMatchBy` konkrétní algoritmus, a také vlastní kritéria ukončení. <xref:System.ServiceModel.Discovery.FindCriteria></span><span class="sxs-lookup"><span data-stu-id="f8b34-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="f8b34-146">Kromě toho ukázka také ukazuje, jak může klient odesílat XML elementy pomocí `Probe` zpráv.</span><span class="sxs-lookup"><span data-stu-id="f8b34-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="f8b34-147">Nakonec se v takovém případě udělaly <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>nějaké změny, jako je například verze použitého protokolu a nastavení protokolu UDP, jak je znázorněno v následujícím konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="f8b34-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
```xml  
<udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="f8b34-148">Následuje kompletní konfigurace klienta použitá v ukázce.</span><span class="sxs-lookup"><span data-stu-id="f8b34-148">The following is the complete client configuration used in the sample.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>        
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>     
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f8b34-149">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="f8b34-149">To use this sample</span></span>  
  
1. <span data-ttu-id="f8b34-150">V této ukázce se používají koncové body HTTP a ke spuštění této ukázky se musí přidat správné seznamy ACL adres URL. Podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) .</span><span class="sxs-lookup"><span data-stu-id="f8b34-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="f8b34-151">Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="f8b34-151">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="f8b34-152">Pokud příkaz nefunguje tak, jak je, je vhodné nahradit doménu a uživatelské jméno pro následující argumenty.</span><span class="sxs-lookup"><span data-stu-id="f8b34-152">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="f8b34-153">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="f8b34-153">Build the solution.</span></span>  
  
3. <span data-ttu-id="f8b34-154">Spusťte spustitelný soubor služby z adresáře buildu.</span><span class="sxs-lookup"><span data-stu-id="f8b34-154">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="f8b34-155">Spusťte klientský spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="f8b34-155">Run the client executable.</span></span> <span data-ttu-id="f8b34-156">Upozorňujeme, že klient může službu vyhledat.</span><span class="sxs-lookup"><span data-stu-id="f8b34-156">Note that the client is able to locate the service.</span></span>  
