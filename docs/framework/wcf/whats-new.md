---
title: Co&#39;s ve Windows Communication Foundation 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], what's new
- Windows Communication Foundation [WCF], what's new
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 091925dd1f505693df0d1eb770bca604cf038667
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="what39s-new-in-windows-communication-foundation-45"></a>Co&#39;s ve Windows Communication Foundation 4.5
Toto téma popisuje nové funkce [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## <a name="wcf-simplification-features"></a>Funkce zjednodušení WCF  
 Množství práce bylo provedeno usnadnění WCF 4.5 aplikace pro vývoj a údržbu. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### <a name="task-based-async-support"></a>Asynchronní podpora založený na úlohách  
 Ve výchozím nastavení generuje přidat odkaz na službu úloh vrácení metody operace asynchronní služby. To se provádí pro synchronní a asynchronní metody. To umožňuje volání operací služby asynchronně pomocí nové úlohy na základě asynchronní programování modelu. Při volání metody vygenerovaný proxy server, WCF vytvoří objekt úlohy představující asynchronní operaci a vrátí, které úlohy pro vás. Úloha se dokončí po dokončení operace.  Při provádění asynchronní operace můžete implementovat jako založený na úlohách asynchronní operace. Další informace najdete v tématu [synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
### <a name="simplified-generated-configuration-files"></a>Zjednodušená generované konfigurační soubory  
 Při přidání odkazu služby v sadě Visual Studio nebo pomocí nástroje SvcUtil.exe, je generována konfiguračního souboru klienta. V předchozích verzích služby WCF tyto konfigurační soubory obsažené hodnotu každé vlastnosti vazby, i když její hodnota je výchozí hodnota. Ve WCF 4.5 generované konfigurační soubory, které obsahují pouze vazby vlastnosti, které jsou nastaveny na jiné než výchozí hodnotu.  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md)  
  
### <a name="contract-first-development"></a>Vývoj s včasným kontraktu  
 WCF nyní obsahuje podporu pro vývoj s včasným kontrakt. Svcutl.exe má /serviceContract přepínač, který vám umožní generovat kontraktů služby a data z dokumentu WSDL.  
  
### <a name="add-service-reference-from-a-portable-subset-project"></a>Přidat odkaz na službu z přenosném dílčím projektu  
 Projekty přenosném dílčím povolit programátorům sestavení .NET udržovat stromu jednoho zdroje a sestavení systému, přičemž musí zároveň podporovat více platformy .NET (plochy, Silverlight, Windows Phone a XBOX). Projekty přenosném dílčím odkazovat pouze na přenosné knihovny .NET, které jsou sestavení rozhraní .NET framework, který lze použít na jakékoli platformě .NET. Možnosti vývojáře je stejný jako přidání odkazu na službu v rámci žádnou jinou aplikaci klienta WCF. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Přidání odkazu služby v přenosném dílčím projektu](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).  
  
