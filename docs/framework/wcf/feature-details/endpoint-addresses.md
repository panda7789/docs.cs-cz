---
title: Adresy koncových bodů
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: 71358ed1c16c3c9b490a41f74dd6319af8eb2e7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593526"
---
# <a name="endpoint-addresses"></a>Adresy koncových bodů
Každý koncový bod má přiřazenou adresu, která se používá k vyhledání a identifikaci koncového bodu. Tato adresa se skládá hlavně z identifikátoru URI (Uniform Resource Identifier), který určuje umístění koncového bodu. Adresa koncového bodu je reprezentovaná v programovacím modelu Windows Communication Foundation (WCF) <xref:System.ServiceModel.EndpointAddress> třídou, která obsahuje volitelnou <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnost, která umožňuje ověřování koncového bodu jinými koncovými body, na kterých se zprávy Exchange, a sadou volitelných <xref:System.ServiceModel.EndpointAddress.Headers%2A> vlastností, které definují jakákoli jiná záhlaví SOAP potřebná k dosažení služby. Volitelné hlavičky obsahují další a podrobnější informace o adresách, které slouží k identifikaci nebo interakci s koncovým bodem služby. Adresa koncového bodu je reprezentovaná na lince jako referenční dokumentace ke službě WS-Addressing Endpoint (EPR).  
  
## <a name="uri-structure-of-an-address"></a>Struktura identifikátoru URI adresy  
 Identifikátor URI adresy pro většinu přenosů má čtyři části. Například čtyři části identifikátoru URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` lze vymezit následujícím způsobem:  
  
- Programu`http:`
  
- Počítačové`www.fabrikam.com`  
  
- volitelné Port: 322  
  
- Cesta:/mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Definování adresy pro službu  
 Adresu koncového bodu pro službu lze zadat buď imperativně pomocí kódu, nebo deklarativně prostřednictvím konfigurace. Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby. Obecně je praktické definovat koncové body služby pomocí konfigurace namísto kódu. Zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.  
  
### <a name="defining-an-address-in-configuration"></a>Definování adresy v konfiguraci  
 Chcete-li definovat koncový bod v konfiguračním souboru, použijte [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element. Podrobnosti a příklad najdete v tématu [určení adresy koncového bodu](../specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Definování adresy v kódu  
 Adresa koncového bodu může být vytvořena v kódu s <xref:System.ServiceModel.EndpointAddress> třídou. Podrobnosti a příklad najdete v tématu [určení adresy koncového bodu](../specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>Koncové body v jazyce WSDL  
 Adresa koncového bodu může být také reprezentovaná v jazyce WSDL jako element WS-Addressing EPR uvnitř odpovídajícího elementu koncového bodu `wsdl:port` . EPR obsahuje adresu koncového bodu a také všechny vlastnosti adresy. Podrobnosti a příklad najdete v tématu [určení adresy koncového bodu](../specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Podpora více vazeb služby IIS v .NET Framework 3,5  
 Poskytovatelé internetových služeb často hostují mnoho aplikací na stejném serveru a webu, aby zvýšili hustotu lokalit a snížili celkové náklady na vlastnictví. Tyto aplikace jsou obvykle svázány s různými základními adresami. Web Internetová informační služba (IIS) může obsahovat více aplikací. K aplikacím v lokalitě je možné přistupovat prostřednictvím jedné nebo více vazeb služby IIS.  
  
 Vazby služby IIS poskytují dvě části informací: protokol vazby a informace o vazbě. Protokol vazby definuje schéma, přes které probíhá komunikace, a informace o vazbě, které slouží k přístupu k webu.  
  
 Následující příklad ukazuje komponenty, které mohou být k dispozici ve vazbě služby IIS:  
  
- Protokol vazby: HTTP  
  
- Informace o vazbě: IP adresa, port, Hlavička hostitele  
  
 Služba IIS může pro každou lokalitu určit více vazeb, což má za následek více základních adres pro každé schéma. Před .NET Framework 3,5 WCF nepodporovalo více adres pro schéma a v případě, že byly zadány, vyvolala <xref:System.ArgumentException> během aktivace.  
  
 .NET Framework 3,5 umožňuje poskytovatelům internetových služeb hostovat více aplikací s různými základními adresami pro stejné schéma ve stejné lokalitě.  
  
 Například lokalita může obsahovat následující základní adresy:  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 V .NET Framework 3,5 zadáte filtr předpon na úrovni domény v konfiguračním souboru. Provedete to pomocí [\<baseAddressPrefixFilters>](../../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) elementu, který obsahuje seznam předpon. Příchozí základní adresy, které poskytuje služba IIS, se filtrují na základě volitelného seznamu předpon. Ve výchozím nastavení, pokud není zadána předpona, jsou předány všechny adresy. Zadáním předpony vydáte pouze odpovídající základní adresu pro dané schéma.  
  
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
  
 V předchozím příkladu `net.tcp://payroll.myorg.com:8000` a `http://shipping.myorg.com:8000` jsou jedinou základní adresou pro jejich příslušné systémy, které jsou předány.  
  
 Nepodporuje `baseAddressPrefixFilter` zástupné znaky.  
  
 Základní adresy poskytované službou IIS mohou mít adresy svázané s jinými schématy, které nejsou uvedeny v `baseAddressPrefixFilters` seznamu. Tyto adresy nejsou vyfiltrovány.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Podpora více vazeb služby IIS v .NET Framework 4 a novějších verzích  
 Od rozhraní .NET 4 můžete povolit podporu více vazeb ve službě IIS bez nutnosti vybírat jednu základní adresu, nastavením nastavení <xref:System.ServiceModel.ServiceHostingEnvironment> <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> na hodnotu true. Tato podpora je omezená na schémata protokolu HTTP.  
  
 Následuje příklad konfiguračního kódu, který používá multipleSiteBindingsEnabled [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) .  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Všechna nastavení baseAddressPrefixFilters jsou pro protokoly HTTP i non-HTTP ignorována, pokud je pomocí tohoto nastavení povoleno více vazeb mezi lokalitami.  
  
 Podrobnosti a příklady najdete v tématu [Podpora více vazeb webu IIS](supporting-multiple-iis-site-bindings.md) a <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> .  
  
