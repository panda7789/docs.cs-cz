---
title: Konfigurace zjišťování v konfiguračním souboru
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 934b04b51b9954cf943f57f33250951048e5671b
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464209"
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="eba18-102">Konfigurace zjišťování v konfiguračním souboru</span><span class="sxs-lookup"><span data-stu-id="eba18-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="eba18-103">Existují čtyři hlavní skupiny nastavení konfigurace používané při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="eba18-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="eba18-104">Toto téma bude stručně popsat každý a zobrazit příklady, jak je nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="eba18-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="eba18-105">V návaznosti na každou sekci bude odkaz na podrobnější dokumentaci o každé oblasti.</span><span class="sxs-lookup"><span data-stu-id="eba18-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="eba18-106">Konfigurace chování</span><span class="sxs-lookup"><span data-stu-id="eba18-106">Behavior Configuration</span></span>  
 <span data-ttu-id="eba18-107">Zjišťování používá chování služby a chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="eba18-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="eba18-108">Chování <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> umožňuje zjišťování pro všechny koncové body služby a umožňuje zadat koncové body oznámení.</span><span class="sxs-lookup"><span data-stu-id="eba18-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="eba18-109">Následující příklad ukazuje, jak <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> přidat a zadat koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="eba18-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="eba18-110">Jakmile zadáte chování, odkaz ujte `service` jej z> prvku <, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="eba18-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
         <!-- Application Endpoint -->  
         <endpoint address="endpoint0"  
                   binding="basicHttpBinding"  
                   contract="IHelloWorldService" />  
         <!-- Discovery Endpoints -->  
         <endpoint kind="udpDiscoveryEndpoint" />  
        </service>  
    </services>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="eba18-111">Aby služba byla zjistitelná, musíte také přidat koncový bod zjišťování, výše <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uvedený příklad přidá standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="eba18-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="eba18-112">Při přidání koncových bodů oznámení je nutné také `services` přidat službu naslouchací proces oznámení do <> prvek, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eba18-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
      <!-- Application Endpoint -->  
      <endpoint address="endpoint0"  
                binding="basicHttpBinding"  
                contract="IHelloWorldService" />  
      <!-- Discovery Endpoints -->  
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <!-- Announcement Listener Configuration -->  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>
```  
  
 <span data-ttu-id="eba18-113">Chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> se používá k povolení nebo zakázání zjišťování konkrétního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="eba18-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="eba18-114">Následující příklad konfiguruje službu se dvěma koncovými body aplikace, jeden s povoleným zjišťováním a druhý se zakázaným zjišťováním.</span><span class="sxs-lookup"><span data-stu-id="eba18-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="eba18-115">Pro každý koncový <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bod je přidáno chování.</span><span class="sxs-lookup"><span data-stu-id="eba18-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService"  
               behaviorConfiguration="helloWorldServiceBehavior">  
  
        <!-- Application Endpoints -->  
        <endpoint address="endpoint0"  
                 binding="basicHttpBinding"  
                 contract="IHelloWorldService"
                 behaviorConfiguration="ep0Behavior" />  
  
        <endpoint address="endpoint1"  
                  binding="basicHttpBinding"  
                  contract="IHelloWorldService"  
                  behaviorConfiguration="ep1Behavior" />  
  
        <!-- Discovery Endpoints -->  
        <endpoint kind="udpDiscoveryEndpoint" />  
      </service>  
   </services>  
   <behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery />  
        </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="ep0Behavior">  
          <endpointDiscovery enabled="true"/>  
        </behavior>  
        <behavior name="ep1Behavior">  
          <endpointDiscovery enabled="false"/>  
        </behavior>  
     </endpointBehaviors>  
   </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="eba18-116">Chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> lze také přidat vlastní metadata do metadat koncového bodu vrácené službou.</span><span class="sxs-lookup"><span data-stu-id="eba18-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="eba18-117">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="eba18-117">The following example shows how to do this.</span></span>  
  
```xml  
<behavior name="ep4Behavior">  
   <endpointDiscovery enabled="true">  
      <extensions>  
         <CustomMetadata>This is custom metadata.</CustomMetadata>  
         <d:Types xmlns:d="http://schemas.xmlsoap.org/ws/2005/04/discovery" xmlns:i="http://printer.example.org/2003/imaging">i:PrintBasic</d:Types>  
         <CustomMetadata netsted="true">  
            <NestedMetadata>This is a nested custom metadata.</NestedMetadata>  
         </CustomMetadata>  
      </extensions>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="eba18-118">Chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> lze také přidat obory a typy, které klienti používají k vyhledávání služeb.</span><span class="sxs-lookup"><span data-stu-id="eba18-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="eba18-119">Následující příklad ukazuje, jak to provést v konfiguračním souboru na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="eba18-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
