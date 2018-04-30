---
title: Ukázka konfigurace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48f153a26181fa549973ec83e413b1294d7c8ce5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="configuration-sample"></a><span data-ttu-id="0d50a-102">Ukázka konfigurace</span><span class="sxs-lookup"><span data-stu-id="0d50a-102">Configuration Sample</span></span>
<span data-ttu-id="0d50a-103">Tento příklad znázorňuje použití konfiguračního souboru zjistitelnost služby.</span><span class="sxs-lookup"><span data-stu-id="0d50a-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d50a-104">Tato ukázka implementuje zjišťování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0d50a-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="0d50a-105">Příklad, který implementuje zjišťování v kódu, naleznete v tématu [základní](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0d50a-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0d50a-106">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="0d50a-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0d50a-107">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0d50a-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0d50a-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0d50a-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0d50a-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0d50a-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="0d50a-110">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="0d50a-110">Service Configuration</span></span>  
 <span data-ttu-id="0d50a-111">Konfigurační soubor v této ukázce ukazuje dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="0d50a-111">The configuration file in this sample demonstrates two features:</span></span>  
  
-   <span data-ttu-id="0d50a-112">Vytváření služby zjistitelný přes standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="0d50a-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
-   <span data-ttu-id="0d50a-113">Úprava informace týkající se zjišťování pro koncový bod aplikace a úpravě některých nastavení související s zjišťování na standardní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="0d50a-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="0d50a-114">Povolit zjišťování, je nutné provést několik změn v konfiguračním souboru aplikace pro službu:</span><span class="sxs-lookup"><span data-stu-id="0d50a-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
-   <span data-ttu-id="0d50a-115">Koncový bod zjišťování musí být přidán do `<service>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0d50a-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="0d50a-116">Toto je standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncový bod.</span><span class="sxs-lookup"><span data-stu-id="0d50a-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="0d50a-117">Toto je systém koncový bod, který přidruží zjišťování služby modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0d50a-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="0d50a-118">Zjišťování služby přijímají zprávy na tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="0d50a-118">The discovery service listens for messages on this endpoint.</span></span>  
  
-   <span data-ttu-id="0d50a-119">A `<serviceDiscovery>` chování je přidán do `<serviceBehaviors>` části.</span><span class="sxs-lookup"><span data-stu-id="0d50a-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="0d50a-120">To umožňuje službě být zjištěny za běhu a používá koncový bod zjišťování pro naslouchání zjišťování bylo zmíněno dříve `Probe` a `Resolve` zprávy.</span><span class="sxs-lookup"><span data-stu-id="0d50a-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="0d50a-121">Služba je s těmito přídavky dvě zjistitelný na zadaný koncový bod zjišťování.</span><span class="sxs-lookup"><span data-stu-id="0d50a-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="0d50a-122">Následující fragment kódu konfigurace zobrazuje služby s koncový bod aplikace a koncový bod zjišťování definované:</span><span class="sxs-lookup"><span data-stu-id="0d50a-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
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
  
 <span data-ttu-id="0d50a-123">Abyste mohli využívat oznámení, musíte přidat koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="0d50a-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="0d50a-124">Chcete-li to provést, upravte konfigurační soubor, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0d50a-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="0d50a-125">Přidání koncového bodu oznámení chování služby zjišťování vytvoří výchozí oznámení klienta pro službu.</span><span class="sxs-lookup"><span data-stu-id="0d50a-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="0d50a-126">To zaručuje, že služba odešle oznámení online a offline při otevření a zavření v uvedeném pořadí služby.</span><span class="sxs-lookup"><span data-stu-id="0d50a-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="0d50a-127">Tento konfigurační soubor překročí pouze tyto jednoduchých kroků změnou Další chování.</span><span class="sxs-lookup"><span data-stu-id="0d50a-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="0d50a-128">Je možné řídit informace týkající se zjišťování pomocí specifické koncové body.</span><span class="sxs-lookup"><span data-stu-id="0d50a-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="0d50a-129">To znamená, uživatel může určit, zda můžete zjistit koncový bod a uživatele můžete také označit tento koncový bod s <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> a vlastních metadat XML.</span><span class="sxs-lookup"><span data-stu-id="0d50a-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="0d50a-130">Chcete-li to provést, musíte přidat uživatele `behaviorConfiguration` vlastnost, která má koncový bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d50a-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="0d50a-131">V tomto případě následující vlastnost je přidána ke koncovému bodu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d50a-131">In this case, the following property is added to the application endpoint.</span></span>  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 <span data-ttu-id="0d50a-132">Teď pomocí elementu konfigurace chování, můžete řídit související zjišťování atributy.</span><span class="sxs-lookup"><span data-stu-id="0d50a-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="0d50a-133">V takovém případě se přidají dva obory pro koncový bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d50a-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
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
  
 <span data-ttu-id="0d50a-134">Další informace o oborech najdete v tématu [najít zjišťování a kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="0d50a-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="0d50a-135">Můžete také ovládat konkrétní podrobnosti o koncový bod zjišťování.</span><span class="sxs-lookup"><span data-stu-id="0d50a-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="0d50a-136">To se provádí prostřednictvím <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="0d50a-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="0d50a-137">V této ukázce se mění verzi protokolu použít i přidávání `maxResponseDelay` atributu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0d50a-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="0d50a-138">Toto je soubor kompletní konfigurace použité v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="0d50a-138">The following is the complete configuration file used in this example:</span></span>  
  
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
  
## <a name="client-configuration"></a><span data-ttu-id="0d50a-139">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="0d50a-139">Client Configuration</span></span>  
 <span data-ttu-id="0d50a-140">V konfiguračním souboru aplikace pro klienta `standardEndpoint` typu `dynamicEndpoint` se používá k zjišťování využívat, jak je znázorněno v následujícím fragmentu kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0d50a-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
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
  
 <span data-ttu-id="0d50a-141">Když klient používá `dynamicEndpoint`, běhové prostředí provádí zjišťování automaticky.</span><span class="sxs-lookup"><span data-stu-id="0d50a-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="0d50a-142">Různá nastavení, které se používají při zjišťování, jako je například názvům definovaným v `discoveryClientSettings` část, která určuje typ koncový bod zjišťování používat:</span><span class="sxs-lookup"><span data-stu-id="0d50a-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="0d50a-143">Najít kritéria použitá pro vyhledání služeb:</span><span class="sxs-lookup"><span data-stu-id="0d50a-143">The find criteria used to search for services:</span></span>  
  
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
  
 <span data-ttu-id="0d50a-144">Tato ukázka rozšiřuje tuto funkci a upraví <xref:System.ServiceModel.Discovery.FindCriteria> používá klienta a také některé vlastnosti standardní `updDiscoveryEndpoint` použít pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="0d50a-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="0d50a-145"><xref:System.ServiceModel.Discovery.FindCriteria> Jsou upravit tak, aby použít obor a konkrétní `scopeMatchBy` algoritmus, jakož i vlastní ukončení kritéria.</span><span class="sxs-lookup"><span data-stu-id="0d50a-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="0d50a-146">Ukázka navíc také ukazuje, jak klient může odesílat elementů XML pomocí `Probe` zprávy.</span><span class="sxs-lookup"><span data-stu-id="0d50a-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="0d50a-147">Nakonec jsou některé změny provedené <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jako jsou například verzi protokolu použitou a jak je znázorněno v následujícím souboru konfigurace nastavení pro konkrétní UDP.</span><span class="sxs-lookup"><span data-stu-id="0d50a-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
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
  
 <span data-ttu-id="0d50a-148">Zde je konfigurace klientů použitá v ukázce.</span><span class="sxs-lookup"><span data-stu-id="0d50a-148">The following is the complete client configuration used in the sample.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0d50a-149">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="0d50a-149">To use this sample</span></span>  
  
1.  <span data-ttu-id="0d50a-150">Tato ukázka používá koncových bodů protokolu HTTP a použít tuto ukázku, správné seznamy ACL adresa URL musí být přidán najdete [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="0d50a-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="0d50a-151">Spuštěním následujícího příkazu na zvýšená oprávnění měli přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="0d50a-151">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="0d50a-152">Můžete nahradit domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, protože je.</span><span class="sxs-lookup"><span data-stu-id="0d50a-152">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="0d50a-153">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="0d50a-153">Build the solution.</span></span>  
  
3.  <span data-ttu-id="0d50a-154">Spusťte spustitelný soubor služby z adresáře sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d50a-154">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="0d50a-155">Spustíte spustitelný soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="0d50a-155">Run the client executable.</span></span> <span data-ttu-id="0d50a-156">Všimněte si, že klient je schopna zjistit službu.</span><span class="sxs-lookup"><span data-stu-id="0d50a-156">Note that the client is able to locate the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d50a-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d50a-157">See Also</span></span>
