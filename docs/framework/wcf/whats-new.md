---
title: Co je nového ve WCF 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], what's new
- Windows Communication Foundation [WCF], what's new
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
ms.openlocfilehash: 8d079613d1970d2a50ddb3449c2a3072010b2c55
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280004"
---
# <a name="whats-new-in-windows-communication-foundation-45"></a>Co je nového ve WCF 4.5

Toto téma popisuje funkce nového na Windows Communication Foundation (WCF) verze 4.5.

## <a name="wcf-simplification-features"></a>Funkce zjednodušení WCF
 Mnoho pracovali jsme usnadnit WCF 4.5 aplikace pro vývoj a údržbu. Další informace najdete v tématu [funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md).

### <a name="task-based-async-support"></a>Podpora asynchronního založené na úlohách
 Ve výchozím nastavení přidejte odkaz na službu generuje vracející úlohy metodám operace asynchronní služby. To se provádí pro synchronní a asynchronní metody. To umožňuje volání operací služby asynchronně pomocí nové založené na úlohách asynchronní programovací model. Při volání metody generované proxy WCF vytvoří objekt úlohy představující asynchronní operaci a vrátí hodnotu, která úloha pro vás. Po dokončení operace dokončení úkolu.  Při provádění asynchronní operace můžete implementovat jako úkolově orientovanou asynchronní operace. Další informace najdete v tématu [synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).

### <a name="simplified-generated-configuration-files"></a>Zjednodušená generovaných konfiguračních souborů
 Při přidání odkazu na službu v sadě Visual Studio nebo pomocí nástroje SvcUtil.exe, je vygenerován soubor konfigurace klienta. V předchozích verzích technologie WCF tyto konfigurační soubory obsahují hodnotu každé vlastnosti vazby i v případě, že její hodnota je výchozí hodnota. Ve WCF 4.5 generovaných konfiguračních souborů obsahují pouze vlastnosti vazby, které jsou nastaveny na jiné než výchozí hodnotu.

 Další informace najdete v tématu [funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md)

### <a name="contract-first-development"></a>Rozvoje prvního kontraktu
 WCF teď obsahují podporu pro rozvoje prvního kontraktu. Svcutl.exe má /serviceContract přepínač, který vám umožní generovat kontrakty služby a dat z dokumentu WSDL.

### <a name="add-service-reference-from-a-portable-subset-project"></a>Přidání odkazu na službu v přenosném dílčím projektu
 Přenosném dílčím projekty povolit programátorům sestavení .NET udržovat stromu jednoho zdrojového kódu a sestavovací systém. současně podporuje více platforem .NET (desktop, Silverlight, Windows Phone a XBOX). Projekty v přenosném dílčím odkazovat pouze na přenosné knihovny .NET, které jsou sestavení rozhraní .NET framework, který můžete použít na jakékoli platformě .NET. Prostředí pro vývojáře je stejné jako přidávání odkazů na služby v rámci jakékoli jiné aplikace klienta WCF. Další informace najdete v tématu [přidat odkaz na službu v projektu přenosná podmnožina](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).

### <a name="aspnet-compatibility-mode-default-changed"></a>Změnit výchozí režim kompatibility ASP.NET
 WCF obsahuje režim kompatibility ASP.NET vývojáři udělit úplný přístup k funkcím v kanálu HTTP technologie ASP.NET při vytváření služeb WCF. Pro použití tohoto režimu, je nutné nastavit `aspNetCompatibilityEnabled` atribut na hodnotu true [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) části souboru Web.config. Kromě toho musí mít všechny služby v této doméně appDomain `RequirementsMode` vlastnost na jeho <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nastavena na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Ve výchozím nastavení <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> je nyní nastaveno na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>. Další informace najdete v tématu [co je nového ve Windows Communication Foundation](../../../docs/framework/wcf/whats-new.md) a [služby WCF a ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).

