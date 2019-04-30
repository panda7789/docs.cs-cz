---
title: Konfigurace zjišťování v konfiguračním souboru
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: c282767e686ac8a6382268aee8b45eb2d1297f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857516"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Konfigurace zjišťování v konfiguračním souboru
Existují čtyři hlavní skupiny konfigurační nastavení používané při zjišťování. Toto téma se stručně popisují každou a zobrazit příklady toho, jak je nakonfigurovat. Po každý oddíl bude obsahovat odkaz na další podrobné dokumentaci týkající se jednotlivých oblastí.  
  
## <a name="behavior-configuration"></a>Konfigurace chování  
 Zjišťování používá chování služby a chování koncového bodu. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Chování umožňuje zjišťování pro všechny koncové body služby a umožňuje určit koncových bodů oznámení.  Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a zadat koncový bod oznámení.  
  
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
  
 Po zadání chování odkazovat na něj z <`service`> element, jak je znázorněno v následujícím příkladu.  
  
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
  
 Aby zjistitelné služby, musíte taky přidat koncový bod zjišťování výše uvedený příklad přidá <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardní koncový bod.  
  
 Při přidání koncových bodů oznámení musíte taky přidat služby naslouchací proces oznámení můžete <`services`> element, jak je znázorněno v následujícím příkladu.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Chování slouží k povolení nebo zakázání zjišťování určitého koncového bodu.  Následující příklad konfiguruje službu s koncovými body dvě aplikace, jednu s povolené zjišťování a jednu s zjišťování zakázán. Pro každý koncový bod <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> chování přidáno.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Chování lze také přidat vlastní metadata do koncového bodu metadat vrácené službou. Následující příklad ukazuje, jak to provést.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Chování lze také přidat obory a typy, které klienti používají k vyhledání služeb. Následující příklad ukazuje, jak to provést v konfiguračním souboru na straně klienta.  
  
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
  
 Další informace o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> naleznete v tématu [přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Konfigurace elementu vazby  
 Konfigurace elementu vazby vás zajímá nejvíce na straně klienta. Konfigurace můžete použít k určení kritérií hledání používá ke zjišťování služby z klientské aplikace WCF.  Následující příklad vytvoří vlastní vazby s <xref:System.ServiceModel.Discovery.DiscoveryClient> kanálu a určuje kritéria hledání, která zahrnuje typu a rozsahu. Kromě toho určuje hodnoty pro <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> a <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> vlastnosti.  
  
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
  
 Tato konfigurace vlastních vazeb musí odkazovat koncový bod klienta:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 Další informace o kritériích hledání najdete v části [hledání zjišťování a kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Další informace o zjišťování a vazby prvky naleznete v tématu [přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Konfigurace standardního koncového bodu  
 Standardní koncové body jsou předdefinovaných koncových bodů, které mají výchozí hodnoty pro jednu nebo více vlastností (adresa, vazbu, kontrakt) nebo jednu nebo více hodnot vlastností, které nelze změnit. Rozhraní .NET 4 se dodává s 3 zjišťování související standardních koncových bodů: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Vazby je standardní koncový bod, který je předem nakonfigurovaný pro operace zjišťování přes vícesměrové vysílání UDP. <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Je standardní koncový bod, který je předem nakonfigurovaný k odeslání zpráv oznámení UDP vazby. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Je standardní koncový bod, který používá zjišťování najít adresu koncového bodu služby zjištěné dynamicky za běhu.  Standardní vazby jsou zadané pomocí <`endpoint`> element, který obsahuje atribut typu, který určil typ standardní koncový bod pro přidání. Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Standardní koncové body se konfigurují v <`standardEndpoints`> element. Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Po přidání konfigurace standardního koncového bodu, odkazují na konfiguraci v <`endpoint`> – element pro každý koncový bod, jak je znázorněno v následujícím příkladu.  
  
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
  
 Na rozdíl od dalších standardních koncových bodů použitých při zjišťování, určete vazbu a smlouvu aktivoval pro <xref:System.ServiceModel.Discovery.DynamicEndpoint>. Následující příklad ukazuje, jak přidat a nakonfigurovat <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
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
  
 Další informace o standardních koncových bodů najdete v části [standardních koncových bodů](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
