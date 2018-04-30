---
title: Ukázka konfigurace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48f153a26181fa549973ec83e413b1294d7c8ce5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="configuration-sample"></a>Ukázka konfigurace
Tento příklad znázorňuje použití konfiguračního souboru zjistitelnost služby.  
  
> [!NOTE]
>  Tato ukázka implementuje zjišťování v konfiguraci. Příklad, který implementuje zjišťování v kódu, naleznete v tématu [základní](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Konfigurace služby  
 Konfigurační soubor v této ukázce ukazuje dvě funkce:  
  
-   Vytváření služby zjistitelný přes standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
-   Úprava informace týkající se zjišťování pro koncový bod aplikace a úpravě některých nastavení související s zjišťování na standardní koncový bod služby.  
  
 Povolit zjišťování, je nutné provést několik změn v konfiguračním souboru aplikace pro službu:  
  
-   Koncový bod zjišťování musí být přidán do `<service>` elementu. Toto je standardní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncový bod. Toto je systém koncový bod, který přidruží zjišťování služby modulu runtime. Zjišťování služby přijímají zprávy na tento koncový bod.  
  
-   A `<serviceDiscovery>` chování je přidán do `<serviceBehaviors>` části. To umožňuje službě být zjištěny za běhu a používá koncový bod zjišťování pro naslouchání zjišťování bylo zmíněno dříve `Probe` a `Resolve` zprávy. Služba je s těmito přídavky dvě zjistitelný na zadaný koncový bod zjišťování.  
  
 Následující fragment kódu konfigurace zobrazuje služby s koncový bod aplikace a koncový bod zjišťování definované:  
  
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
  
 Přidání koncového bodu oznámení chování služby zjišťování vytvoří výchozí oznámení klienta pro službu. To zaručuje, že služba odešle oznámení online a offline při otevření a zavření v uvedeném pořadí služby.  
  
 Tento konfigurační soubor překročí pouze tyto jednoduchých kroků změnou Další chování. Je možné řídit informace týkající se zjišťování pomocí specifické koncové body. To znamená, uživatel může určit, zda můžete zjistit koncový bod a uživatele můžete také označit tento koncový bod s <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> a vlastních metadat XML. Chcete-li to provést, musíte přidat uživatele `behaviorConfiguration` vlastnost, která má koncový bod aplikace. V tomto případě následující vlastnost je přidána ke koncovému bodu aplikace.  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 Teď pomocí elementu konfigurace chování, můžete řídit související zjišťování atributy. V takovém případě se přidají dva obory pro koncový bod aplikace.  
  
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
  
 Další informace o oborech najdete v tématu [najít zjišťování a kritéria hledání](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Můžete také ovládat konkrétní podrobnosti o koncový bod zjišťování. To se provádí prostřednictvím <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. V této ukázce se mění verzi protokolu použít i přidávání `maxResponseDelay` atributu, jak je znázorněno v následujícím příkladu kódu.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Toto je soubor kompletní konfigurace použité v tomto příkladu:  
  
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
 V konfiguračním souboru aplikace pro klienta `standardEndpoint` typu `dynamicEndpoint` se používá k zjišťování využívat, jak je znázorněno v následujícím fragmentu kódu konfigurace.  
  
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
  
 Když klient používá `dynamicEndpoint`, běhové prostředí provádí zjišťování automaticky. Různá nastavení, které se používají při zjišťování, jako je například názvům definovaným v `discoveryClientSettings` část, která určuje typ koncový bod zjišťování používat:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Najít kritéria použitá pro vyhledání služeb:  
  
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
  
 Tato ukázka rozšiřuje tuto funkci a upraví <xref:System.ServiceModel.Discovery.FindCriteria> používá klienta a také některé vlastnosti standardní `updDiscoveryEndpoint` použít pro vyhledávání. <xref:System.ServiceModel.Discovery.FindCriteria> Jsou upravit tak, aby použít obor a konkrétní `scopeMatchBy` algoritmus, jakož i vlastní ukončení kritéria. Ukázka navíc také ukazuje, jak klient může odesílat elementů XML pomocí `Probe` zprávy. Nakonec jsou některé změny provedené <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jako jsou například verzi protokolu použitou a jak je znázorněno v následujícím souboru konfigurace nastavení pro konkrétní UDP.  
  
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
  
 Zde je konfigurace klientů použitá v ukázce.  
  
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
  
1.  Tato ukázka používá koncových bodů protokolu HTTP a použít tuto ukázku, správné seznamy ACL adresa URL musí být přidán najdete [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti. Spuštěním následujícího příkazu na zvýšená oprávnění měli přidat příslušné seznamy ACL. Můžete nahradit domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, protože je. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Sestavte řešení.  
  
3.  Spusťte spustitelný soubor služby z adresáře sestavení.  
  
4.  Spustíte spustitelný soubor klienta. Všimněte si, že klient je schopna zjistit službu.  
  
## <a name="see-also"></a>Viz také