### <a name="new-transport-default-values"></a>Nové výchozí hodnoty přenosu
 Pro zjednodušení změnili konfiguraci počtu přenosu vlastnost výchozí hodnoty. Další informace najdete v tématu [funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md).

### <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
 <xref:System.Xml.XmlDictionaryReaderQuotas> obsahuje hodnoty konfigurovatelné kvóty pro čtenáře slovníku XML, které omezují množství paměťových prostředků využívaných kodéru při vytváření zprávy. Během těchto kvót je možné konfigurovat, výchozí hodnoty změnily snižovat možnost, že vývojář bude nutné nastavit explicitně. Další informace najdete v tématu [funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md).

### <a name="wcf-configuration-validation"></a>Ověření konfigurace WCF
 Jako součást procesu sestavení v sadě Visual Studio se teď ověřují konfiguračních souborů WCF pro atributy definované v rámci projektu. Pokud se ověření nezdaří, zobrazí se seznam chyby nebo varování ověření v sadě Visual Studio.

### <a name="xml-editor-tooltips"></a>Popisy tlačítek editoru XML
 Aby pomohli se nové i stávající vývojáři služeb WCF ke konfiguraci jeho služeb, editoru XML pro Visual Studio nyní poskytuje popisky pro každý prvek konfigurace a její vlastnosti, které je součástí konfiguračního souboru služby.

## <a name="streaming-improvements"></a>Vylepšení datových proudů
 Přidání podpory pro true asynchronního streamování kde straně odesílání nyní neblokuje vlákna Pokud na straně příjmu není čtení nebo pomalé a tím zvyšuje škálovatelnost čtení. Odebrat omezení do vyrovnávací paměti zpráv, když klient odešle, že se že služba WCF hostovaná zapsal zprávu na službu IIS. Další informace najdete v tématu [funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md).

## <a name="simplifying-exposing-an-endpoint-over-https-with-iis"></a>Usnadnění vystavení koncového bodu prostřednictvím protokolu HTTPS se službou IIS
 Pro zjednodušení zveřejnění koncového bodu prostřednictvím protokolu HTTPS se přidala mapování protokol HTTPS. Pokud chcete povolit koncový bod HTTPS, ujistěte se, že má váš web vazbu HTTPS a nakonfigurovat certifikát SSL a jednoduše povolit HTTPS pro virtuální adresář, který je hostitelem služby. Jestli jsou metadata povolená pro službu, ji budou přístupné přes protokol HTTPS také.

## <a name="generating-a-single-wsdl-document"></a>Generování jednoho WSDL dokument
 Některé balíčky třetích stran zpracování WSDL, nebudou se moct ke zpracování dokumentů WSDL, které mají závislosti na jiných dokumentů prostřednictvím příkazu.  WCF teď umožňuje určit, že všechny informace o WSDL vrátit v jednom dokumentu. Požádat o jediný dokument WSDL připojit "? singleWSDL" na identifikátor URI, pokud se požaduje metadata ze služby.

