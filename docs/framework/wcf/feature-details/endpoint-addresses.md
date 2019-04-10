---
title: Adresy koncových bodů
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: f59b8403ecb683dafa6963565da46e517b5a2cbc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220432"
---
# <a name="endpoint-addresses"></a>Adresy koncových bodů
Každý koncový bod má adresu přidruženo, který se používá k vyhledání a identifikaci koncového bodu. Tato adresa sestává především z identifikátor URI (Uniform Resource), která určuje umístění koncového bodu. Adresa koncového bodu je vyjádřena v programovacím modelu pomocí rozhraní Windows Communication Foundation (WCF) <xref:System.ServiceModel.EndpointAddress> třídu, která obsahuje volitelný <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnost, která umožňuje ověření koncového bodu jiné koncové body, které vyměňovat zprávy a sadu volitelné <xref:System.ServiceModel.EndpointAddress.Headers%2A> vlastnosti, které definují další hlavičky SOAP, vyžaduje ke zpřístupnění služby. Poskytují další volitelné záhlaví a podrobnější informace o adresách k vaší identifikaci nebo interakci s koncový bod služby. Adresa koncového bodu je reprezentována na lince jako referenci koncového bodu WS-Addressing (EPR).  
  
## <a name="uri-structure-of-an-address"></a>Identifikátor URI struktury adresy  
 Adresa URI pro většinu přenosy obsahuje čtyři části. Například čtyři části identifikátoru URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` může být uvedeno následujícím způsobem:  
  
-   Schéma: `http:`
  
-   Počítač: `www.fabrikam.com`  
  
-   (volitelné) Port: 322  
  
-   Path: /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Definování adresy pro služby  
 Adresa koncového bodu služby lze zadat buď imperativně pomocí kódu nebo deklarativně prostřednictvím konfigurace. Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby. Obecně je praktičtější k definování koncových bodů služby pomocí konfigurace namísto kódu. Udržování vazby a adresování informace mimo kód umožňující změnit bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci.  
  
### <a name="defining-an-address-in-configuration"></a>Definování adresy v konfiguraci  
 Chcete-li definovat koncový bod v konfiguračním souboru, použijte [ \<koncový bod >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu. Podrobnosti a příklad najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Definování adresy v kódu  
 Adresy koncového bodu je možné vytvořit v kódu pomocí <xref:System.ServiceModel.EndpointAddress> třídy. Podrobnosti a příklad najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>Koncové body v jazyce WSDL  
 Adresy koncového bodu můžou být vyjádřeny i v jazyce WSDL jako element WS-Addressing EPR uvnitř odpovídající koncový bod `wsdl:port` elementu. EPR obsahuje adresu koncového bodu, jakož i všechny vlastnosti adresy. Podrobnosti a příklad najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Více IIS vazby podpora v rozhraní .NET Framework 3.5  
 Poskytovatelé internetového připojení často hostovat mnoho aplikací na stejný server a server pro zvýšení hustoty lokality a snížení celkových nákladů na vlastnictví. Tyto aplikace jsou obvykle vázány na jiné základní adresy. Na serveru Internetové informační služby (IIS) webu může obsahovat více aplikací. Aplikace v lokalitě přístupné prostřednictvím jedné nebo více vazeb služby IIS.  
  
 Vazby služby IIS poskytuje dva druhy údajů: protokol vazby a informace o vazbě. Protokol vazby definuje schéma, přes které probíhá komunikace a informace o vazbě je informace, které slouží pro přístup k webu.  
  
 Následující příklad ukazuje součásti, které mohou být přítomny v vazbu služby IIS:  
  
-   Vazba protokolu: HTTP  
  
-   Informace o vazbě: IP adresu, Port, Hlavička hostitele  
  
 Služba IIS můžete určit víc vazeb pro každou lokalitu, což vede k více bázové adresy pro každé schéma. Před verzí [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], WCF nepodporují více adres pro schéma a pokud byl zadán, vyvolala <xref:System.ArgumentException> během aktivace.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Umožňuje poskytovatelům služeb sítě Internet k hostování více aplikací s jinou bázové adresy pro stejné schéma na stejném místě.  
  
 Web může obsahovat například následující základní adresy:  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 S [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], zadejte předponu filtr na úrovni AppDomain v konfiguračním souboru. To provedete [ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) element, který obsahuje seznam předpon. Příchozí základní adresy poskytované službou IIS, jsou filtrovány podle seznamu volitelné předpony. Ve výchozím nastavení Pokud není zadána předponu, všechny adresy se předaly. Určení výsledky předponu v pouze odpovídající základní adresa pro toto schéma, které se budou předávat.  
  
 Následuje příklad konfiguračního kódu, který používá filtry předponu.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 V předchozím příkladu `net.tcp://payroll.myorg.com:8000` a `http://shipping.myorg.com:8000` jsou pouze základní adresy pro jejich příslušných systémů, které jsou předány prostřednictvím.  
  
 `baseAddressPrefixFilter` Nepodporuje zástupné znaky.  
  
 Základní adresy poskytované službou IIS pravděpodobně vázán na jiná schémata není k dispozici v adresy `baseAddressPrefixFilters` seznamu. Tyto adresy nejsou odfiltrovány.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Více podpora služby IIS vazby v rozhraní .NET Framework 4 a novější  
 Od verze .NET 4, můžete povolit podporu pro víc vazeb ve službě IIS bez nutnosti vybrat jednu základní adresu, tak, že nastavíte <xref:System.ServiceModel.ServiceHostingEnvironment>společnosti <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> nastavení na hodnotu true. Tato podpora je omezena na schémata protokolu HTTP.  
  
 Následuje příklad konfiguračního kódu, který používá multipleSiteBindingsEnabled na [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Všechna nastavení baseAddressPrefixFilters ignorovány pro protokol HTTP a jiných protokolů než HTTP, pokud víc vazeb webu jsou povolené použití tohoto nastavení.  
  
 Podrobnosti a příklady najdete v tématu [podpora víc vazeb webu IIS](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) a <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.  
  
## <a name="extending-addressing-in-wcf-services"></a>Rozšíření adresování ve službách WCF  
 Výchozí adresování model služeb WCF používá adresu koncového bodu identifikátor URI pro následující účely:  
  
-   Chcete-li určit naslouchání adresu služby, umístění, ve kterém naslouchá koncový bod pro zprávy,  
  
-   Pokud chcete zadat filtr adres protokolu SOAP, adresu koncového bodu očekává jako záhlaví SOAP.  
  
 Hodnoty pro každou z těchto důvodů se dá nastavit zvlášť, umožňuje několik rozšíření adresování tohoto scénáře titulní užitečné:  
  
-   Zprostředkovatelů SOAP: zpráva odeslaná klientem, prochází přes jeden nebo více dalších služeb, které zpracovávají zprávy předtím, než dosáhne konečného cíle. Zprostředkovatelů SOAP můžete provádět různé úlohy, jako je například ukládání do mezipaměti, směrování, Vyrovnávání zatížení nebo schéma ověřování na zprávy. Tento scénář lze dosáhnout odesílání zpráv do samostatné fyzické adresy (`via`), který cílí zprostředkující spíše než jenom do logického adresního (`wsa:To`), který cílí na ultimate cíl.  
  
-   Naslouchání adresu koncového bodu je privátní identifikátor URI a je nastavena na jinou hodnotu než jeho `listenURI` vlastnost.  
  
 Adresy, které jsou přenos `via` Určuje umístění, ke kterému by měl zprávu nejdřív pošle na cestě na jiných vzdálených adres podle `to` parametr, ve kterém se služba nachází. Ve většině scénářů Internetu `via` identifikátor URI je stejné jako <xref:System.ServiceModel.EndpointAddress.Uri%2A> vlastnost finální `to` adresu služby. Pouze rozlišovat mezi tyto dvě adresy, když je nutné provést ruční směrování.  
  
### <a name="addressing-headers"></a>Hlavičky adresy  
 Koncový bod vyřešíte tak, že jednu nebo víc hlaviček SOAP kromě svůj základní identifikátor URI. Jedna sada scénáře, kde je to užitečné je sada SOAP zprostředkující scénáře, kdy vyžaduje, aby koncový bod klientům tohoto koncového bodu zahrnout záhlaví SOAP určenou pro zprostředkovatele.  
  
 Můžete definovat vlastní adresu záhlaví dvěma způsoby – buď prostřednictvím kódu nebo konfigurace:  
  
-   V kódu, vytvořte vlastní adresu záhlaví pomocí <xref:System.ServiceModel.Channels.AddressHeader> třídy a pak použije v procesu vytváření <xref:System.ServiceModel.EndpointAddress>.  
  
-   V konfiguraci, vlastní [ \<záhlaví >](../../configure-apps/file-schema/wcf/headers.md) jsou určené jako podřízené objekty [ \<koncový bod >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu.  
  
 Konfigurace je obecně vhodnější pro kódování, jak to vám umožní změnit záhlaví po nasazení.  
  
### <a name="custom-listening-addresses"></a>Vlastní naslouchání adresy  
 Můžete nastavit adresu naslouchání na jinou hodnotu než identifikátor URI koncového bodu. To je užitečné v zprostředkující scénářích, kdy adresu SOAP zpřístupní které veřejné SOAP zprostředkující, že adresa, ve kterém ve skutečnosti naslouchá koncový bod je privátní síť.  
  
 Můžete zadat vlastní adresu naslouchání pomocí kódu nebo konfigurace:  
  
-   V kódu, zadejte vlastní adresu naslouchání tak, že přidáte <xref:System.ServiceModel.Description.ClientViaBehavior> třídy do kolekce chování koncového bodu.  
  
-   V konfiguraci, zadejte vlastní adresu naslouchání s `ListenUri` atribut služby [ \<koncový bod >](../../configure-apps/file-schema/wcf/endpoint-element.md) elementu.  
  
### <a name="custom-soap-address-filter"></a>Filtr adresy vlastního protokolu SOAP  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A> Se používá ve spojení s některým <xref:System.ServiceModel.EndpointAddress.Headers%2A> vlastnost pro definování filtr adresy koncového bodu SOAP (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>). Ve výchozím nastavení, tento filtr ověří, jestli příchozí zprávy `To` záhlaví zprávy, který se shoduje s koncovým bodem je identifikátor URI a všechny hlavičky vyžaduje koncový bod se nacházejí ve zprávě.  
  
 V některých scénářích, koncový bod přijímá všechny zprávy, které přicházejí na základní přenos a nejen ti s odpovídající `To` záhlaví. Chcete-li povolit, může uživatel použít <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> třídy.  
  
## <a name="see-also"></a>Viz také:

- [Zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)
- [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
