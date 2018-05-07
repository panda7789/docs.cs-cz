---
title: Adresy koncových bodů
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: 46278e35c6966e473f5a800f7e99814efd7b943c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-addresses"></a>Adresy koncových bodů
Každý koncový bod má adresu přidruženo, který se používá k vyhledat a identifikovat koncový bod. Tato adresa se skládá především z identifikátor URI (Uniform Resource), která určuje umístění koncového bodu. Adresa koncového bodu je reprezentována v programovací model Windows Communication Foundation (WCF) pomocí <xref:System.ServiceModel.EndpointAddress> třídy, která obsahuje volitelný <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnost, která umožňuje ověření koncového bodu pomocí dalších koncových bodů, výměnu zpráv s ním a sadu volitelné <xref:System.ServiceModel.EndpointAddress.Headers%2A> vlastnosti, které definují jiné záhlaví SOAP, vyžaduje ke zpřístupnění služby. Zadejte další volitelné hlavičky a podrobnější informace o přidělování k vaší identifikaci nebo interakci s koncový bod služby. Adresa koncového bodu je reprezentován v drátové síti WS-Addressing reference koncového bodu (EPR).  
  
## <a name="uri-structure-of-an-address"></a>Identifikátor URI Struktura adresy  
 Adresa URI pro většinu přenosy má čtyři části. Například čtyři části identifikátoru URI http://www.fabrikam.com:322/mathservice.svc/secureEndpoint může být uvedeno následujícím způsobem:  
  
-   Schéma: http:  
  
-   Počítač: www.fabrikam.com  
  
-   (volitelné) Port: 322  
  
-   Path: /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Definování adresu pro službu  
 Adresa koncového bodu pro služby můžete zadat buď imperativní pomocí kódu nebo deklarativně pomocí konfigurace. Definování koncové body v kódu obvykle není praktické protože jsou obvykle liší od těch, které používá při služby je vyvíjen vazeb a adresy pro v nasazené službě. Obecně je praktičtější definovat koncové body služby pomocí konfigurace, nikoli kódu. Zachování vazby a adresování informace mimo kód vám umožní se změnit bez nutnosti znovu zkompiluje nebo znovu nasadit aplikaci.  
  