## <a name="websocket-support"></a>Podpora protokolu WebSocket
 Protokoly Websocket je technologie, která poskytuje skutečnou obousměrnou komunikaci přes porty 80 a 443 s charakteristikami výkonu, podobně jako na TCP. Aby mohly podporovat komunikaci pomocí protokolu WebSocket přenosového byly přidány dva nové vazby. <xref:System.ServiceModel.NetHttpBinding> a <xref:System.ServiceModel.NetHttpsBinding>. Další informace najdete v tématu: [Vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="new-transport-default-values"></a>Nové výchozí hodnoty přenosu
 Následující tabulka popisuje nastavení, které se změnily a kde najít další informace.

|Vlastnost|On|Nová výchozí hodnota|Další informace najdete v tématu|
|--------------|--------|-----------------|------------------------------|
|třídě channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 * počet procesorů|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * počet procesorů pro přenos<br /><br /> 4 \* počtu procesorů pro SMSvcHost.exe|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> [Konfigurace služby Sdílení portů Net.TCP](../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * počet procesorů|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 sekund|[Konfigurace služby sdílení portů Net.TCP](../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)|

## <a name="xml-editor-tooltips"></a>Popisy tlačítek editoru XML
 Aby pomohli se nové i stávající vývojáři služeb WCF ke konfiguraci jeho služeb, editoru XML pro Visual Studio nyní poskytuje popisky pro každý prvek konfigurace a její vlastnosti, které je součástí konfiguračního souboru služby.

## <a name="configuring-wcf-services-in-code"></a>Konfigurace služeb WCF v kódu
 Windows Communication Foundation (WCF) umožňuje vývojářům konfigurovat služeb pomocí konfiguračních souborů nebo kódu.  Konfigurační soubory jsou užitečné, pokud je potřeba nakonfigurovat po nasazení služby. Při použití konfiguračních souborů, odborníci na IT jenom je potřeba aktualizovat konfigurační soubor, žádné rekompilace je povinný. Konfigurační soubory, ale lze komplexní a obtížné na správu. Neexistuje žádná podpora pro ladění konfigurační soubory a konfigurační prvky, které je odkazováno dle názvy, které umožňuje vytváření konfigurační soubory obtížné a náchylné k chybě. WCF můžete také nakonfigurovat v kódu. V dřívějších verzích konfigurace služby WCF (4.0 a starší) v kódu bylo snadné v místním prostředí scénáře <xref:System.ServiceModel.ServiceHost> třída je možné nakonfigurovat koncové body a chování před voláním ServiceHost.Open povolená. Ve scénářích hostovaná na webu, ale nemáte přístup k <xref:System.ServiceModel.ServiceHost> třídy. Konfigurace webového hostovaná služba byla potřeba k vytvoření `System.ServiceModel.ServiceHostFactory` vytvořený <xref:System.ServiceModel.Activation.ServiceHostFactory> a provedení všech potřebných konfigurace. Počínaje .NET 4.5 WCF poskytuje snadný způsob, jak nakonfigurovat i v místním prostředí a web hostované služby v kódu. Další informace najdete v tématu [konfigurace služby WCF v kódu](../../../docs/framework/wcf/configuring-wcf-services-in-code.md).

## <a name="channelfactory-caching"></a>Ukládání do mezipaměti ChannelFactory
 Pomocí klientských aplikací WCF <xref:System.ServiceModel.ChannelFactory%601> třídy za účelem vytvoření komunikačního kanálu službou WCF.  Vytváření <xref:System.ServiceModel.ChannelFactory%601> instance způsobuje zvýšení zatížení, protože zahrnuje následující operace:

1.  Vytváření <xref:System.ServiceModel.Description.ContractDescription> stromu

2.  Odráží všechny požadované typy CLR

3.  Vytváření kanálu zásobníku

4.  Uvolnění prostředků

 Abyste minimalizovali Tato dodatečná režie, WCF můžete ukládat do mezipaměti objektů pro vytváření kanálů při použití proxy serveru klienta WCF. Další informace najdete v tématu [objekt pro vytváření kanálů a ukládání do mezipaměti](../../../docs/framework/wcf/feature-details/channel-factory-and-caching.md).

## <a name="compression-and-the-binary-encoder"></a>Komprese při přenosu a binárního kodéru
 Od verze WCF 4.5 binárního kodéru WCF přidává podporu pro kompresi. Typ komprese, která má nakonfigurovanou <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> vlastnost. Musíte nakonfigurovat klienta a služby <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> vlastnost. Komprese bude fungovat pro protokoly HTTP, HTTPS a protokolu TCP. Pokud klient Určuje použití komprese, ale služba nepodporuje výjimce protokolu je vyvolána označující neshodou protokolu. Další informace najdete v tématu [výběr kodéru zprávy](../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)

## <a name="udp"></a>UDP
 Byla přidána podpora pro přenos UDP, který umožňuje vývojářům zapisovat služby využívající "zprávy vypal a zapomeň" zasílání zpráv. Klient odešle zprávu službě a očekává, že žádná odpověď ze služby.

## <a name="multiple-authentication-support"></a>Podpora více ověřování
 Byla přidána podpora pro podporu více režimů ověřování, jako podporovaný službou IIS, v jednom koncovém bodu WCF při použití přenosového protokolu HTTP a zabezpečení přenosu. Služba IIS umožňuje povolit více režimů ověřování ve virtuálním adresáři, tato funkce umožňuje jednom koncovém bodu WCF podporovat více režimů ověřování povoleno pro virtuální adresář, kde se hostuje službu WCF.

## <a name="idn-support"></a>Podpora IDN
 Byla přidána podpora umožňující službám WCF pomocí mezinárodních názvů domén. Další informace najdete v části [WCF a mezinárodní názvy domén](../../../docs/framework/wcf/feature-details/wcf-and-internationalized-domain-names.md).

## <a name="httpclient"></a>HttpClient
 Novou třídu s názvem <xref:System.Net.Http.HttpClient> byl přidán do značně zjednodušují práci s požadavky HTTP. Další informace najdete v tématu [vytvářet aplikace sociálních sítí a spojení s HTTP services](https://go.microsoft.com/fwlink/?LinkId=231886) a [ukázkou klienta HTTP](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664).

## <a name="configuration-intellisense"></a>Konfigurace technologie Intellisense
 Hodnoty atributů v konfiguračních souborech pro vlastní atributy definované v projektu nyní podporu technologie intellisense usnadňuje práci s konfiguracemi rychle a přesně.

## <a name="configuration-tooltips"></a>Konfigurace popisků
 WCF elementů a atributů teď snadněji muset popisků v editoru XML a přesně identifikovat účel elementu nebo atributu.

## <a name="paste-data-as-classes"></a>Vložte Data jako třídy
 V projektu WCF datové typy definované v souboru XML (jako jsou přístupné na službu) můžete vložit přímo do kódu stránky. Typ XML budou vloženy jako typ CLR. Zobrazit [generování tříd datových typů z XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md) další podrobnosti.

## <a name="webservicehost-and-default-endpoints"></a>Hostitel WebServiceHost a výchozí koncové body
 V sadě Visual Studio 2010 Hostitel WebServiceHost automaticky vytvoří výchozí koncový bod, jestli koncový bod explicitně zadán, nebo ne. V sadě Visual Studio 2012 a novější Hostitel WebServiceHost pouze vytvoří výchozí koncový bod, pokud jsou explicitně přidány žádné koncové body. Pokud se váš klient očekává výchozí koncový bod, můžete explicitně přidat koncový bod a přejděte klienta. Alternativně můžete říct, WCF, které chcete vrátit zpět na předchozí chování přidáním následujícího nastavení do konfiguračního souboru aplikace

```xml
<appSettings>
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>
  </appSettings>
```

## <a name="ihttpcookiecontainermanager"></a>IHttpCookieContainerManager
 Toto rozhraní vystavené <xref:System.ServiceModel.Channels.IChannelFactory%601>, umožňuje pracovat se soubory cookie na straně klienta mnohem jednodušší. Pokud AllowCookies nastavená na hodnotu true na vazbě, dostanete souborů cookie pomocí následujícího kódu:

```csharp
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();
System.Net.CookieContainer container = cookieManager.CookieContainer;
```

 Potom můžete načíst nebo nastavit soubory cookie z <xref:System.Net.CookieContainer>. Když AllowCookies je nastavené na false, můžete ručně načíst soubory cookie v <xref:System.ServiceModel.OperationContext> a odeslat ji v jiných požadavků pomocí jiného <xref:System.ServiceModel.OperationContext> nebo inspektoru zprávy. Rozhraní IHttpCookieContainerManager umožňuje ověřovat uživatele pomocí služby a souboru cookie pro ověřování, vrátí tyto služby používat k ověřování s jinými službami.
