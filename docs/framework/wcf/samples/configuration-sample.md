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
# <a name="configuration-sample"></a>Ukázka konfigurace
Tato ukázka ukazuje použití konfiguračního souboru, aby služba zjistitelné.  
  
> [!NOTE]
> Tato ukázka implementuje zjišťování v konfiguraci. Ukázka, která implementuje zjišťování v kódu, naleznete v [tématu Basic](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Konfigurace služby  
 Konfigurační soubor v této ukázce ukazuje dvě funkce:  
  
- Díky službě zjistitelné přes <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>standard .  
  
- Úprava informací souvisejících s zjišťováním pro koncový bod aplikace služby a úprava některých nastavení souvisejících s zjišťováním na standardním koncovém bodu.  
  
 Chcete-li povolit zjišťování, musí být provedeno několik změn v konfiguračním souboru aplikace pro službu:  
  
- Koncový bod zjišťování musí být `<service>` přidán do prvku. Toto je <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardní koncový bod. Toto je koncový bod systému, který modul runtime přidruží ke službě zjišťování. Služba zjišťování naslouchá zprávy v tomto koncovém bodě.  
  
- Chování `<serviceDiscovery>` je přidán `<serviceBehaviors>` do oddílu. To umožňuje službu zjistit za běhu a používá koncový bod zjišťování `Probe` již `Resolve` bylo zmíněno dříve naslouchat zjišťování a zprávy. S těmito dvěma dodatky služby je zjistitelné na koncovém bodu zjišťování zadané.  
  
 Následující fragment konfigurace zobrazuje službu s koncovým bodem aplikace a definovaným koncovým bodem zjišťování:  
  
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
  
 Chcete-li využít oznámení, budete muset přidat koncový bod oznámení. Chcete-li to provést, upravte konfigurační soubor, jak je znázorněno v následujícím kódu.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Přidání koncového bodu oznámení do chování služby zjišťování vytvoří výchozí ho klienta oznámení pro službu. To zaručuje, že služba odešle online a offline oznámení při otevření a zavření služby.  
  
 Tento konfigurační soubor přesahuje pouze tyto jednoduché kroky úpravou dalšíchování. Je možné řídit informace související s zjišťováním pomocí konkrétních koncových bodů. To znamená, že uživatel může určit, zda lze zjistit koncový bod <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> a uživatel může také označit tento koncový bod a vlastní metadata XML. Chcete-li to provést, `behaviorConfiguration` musí uživatel přidat vlastnost do koncového bodu aplikace. V tomto případě je do koncového bodu aplikace přidána následující vlastnost.  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 Nyní prostřednictvím prvku konfigurace chování můžete řídit atributy související s zjišťováním. V tomto případě jsou do koncového bodu aplikace přidány dva obory.  
  
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
  
 Další informace o oborech naleznete v [tématech Hledání zjišťování a Hledání kritérií](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Můžete také řídit konkrétní podrobnosti koncového bodu zjišťování. To se provádí <xref:System.ServiceModel.Configuration.StandardEndpointsSection>prostřednictvím . V této ukázce je změněna verze použitého protokolu a přidání atributu, `maxResponseDelay` jak je znázorněno v následujícím příkladu kódu.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Následuje úplný konfigurační soubor použitý v tomto příkladu:  
  
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
  
## <a name="client-configuration"></a>Konfigurace klienta  
 V konfiguračním souboru `standardEndpoint` aplikace `dynamicEndpoint` pro klienta se typ používá k využití zjišťování, jak je znázorněno v následujícím fragmentu konfigurace.  
  
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
  
 Pokud klient používá `dynamicEndpoint`modul , modul runtime provede zjišťování automaticky. Při zjišťování se používají různá nastavení, `discoveryClientSettings` například ta definovaná v části, která určuje typ koncového bodu zjišťování, který se má použít:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Kritéria hledání používaná k vyhledávání služeb:  
  
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
  
 Tato ukázka rozšiřuje tuto funkci a <xref:System.ServiceModel.Discovery.FindCriteria> upravuje použití klienta, stejně jako `updDiscoveryEndpoint` některé vlastnosti standardu používaného pro zjišťování. Jsou <xref:System.ServiceModel.Discovery.FindCriteria> upraveny tak, aby `scopeMatchBy` používaly obor a konkrétní algoritmus, stejně jako vlastní kritéria ukončení. Kromě toho ukázka také ukazuje, jak klient `Probe` může odesílat elementy XML pomocí zpráv. Nakonec jsou provedeny některé změny <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>v , například verze použitého protokolu a nastavení specifická pro Protokol UDP, jak je znázorněno v následujícím konfiguračním souboru.  
  
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
  
 Následuje úplná konfigurace klienta použitá v ukázce.  
  
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
  
#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek  
  
1. Tato ukázka používá koncové body HTTP a ke spuštění této ukázky musí být přidány správné adresy ACL správné adresy URL. Další informace naleznete [v tématu Konfigurace protokolů HTTP a HTTPS](../feature-details/configuring-http-and-https.md). Provedení následujícího příkazu se zvýšeným oprávněním by mělo přidat příslušné akly. Pokud příkaz nefunguje tak, jak je, můžete nahradit doménu a uživatelské jméno následujícími argumenty. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Sestavte řešení.  
  
3. Spusťte spustitelný soubor služby z adresáře sestavení.  
  
4. Spusťte spustitelný soubor klienta. Všimněte si, že klient je schopen vyhledat službu.  
