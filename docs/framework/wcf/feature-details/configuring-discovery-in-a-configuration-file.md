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
# <a name="configuring-discovery-in-a-configuration-file"></a>Konfigurace zjišťování v konfiguračním souboru
Existují čtyři hlavní skupiny nastavení konfigurace používané při zjišťování. Toto téma bude stručně popsat každý a zobrazit příklady, jak je nakonfigurovat. V návaznosti na každou sekci bude odkaz na podrobnější dokumentaci o každé oblasti.  
  
## <a name="behavior-configuration"></a>Konfigurace chování  
 Zjišťování používá chování služby a chování koncového bodu. Chování <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> umožňuje zjišťování pro všechny koncové body služby a umožňuje zadat koncové body oznámení.  Následující příklad ukazuje, jak <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> přidat a zadat koncový bod oznámení.  
  
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
  
 Jakmile zadáte chování, odkaz ujte `service` jej z> prvku <, jak je znázorněno v následující ukázce.  
  
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
  
 Aby služba byla zjistitelná, musíte také přidat koncový bod zjišťování, výše <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uvedený příklad přidá standardní koncový bod.  
  
 Při přidání koncových bodů oznámení je nutné také `services` přidat službu naslouchací proces oznámení do <> prvek, jak je znázorněno v následujícím příkladu.  
  
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
  
 Chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> se používá k povolení nebo zakázání zjišťování konkrétního koncového bodu.  Následující příklad konfiguruje službu se dvěma koncovými body aplikace, jeden s povoleným zjišťováním a druhý se zakázaným zjišťováním. Pro každý koncový <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bod je přidáno chování.  
  
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
  
 Chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> lze také přidat vlastní metadata do metadat koncového bodu vrácené službou. Následující příklad ukazuje, jak to provést.  
  
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
  
 Chování <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> lze také přidat obory a typy, které klienti používají k vyhledávání služeb. Následující příklad ukazuje, jak to provést v konfiguračním souboru na straně klienta.  
  
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
  
 Další informace <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> o <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> přehledu zjišťování WCF a informací naleznete v [tématu WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Konfigurace prvku vazby  
 Konfigurace prvku vazby je nejzajímavější na straně klienta. Pomocí konfigurace můžete určit kritéria hledání použitá ke zjišťování služeb z klientské aplikace WCF.  Následující příklad vytvoří vlastní vazbu s kanálem <xref:System.ServiceModel.Discovery.DiscoveryClient> a určuje kritéria hledání, která zahrnuje typ a obor. Kromě toho určuje hodnoty <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> pro <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> vlastnosti a.  
  
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
  
 Na tuto vlastní konfiguraci vazby musí odkazovat koncový bod klienta:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 Další informace o kritériích hledání naleznete v [tématech Hledání zjišťování a Kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Další informace o zjišťování a vazby prvků [naleznete, WCF Discovery Přehled](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Standardní konfigurace koncového bodu  
 Standardní koncové body jsou předdefinované koncové body, které mají výchozí hodnoty pro jednu nebo více vlastností (adresa, vazba nebo smlouva) nebo jednu nebo více hodnot vlastností, které se nemohou změnit. .NET 4 je dodáván se 3 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>standardními <xref:System.ServiceModel.Discovery.DynamicEndpoint>koncovými body souvisejícími s zjišťováním: , , a .  Jedná <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> se o standardní koncový bod, který je předem nakonfigurován pro operace zjišťování přes vazbu vícesměrového vysílání UDP. Jedná <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> se o standardní koncový bod, který je předem nakonfigurován tak, aby odesílá zprávy o oznámení prostřednictvím vazby UDP. Jedná <xref:System.ServiceModel.Discovery.DynamicEndpoint> se o standardní koncový bod, který používá zjišťování k dynamickému vyhledání adresy koncového bodu zjištěné služby za běhu.  Standardní vazby jsou určeny s <`endpoint`> prvek, který obsahuje atribut kind, který zadal typ standardního koncového bodu, který má být přidat. Následující příklad ukazuje, jak <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> přidat <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>a .  
  
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
  
 Standardní koncové body jsou `standardEndpoints` konfigurovány v prvku <>. Následující příklad ukazuje, jak <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> nakonfigurovat a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Po přidání standardní konfigurace koncového bodu se odkazujte `endpoint` na konfiguraci v <> element u každého koncového bodu, jak je znázorněno na následující ukázce.  
  
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
  
 Na rozdíl od jiných standardních koncových bodů používaných při zjišťování zadáte vazbu a smlouvu pro <xref:System.ServiceModel.Discovery.DynamicEndpoint>. Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.DynamicEndpoint>a nakonfigurovat .  
  
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
  
 Další informace o standardních koncových bodech naleznete [v tématu Standardní koncové body](standard-endpoints.md).
