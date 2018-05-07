---
title: Konfigurace zjišťování v konfiguračním souboru
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: c282767e686ac8a6382268aee8b45eb2d1297f5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Konfigurace zjišťování v konfiguračním souboru
Existují čtyři hlavní skupiny nastavení konfigurace používané při zjišťování. Toto téma se stručně popisují každou a obsahuje příklady způsob jejich konfigurace. Následující každý oddíl bude odkaz na další podrobnější dokumentaci o každou oblast.  
  
## <a name="behavior-configuration"></a>Konfigurace chování  
 Zjišťování používá chování služby a chování koncový bod. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Chování umožňuje zjišťování pro všechny koncové body služby a umožňuje vám určit koncových bodů oznámení.  Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a zadejte koncový bod oznámení.  
  
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
  
 Jakmile zadáte chování, odkazovat z <`service`> elementu, jak znázorňuje následující ukázka.  
  
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
  
 Aby služba zjistitelné, musíte taky přidat koncový bod zjišťování v předchozím příkladu přidá <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardní koncový bod.  
  
 Když přidáte koncových bodů oznámení musíte taky přidat služby naslouchací proces oznámení můžete <`services`> elementu, jak je znázorněno v následujícím příkladu.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Chování slouží k povolení nebo zakázání zjišťování konkrétní koncového bodu.  Následující příklad konfiguruje službu s dva koncové body aplikaci, jednu s povolené zjišťování a jednu s zjišťování zakázána. Pro každý koncový bod <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> chování je přidána.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Chování lze také přidat vlastní metadata do metadat koncového bodu vrácený službou. Následující příklad ukazuje, jak to provést.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Chování lze také přidat obory a typy, které klienti používat pro vyhledávání služeb. Následující příklad ukazuje, jak to udělat v konfiguračním souboru na straně klienta.  
  
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
  
 Další informace o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> najdete v části [přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Konfigurace vazeb – Element  
 Vazba element konfigurace je nejvíce zajímavé na straně klienta. Konfigurace můžete použít k určení kritérií hledání používá ke zjišťování služby z klientské aplikace WCF.  Následující příklad vytvoří vlastní vazby s <xref:System.ServiceModel.Discovery.DiscoveryClient> kanálu a určuje kritéria hledání, které zahrnuje typu a rozsahu. Kromě toho určuje hodnoty pro <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> a <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> vlastnosti.  
  
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
  
 Další informace o kritériích hledání najdete v části [najít zjišťování a kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Další informace o zjišťování a vazba elementy najdete [přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Konfigurace standardní koncového bodu  
 Standardní koncové body jsou předdefinované koncové body, které mají výchozí hodnoty pro jednu nebo více vlastností (adresa, vazba, kontrakt) nebo jeden nebo více hodnoty vlastností, které nelze změnit. Rozhraní .NET 4 se dodává s 3 zjišťování související standardní koncové body: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Je standardní koncový bod, který je předem nakonfigurován pro operace zjišťování přes vícesměrové vysílání UDP vazby. <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Je standardní koncový bod, který je předem nakonfigurovaný k odeslání zpráv oznámení vazbu UDP. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Je standardní koncový bod, který používá zjišťování k vyhledání adresa koncového bodu služby zjištěné dynamicky za běhu.  Standardní vazby jsou zadané s <`endpoint`> elementu, který obsahuje typu atributu, který zadaný typ standardní koncového bodu pro přidání. Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Standardní koncové body jsou nakonfigurované v <`standardEndpoints`> elementu. Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Po přidání konfiguraci standardní koncového bodu, konfigurace v odkazovat <`endpoint`> element pro každý koncový bod, jak znázorňuje následující ukázka.  
  
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
  
 Na rozdíl od jiných standardní koncových bodů použitých při zjišťování, zadání vazby a smlouvy, kterou <xref:System.ServiceModel.Discovery.DynamicEndpoint>. Následující příklad ukazuje, jak přidávat a konfigurovat <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
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
  
 Další informace o standardních koncových bodů v tématu [standardní koncové body](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
