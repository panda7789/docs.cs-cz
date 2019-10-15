---
title: WCF a ASP.NET Web API
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: 302415a67a953d157b0aee8aa126786d2d0c4e62
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320253"
---
# <a name="wcf-and-aspnet-web-api"></a>WCF a ASP.NET Web API
WCF je jednotný programovací model Microsoftu pro vytváření aplikací orientovaných na služby. Umožňuje vývojářům vytvářet zabezpečená a spolehlivá řešení s podporou transakcí, která integrují napříč platformami a vzájemně spolupracují se stávajícími investicemi. [Webové rozhraní API ASP.NET](https://www.asp.net/web-api) je rozhraní, které usnadňuje sestavování služeb HTTP, které dosáhnou široké škály klientů, včetně prohlížečů a mobilních zařízení. Webové rozhraní API ASP.NET je ideální platformou pro sestavování aplikací RESTful na .NET Framework. V tomto tématu najdete pokyny, které vám pomůžou určit, která technologie bude nejlépe vyhovovat vašim potřebám.  
  
## <a name="choosing-which-technology-to-use"></a>Volba technologie, která se má použít  
 Následující tabulka popisuje hlavní funkce jednotlivých technologií.  
  
|WCF|Rozhraní API pro ASP.NET Web|  
|---------|---------------------|  
|Umožňuje vytvářet služby, které podporují víc přenosových protokolů (HTTP, TCP, UDP a vlastní přenosy), a umožňuje mezi nimi přepínat.|Pouze HTTP. Model programování první třídy pro HTTP. Vhodnější pro přístup z různých prohlížečů, mobilních zařízení a umožnění širšího dosahu.|  
|Umožňuje vytvářet služby, které podporují více kódování (text, MTOM a binární) stejného typu zprávy a umožňují přepínání mezi nimi.|Umožňuje sestavovat webová rozhraní API, která podporují širokou škálu typů médií, včetně XML, JSON atd.|  
|Podporuje vytváření služeb s normami WS-*, jako jsou spolehlivé zasílání zpráv, transakcí a zabezpečení zpráv.|Používá základní protokoly a formáty jako HTTP, WebSockets, SSL, JSON a XML. Neexistují žádné podpory pro protokoly vyšší úrovně, jako jsou například spolehlivé zasílání zpráv nebo transakcí.|  
|Podporuje vzorce požadavků a odpovědí, jednosměrné a duplexní výměnu zpráv.|HTTP je požadavek nebo odpověď, ale další vzory je možné podporovat prostřednictvím integrace [signálů](https://github.com/SignalR/SignalR) a WebSockets.|  
|Služby WCF SOAP je možné popsány v tématu WSDL, což umožňuje automatizované nástroje pro generování proxy serverů klientů, a to i pro služby se složitými schématy.|Existuje mnoho způsobů, jak popsat webové rozhraní API v rozsahu od automaticky vygenerované stránky s nápovědu HTML popisující fragmenty do strukturovaných metadat pro integrovaná rozhraní API OData.|  
|Dodává se s rozhraním .NET Framework.|Dodává se s rozhraním .NET Framework, ale je open source a je k dispozici mimo IP síť jako nezávislé stažení.|  
  
 Využijte WCF k vytváření spolehlivých zabezpečených webových služeb, které jsou přístupné přes celou řadu přenosů. Pomocí webového rozhraní API ASP.NET můžete vytvářet služby založené na protokolu HTTP, které jsou přístupné z široké škály klientů. Pokud vytváříte a navrhujete nové služby ve stylu REST, použijte webové rozhraní API ASP.NET. I když služba WCF poskytuje podporu pro psaní služeb ve stylu REST, podpora REST ve webovém rozhraní API ASP.NET je dokončena a všechna budoucí vylepšení funkcí REST budou provedena ve webovém rozhraní API ASP.NET. Pokud máte existující službu WCF a chcete zpřístupnit další koncové body REST, použijte WCF a <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Viz také:

- [Co je Windows Communication Foundation](whats-wcf.md)
- [Základní koncepty Windows Communication Foundation](fundamental-concepts.md)
