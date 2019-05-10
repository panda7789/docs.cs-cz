---
title: Ukázka konfigurace
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 8c96b41877fa56f486bec03a10dcbf47bac9e37a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651054"
---
# <a name="configuration-sample"></a>Ukázka konfigurace
Tento příklad ukazuje použití konfiguračního souboru služby zjistitelnost.  
  
> [!NOTE]
>  Tato ukázka implementuje zjišťování v konfiguraci. Příklad, který implementuje zjišťování v kódu, naleznete v tématu [základní](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Konfigurace služby  
 Konfigurační soubor v této ukázce ukazuje dvě funkce:  
  
- Provádění zjistitelné služby přes standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
- Úprava informace týkající se zjišťování pro koncový bod aplikace a úpravu některá nastavení týkající se zjišťování pro standardní koncový bod služby.  
  
 Povolit zjišťování, musí provést několik změn v konfiguračním souboru aplikace pro službu:  
  
- Koncový bod zjišťování musí být přidané do `<service>` elementu. Toto je standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncového bodu. Toto je koncový bod systému, která modul runtime přidruží ke zjišťování služby. Služba zjišťování přijímají zprávy na tomto koncovém bodu.  
  
- A `<serviceDiscovery>` chování přidáno `<serviceBehaviors>` oddílu. Tato možnost povoluje službu, která mají být zjišťované, a za běhu a používá koncový bod zjišťování pro naslouchání zjišťování již bylo zmíněno dříve `Probe` a `Resolve` zprávy. Tato služba je s těmito přídavky dvě zjistitelné na zadaný koncový bod zjišťování.  
  
 Následující fragment kódu config ukazuje služba se koncový bod aplikace a definovaný koncový bod zjišťování:  
  
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
  
 Abyste mohli využívat oznámení, musíte přidat koncový bod oznámení. Chcete-li to provést, upravte konfigurační soubor, jak je znázorněno v následujícím kódu.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Přidání koncového bodu oznámení k chování služby zjišťování vytvoří výchozí oznámení klienta pro službu. Zaručí se tak, že služba se pošle oznámení online a offline při otevření a zavření v uvedeném pořadí služby.  
  
 Tento konfigurační soubor jde nad rámec pouze tyto jednoduchých krocích tak, že upravíte Další chování. Je možné řídit informace týkající se zjišťování pomocí konkrétní koncové body. To znamená, můžete uživatele řídit, zda lze zjistit koncový bod a uživatele můžete také označit tento koncový bod s <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> a vlastních metadat XML. Chcete-li to provést, musíte přidat uživatele `behaviorConfiguration` vlastnost koncový bod aplikace. V takovém případě je přidána následující vlastnost koncový bod aplikace.  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 Teď prostřednictvím konfiguračního elementu chování, můžete řídit atributy vztahující se k zjišťování. V takovém případě dva obory se přidají do koncového bodu aplikace.  
  
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
  
 Další informace o oborech najdete v tématu [hledání zjišťování a kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Můžete také určit konkrétní podrobnosti o koncový bod zjišťování. To se provádí prostřednictvím <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. V této ukázce je verze protokolu používá upravit a přidání `maxResponseDelay` atributu, jak je znázorněno v následujícím příkladu kódu.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Kompletní konfigurace souboru použitého v tomto příkladu je následující:  
  
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
 V konfiguračním souboru aplikace pro klienta `standardEndpoint` typu `dynamicEndpoint` se používá ke zjišťování využívat, jak je znázorněno v následujícím fragmentu kódu config.  
  
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
  
 Pokud klient používá `dynamicEndpoint`, modul runtime automaticky provádí zjišťování. Různá nastavení, které se používají při zjišťování, jako je například jsou definované v `discoveryClientSettings` oddíl, který určuje typ koncového bodu zjišťování použití:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Kritéria hledání k vyhledání služeb:  
  
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
  
 Tento příklad rozšiřuje tuto funkci a změní <xref:System.ServiceModel.Discovery.FindCriteria> používán klienta, a také některé vlastnosti standardní `updDiscoveryEndpoint` používá pro zjišťování. <xref:System.ServiceModel.Discovery.FindCriteria> Jsou upravený, aby používal rozsah a konkrétní `scopeMatchBy` algoritmus, stejně jako vlastní ukončení kritéria. Kromě toho vzorek ukazuje, jak může klient odeslat elementů XML pomocí `Probe` zprávy. A konečně, se některé změny provedené <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jako je verze protokolu používá a nastavení specifická pro UDP, jak je znázorněno v následující konfigurační soubor.  
  
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
  
 Následuje kompletní klienta Konfigurace použité v ukázce.  
  
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
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1. Tato ukázka používá koncové body HTTP a použít tuto ukázku, správné seznamy ACL adresy URL musí být přidán viz [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti. Provádění se zvýšenými oprávněními následující příkaz by měl přidat příslušné seznamy ACL. Můžete nahradit doména a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, jak je. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Sestavte řešení.  
  
3. Spusťte spustitelný soubor služby z adresáře sestavení.  
  
4. Spusťte klientský spustitelný soubor. Všimněte si, že se najít službu klienta.  