### <a name="defining-an-address-in-configuration"></a>Definování adresu v konfiguraci  
 Chcete-li definovat koncový bod v konfiguračním souboru, použijte [ \<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element. Podrobnosti a příklad najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Definování adresu v kódu  
 Adresy koncového bodu se dají vytvářet v kódu pomocí <xref:System.ServiceModel.EndpointAddress> třídy. Podrobnosti a příklad najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>Koncové body v jazyce WSDL  
 Adresy koncového bodu může být také reprezentována v jazyce WSDL jako element WS-Addressing EPR uvnitř odpovídající koncový bod `wsdl:port` elementu. EPR obsahuje adresu pro koncový bod, jakož i všechny vlastnosti adresy. Podrobnosti a příklad najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Více IIS vazby podpora v rozhraní .NET Framework 3.5  
 Poskytovatelé služeb často hostovat mnoho aplikací na stejném serveru a lokality ke zvýšení hustoty lokality a snížit náklady na vlastnictví. Tyto aplikace jsou obvykle vázány na jiné základní adresy. Webovém serveru Internetové informační služby (IIS) může obsahovat více aplikací. Aplikace v lokalitě je přístupná přes jeden nebo více vazby služby IIS.  
  
 Vazby služby IIS poskytují dva kusy informací: protokol vazby a informace o vazbě. Protokol vazby definuje schéma, přes který probíhá komunikace a informace o vazbě je informace, které slouží pro přístup k webu.  
  
 Následující příklad ukazuje, součásti, které mohou existovat v vazbu služby IIS:  
  
-   Vytvoření vazby protokolu: HTTP  
  
-   Informace o vazbě: IP adresu, Port, Hlavička hostitele  
  
 Služba IIS můžete určit víc vazeb pro každou lokalitu, což vede k více základní adresy pro každé schéma. Před verzí [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], WCF nepodporoval více adres pro schéma a, pokud byly zadané, došlo <xref:System.ArgumentException> během aktivace.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Umožňuje poskytovatelům internetových služeb pro hostování více aplikací s jiné základní adresy pro stejné schéma ve stejné lokalitě.  
  
 Například lokality může obsahovat následující základní adresy:  
  
-   http://payroll.myorg.com/Service.svc  
  
-   http://shipping.myorg.com/Service.svc  
  
 S [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], zadejte předponu filtr na úrovni domény aplikace v konfiguračním souboru. Můžete to provést pomocí [ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) element, který obsahuje seznam předpon. Příchozí základní adresy poskytované službou IIS, jsou filtrovány podle seznamu volitelné předponu. Ve výchozím nastavení Pokud není zadána předpony, všechny adresy se předaly. Zadání předpony výsledky pouze odpovídající základní adresu pro tento schéma, které se budou předávat.  
  
 Následuje příklad konfigurace kód, který používá předpona filtry.  
  
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
  
 V předchozím příkladu net.tcp://payroll.myorg.com: 8000 a http://shipping.myorg.com:8000 jsou pouze základní adresy, jejich příslušné schémat, které se předávají prostřednictvím.  
  
 `baseAddressPrefixFilter` Nepodporuje zástupné znaky.  
  
 Základní adresy poskytované službou IIS pravděpodobně adresy vázaný na jiná schémata nejsou k dispozici v `baseAddressPrefixFilters` seznamu. Tyto adresy nejsou odfiltrována.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Služba IIS vazby podpora více v rozhraní .NET Framework 4 a novější  
 Od verze .NET 4, můžete povolit podporu pro víc vazeb ve službě IIS bez nutnosti vyberte jednu základní adresu, a to nastavením <xref:System.ServiceModel.ServiceHostingEnvironment>na <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> nastavení na hodnotu true. Tato podpora je omezena na schémata protokolu HTTP.  
  
 Tady je příklad konfigurace kód, který používá multipleSiteBindingsEnabled na [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Všechna nastavení baseAddressPrefixFilters ignorují pro protokol HTTP a jiných protokolů než HTTP, pokud víc vazeb webu jsou povolené použití tohoto nastavení.  
  
 Podrobnosti a příklady naleznete v tématu [podpora víc vazeb webu IIS](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) a <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.  
  
## <a name="extending-addressing-in-wcf-services"></a>Rozšíření adresování ve službách WCF  
 Výchozí hodnota adresování modelu služby WCF používá adresa URI koncového bodu pro následující účely:  
  
-   Chcete-li určit naslouchání adresu služby, umístění, ve kterém koncový bod přijímá zprávy,  
  
-   Pokud chcete zadat filtr adres protokolu SOAP, adresu koncový bod očekává jako hlavičku protokolu SOAP.  
  
 Hodnoty pro každý z těchto účely lze zadat samostatně, povolení několik rozšíření adres užitečné scénáře této stránky:  
  
-   SOAP prostředníci: zprávy odeslané klientem prochází minimálně jeden další služby, které zpracovat zprávu, než dorazí do cílového místa. SOAP prostředníci můžete provádět různé úlohy, jako je například ukládání do mezipaměti, směrování, Vyrovnávání zatížení nebo schéma ověřování na zprávy. Tento scénář se dosahuje prostřednictvím odesílání zpráv do samostatné fyzické adresy (`via`), která se zaměřuje zprostředkující spíše než jenom na logickou adresu (`wsa:To`), která se zaměřuje ultimate cíl.  
  
-   Naslouchání adresa koncového bodu je privátní identifikátor URI a je nastavena na jinou hodnotu než jeho `listenURI` vlastnost.  
  
 Přenos adresu, kterou `via` Určuje umístění, na kterou má zpráva původně odeslána směrem k některé Vzdálená adresa zadanou `to` parametr, kdy se služba nachází. Ve většině scénářů Internet `via` identifikátoru URI je stejný jako <xref:System.ServiceModel.EndpointAddress.Uri%2A> vlastnost konečné `to` adresa služby. Pouze rozlišit mezi tyto dvě adresy, když je nutné provést ruční směrování.  
  
### <a name="addressing-headers"></a>Adresování hlavičky  
 Koncový bod lze řešit nejméně jedno záhlaví SOAP kromě jeho základní identifikátor URI. Jednu sadu scénáře, kde to je užitečné je sada SOAP zprostředkující scénáře, kde koncového bodu vyžaduje klientům tohoto koncového bodu patří zaměřený na prostředníci hlavičky SOAP.  
  
 Můžete definovat vlastní adresu hlavičky dvěma způsoby – pomocí kódu nebo konfigurace:  
  
-   V kódu, vytvořte vlastní adresu hlavičky pomocí <xref:System.ServiceModel.Channels.AddressHeader> třídy a pak se použije při sestavování <xref:System.ServiceModel.EndpointAddress>.  
  
-   V konfiguraci, vlastní [ \<hlavičky >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) jsou určené jako podřízené objekty [ \<endpoint >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.  
  
 Konfigurace je obecně vhodnější kódu, jak ho můžete změnit hlavičky po nasazení.  
  
### <a name="custom-listening-addresses"></a>Vlastní naslouchání adresy  
 Můžete nastavit adresu naslouchání na jinou hodnotu než identifikátor URI pro koncový bod. To je užitečné v zprostředkující scénářích, kdy adresu SOAP mají být exponovány které veřejné protokolu SOAP zprostředkující, zatímco adresa, kde ve skutečnosti naslouchá koncový bod je a privátní sítě.  
  
 Můžete určit vlastní adresu naslouchání pomocí kódu nebo konfigurace:  
  
-   V kódu, zadejte vlastní adresu naslouchání přidáním <xref:System.ServiceModel.Description.ClientViaBehavior> třída do kolekce chování pro koncový bod.  
  
-   V konfiguraci, zadejte vlastní adresu naslouchání s `ListenUri` atribut služby [ \<endpoint >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.  
  
### <a name="custom-soap-address-filter"></a>Filtr adres vlastní SOAP  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A> Se používá ve spojení s žádným <xref:System.ServiceModel.EndpointAddress.Headers%2A> vlastnost definovat filtr adresy koncového bodu protokolu SOAP (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>). Ve výchozím nastavení, tento filtr ověřuje, že má příchozí zprávy `To` záhlaví zprávy, který se shoduje s koncovým bodem je identifikátor URI a zda jsou všechny hlaviček vyžaduje koncový bod ve zprávě.  
  
 V některých scénářích koncový bod přijímá všechny zprávy, které přicházejí na základní přenos a nikoli pouze ty s příslušnou `To` záhlaví. Chcete-li povolit, uživatel může použít <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> třídy.  
  
## <a name="see-also"></a>Viz také  
 [Zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