```xml  
<behavior name="ep2Behavior">  
   <endpointDiscovery enabled="true">  
      <scopes>  
         <add scope="http://www.microsoft.com/building42/floor1"/>  
         <add scope="ldap:///ou=engineeringo=examplecomc=us"/>  
      </scopes>  
      <types>  
         <add name="test" namespace="http://example.microsoft.com/" />  
         <add name="additionalContract" namespace="http://example.microsoft.com/" />  
      </types>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="eba18-120">Další informace <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> o <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> přehledu zjišťování WCF a informací naleznete v [tématu WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eba18-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="eba18-121">Konfigurace prvku vazby</span><span class="sxs-lookup"><span data-stu-id="eba18-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="eba18-122">Konfigurace prvku vazby je nejzajímavější na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="eba18-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="eba18-123">Pomocí konfigurace můžete určit kritéria hledání použitá ke zjišťování služeb z klientské aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="eba18-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="eba18-124">Následující příklad vytvoří vlastní vazbu s kanálem <xref:System.ServiceModel.Discovery.DiscoveryClient> a určuje kritéria hledání, která zahrnuje typ a obor.</span><span class="sxs-lookup"><span data-stu-id="eba18-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="eba18-125">Kromě toho určuje hodnoty <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> pro <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> vlastnosti a.</span><span class="sxs-lookup"><span data-stu-id="eba18-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
```xml  
<bindings>  
   <customBinding>  
      <!-- Binding Configuration for the Application Endpoint -->  
      <binding name="discoBindingConfiguration">  
         <discoveryClient>  
            <endpoint kind="discoveryEndpoint"  
                      address="http://localhost:8000/ConfigTest/Discovery"  
                      binding="customBinding"  
                      bindingConfiguration="httpSoap12WSAddressing10"/>  
            <findCriteria duration="00:00:10" maxResults="2">  
              <types>  
                <add name="IHelloWorldService"/>  
              </types>  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>
            </findCriteria>  
          </discoveryClient>  
          <textMessageEncoding messageVersion="Soap11"/>  
          <httpTransport />  
      </binding>
   </customBinding>
