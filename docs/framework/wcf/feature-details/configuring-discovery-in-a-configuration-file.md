---
title: Konfigurace zjišťování v konfiguračním souboru
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 0ad44d0ad1f0d67d84cc42f6b9938d096c245417
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834762"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Konfigurace zjišťování v konfiguračním souboru
Ve zjišťování se používají čtyři hlavní skupiny nastavení konfigurace. V tomto tématu se stručně popíší jednotlivé a příklady, jak je nakonfigurovat. V každém oddílu se bude odkazovat na podrobnější dokumentaci k jednotlivým oblastem.  
  
## <a name="behavior-configuration"></a>Konfigurace chování  
 Funkce zjišťování používá chování služby a koncové body. Chování <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> umožňuje zjišťování všech koncových bodů služby a umožňuje zadat koncové body oznámení.  Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a zadat koncový bod oznámení.  
  
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
  
 Jakmile zadáte chování, odkazujte na něj z < `service` > prvku, jak je znázorněno v následující ukázce.  
  
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
  
 Aby bylo možné službu zjistit, je nutné také přidat koncový bod zjišťování, výše uvedený příklad přidá standardní koncový bod <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
 Když přidáte koncové body oznámení, musíte také přidat službu naslouchacího procesu oznámení do < elementu `services` >, jak je znázorněno v následujícím příkladu.  
  
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
  
 Chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> slouží k povolení nebo zakázání zjišťování konkrétního koncového bodu.  Následující příklad nakonfiguruje službu se dvěma koncovými body aplikace, jednu s povoleným zjišťováním a jednu se zakázaným zjišťováním. U každého koncového bodu se přidá chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.  
  
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
  
 Chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> lze také použít k přidání vlastních metadat do metadat koncového bodu vrácených službou. Následující příklad ukazuje, jak to provést.  
  
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
  
 Chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> lze také použít k přidání oborů a typů, které klienti používají k hledání služeb. Následující příklad ukazuje, jak to provést v konfiguračním souboru na straně klienta.  
  
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
  
 Další informace o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> najdete v tématu [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Konfigurace elementu vazby  
 Konfigurace elementu vazby je nejzajímavější na straně klienta. Pomocí konfigurace můžete určit kritéria hledání používaná ke zjišťování služeb z klientské aplikace WCF.  Následující příklad vytvoří vlastní vazbu s kanálem <xref:System.ServiceModel.Discovery.DiscoveryClient> a určí kritéria hledání, která obsahují typ a rozsah. Kromě toho určuje hodnoty vlastností <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> a <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>.  
  
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
  
 Na tuto konfiguraci vlastní vazby se musí odkazovat koncový bod klienta:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 Další informace o kritériích hledání najdete v tématu [vyhledání a kritéria hledáníy zjišťování](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Další informace o zjišťování a vázání prvků naleznete v tématu [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md) .  
  
## <a name="standard-endpoint-configuration"></a>Konfigurace standardního koncového bodu  
 Standardní koncové body jsou předdefinované koncové body, které mají výchozí hodnoty pro jednu nebo více vlastností (adresa, vazba nebo kontrakt), nebo jednu nebo více hodnot vlastností, které nelze změnit. .NET 4 dodává se 3 standardními koncovými body související se zjišťováním: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  @No__t-0 je standardní koncový bod, který je předem nakonfigurovaný pro operace zjišťování prostřednictvím vazby vícesměrového vysílání UDP. @No__t-0 je standardní koncový bod, který je předem nakonfigurovaný tak, aby odesílal oznamovací zprávy přes vazbu UDP. @No__t-0 je standardní koncový bod, který používá zjišťování k vyhledání adresy koncového bodu zjištěné služby dynamicky za běhu.  Standardní vazby jsou určeny pomocí < elementu `endpoint` >, který obsahuje atribut druhu, který určuje typ standardního koncového bodu, který chcete přidat. Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Standardní koncové body jsou nakonfigurovány v < `standardEndpoints` > elementu. Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Jakmile přidáte standardní konfiguraci koncového bodu, odkazujte na konfiguraci v < elementu `endpoint` > pro každý koncový bod, jak je znázorněno v následující ukázce.  
  
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
  
 Na rozdíl od ostatních standardních koncových bodů používaných ve zjišťování zadáte vazbu a kontrakt pro <xref:System.ServiceModel.Discovery.DynamicEndpoint>. Následující příklad ukazuje, jak přidat a nakonfigurovat <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
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
  
 Další informace o standardních koncových bodech naleznete v tématu [Standardní koncové body](standard-endpoints.md).
