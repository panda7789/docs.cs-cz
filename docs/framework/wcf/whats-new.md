---
title: Co je nového ve WCF 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], what's new
- Windows Communication Foundation [WCF], what's new
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
ms.openlocfilehash: b22266efe2e775acd04c400cf9da50bffab28183
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449501"
---
# <a name="whats-new-in-windows-communication-foundation-45"></a>Co je nového ve WCF 4.5

Toto téma popisuje nové funkce Windows Communication Foundation (WCF) verze 4,5.

## <a name="wcf-simplification-features"></a>Funkce zjednodušení WCF

Pro snazší vývoj a údržbu aplikací WCF 4,5 bylo provedeno mnoho práce. Další informace najdete v tématu [funkce pro zjednodušení služby WCF](wcf-simplification-features.md).

### <a name="task-based-async-support"></a>Asynchronní podpora založená na úlohách

Ve výchozím nastavení Přidat odkaz na službu generuje metody asynchronních operací služby, které vrací úlohy. Tato operace se provádí pro synchronní i asynchronní metody. To umožňuje asynchronní volání operací služby pomocí nového asynchronního programovacího modelu založeného na úlohách. Při volání vygenerované metody proxy vytvoří WCF objekt Task, který reprezentuje asynchronní operaci a vrátí tento úkol. Úkol se dokončí, až se operace dokončí. Při implementaci asynchronní operace ji můžete implementovat jako asynchronní operaci založenou na úlohách. Další informace naleznete v tématu [synchronní a asynchronní operace](synchronous-and-asynchronous-operations.md).

### <a name="simplified-generated-configuration-files"></a>Zjednodušené generované konfigurační soubory

Když přidáte odkaz na službu v aplikaci Visual Studio nebo použijete nástroj SvcUtil. exe, vygeneruje se konfigurační soubor klienta. V předchozích verzích služby WCF tyto konfigurační soubory obsahovaly hodnotu každé vlastnosti vazby, a to i v případě, že její hodnota je výchozí hodnota. Ve WCF 4,5 generované konfigurační soubory obsahují pouze vlastnosti vazby, které jsou nastaveny na hodnotu, která není výchozí.

Další informace najdete v tématu [funkce pro zjednodušení služby WCF](wcf-simplification-features.md).

### <a name="contract-first-development"></a>Vývoj pro první smlouvu

WCF teď podporuje vývoj pro první smlouvu. Svcutil. exe má přepínač/serviceContract, který umožňuje vygenerovat kontrakty služeb a dat z dokumentu WSDL.

### <a name="add-service-reference-from-a-portable-subset-project"></a>Přidat odkaz na službu z přenositelné podmnožiny projektu

Přenositelné podmnožiny projektů umožňují programátorům sestavení .NET udržovat jeden zdrojový strom a systém sestavení a přitom stále podporovat více platforem .NET (Desktop, Silverlight, Windows Phone a Xbox). Přenositelné Podmnožinové projekty odkazují pouze na přenosné knihovny .NET, které jsou sestaveními, která lze použít na libovolné platformě .NET. Prostředí pro vývojáře je stejné jako přidání odkazu na službu do jakékoli jiné klientské aplikace WCF. Další informace naleznete v tématu [Přidat odkaz na službu v přenositelné podmnožině projektu](add-service-reference-in-a-portable-subset-project.md).

### <a name="aspnet-compatibility-mode-default-changed"></a>Režim kompatibility ASP.NET se ve výchozím nastavení změnil

Služba WCF poskytuje ASP.NET režim kompatibility pro udělení přístupu vývojářům úplný přístup k funkcím v kanálu HTTP ASP.NET při psaní služeb WCF. Chcete-li použít tento režim, je nutné nastavit atribut `aspNetCompatibilityEnabled` na hodnotu true v části [\<serviceHostingEnvironment >](../configure-apps/file-schema/wcf/servicehostingenvironment.md) souboru Web. config. Kromě toho musí mít kterákoli služba v této doméně appDomain vlastnost `RequirementsMode` v <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nastavená na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Ve výchozím nastavení je <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nyní nastaveno na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>. Další informace najdete v tématu [služby WCF a ASP.NET](./feature-details/wcf-services-and-aspnet.md).

