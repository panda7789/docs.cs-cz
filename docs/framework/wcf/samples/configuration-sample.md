---
title: Ukázka konfigurace
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 5ac72db1fce0862381cd614499b5db4b9d95b2d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183907"
---
# <a name="configuration-sample"></a><span data-ttu-id="4d70c-102">Ukázka konfigurace</span><span class="sxs-lookup"><span data-stu-id="4d70c-102">Configuration Sample</span></span>
<span data-ttu-id="4d70c-103">Tato ukázka ukazuje použití konfiguračního souboru, aby služba zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="4d70c-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d70c-104">Tato ukázka implementuje zjišťování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4d70c-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="4d70c-105">Ukázka, která implementuje zjišťování v kódu, naleznete v [tématu Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4d70c-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4d70c-106">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4d70c-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4d70c-107">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4d70c-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4d70c-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4d70c-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d70c-109">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4d70c-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="4d70c-110">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="4d70c-110">Service Configuration</span></span>  
 <span data-ttu-id="4d70c-111">Konfigurační soubor v této ukázce ukazuje dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="4d70c-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="4d70c-112">Díky službě zjistitelné přes <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>standard .</span><span class="sxs-lookup"><span data-stu-id="4d70c-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="4d70c-113">Úprava informací souvisejících s zjišťováním pro koncový bod aplikace služby a úprava některých nastavení souvisejících s zjišťováním na standardním koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="4d70c-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="4d70c-114">Chcete-li povolit zjišťování, musí být provedeno několik změn v konfiguračním souboru aplikace pro službu:</span><span class="sxs-lookup"><span data-stu-id="4d70c-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="4d70c-115">Koncový bod zjišťování musí být `<service>` přidán do prvku.</span><span class="sxs-lookup"><span data-stu-id="4d70c-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="4d70c-116">Toto je <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4d70c-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="4d70c-117">Toto je koncový bod systému, který modul runtime přidruží ke službě zjišťování.</span><span class="sxs-lookup"><span data-stu-id="4d70c-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="4d70c-118">Služba zjišťování naslouchá zprávy v tomto koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="4d70c-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="4d70c-119">Chování `<serviceDiscovery>` je přidán `<serviceBehaviors>` do oddílu.</span><span class="sxs-lookup"><span data-stu-id="4d70c-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="4d70c-120">To umožňuje službu zjistit za běhu a používá koncový bod zjišťování `Probe` již `Resolve` bylo zmíněno dříve naslouchat zjišťování a zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d70c-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="4d70c-121">S těmito dvěma dodatky služby je zjistitelné na koncovém bodu zjišťování zadané.</span><span class="sxs-lookup"><span data-stu-id="4d70c-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="4d70c-122">Následující fragment konfigurace zobrazuje službu s koncovým bodem aplikace a definovaným koncovým bodem zjišťování:</span><span class="sxs-lookup"><span data-stu-id="4d70c-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
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
  
 <span data-ttu-id="4d70c-123">Chcete-li využít oznámení, budete muset přidat koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="4d70c-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="4d70c-124">Chcete-li to provést, upravte konfigurační soubor, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4d70c-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="4d70c-125">Přidání koncového bodu oznámení do chování služby zjišťování vytvoří výchozí ho klienta oznámení pro službu.</span><span class="sxs-lookup"><span data-stu-id="4d70c-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="4d70c-126">To zaručuje, že služba odešle online a offline oznámení při otevření a zavření služby.</span><span class="sxs-lookup"><span data-stu-id="4d70c-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="4d70c-127">Tento konfigurační soubor přesahuje pouze tyto jednoduché kroky úpravou dalšíchování.</span><span class="sxs-lookup"><span data-stu-id="4d70c-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="4d70c-128">Je možné řídit informace související s zjišťováním pomocí konkrétních koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="4d70c-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="4d70c-129">To znamená, že uživatel může určit, zda lze zjistit koncový bod <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> a uživatel může také označit tento koncový bod a vlastní metadata XML.</span><span class="sxs-lookup"><span data-stu-id="4d70c-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="4d70c-130">Chcete-li to provést, `behaviorConfiguration` musí uživatel přidat vlastnost do koncového bodu aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d70c-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="4d70c-131">V tomto případě je do koncového bodu aplikace přidána následující vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4d70c-131">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="4d70c-132">Nyní prostřednictvím prvku konfigurace chování můžete řídit atributy související s zjišťováním.</span><span class="sxs-lookup"><span data-stu-id="4d70c-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="4d70c-133">V tomto případě jsou do koncového bodu aplikace přidány dva obory.</span><span class="sxs-lookup"><span data-stu-id="4d70c-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
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
  
 <span data-ttu-id="4d70c-134">Další informace o oborech naleznete v [tématech Hledání zjišťování a Hledání kritérií](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="4d70c-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="4d70c-135">Můžete také řídit konkrétní podrobnosti koncového bodu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="4d70c-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="4d70c-136">To se provádí <xref:System.ServiceModel.Configuration.StandardEndpointsSection>prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="4d70c-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="4d70c-137">V této ukázce je změněna verze použitého protokolu a přidání atributu, `maxResponseDelay` jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4d70c-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="4d70c-138">Následuje úplný konfigurační soubor použitý v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="4d70c-138">The following is the complete configuration file used in this example:</span></span>  
  
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
  
## <a name="client-configuration"></a><span data-ttu-id="4d70c-139">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="4d70c-139">Client Configuration</span></span>  
 <span data-ttu-id="4d70c-140">V konfiguračním souboru `standardEndpoint` aplikace `dynamicEndpoint` pro klienta se typ používá k využití zjišťování, jak je znázorněno v následujícím fragmentu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4d70c-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
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
  
 <span data-ttu-id="4d70c-141">Pokud klient používá `dynamicEndpoint`modul , modul runtime provede zjišťování automaticky.</span><span class="sxs-lookup"><span data-stu-id="4d70c-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="4d70c-142">Při zjišťování se používají různá nastavení, `discoveryClientSettings` například ta definovaná v části, která určuje typ koncového bodu zjišťování, který se má použít:</span><span class="sxs-lookup"><span data-stu-id="4d70c-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="4d70c-143">Kritéria hledání používaná k vyhledávání služeb:</span><span class="sxs-lookup"><span data-stu-id="4d70c-143">The find criteria used to search for services:</span></span>  
  
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
  
 <span data-ttu-id="4d70c-144">Tato ukázka rozšiřuje tuto funkci a <xref:System.ServiceModel.Discovery.FindCriteria> upravuje použití klienta, stejně jako `updDiscoveryEndpoint` některé vlastnosti standardu používaného pro zjišťování.</span><span class="sxs-lookup"><span data-stu-id="4d70c-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="4d70c-145">Jsou <xref:System.ServiceModel.Discovery.FindCriteria> upraveny tak, aby `scopeMatchBy` používaly obor a konkrétní algoritmus, stejně jako vlastní kritéria ukončení.</span><span class="sxs-lookup"><span data-stu-id="4d70c-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="4d70c-146">Kromě toho ukázka také ukazuje, jak klient `Probe` může odesílat elementy XML pomocí zpráv.</span><span class="sxs-lookup"><span data-stu-id="4d70c-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="4d70c-147">Nakonec jsou provedeny některé změny <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>v , například verze použitého protokolu a nastavení specifická pro Protokol UDP, jak je znázorněno v následujícím konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="4d70c-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
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
  
 <span data-ttu-id="4d70c-148">Následuje úplná konfigurace klienta použitá v ukázce.</span><span class="sxs-lookup"><span data-stu-id="4d70c-148">The following is the complete client configuration used in the sample.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4d70c-149">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="4d70c-149">To use this sample</span></span>  
  
1. <span data-ttu-id="4d70c-150">Tato ukázka používá koncové body HTTP a ke spuštění této ukázky musí být přidány správné adresy ACL správné adresy URL.</span><span class="sxs-lookup"><span data-stu-id="4d70c-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="4d70c-151">Další informace naleznete [v tématu Konfigurace protokolů HTTP a HTTPS](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="4d70c-151">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="4d70c-152">Provedení následujícího příkazu se zvýšeným oprávněním by mělo přidat příslušné akly.</span><span class="sxs-lookup"><span data-stu-id="4d70c-152">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="4d70c-153">Pokud příkaz nefunguje tak, jak je, můžete nahradit doménu a uživatelské jméno následujícími argumenty.</span><span class="sxs-lookup"><span data-stu-id="4d70c-153">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="4d70c-154">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="4d70c-154">Build the solution.</span></span>  
  
3. <span data-ttu-id="4d70c-155">Spusťte spustitelný soubor služby z adresáře sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d70c-155">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="4d70c-156">Spusťte spustitelný soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="4d70c-156">Run the client executable.</span></span> <span data-ttu-id="4d70c-157">Všimněte si, že klient je schopen vyhledat službu.</span><span class="sxs-lookup"><span data-stu-id="4d70c-157">Note that the client is able to locate the service.</span></span>  
