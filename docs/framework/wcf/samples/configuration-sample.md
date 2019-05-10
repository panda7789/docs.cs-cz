---
title: Ukázka konfigurace
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 8c96b41877fa56f486bec03a10dcbf47bac9e37a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651054"
---
# <a name="configuration-sample"></a><span data-ttu-id="08acb-102">Ukázka konfigurace</span><span class="sxs-lookup"><span data-stu-id="08acb-102">Configuration Sample</span></span>
<span data-ttu-id="08acb-103">Tento příklad ukazuje použití konfiguračního souboru služby zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="08acb-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08acb-104">Tato ukázka implementuje zjišťování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="08acb-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="08acb-105">Příklad, který implementuje zjišťování v kódu, naleznete v tématu [základní](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="08acb-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="08acb-106">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="08acb-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="08acb-107">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="08acb-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="08acb-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="08acb-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="08acb-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="08acb-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="08acb-110">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="08acb-110">Service Configuration</span></span>  
 <span data-ttu-id="08acb-111">Konfigurační soubor v této ukázce ukazuje dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="08acb-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="08acb-112">Provádění zjistitelné služby přes standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="08acb-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="08acb-113">Úprava informace týkající se zjišťování pro koncový bod aplikace a úpravu některá nastavení týkající se zjišťování pro standardní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="08acb-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="08acb-114">Povolit zjišťování, musí provést několik změn v konfiguračním souboru aplikace pro službu:</span><span class="sxs-lookup"><span data-stu-id="08acb-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="08acb-115">Koncový bod zjišťování musí být přidané do `<service>` elementu.</span><span class="sxs-lookup"><span data-stu-id="08acb-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="08acb-116">Toto je standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="08acb-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="08acb-117">Toto je koncový bod systému, která modul runtime přidruží ke zjišťování služby.</span><span class="sxs-lookup"><span data-stu-id="08acb-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="08acb-118">Služba zjišťování přijímají zprávy na tomto koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="08acb-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="08acb-119">A `<serviceDiscovery>` chování přidáno `<serviceBehaviors>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="08acb-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="08acb-120">Tato možnost povoluje službu, která mají být zjišťované, a za běhu a používá koncový bod zjišťování pro naslouchání zjišťování již bylo zmíněno dříve `Probe` a `Resolve` zprávy.</span><span class="sxs-lookup"><span data-stu-id="08acb-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="08acb-121">Tato služba je s těmito přídavky dvě zjistitelné na zadaný koncový bod zjišťování.</span><span class="sxs-lookup"><span data-stu-id="08acb-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="08acb-122">Následující fragment kódu config ukazuje služba se koncový bod aplikace a definovaný koncový bod zjišťování:</span><span class="sxs-lookup"><span data-stu-id="08acb-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
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
  
 <span data-ttu-id="08acb-123">Abyste mohli využívat oznámení, musíte přidat koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="08acb-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="08acb-124">Chcete-li to provést, upravte konfigurační soubor, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="08acb-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="08acb-125">Přidání koncového bodu oznámení k chování služby zjišťování vytvoří výchozí oznámení klienta pro službu.</span><span class="sxs-lookup"><span data-stu-id="08acb-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="08acb-126">Zaručí se tak, že služba se pošle oznámení online a offline při otevření a zavření v uvedeném pořadí služby.</span><span class="sxs-lookup"><span data-stu-id="08acb-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="08acb-127">Tento konfigurační soubor jde nad rámec pouze tyto jednoduchých krocích tak, že upravíte Další chování.</span><span class="sxs-lookup"><span data-stu-id="08acb-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="08acb-128">Je možné řídit informace týkající se zjišťování pomocí konkrétní koncové body.</span><span class="sxs-lookup"><span data-stu-id="08acb-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="08acb-129">To znamená, můžete uživatele řídit, zda lze zjistit koncový bod a uživatele můžete také označit tento koncový bod s <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> a vlastních metadat XML.</span><span class="sxs-lookup"><span data-stu-id="08acb-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="08acb-130">Chcete-li to provést, musíte přidat uživatele `behaviorConfiguration` vlastnost koncový bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="08acb-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="08acb-131">V takovém případě je přidána následující vlastnost koncový bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="08acb-131">In this case, the following property is added to the application endpoint.</span></span>  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 <span data-ttu-id="08acb-132">Teď prostřednictvím konfiguračního elementu chování, můžete řídit atributy vztahující se k zjišťování.</span><span class="sxs-lookup"><span data-stu-id="08acb-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="08acb-133">V takovém případě dva obory se přidají do koncového bodu aplikace.</span><span class="sxs-lookup"><span data-stu-id="08acb-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
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
  
 <span data-ttu-id="08acb-134">Další informace o oborech najdete v tématu [hledání zjišťování a kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="08acb-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="08acb-135">Můžete také určit konkrétní podrobnosti o koncový bod zjišťování.</span><span class="sxs-lookup"><span data-stu-id="08acb-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="08acb-136">To se provádí prostřednictvím <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="08acb-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="08acb-137">V této ukázce je verze protokolu používá upravit a přidání `maxResponseDelay` atributu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="08acb-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="08acb-138">Kompletní konfigurace souboru použitého v tomto příkladu je následující:</span><span class="sxs-lookup"><span data-stu-id="08acb-138">The following is the complete configuration file used in this example:</span></span>  
  
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
  
## <a name="client-configuration"></a><span data-ttu-id="08acb-139">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="08acb-139">Client Configuration</span></span>  
 <span data-ttu-id="08acb-140">V konfiguračním souboru aplikace pro klienta `standardEndpoint` typu `dynamicEndpoint` se používá ke zjišťování využívat, jak je znázorněno v následujícím fragmentu kódu config.</span><span class="sxs-lookup"><span data-stu-id="08acb-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
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
  
 <span data-ttu-id="08acb-141">Pokud klient používá `dynamicEndpoint`, modul runtime automaticky provádí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="08acb-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="08acb-142">Různá nastavení, které se používají při zjišťování, jako je například jsou definované v `discoveryClientSettings` oddíl, který určuje typ koncového bodu zjišťování použití:</span><span class="sxs-lookup"><span data-stu-id="08acb-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="08acb-143">Kritéria hledání k vyhledání služeb:</span><span class="sxs-lookup"><span data-stu-id="08acb-143">The find criteria used to search for services:</span></span>  
  
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
  
 <span data-ttu-id="08acb-144">Tento příklad rozšiřuje tuto funkci a změní <xref:System.ServiceModel.Discovery.FindCriteria> používán klienta, a také některé vlastnosti standardní `updDiscoveryEndpoint` používá pro zjišťování.</span><span class="sxs-lookup"><span data-stu-id="08acb-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="08acb-145"><xref:System.ServiceModel.Discovery.FindCriteria> Jsou upravený, aby používal rozsah a konkrétní `scopeMatchBy` algoritmus, stejně jako vlastní ukončení kritéria.</span><span class="sxs-lookup"><span data-stu-id="08acb-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="08acb-146">Kromě toho vzorek ukazuje, jak může klient odeslat elementů XML pomocí `Probe` zprávy.</span><span class="sxs-lookup"><span data-stu-id="08acb-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="08acb-147">A konečně, se některé změny provedené <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jako je verze protokolu používá a nastavení specifická pro UDP, jak je znázorněno v následující konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="08acb-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
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
  
 <span data-ttu-id="08acb-148">Následuje kompletní klienta Konfigurace použité v ukázce.</span><span class="sxs-lookup"><span data-stu-id="08acb-148">The following is the complete client configuration used in the sample.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="08acb-149">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="08acb-149">To use this sample</span></span>  
  
1. <span data-ttu-id="08acb-150">Tato ukázka používá koncové body HTTP a použít tuto ukázku, správné seznamy ACL adresy URL musí být přidán viz [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="08acb-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="08acb-151">Provádění se zvýšenými oprávněními následující příkaz by měl přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="08acb-151">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="08acb-152">Můžete nahradit doména a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, jak je.</span><span class="sxs-lookup"><span data-stu-id="08acb-152">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="08acb-153">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="08acb-153">Build the solution.</span></span>  
  
3. <span data-ttu-id="08acb-154">Spusťte spustitelný soubor služby z adresáře sestavení.</span><span class="sxs-lookup"><span data-stu-id="08acb-154">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="08acb-155">Spusťte klientský spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="08acb-155">Run the client executable.</span></span> <span data-ttu-id="08acb-156">Všimněte si, že se najít službu klienta.</span><span class="sxs-lookup"><span data-stu-id="08acb-156">Note that the client is able to locate the service.</span></span>  