### <a name="new-transport-default-values"></a>Nové výchozí hodnoty přenosu

Aby se zjednodušila konfigurace, změnila se počet výchozích hodnot vlastností přenosu. Další informace najdete v tématu [funkce pro zjednodušení služby WCF](wcf-simplification-features.md).

### <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas> obsahuje konfigurovatelné hodnoty kvóty pro čtečky slovníku XML, které omezují velikost paměti využívané kodérem při vytváření zprávy. I když jsou tyto kvóty konfigurovatelné, výchozí hodnoty se změní tak, aby se minimalizovala možnost, že ji vývojář musí explicitně nastavit. Další informace najdete v tématu [funkce pro zjednodušení služby WCF](wcf-simplification-features.md).

### <a name="wcf-configuration-validation"></a>Ověřování konfigurace WCF

Jako součást procesu sestavení v rámci sady Visual Studio jsou nyní ověřovány konfigurační soubory WCF pro atributy definované v rámci projektu. V aplikaci Visual Studio se zobrazí seznam chyb ověřování nebo upozornění, pokud se ověření nepovede.

### <a name="xml-editor-tooltips"></a>Popisy editoru XML

Editor XML sady Visual Studio nyní poskytuje popisy pro každý prvek konfigurace a jeho vlastnosti, které jsou součástí konfiguračního souboru služby, aby bylo možné pomáhat novým a stávajícím vývojářům služby WCF konfigurovat své služby.

## <a name="streaming-improvements"></a>Vylepšení streamování

Byla přidána podpora pro skutečný asynchronní streamování, kde odesílající strana teď neblokuje vlákna, pokud se na straně příjmu nečte nebo pomalu čte a zvyšuje škálovatelnost. Odstranila se omezení ukládání zpráv do vyrovnávací paměti, když klient odešle streamovaná zpráva službě WCF hostované službou IIS. Další informace najdete v tématu [funkce pro zjednodušení služby WCF](wcf-simplification-features.md).

## <a name="simplifying-exposing-an-endpoint-over-https-with-iis"></a>Zjednodušení vystavení koncového bodu přes HTTPS se službou IIS

Bylo přidáno mapování protokolu HTTPS, které zjednodušuje vystavení koncového bodu přes HTTPS. Pokud chcete povolit koncový bod HTTPS, ujistěte se, že váš web má nakonfigurovanou vazbu HTTPS a certifikát SSL, a pak jednoduše povolte HTTPS pro virtuální adresář, který hostuje službu. Pokud jsou metadata pro službu povolená, budou vystavená i přes HTTPS.

## <a name="generating-a-single-wsdl-document"></a>Generování jednoho dokumentu WSDL

Některé zásobníky zpracování WSDL třetích stran nemohou zpracovávat dokumenty WSDL, které mají závislosti na jiných dokumentech prostřednictvím XSD: import. WCF teď umožňuje určit, že se všechny informace WSDL budou vracet v jednom dokumentu. Pro vyžádání jednoho dokumentu WSDL připojit "? singleWSDL" k identifikátoru URI při žádosti o metadata ze služby.

## <a name="websocket-support"></a>Podpora protokolu WebSocket

WebSockets je technologie, která poskytuje skutečnou obousměrnou komunikaci přes porty 80 a 443 s charakteristikami výkonu podobnými TCP. Přidali jsme dvě nové vazby, které podporují komunikaci prostřednictvím přenosu protokolu WebSocket. <xref:System.ServiceModel.NetHttpBinding> a <xref:System.ServiceModel.NetHttpsBinding>. Další informace najdete v tématu: [systémem poskytované vazby](system-provided-bindings.md).

## <a name="new-transport-default-values"></a>Nové výchozí hodnoty přenosu

Následující tabulka popisuje nastavení, která se změnila a kde najít další informace.