### <a name="aspnet-compatibility-mode-default-changed"></a>Výchozí režim kompatibility ASP.NET změnit  
 WCF poskytuje režim kompatibility ASP.NET udělit vývojáři úplný přístup k funkcím v kanálu ASP.NET HTTP při zápisu služby WCF. Chcete-li použít tento režim, musíte nastavit `aspNetCompatibilityEnabled` atributu na hodnotu true v [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) části souboru Web.config. Kromě toho musí mít všechny služby v této doméně appDomain `RequirementsMode` vlastnost na jeho <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nastavena na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Ve výchozím nastavení <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> je teď nastavená na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Co je nového ve službě Windows Communication Foundation](../../../docs/framework/wcf/whats-new.md) a [služby WCF a ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
### <a name="new-transport-default-values"></a>Nové výchozí hodnoty přenosu  
 Aby bylo možné zjednodušit konfiguraci změnily počet přenosu vlastnost výchozí hodnoty. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas> obsahuje hodnoty konfigurovat kvóty pro slovník čtečky XML, které omezit množství paměti využívaných kodér při vytváření zprávu. Při těchto kvót se dají konfigurovat, výchozí hodnoty změnili na zmírnění možnost, že vývojář nutné explicitně nastaven. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### <a name="wcf-configuration-validation"></a>Ověření konfigurace WCF  
 Jako součást procesu sestavení v sadě Visual Studio se teď ověří WCF konfigurační soubory pro atributy definované v projektu. Seznam chyb při ověřování nebo upozornění se zobrazí v sadě Visual Studio, pokud se ověření nezdaří.  
  
### <a name="xml-editor-tooltips"></a>Popisy tlačítek Editor XML  
 Abyste pomohli nových nebo stávajících vývojáři služeb WCF konfigurace služeb, editor souborů XML Visual Studio teď poskytuje popisy tlačítek pro každý element, konfigurace a její vlastnosti, které je součástí konfigurační soubor služby.  
  
## <a name="streaming-improvements"></a>Streamování vylepšení  
 Přidaná podpora pro true asynchronní streamování kde straně odesílání teď neblokuje vláken pokud straně příjmu není čtení nebo pomalé v režimu čtení a zvyšovat škálovatelnost. Odebrat omezení vyrovnávací paměti zpráv, když klient odešle, že přenášené datovými proudy zprávy na službu IIS hostované služby WCF. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Funkce zjednodušení WCF](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
## <a name="simplifying-exposing-an-endpoint-over-https-with-iis"></a>Ke zjednodušení vystavení koncový bod HTTPS se službou IIS  
 Pro zjednodušení vystavení koncový bod HTTPS se přidal mapování protokolu HTTPS. Chcete-li povolit koncový bod HTTPS, zajistěte, aby byl váš web služby vazbu HTTPS a nakonfigurovat certifikát SSL a jednoduše povolit HTTPS pro virtuální adresář, který je hostitelem služby. Pokud metadat je povolen pro službu, je k dispozici prostřednictvím protokolu HTTPS také.  
  
## <a name="generating-a-single-wsdl-document"></a>Generování jednoho WSDL dokumentu  
 Zásobníky WSDL zpracování některých třetích stran, nejsou schopna zpracovat WSDL dokumenty, které mají závislosti na jiných dokumentů prostřednictvím xsd:import.  WCF umožňuje určit, že všechny informace o WSDL vráceny do jednoho dokumentu. Požádat o jednotlivý dokument WSDL připojit "? singleWSDL" k identifikátoru URI při požaduje metadata ze služby.  
  
## <a name="websocket-support"></a>Podpora protokolu WebSocket  
 Technologie WebSockets je technologie, která poskytuje true obousměrnou komunikaci přes porty 80 a 443 protokolu TCP podobné charakteristiky. Aby mohly podporovat komunikaci pomocí přenosového protokolu WebSocket byly přidány dva nové vazby. <xref:System.ServiceModel.NetHttpBinding> a <xref:System.ServiceModel.NetHttpsBinding>. Další informace najdete v tématu: [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="new-transport-default-values"></a>Nové výchozí hodnoty přenosu  
 Následující tabulka popisuje nastavení, které se změnily a kde najít další informace.  
  
|Vlastnost|On|Nový výchozí|Další informace najdete v tématu|  
|--------------|--------|-----------------|------------------------------|  
|ChannelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 * počet procesorů|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * počet procesorů pro přenos<br /><br /> 4 \* počet procesorů pro SMSvcHost.exe|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> [Konfigurace služby Sdílení portů Net.TCP](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * počet procesorů|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 sekund|[Konfigurace služby sdílení portů Net.TCP](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
  
## <a name="xml-editor-tooltips"></a>Popisy tlačítek Editor XML  
 Abyste pomohli nových nebo stávajících vývojáři služeb WCF konfigurace služeb, editor souborů XML Visual Studio teď poskytuje popisy tlačítek pro každý element, konfigurace a její vlastnosti, které je součástí konfigurační soubor služby.  
  
## <a name="configuring-wcf-services-in-code"></a>Konfigurace služeb WCF v kódu  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] umožňuje vývojářům konfigurovat služeb pomocí konfiguračních souborů nebo kódu.  Konfigurační soubory jsou užitečné, když je potřeba nakonfigurovat po nasazení služby. Při použití konfigurační soubory, odborník v oblasti IT pouze musí aktualizovat konfigurační soubor, není třeba žádné opětovnou kompilaci. Konfigurační soubory, však může být složité a obtížné. Neexistuje žádná podpora pro ladění konfigurační soubory a konfigurace – elementy odkazují názvy, které umožňuje vytváření konfigurační soubory k chybám a obtížná. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] také umožňuje konfigurovat služby v kódu. V dřívějších verzích [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 a starší) konfigurace služby v kódu se snadno ve vlastním hostováním scénářů <xref:System.ServiceModel.ServiceHost> třída povolena, můžete nakonfigurovat koncové body a chování před volání ServiceHost.Open. Ve scénářích hostovaná na webu, ale nemáte přístup k <xref:System.ServiceModel.ServiceHost> třídy. Konfigurace webové hostované služby, bylo potřeba vytvořit `System.ServiceModel.ServiceHostFactory` vytvořené <xref:System.ServiceModel.Activation.ServiceHostFactory> a provést všechny potřebné konfigurace. Od verze rozhraní .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] poskytuje snadný způsob, jak nakonfigurovat i samoobslužně hostované a webové hostované služby v kódu. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Konfigurace služeb WCF v kódu](../../../docs/framework/wcf/configuring-wcf-services-in-code.md).  
  
## <a name="channelfactory-caching"></a>Ukládání do mezipaměti ChannelFactory  
 Pomocí klientských aplikací WCF <xref:System.ServiceModel.ChannelFactory%601> třída k vytvoření kanálu komunikace se službou WCF.  Vytváření <xref:System.ServiceModel.ChannelFactory%601> instance způsobuje zvýšení zatížení, protože se týká následující operace:  
  
1.  Vytváření <xref:System.ServiceModel.Description.ContractDescription> stromu  
  
2.  Odrážející všechny požadované typy CLR  
  
3.  Vytváření kanálu zásobníku  
  
4.  Uvolnění prostředků  
  
 Abyste minimalizovali Tato dodatečná režie, můžete WCF mezipaměti objektů Factory kanál, když používáte proxy server klienta WCF. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Kanálu tovární nastavení a ukládání do mezipaměti](../../../docs/framework/wcf/feature-details/channel-factory-and-caching.md).  
  
## <a name="compression-and-the-binary-encoder"></a>Komprese a binární kodér  
 Od verze WCF 4.5 binární kodér WCF přidává podporu pro kompresi. Typ komprese nastavena <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> vlastnost. Musíte nakonfigurovat klienta a služby <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> vlastnost. Komprese bude fungovat pro protokoly HTTP, HTTPS a TCP. Pokud klient Určuje použití komprese, ale služba nepodporuje protokol výjimka je vyvolána, označující neshoda protokolu. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Výběr kodéru zprávy](../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
  
## <a name="udp"></a>UDP  
 Byla přidána podpora pro přenos UDP, což vývojářům umožňuje zápis služeb, které používají "fire a zapomněli" zasílání zpráv. Klient odešle zprávu do služby a očekává žádná odpověď ze služby.  
  
## <a name="multiple-authentication-support"></a>Podpora více ověřování  
 Byla přidána podpora pro podporu více režimy ověřování, jako podporovaný službou IIS, jeden koncový bod WCF při používání přenosového protokolu HTTP a zabezpečení přenosu. Služba IIS umožňuje povolit více režimy ověřování ve virtuálním adresáři, tato funkce umožňuje jeden koncový bod WCF pro podporu režimů více ověřování povolené pro virtuální adresář, který je hostitelem služby WCF.  
  
## <a name="idn-support"></a>Podpora IDN.  
 Byla přidána podpora umožňující službám WCF pomocí mezinárodních názvů domén. Další informace najdete v části [WCF a mezinárodní názvy domén](../../../docs/framework/wcf/feature-details/wcf-and-internationalized-domain-names.md).  
  
## <a name="httpclient"></a>HttpClient  
 Novou třídu s názvem <xref:System.Net.Http.HttpClient> byl přidán do mnohem snazší práce s požadavky HTTP. Další informace najdete v tématu [převedení aplikace na sociálních a připojený se službami HTTP](http://go.microsoft.com/fwlink/?LinkId=231886) a [ukázka klienta HTTP](http://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664).  
  
## <a name="configuration-intellisense"></a>Konfigurace technologie Intellisense  
 Hodnoty atributů v konfiguračních souborech pro vlastní atributy definované v projektu nyní podporu technologie intellisense pro usnadnění práce s konfigurací rychle a přesně.  
  
## <a name="configuration-tooltips"></a>Popisy tlačítek konfigurace  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] elementy a atributy teď snadněji muset popisů tlačítek v editoru XML a přesně zjistit účel elementu nebo atributu.  
  
## <a name="paste-data-as-classes"></a>Vkládání dat jako třídy  
 V projektu WCF typy dat definované v XML (jako jsou viditelné ve službě) lze vložit přímo do kódu stránky. Typ XML budou vloženy jako typ CLR. V tématu [generování tříd datových typů z XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md) další podrobnosti.  
  
## <a name="webservicehost-and-default-endpoints"></a>Hostitel WebServiceHost a výchozí koncové body  
 V sadě Visual Studio 2010 Hostitel WebServiceHost automaticky vytvoří výchozí koncový bod, jestli koncový bod explicitně určena, nebo ne. V hostitel Visual Studio 2012 WebServiceHost pouze vytvoří výchozí koncový bod Pokud jsou přidané žádné koncové body. Pokud váš klient je očekáván výchozí koncový bod, můžete výslovně přidání koncového bodu a nasměrujte klienta. Alternativně můžete zjistit, WCF se vrátit zpět na předchozí chování přidáním následujícího nastavení do konfiguračního souboru aplikace  
  
```xml  
<appSettings>  
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>  
  </appSettings>  
```  
  
## <a name="ihttpcookiecontainermanager"></a>IHttpCookieContainerManager  
 Toto rozhraní, které jsou vystavené <xref:System.ServiceModel.Channels.IChannelFactory%601>, díky práci se soubory cookie na straně klienta mnohem jednodušší. Když je AllowCookies nastavená na hodnotu true u vazby, dostanete souborů cookie pomocí následujícího kódu:  
  
```csharp  
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();   
System.Net.CookieContainer container = cookieManager.CookieContainer;  
```  
  
 Potom můžete načíst nebo nastavit z soubory cookie <xref:System.Net.CookieContainer>. Pokud AllowCookies je nastavená na hodnotu false, můžete ručně načíst soubory cookie pomocí <xref:System.ServiceModel.OperationContext> a odesílat v ostatních požadavků pomocí jiného <xref:System.ServiceModel.OperationContext> nebo inspector zprávy. Rozhraní IHttpCookieContainerManager umožňuje ověření uživatele se službou a pomocí ověřovacího souboru cookie vrácený služby k ověření s jinými službami.