</bindings>  
```  
  
 <span data-ttu-id="eba18-126">Na tuto vlastní konfiguraci vazby musí odkazovat koncový bod klienta:</span><span class="sxs-lookup"><span data-stu-id="eba18-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="eba18-127">Další informace o kritériích hledání naleznete v [tématech Hledání zjišťování a Kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="eba18-127">For more information about find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="eba18-128">Další informace o zjišťování a vazby prvků [naleznete, WCF Discovery Přehled](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="eba18-128">For more information about discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="eba18-129">Standardní konfigurace koncového bodu</span><span class="sxs-lookup"><span data-stu-id="eba18-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="eba18-130">Standardní koncové body jsou předdefinované koncové body, které mají výchozí hodnoty pro jednu nebo více vlastností (adresa, vazba nebo smlouva) nebo jednu nebo více hodnot vlastností, které se nemohou změnit.</span><span class="sxs-lookup"><span data-stu-id="eba18-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="eba18-131">.NET 4 je dodáván se 3 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>standardními <xref:System.ServiceModel.Discovery.DynamicEndpoint>koncovými body souvisejícími s zjišťováním: , , a .</span><span class="sxs-lookup"><span data-stu-id="eba18-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="eba18-132">Jedná <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> se o standardní koncový bod, který je předem nakonfigurován pro operace zjišťování přes vazbu vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="eba18-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="eba18-133">Jedná <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> se o standardní koncový bod, který je předem nakonfigurován tak, aby odesílá zprávy o oznámení prostřednictvím vazby UDP.</span><span class="sxs-lookup"><span data-stu-id="eba18-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="eba18-134">Jedná <xref:System.ServiceModel.Discovery.DynamicEndpoint> se o standardní koncový bod, který používá zjišťování k dynamickému vyhledání adresy koncového bodu zjištěné služby za běhu.</span><span class="sxs-lookup"><span data-stu-id="eba18-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="eba18-135">Standardní vazby jsou určeny s <`endpoint`> prvek, který obsahuje atribut kind, který zadal typ standardního koncového bodu, který má být přidat.</span><span class="sxs-lookup"><span data-stu-id="eba18-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="eba18-136">Následující příklad ukazuje, jak <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> přidat <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>a .</span><span class="sxs-lookup"><span data-stu-id="eba18-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>  
```  
  
 <span data-ttu-id="eba18-137">Standardní koncové body jsou `standardEndpoints` konfigurovány v prvku <>.</span><span class="sxs-lookup"><span data-stu-id="eba18-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="eba18-138">Následující příklad ukazuje, jak <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> nakonfigurovat a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="eba18-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<standardEndpoints>  
      <udpAnnouncementEndpoint>  
        <standardEndpoint
            name="udpAnnouncementEndpointSettings"
            multicastAddress="soap.udp://239.255.255.250:3703"
            maxAnnouncementDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="1028"  
            maxPendingMessageCount="10"  
            maxMulticastRetransmitCount="3"  
            maxUnicastRetransmitCount="2"  
            socketReceiveBufferSize="131072"  
            timeToLive="2" />  
        </standardEndpoint>  
      </udpAnnouncementEndpoint>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
            name="udpDiscoveryEndpointSettings"  
            multicastAddress="soap.udp://239.255.255.252:3704"  
            maxResponseDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="2048"  
            maxPendingMessageCount="5"  
            maxReceivedMessageSize="8192"  
            maxBufferPoolSize="262144"/>  
        </standardEndpoint>  
      </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="eba18-139">Po přidání standardní konfigurace koncového bodu se odkazujte `endpoint` na konfiguraci v <> element u každého koncového bodu, jak je znázorněno na následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="eba18-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="udpDiscoveryEndpointSettings"/>  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" endpointConfiguration="udpAnnouncementEndpointSettings" >  
   </service>  
</services>  
```  
  
 <span data-ttu-id="eba18-140">Na rozdíl od jiných standardních koncových bodů používaných při zjišťování zadáte vazbu a smlouvu pro <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="eba18-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="eba18-141">Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.DynamicEndpoint>a nakonfigurovat .</span><span class="sxs-lookup"><span data-stu-id="eba18-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint kind="dynamicEndpoint" binding="basicHttpBinding" contract="IHelloWorldService" endpointConfiguration="dynamicEndpointConfiguration" />  
    </client>
   <standardEndpoints>  
      <dynamicEndpoint>  
         <standardEndpoint name="dynamicEndpointConfiguration">  
             <discoveryClientSettings>  
              <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="2">  
                 <types>  
                   <add name="IHelloWorldService"/>  
                 </types>  
                 <scopes>  
                   <add scope="http://www.microsoft.com/building42/floor1"/>  
                 </scopes>  
                 <extensions>  
                   <CustomMetadata>This is custom metadata.</CustomMetadata>
                 </extensions>  
               </findCriteria>  
             </discoveryClientSettings>  
           </standardEndpoint>  
         </dynamicEndpoint>  
   </standardEndpoints>  
</system.ServiceModel>  
```  
  
 <span data-ttu-id="eba18-142">Další informace o standardních koncových bodech naleznete [v tématu Standardní koncové body](standard-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="eba18-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
