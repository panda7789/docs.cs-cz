---
title: Adresy koncových bodů
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: cbae03c52f3cc39f7afd422a34b16e99a60d9f3a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283223"
---
# <a name="endpoint-addresses"></a>Adresy koncových bodů
Každý koncový bod má přiřazenou adresu, která se používá k vyhledání a identifikaci koncového bodu. Tato adresa se skládá hlavně z identifikátoru URI (Uniform Resource Identifier), který určuje umístění koncového bodu. Adresa koncového bodu je reprezentována v programovacím modelu Windows Communication Foundation (WCF) pomocí <xref:System.ServiceModel.EndpointAddress> třídy, která obsahuje volitelnou <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnost, která umožňuje ověřování koncového bodu jinými koncovými body, které se v něm vyměňují zprávy, a sadu volitelných <xref:System.ServiceModel.EndpointAddress.Headers%2A> vlastností, které definují jakákoli jiná záhlaví SOAP potřebná k dosažení služby. Volitelné hlavičky obsahují další a podrobnější informace o adresách, které slouží k identifikaci nebo interakci s koncovým bodem služby. Adresa koncového bodu je reprezentovaná na lince jako referenční dokumentace ke službě WS-Addressing Endpoint (EPR).  
  
## <a name="uri-structure-of-an-address"></a>Struktura identifikátoru URI adresy  
 Identifikátor URI adresy pro většinu přenosů má čtyři části. Například čtyři části `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` identifikátoru URI lze vymezit následujícím způsobem:  
  
- Schéma: `http:`
  
- Počítač: `www.fabrikam.com`  
  
- volitelné Port: 322  
  
- Path: /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Definování adresy pro službu  
 Adresu koncového bodu pro službu lze zadat buď imperativně pomocí kódu, nebo deklarativně prostřednictvím konfigurace. Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby. Obecně je praktické definovat koncové body služby pomocí konfigurace namísto kódu. Zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.  
  
