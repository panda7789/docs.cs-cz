---
title: Ukázka konfigurace
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 78108dc9b28657f0479e9e39ad134f03cf6c877b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714958"
---
# <a name="configuration-sample"></a>Ukázka konfigurace
Tato ukázka demonstruje použití konfiguračního souboru k tomu, aby služba byla zjistitelná.  
  
> [!NOTE]
> Tato ukázka implementuje zjišťování v konfiguraci. Ukázku, která implementuje zjišťování v kódu, naleznete v tématu [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Konfigurace služby  
 Konfigurační soubor v této ukázce ukazuje dvě funkce:  
  
- Zajištění zjistitelnosti služby na úrovni Standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
- Úprava informací týkajících se zjišťování pro koncový bod aplikace služby a úpravu některých nastavení týkajících se zjišťování na standardním koncovém bodu.  
  
 Chcete-li povolit zjišťování, je nutné provést několik změn v konfiguračním souboru aplikace pro tuto službu:  
  
- Koncový bod zjišťování musí být přidán do prvku `<service>`. Toto je standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncový bod. Toto je systémový koncový bod, který modul runtime přidruží ke službě zjišťování. Služba zjišťování naslouchá zprávám v tomto koncovém bodě.  
  
- Do části `<serviceBehaviors>` se přidá chování `<serviceDiscovery>`. To umožňuje, aby se služba zjistila za běhu a používala koncový bod zjišťování, který se dřív uvedl, aby naslouchal `Probe` zjišťování a `Resolve` zpráv. S těmito dvěma dodatky je služba zjistitelná v zadaném koncovém bodu zjišťování.  
  
 Následující fragment kódu konfigurace ukazuje službu s koncovým bodem aplikace a uživatelem definovaným koncovým bodem zjišťování:  
  
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
  
 Pokud chcete využít oznámení, budete muset přidat koncový bod oznámení. Uděláte to tak, že upravíte konfigurační soubor, jak je znázorněno v následujícím kódu.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Přidání koncového bodu oznámení do chování služby zjišťování vytvoří pro službu výchozího klienta oznámení. To zaručuje, že služba při otevření a uzavření služby pošle online a offline oznámení.  
  
 Tento konfigurační soubor překračuje jenom tyto jednoduché kroky úpravou dalšího chování. Informace související se zjišťováním je možné řídit pomocí konkrétních koncových bodů. To znamená, že uživatel může řídit, jestli se může koncový bod zjistit, a uživatel může tento koncový bod označit jako <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> a vlastní metadata XML. K tomu musí uživatel přidat do koncového bodu aplikace vlastnost `behaviorConfiguration`. V tomto případě je do koncového bodu aplikace přidána následující vlastnost.  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 Nyní lze prostřednictvím elementu konfigurace chování řídit atributy související se zjišťováním. V tomto případě se do koncového bodu aplikace přidají dva obory.  
  
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
  
 Další informace o oborech najdete v tématu [vyhledání a kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Můžete také řídit konkrétní podrobnosti koncového bodu zjišťování. To se provádí prostřednictvím <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. V této ukázce je upravena verze použitého protokolu a také přidání atributu `maxResponseDelay`, jak je znázorněno v následujícím příkladu kódu.  
  
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
 V konfiguračním souboru aplikace pro klienta je `standardEndpoint` typu `dynamicEndpoint` použit k využití zjišťování, jak je znázorněno v následujícím fragmentu konfigurace.  
  
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
  
 Když klient používá `dynamicEndpoint`, modul runtime provádí zjišťování automaticky. Během zjišťování se používají různá nastavení, jako jsou ta definovaná v části `discoveryClientSettings`, která určuje typ koncového bodu zjišťování, který se má použít:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Kritéria hledání používaná k hledání služeb:  
  
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
  
 Tato ukázka rozšiřuje tuto funkci a upraví <xref:System.ServiceModel.Discovery.FindCriteria> používané klientem a také některé vlastnosti standardních `updDiscoveryEndpoint` používaných pro zjišťování. <xref:System.ServiceModel.Discovery.FindCriteria> jsou upraveny tak, aby používaly obor a konkrétní `scopeMatchBy` algoritmus, a také vlastní kritéria ukončení. Kromě toho ukázka také ukazuje, jak může klient odesílat XML prvky pomocí `Probe`ch zpráv. Nakonec se v <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>provedou nějaké změny, jako je například verze použitého protokolu a nastavení protokolu UDP, jak je znázorněno v následujícím konfiguračním souboru.  
  
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
  
 Následuje kompletní konfigurace klienta použitá v ukázce.  
  
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
  
#### <a name="to-use-this-sample"></a>Použití této ukázky  
  
1. V této ukázce se používají koncové body HTTP a ke spuštění této ukázky se musí přidat správné seznamy ACL adres URL. Podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) . Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL. Pokud příkaz nefunguje tak, jak je, je vhodné nahradit doménu a uživatelské jméno pro následující argumenty. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Sestavte řešení.  
  
3. Spusťte spustitelný soubor služby z adresáře buildu.  
  
4. Spusťte klientský spustitelný soubor. Upozorňujeme, že klient může službu vyhledat.  
