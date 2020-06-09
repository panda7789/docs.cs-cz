---
title: Konfigurace zjišťování v konfiguračním souboru
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 59eaecb7e34b9105bc694f444d98c13c036d552f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597550"
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="06c52-102">Konfigurace zjišťování v konfiguračním souboru</span><span class="sxs-lookup"><span data-stu-id="06c52-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="06c52-103">Ve zjišťování se používají čtyři hlavní skupiny nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="06c52-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="06c52-104">V tomto tématu se stručně popíší jednotlivé a příklady, jak je nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="06c52-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="06c52-105">V každém oddílu se bude odkazovat na podrobnější dokumentaci k jednotlivým oblastem.</span><span class="sxs-lookup"><span data-stu-id="06c52-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="06c52-106">Konfigurace chování</span><span class="sxs-lookup"><span data-stu-id="06c52-106">Behavior Configuration</span></span>  
 <span data-ttu-id="06c52-107">Funkce zjišťování používá chování služby a koncové body.</span><span class="sxs-lookup"><span data-stu-id="06c52-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="06c52-108"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Chování umožňuje zjišťování všech koncových bodů služby a umožňuje zadat koncové body oznámení.</span><span class="sxs-lookup"><span data-stu-id="06c52-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="06c52-109">Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a zadat koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="06c52-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="06c52-110">Jakmile zadáte chování, odkazujte na něj z <`service`> elementu, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="06c52-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="06c52-111">Aby bylo možné službu zjistit, je nutné také přidat koncový bod zjišťování, výše uvedený příklad přidá <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="06c52-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="06c52-112">Když přidáte koncové body oznámení, musíte také přidat službu naslouchacího procesu oznámení do prvku <`services`>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="06c52-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="06c52-113"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Chování se používá k povolení nebo zakázání zjišťování konkrétního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="06c52-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="06c52-114">Následující příklad nakonfiguruje službu se dvěma koncovými body aplikace, jednu s povoleným zjišťováním a jednu se zakázaným zjišťováním.</span><span class="sxs-lookup"><span data-stu-id="06c52-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="06c52-115">U každého koncového bodu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> se přidají chování.</span><span class="sxs-lookup"><span data-stu-id="06c52-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="06c52-116"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Chování lze také použít k přidání vlastních metadat do metadat koncového bodu vrácených službou.</span><span class="sxs-lookup"><span data-stu-id="06c52-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="06c52-117">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="06c52-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="06c52-118"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Chování lze také použít k přidání oborů a typů, které klienti používají k hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="06c52-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="06c52-119">Následující příklad ukazuje, jak to provést v konfiguračním souboru na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="06c52-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 <span data-ttu-id="06c52-120">Další informace o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> najdete v tématu [Přehled zjišťování WCF](wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="06c52-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="06c52-121">Konfigurace elementu vazby</span><span class="sxs-lookup"><span data-stu-id="06c52-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="06c52-122">Konfigurace elementu vazby je nejzajímavější na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="06c52-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="06c52-123">Pomocí konfigurace můžete určit kritéria hledání používaná ke zjišťování služeb z klientské aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="06c52-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="06c52-124">Následující příklad vytvoří vlastní vazbu s <xref:System.ServiceModel.Discovery.DiscoveryClient> kanálem a určí kritéria hledání, která obsahují typ a rozsah.</span><span class="sxs-lookup"><span data-stu-id="06c52-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="06c52-125">Kromě toho určuje hodnoty <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> vlastností a.</span><span class="sxs-lookup"><span data-stu-id="06c52-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="06c52-126">Na tuto konfiguraci vlastní vazby se musí odkazovat koncový bod klienta:</span><span class="sxs-lookup"><span data-stu-id="06c52-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="06c52-127">Další informace o kritériích hledání najdete v tématu [vyhledání a kritéria hledáníy zjišťování](discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="06c52-127">For more information about find criteria see [Discovery Find and FindCriteria](discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="06c52-128">Další informace o zjišťování a vázání prvků naleznete v tématu [Přehled zjišťování WCF](wcf-discovery-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="06c52-128">For more information about discovery and binding elements see, [WCF Discovery Overview](wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="06c52-129">Konfigurace standardního koncového bodu</span><span class="sxs-lookup"><span data-stu-id="06c52-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="06c52-130">Standardní koncové body jsou předdefinované koncové body, které mají výchozí hodnoty pro jednu nebo více vlastností (adresa, vazba nebo kontrakt), nebo jednu nebo více hodnot vlastností, které nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="06c52-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="06c52-131">.NET 4 dodává se 3 standardními koncovými body související se zjišťováním: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> , <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> a <xref:System.ServiceModel.Discovery.DynamicEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="06c52-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="06c52-132"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>Je standardní koncový bod, který je předem nakonfigurovaný pro operace zjišťování prostřednictvím vazby vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="06c52-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="06c52-133"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>Je standardní koncový bod, který je předem nakonfigurovaný tak, aby odesílal oznamovací zprávy přes vazbu UDP.</span><span class="sxs-lookup"><span data-stu-id="06c52-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="06c52-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint>Je standardní koncový bod, který používá zjišťování k vyhledání adresy koncového bodu zjištěné služby dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="06c52-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="06c52-135">Standardní vazby jsou zadány pomocí `endpoint` elementu <>, který obsahuje atribut druhu, který určuje typ standardního koncového bodu, který chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="06c52-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="06c52-136">Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="06c52-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="06c52-137">Standardní koncové body jsou konfigurovány v <`standardEndpoints`> elementu.</span><span class="sxs-lookup"><span data-stu-id="06c52-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="06c52-138">Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="06c52-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="06c52-139">Jakmile přidáte standardní konfiguraci koncového bodu, odkazujte na konfiguraci v prvku <`endpoint`> pro každý koncový bod, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="06c52-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="06c52-140">Na rozdíl od ostatních standardních koncových bodů používaných ve zjišťování určujete vazbu a kontrakt pro <xref:System.ServiceModel.Discovery.DynamicEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="06c52-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="06c52-141">Následující příklad ukazuje, jak přidat a nakonfigurovat <xref:System.ServiceModel.Discovery.DynamicEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="06c52-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="06c52-142">Další informace o standardních koncových bodech naleznete v tématu [Standardní koncové body](standard-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="06c52-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