### <a name="defining-an-address-in-configuration"></a>Definování adresy v konfiguraci  
 Pokud chcete v konfiguračním souboru definovat koncový bod, použijte [> elementu\<koncového bodu](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) . Podrobnosti a příklad najdete v tématu [určení adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Definování adresy v kódu  
 Adresa koncového bodu může být vytvořena v kódu pomocí třídy <xref:System.ServiceModel.EndpointAddress>. Podrobnosti a příklad najdete v tématu [určení adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>Koncové body v jazyce WSDL  
 Adresa koncového bodu může být také reprezentovaná v jazyce WSDL jako element WS-Addressing EPR uvnitř elementu `wsdl:port` příslušného koncového bodu. EPR obsahuje adresu koncového bodu a také všechny vlastnosti adresy. Podrobnosti a příklad najdete v tématu [určení adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Podpora více vazeb služby IIS v .NET Framework 3,5  
 Poskytovatelé internetových služeb často hostují mnoho aplikací na stejném serveru a webu, aby zvýšili hustotu lokalit a snížili celkové náklady na vlastnictví. Tyto aplikace jsou obvykle svázány s různými základními adresami. Web Internetová informační služba (IIS) může obsahovat více aplikací. K aplikacím v lokalitě je možné přistupovat prostřednictvím jedné nebo více vazeb služby IIS.  
  
 Vazby služby IIS poskytují dvě části informací: protokol vazby a informace o vazbě. Protokol vazby definuje schéma, přes které probíhá komunikace, a informace o vazbě, které slouží k přístupu k webu.  
  
 Následující příklad ukazuje komponenty, které mohou být k dispozici ve vazbě služby IIS:  
  
- Protokol vazby: HTTP  
  
- Informace o vazbě: IP adresa, port, Hlavička hostitele  
  
 Služba IIS může pro každou lokalitu určit více vazeb, což má za následek více základních adres pro každé schéma. Před .NET Framework 3,5 WCF nepodporovalo více adres pro schéma a v případě, že byly zadány, vyvolalo během aktivace <xref:System.ArgumentException>.  
  
 .NET Framework 3,5 umožňuje poskytovatelům internetových služeb hostovat více aplikací s různými základními adresami pro stejné schéma ve stejné lokalitě.  
  
 Například lokalita může obsahovat následující základní adresy:  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 V .NET Framework 3,5 zadáte filtr předpon na úrovni domény v konfiguračním souboru. Můžete to provést pomocí elementu [\<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) , který obsahuje seznam předpon. Příchozí základní adresy, které poskytuje služba IIS, se filtrují na základě volitelného seznamu předpon. Ve výchozím nastavení, pokud není zadána předpona, jsou předány všechny adresy. Zadáním předpony vydáte pouze odpovídající základní adresu pro dané schéma.  
  
 Následuje příklad konfiguračního kódu, který používá filtry předpony.  
  
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
  
 V předchozím příkladu jsou `net.tcp://payroll.myorg.com:8000` a `http://shipping.myorg.com:8000` jedinou základní adresou pro jejich příslušné systémy, které jsou předány.  
  
 `baseAddressPrefixFilter` nepodporuje zástupné znaky.  
  
 Základní adresy poskytované službou IIS mohou mít adresy svázané s jinými schématy, které nejsou k dispozici v seznamu `baseAddressPrefixFilters`. Tyto adresy nejsou vyfiltrovány.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Podpora více vazeb služby IIS v .NET Framework 4 a novějších verzích  
 Od rozhraní .NET 4 můžete povolit podporu více vazeb ve službě IIS bez výběru jedné základní adresy nastavením <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> nastavení <xref:System.ServiceModel.ServiceHostingEnvironment>na hodnotu true. Tato podpora je omezená na schémata protokolu HTTP.  
  
 Následuje příklad konfiguračního kódu, který používá multipleSiteBindingsEnabled v [>\<serviceHostingEnvironment](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Všechna nastavení baseAddressPrefixFilters jsou pro protokoly HTTP i non-HTTP ignorována, pokud je pomocí tohoto nastavení povoleno více vazeb mezi lokalitami.  
  
 Podrobnosti a příklady najdete v tématu [Podpora více vazeb webu IIS](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) a <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.  
  
## <a name="extending-addressing-in-wcf-services"></a>Rozšiřování adres ve službách WCF  
 Výchozí model adresování služeb WCF používá identifikátor URI adresy koncového bodu pro následující účely:  
  
- Chcete-li zadat adresu naslouchání služby, umístění, kde koncový bod naslouchá zprávám,  
  
- Chcete-li zadat filtr adres SOAP, adresa, kterou koncový bod očekává jako hlavičku protokolu SOAP.  
  
 Hodnoty pro každý z těchto účelů se dají zadat samostatně, což umožňuje několik rozšíření adres, která se týkají užitečných scénářů:  
  
- Zprostředkovatelé SOAP: zpráva odeslaná klientem projde jednu nebo více dalších služeb, které zpracovávají zprávu předtím, než dosáhnou konečného cíle. Zprostředkovatelé SOAP můžou pro zprávy provádět různé úkoly, jako je ukládání do mezipaměti, směrování, Vyrovnávání zatížení nebo ověřování schématu. Tento scénář je možné provést odesláním zpráv na samostatnou fyzickou adresu (`via`), která cílí na zprostředkující místo jenom na logickou adresu (`wsa:To`), která cílí na konečný cíl.  
  
- Přijímající adresa koncového bodu je privátní identifikátor URI a je nastaven na jinou hodnotu než vlastnost `listenURI`.  
  
 Přenosová adresa, kterou `via` určuje, je umístění, do kterého má být zpráva zpočátku odeslána, na jinou vzdálenou adresu určenou parametrem `to`, na kterém je služba umístěna. Ve většině scénářů v Internetu je `via` identifikátor URI stejný jako vlastnost <xref:System.ServiceModel.EndpointAddress.Uri%2A> konečné `to` adresy služby. V případě ručního směrování musíte rozlišovat jenom mezi těmito dvěma adresami.  
  
### <a name="addressing-headers"></a>Hlavičky adresování  
 Kromě základního identifikátoru URI může koncový bod adresovat jedna nebo více hlaviček SOAP. Jedna sada scénářů, kde je to užitečné, je sada zprostředkujících scénářů SOAP, kdy koncový bod vyžaduje, aby klienti tohoto koncového bodu zahrnuli hlavičky SOAP cílené na zprostředkovatele.  
  
 Vlastní hlavičky adres můžete definovat dvěma způsoby – buď pomocí kódu, nebo konfigurace:  
  
- V kódu vytvořte vlastní záhlaví adres pomocí třídy <xref:System.ServiceModel.Channels.AddressHeader> a pak použijte při konstrukci <xref:System.ServiceModel.EndpointAddress>.  
  
- V konfiguraci jsou vlastní [\<hlaviček >](../../configure-apps/file-schema/wcf/headers.md) zadány jako podřízené prvky [>ho koncového bodu\<](../../configure-apps/file-schema/wcf/endpoint-of-client.md) .  
  
 Konfigurace je obecně vhodnější pro kód, protože umožňuje změnit hlavičky po nasazení.  
  
### <a name="custom-listening-addresses"></a>Vlastní naslouchající adresy  
 Můžete nastavit naslouchající adresu na jinou hodnotu, než je identifikátor URI koncového bodu. To je užitečné ve zprostředkujících scénářích, kde je adresa SOAP vystavena jako veřejná zprostředkovatel SOAP, zatímco adresa, kde aktuálně naslouchá koncový bod, je adresa privátní sítě.  
  
 Vlastní naslouchající adresu můžete zadat buď pomocí kódu, nebo podle konfigurace:  
  
- V kódu zadejte vlastní naslouchající adresu přidáním třídy <xref:System.ServiceModel.Description.ClientViaBehavior> do kolekce chování koncového bodu.  
  
- V části Konfigurace zadejte vlastní naslouchající adresu s atributem `ListenUri` [\<elementu koncového bodu služby >](../../configure-apps/file-schema/wcf/endpoint-element.md) .  
  
### <a name="custom-soap-address-filter"></a>Vlastní filtr adres SOAP  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A> se používá společně s jakoukoliv vlastností <xref:System.ServiceModel.EndpointAddress.Headers%2A> k definování filtru adres SOAP koncového bodu (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>). Ve výchozím nastavení tento filtr ověřuje, že příchozí zpráva má `To` záhlaví zprávy odpovídající identifikátoru URI koncového bodu a že ve zprávě jsou přítomna všechna požadovaná záhlaví koncových bodů.  
  
 V některých případech koncový bod obdrží všechny zprávy, které dorazí na příslušný přenos, a ne pouze ty, které mají odpovídající hlavičku `To`. Chcete-li tuto možnost povolit, může uživatel použít třídu <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>.  
  
## <a name="see-also"></a>Viz také:

- [Zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)
- [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
