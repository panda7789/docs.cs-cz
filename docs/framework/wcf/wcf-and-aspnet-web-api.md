---
title: WCF a ASP.NET Web API
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: d805c09bef45932ba006a213343429ae7c9303df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192001"
---
# <a name="wcf-and-aspnet-web-api"></a>WCF a ASP.NET Web API
WCF je jednotný programovací model pro vytváření aplikací orientovaných na služby od Microsoftu. Umožňuje vývojářům vytvářet zabezpečená, spolehlivá a počet řešení, které se integrují napříč platformami vzájemnou spolupráci se službami stávajících investic. [Rozhraní ASP.NET Web API](https://www.asp.net/web-api) je architektura, která usnadňuje sestavování služeb HTTP, které jsou poskytovány širokému spektru klientů, včetně prohlížečů a mobilních zařízení. ASP.NET Web API je ideální platformu pro sestavování aplikací RESTful v rozhraní .NET Framework. Toto téma představuje některé pokyny, které vám pomohou rozhodnout, technologii, která bude nejlépe vyhovovat vašim potřebám.  
  
## <a name="choosing-which-technology-to-use"></a>Výběr technologii, která má použít  
 Následující tabulka popisuje hlavní funkce každou technologii.  
  
|WCF|Rozhraní API pro ASP.NET Web|  
|---------|---------------------|  
|Umožňuje vytváření služeb, které podporují víc protokolů přenosu (HTTP, TCP, UDP a vlastní přenosy) a umožňuje přepínání mezi nimi.|Jenom HTTP. Prvotřídní programovací model pro protokol HTTP. Vhodnější pro přístup z různých prohlížečů, mobilní zařízení, povolení etc široký dosah.|  
|Umožňuje vytvářet služby, které podporují více kódování (Text, MTOM a binární) stejná zpráva typu a umožňuje přepínání mezi nimi.|Umožňuje vytvářet webová rozhraní API, které podporují celou řadu typů médií, včetně XML, JSON atd.|  
|Podporuje vytváření služeb WS-* standardy, jako je spolehlivé zasílání zpráv, transakce, zabezpečení zpráv.|Používá základní protokol a formáty, jako jsou HTTP, protokoly Websocket, protokol SSL, JSON a XML. Není dostupná podpora pro protokoly vyšší úrovně, jako je například spolehlivé zasílání zpráv nebo transakce.|  
|Podporuje požadavek-odpověď, jeden způsob, jak a duplexní způsoby zprávy exchange.|HTTP je požadavek/odpověď, ale další vzory mohou být podporovány prostřednictvím [SignalR](https://github.com/SignalR/SignalR) a integrace objekty Websocket.|  
|Služby WCF SOAP lze popsat v jazyce WSDL umožňuje automatizované nástroje pro generování proxy klienta i pro služby s komplexní schémata.|Není k dispozici různé způsoby popisu webového rozhraní API od automaticky generované nápovědy stránku HTML s popisem fragmentů kódu s cílem strukturovaných metadat pro OData integrovaná rozhraní API.|  
|Se dodává s rozhraním .NET framework.|Dodává se sadou .NET framework, ale je open source a je také k dispozici out-of-band jako nezávislé soubor ke stažení.|  
  
 Použijte k vytvoření spolehlivé a zabezpečené webové služby, které jsou přístupné přes celou řadu přenosy WCF. Použijte k vytvoření založené na protokolu HTTP služby, které jsou k dispozici v celé řadě klientských rozhraní ASP.NET Web API. Webové rozhraní API technologie ASP.NET použijte, pokud jsou vytvoření a návrh nové služby ve stylu REST. I když WCF poskytuje podporu pro psaní stylu REST služby, podpora pro REST v rozhraní ASP.NET Web API je kompletní a všechna budoucí vylepšení funkce REST budou k dispozici v rozhraní ASP.NET Web API. Pokud máte existující službu WCF a chcete zobrazit další koncové body REST, použijte WCF a <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Viz také:

- [Co je to Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)
- [Základní koncepty služby Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