|Vlastnost|Zapnuto|Nové výchozí|Další informace najdete v tématu|
|--------------|--------|-----------------|------------------------------|
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 * počet procesorů|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * počet procesorů pro přenos<br /><br /> 4 \* počet procesorů pro SMSvcHost. exe|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> [Konfigurace služby sdílení portů Net. TCP](./feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * počet procesorů|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 sekund|[Konfigurace služby sdílení portů Net.TCP](./feature-details/configuring-the-net-tcp-port-sharing-service.md)|

## <a name="xml-editor-tooltips"></a>Popisy editoru XML

Editor XML sady Visual Studio nyní poskytuje popisy pro každý prvek konfigurace a jeho vlastnosti, které jsou součástí konfiguračního souboru služby, aby bylo možné pomáhat novým a stávajícím vývojářům služby WCF konfigurovat své služby.

## <a name="configuring-wcf-services-in-code"></a>Konfigurace služeb WCF v kódu

Windows Communication Foundation (WCF) umožňuje vývojářům nakonfigurovat služby pomocí konfiguračních souborů nebo kódu. Konfigurační soubory jsou užitečné, když po nasazení potřebujete nakonfigurovat službu. Při použití konfiguračních souborů potřebuje IT specialista aktualizovat pouze konfigurační soubor, není nutné znovu zkompilována. Konfigurační soubory ale mohou být složité a obtížné udržovat. Neexistuje žádná podpora pro ladění konfiguračních souborů a konfigurační prvky jsou odkazovány pomocí názvů, které usnadňují a obtíže při vytváření konfiguračních souborů. WCF také umožňuje nakonfigurovat služby v kódu. V dřívějších verzích WCF (4,0 a starší) konfigurace služeb v kódu byla v rámci scénářů s vlastním hostováním velmi snadná, <xref:System.ServiceModel.ServiceHost> třídy vám umožňují nakonfigurovat koncové body a chování před voláním třídy ServiceHost. Open. Ve scénářích, kde se nachází web, ale nemáte přístup k třídě <xref:System.ServiceModel.ServiceHost>. Pro konfiguraci webové hostované služby jste museli vytvořit `System.ServiceModel.ServiceHostFactory`, která vytvořila <xref:System.ServiceModel.Activation.ServiceHostFactory> a provedla všechny potřebné konfigurace. Počínaje verzí .NET 4,5 nabízí WCF snazší způsob, jak v kódu nakonfigurovat služby hostované v místním prostředí i na webu. Další informace najdete v tématu [Konfigurace služeb WCF v kódu](configuring-wcf-services-in-code.md).

## <a name="channelfactory-caching"></a>Třída ChannelFactory pro ukládání do mezipaměti

Klientské aplikace WCF používají třídu <xref:System.ServiceModel.ChannelFactory%601> k vytvoření komunikačního kanálu se službou WCF. Vytváření instancí <xref:System.ServiceModel.ChannelFactory%601> způsobí určitou režii, protože zahrnuje následující operace:

1. Sestavování stromu <xref:System.ServiceModel.Description.ContractDescription>

2. Reflektování všech požadovaných typů CLR

3. Sestavování zásobníku kanálů

4. Odstraňování prostředků

Pro lepší minimalizaci této režie může WCF při použití proxy serveru WCF ukládat do mezipaměti objekty kanálu. Další informace najdete v tématu [vytváření kanálů a ukládání do mezipaměti](./feature-details/channel-factory-and-caching.md).

## <a name="compression-and-the-binary-encoder"></a>Komprese a binární kodér

Počínaje WCF 4,5 binární kodér WCF přidá podporu pro kompresi. Typ komprese je nakonfigurován s vlastností <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A>. Klient i služba musí nakonfigurovat vlastnost <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A>. Komprese bude fungovat pro protokoly HTTP, HTTPS a TCP. Pokud klient určí použití komprese, ale služba je nepodporuje, je vyvolána výjimka protokolu oznamující neshodu protokolu. Další informace najdete v tématu [Volba kodéru zpráv](./feature-details/choosing-a-message-encoder.md).

## <a name="udp"></a>UDP

Byla přidána podpora pro přenos UDP, který vývojářům umožňuje psát služby, které používají zasílání zpráv "Fire and zapomene". Klient pošle zprávu službě a neočekává odpověď ze služby.

## <a name="multiple-authentication-support"></a>Podpora více ověřování

Přidala se podpora pro podporu více režimů ověřování, jak je podporovaná službou IIS, na jednom koncovém bodu WCF při použití přenosu HTTP a zabezpečení přenosu. Služba IIS umožňuje ve virtuálním adresáři povolit více režimů ověřování. Tato funkce umožňuje jednomu koncovému bodu WCF podporovat vícenásobné režimy ověřování povolené pro virtuální adresář, ve kterém je hostovaná služba WCF.

## <a name="idn-support"></a>Podpora IDN

Přidala se podpora, aby služba WCF mohla používat mezinárodní názvy domén. Další informace najdete v tématu [WCF a mezinárodní názvy domén](./feature-details/wcf-and-internationalized-domain-names.md).

## <a name="httpclient"></a>HttpClient

Přidala se nová třída s názvem <xref:System.Net.Http.HttpClient>, která zajistí mnohem snazší práci s požadavky HTTP. Další informace najdete v tématu [vytváření aplikací v sociálních sítích a jejich připojení ke službám http](https://channel9.msdn.com/Events/BUILD/BUILD2011/PLAT-581T) a [ukázce klienta http](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664).

## <a name="configuration-intellisense"></a>Technologie IntelliSense pro konfiguraci

Hodnoty atributů v konfiguračních souborech pro vlastní atributy definované v projektu teď podporují technologii IntelliSense, která usnadňuje práci s konfiguracemi rychle a přesně.

## <a name="configuration-tooltips"></a>Popisy konfigurace

Prvky a atributy služby WCF mají nyní popisy tlačítek v editoru XML pro snadnější a přesnější identifikaci účelu elementu nebo atributu.

## <a name="paste-data-as-classes"></a>Vložit data jako třídy

V projektu WCF mohou být datové typy definované v jazyce XML (například zpřístupněny ve službě) vloženy přímo do znakové stránky. Typ XML bude vložen jako typ CLR. Další podrobnosti najdete v tématu [generování tříd datových typů z XML](generating-data-type-classes-from-xml.md) .

## <a name="webservicehost-and-default-endpoints"></a>WebServiceHost a výchozí koncové body

V aplikaci Visual Studio 2010 WebServiceHost automaticky vytvořila výchozí koncový bod bez ohledu na to, jestli jste zadali explicitně koncový bod. V aplikaci Visual Studio 2012 a novějších, WebServiceHost vytvoří pouze výchozí koncový bod, pokud nejsou explicitně přidány žádné koncové body. Pokud klient očekává výchozí koncový bod, můžete explicitně přidat koncový bod a nasměrovat klienta na něj. Případně můžete službě WCF sdělit, aby se vrátila zpět k předchozímu chování tím, že do konfiguračního souboru aplikace přidáte následující nastavení.

```xml
<appSettings>
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>
  </appSettings>
```

## <a name="ihttpcookiecontainermanager"></a>IHttpCookieContainerManager

Toto rozhraní, které je zveřejněné pomocí <xref:System.ServiceModel.Channels.IChannelFactory%601>, usnadňuje práci s soubory cookie na straně klienta. Když je u vazby AllowCookies nastaveno na hodnotu true, můžete získat přístup k souborům cookie pomocí následujícího kódu:

```csharp
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();
System.Net.CookieContainer container = cookieManager.CookieContainer;
```

Pak můžete načíst nebo nastavit soubory cookie z <xref:System.Net.CookieContainer>. Pokud je AllowCookies nastaveno na hodnotu false, můžete soubory cookie ručně načíst pomocí <xref:System.ServiceModel.OperationContext> a odeslat je do jiných požadavků pomocí jiného <xref:System.ServiceModel.OperationContext> nebo kontroly zpráv. Rozhraní IHttpCookieContainerManager umožňuje ověřit uživatele pomocí služby a použít ověřovací soubor cookie vrácený touto službou k ověřování s ostatními službami.
