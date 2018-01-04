---
title: "Konfigurace zjišťování v konfiguračním souboru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43344fc5411236fbb7420fd4d58526b3e0351d4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="79ffb-102">Konfigurace zjišťování v konfiguračním souboru</span><span class="sxs-lookup"><span data-stu-id="79ffb-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="79ffb-103">Existují čtyři hlavní skupiny nastavení konfigurace používané při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="79ffb-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="79ffb-104">Toto téma se stručně popisují každou a obsahuje příklady způsob jejich konfigurace.</span><span class="sxs-lookup"><span data-stu-id="79ffb-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="79ffb-105">Následující každý oddíl bude odkaz na další podrobnější dokumentaci o každou oblast.</span><span class="sxs-lookup"><span data-stu-id="79ffb-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="79ffb-106">Konfigurace chování</span><span class="sxs-lookup"><span data-stu-id="79ffb-106">Behavior Configuration</span></span>  
 <span data-ttu-id="79ffb-107">Zjišťování používá chování služby a chování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="79ffb-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="79ffb-108"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Chování umožňuje zjišťování pro všechny koncové body služby a umožňuje vám určit koncových bodů oznámení.</span><span class="sxs-lookup"><span data-stu-id="79ffb-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="79ffb-109">Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a zadejte koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="79ffb-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
```  
  
 <span data-ttu-id="79ffb-110">Jakmile zadáte chování, odkazovat z <`service`> elementu, jak znázorňuje následující ukázka.</span><span class="sxs-lookup"><span data-stu-id="79ffb-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
    </service>  
```  
  
 <span data-ttu-id="79ffb-111">Aby služba zjistitelné, musíte taky přidat koncový bod zjišťování v předchozím příkladu přidá <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="79ffb-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="79ffb-112">Když přidáte koncových bodů oznámení musíte taky přidat služby naslouchací proces oznámení můžete <`services`> elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="79ffb-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
```  
  
 <span data-ttu-id="79ffb-113"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Chování slouží k povolení nebo zakázání zjišťování konkrétní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="79ffb-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="79ffb-114">Následující příklad konfiguruje službu s dva koncové body aplikaci, jednu s povolené zjišťování a jednu s zjišťování zakázána.</span><span class="sxs-lookup"><span data-stu-id="79ffb-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="79ffb-115">Pro každý koncový bod <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> chování je přidána.</span><span class="sxs-lookup"><span data-stu-id="79ffb-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
```  
  
 <span data-ttu-id="79ffb-116"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Chování lze také přidat vlastní metadata do metadat koncového bodu vrácený službou.</span><span class="sxs-lookup"><span data-stu-id="79ffb-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="79ffb-117">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="79ffb-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="79ffb-118"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Chování lze také přidat obory a typy, které klienti používat pro vyhledávání služeb.</span><span class="sxs-lookup"><span data-stu-id="79ffb-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="79ffb-119">Následující příklad ukazuje, jak to udělat v konfiguračním souboru na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="79ffb-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="79ffb-120"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> najdete v části [přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="79ffb-120"> <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="79ffb-121">Konfigurace vazeb – Element</span><span class="sxs-lookup"><span data-stu-id="79ffb-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="79ffb-122">Vazba element konfigurace je nejvíce zajímavé na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="79ffb-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="79ffb-123">Konfigurace můžete použít k určení kritérií hledání používá ke zjišťování služby z klientské aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="79ffb-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="79ffb-124">Následující příklad vytvoří vlastní vazby s <xref:System.ServiceModel.Discovery.DiscoveryClient> kanálu a určuje kritéria hledání, které zahrnuje typu a rozsahu.</span><span class="sxs-lookup"><span data-stu-id="79ffb-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="79ffb-125">Kromě toho určuje hodnoty pro <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> a <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="79ffb-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
```  
  
 <span data-ttu-id="79ffb-126">Tato konfigurace vlastních vazeb musí odkazovat koncový bod klienta:</span><span class="sxs-lookup"><span data-stu-id="79ffb-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="79ffb-127">najít, najdete v části kritéria [najít zjišťování a kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="79ffb-127"> find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="79ffb-128">zjišťování a vazba elementy najdete [přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="79ffb-128"> discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="79ffb-129">Konfigurace standardní koncového bodu</span><span class="sxs-lookup"><span data-stu-id="79ffb-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="79ffb-130">Standardní koncové body jsou předdefinované koncové body, které mají výchozí hodnoty pro jednu nebo více vlastností (adresa, vazba, kontrakt) nebo jeden nebo více hodnoty vlastností, které nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="79ffb-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="79ffb-131">Rozhraní .NET 4 se dodává s 3 zjišťování související standardní koncové body: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="79ffb-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="79ffb-132"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Je standardní koncový bod, který je předem nakonfigurován pro operace zjišťování přes vícesměrové vysílání UDP vazby.</span><span class="sxs-lookup"><span data-stu-id="79ffb-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="79ffb-133"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Je standardní koncový bod, který je předem nakonfigurovaný k odeslání zpráv oznámení vazbu UDP.</span><span class="sxs-lookup"><span data-stu-id="79ffb-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="79ffb-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Je standardní koncový bod, který používá zjišťování k vyhledání adresa koncového bodu služby zjištěné dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="79ffb-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="79ffb-135">Standardní vazby jsou zadané s <`endpoint`> elementu, který obsahuje typu atributu, který zadaný typ standardní koncového bodu pro přidání.</span><span class="sxs-lookup"><span data-stu-id="79ffb-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="79ffb-136">Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="79ffb-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="79ffb-137">Standardní koncové body jsou nakonfigurované v <`standardEndpoints`> elementu.</span><span class="sxs-lookup"><span data-stu-id="79ffb-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="79ffb-138">Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="79ffb-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
```  
  
 <span data-ttu-id="79ffb-139">Po přidání konfiguraci standardní koncového bodu, konfigurace v odkazovat <`endpoint`> element pro každý koncový bod, jak znázorňuje následující ukázka.</span><span class="sxs-lookup"><span data-stu-id="79ffb-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="79ffb-140">Na rozdíl od jiných standardní koncových bodů použitých při zjišťování, zadání vazby a smlouvy, kterou <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="79ffb-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="79ffb-141">Následující příklad ukazuje, jak přidávat a konfigurovat <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="79ffb-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="79ffb-142">Standardní koncové body, najdete v části [standardní koncové body](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="79ffb-142"> standard endpoints see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span></span>