## <a name="extending-addressing-in-wcf-services"></a>Rozšiřování adres ve službách WCF  
 Výchozí model adresování služeb WCF používá identifikátor URI adresy koncového bodu pro následující účely:  
  
- Chcete-li zadat adresu naslouchání služby, umístění, kde koncový bod naslouchá zprávám,  
  
- Chcete-li zadat filtr adres SOAP, adresa, kterou koncový bod očekává jako hlavičku protokolu SOAP.  
  
 Hodnoty pro každý z těchto účelů se dají zadat samostatně, což umožňuje několik rozšíření adres, která se týkají užitečných scénářů:  
  
- Zprostředkovatelé SOAP: zpráva odeslaná klientem projde jednu nebo více dalších služeb, které zpracovávají zprávu předtím, než dosáhnou konečného cíle. Zprostředkovatelé SOAP můžou pro zprávy provádět různé úkoly, jako je ukládání do mezipaměti, směrování, Vyrovnávání zatížení nebo ověřování schématu. Tento scénář je možné provést odesláním zpráv na samostatnou fyzickou adresu ( `via` ), která cílí na zprostředkovatele, a ne jenom na logickou adresu ( `wsa:To` ), která cílí na konečné cíle.  
  
- Přijímající adresa koncového bodu je privátní identifikátor URI a je nastaven na jinou hodnotu než jeho `listenURI` vlastnost.  
  
 Přenosová adresa, kterou `via` Určuje, je umístění, do kterého má být zpráva zpočátku odeslána, na jinou vzdálenou adresu určenou `to` parametrem, ve kterém je služba umístěna. Ve většině scénářů v Internetu `via` je identifikátor URI stejný jako <xref:System.ServiceModel.EndpointAddress.Uri%2A> vlastnost konečné `to` adresy služby. V případě ručního směrování musíte rozlišovat jenom mezi těmito dvěma adresami.  
  
### <a name="addressing-headers"></a>Hlavičky adresování  
 Kromě základního identifikátoru URI může koncový bod adresovat jedna nebo více hlaviček SOAP. Jedna sada scénářů, kde je to užitečné, je sada zprostředkujících scénářů SOAP, kdy koncový bod vyžaduje, aby klienti tohoto koncového bodu zahrnuli hlavičky SOAP cílené na zprostředkovatele.  
  
 Vlastní hlavičky adres můžete definovat dvěma způsoby – buď pomocí kódu, nebo konfigurace:  
  
- V kódu vytvořte vlastní záhlaví adres pomocí <xref:System.ServiceModel.Channels.AddressHeader> třídy a pak použijte při konstrukci <xref:System.ServiceModel.EndpointAddress> .  
  
- V konfiguraci jsou vlastní [\<headers>](../../configure-apps/file-schema/wcf/headers.md) prvky zadány jako podřízené položky [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu.  
  
 Konfigurace je obecně vhodnější pro kód, protože umožňuje změnit hlavičky po nasazení.  
  
### <a name="custom-listening-addresses"></a>Vlastní naslouchající adresy  
 Můžete nastavit naslouchající adresu na jinou hodnotu, než je identifikátor URI koncového bodu. To je užitečné ve zprostředkujících scénářích, kde je adresa SOAP vystavena jako veřejná zprostředkovatel SOAP, zatímco adresa, kde aktuálně naslouchá koncový bod, je adresa privátní sítě.  
  
 Vlastní naslouchající adresu můžete zadat buď pomocí kódu, nebo podle konfigurace:  
  
- V kódu zadejte vlastní naslouchající adresu přidáním <xref:System.ServiceModel.Description.ClientViaBehavior> třídy do kolekce chování koncového bodu.  
  
- V části Konfigurace zadejte vlastní naslouchající adresu s `ListenUri` atributem [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) elementu služby.  
  
### <a name="custom-soap-address-filter"></a>Vlastní filtr adres SOAP  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A>Používá se ve spojení s jakoukoliv <xref:System.ServiceModel.EndpointAddress.Headers%2A> vlastností k definování filtru adres SOAP koncového bodu ( <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ). Ve výchozím nastavení tento filtr ověřuje, že příchozí zpráva má `To` záhlaví zprávy odpovídající identifikátoru URI koncového bodu a že ve zprávě jsou přítomna všechna požadovaná záhlaví koncových bodů.  
  
 V některých případech koncový bod obdrží všechny zprávy, které dorazí na příslušný přenos, a ne pouze ty s odpovídající `To` hlavičkou. Chcete-li tuto možnost povolit, může uživatel použít <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> třídu.  
  
## <a name="see-also"></a>Viz také

- [Zadání adresy koncového bodu](../specifying-an-endpoint-address.md)
- [Identita a ověřování služby](service-identity-and-authentication.md)
