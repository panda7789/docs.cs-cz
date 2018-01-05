---
title: WCF a ASP.NET Web API
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1270eb202a1e8cbf1a297a13593dd0aa6046cb6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-and-aspnet-web-api"></a>WCF a ASP.NET Web API
WCF je jednotný programovací model pro vytváření aplikací orientovaných na služby společnosti Microsoft. Umožňuje vývojářům vytvářet bezpečné, spolehlivé a zpracovaných řešení, které integrovat do různých platforem a zajistit vzájemnou funkční spolupráci s stávajících investic. [Rozhraní ASP.NET Web API](http://www.asp.net/web-api) je rozhraní, které usnadňuje sestavování služeb HTTP, které využity širokou škálou klientů včetně prohlížečů a mobilních zařízení. Rozhraní ASP.NET Web API je ideální platformu pro sestavování aplikací RESTful v rozhraní .NET Framework. Toto téma představuje některé pokyny, které vám pomohou rozhodnout, technologii, která bude nejlépe vyhovovat vašim potřebám.  
  
## <a name="choosing-which-technology-to-use"></a>Výběr technologii, která má použít  
 Následující tabulka popisuje hlavní funkce každou technologii.  
  
|WCF|Rozhraní API pro ASP.NET Web|  
|---------|---------------------|  
|Umožňuje vytváření služeb, které podporují víc protokolů přenosu (HTTP, TCP, UDP a vlastní přenosy) a umožňuje přepínání mezi nimi.|Pouze HTTP. První třídy programovací model pro protokol HTTP. Nejvhodnější pro přístup z různých prohlížečů, mobilní zařízení apod povolení celý dosáhnout.|  
|Povoluje vytváření služeb, které podporují více kódování (Text, MTOM a binární) stejná zpráva typu a umožňuje přepínání mezi nimi.|Umožňuje vytvářet webové rozhraní API, které podporují celou řadu typů médií, včetně XML, JSON atd.|  
|Podporuje vytváření služeb s WS-* standardy jako zabezpečení zpráv spolehlivého zasílání zpráv a transakce.|Základní protokolu a hodnot, jako je například HTTP, Websocket, SSL, JSON a XML. Neexistuje žádná podpora pro protokoly vyšší úrovně, jako je například spolehlivé zasílání zpráv nebo transakce.|  
|Podporuje vzory exchange zprávu požadavku a odpovědi, jeden způsob a duplexní režim.|HTTP je požadavek a odpověď, ale další vzory může podporovat prostřednictvím [SignalR](https://github.com/SignalR/SignalR) a integrace objekty WebSockets.|  
|Služby WCF SOAP můžete popsané v WSDL umožňuje automatizované nástroje pro generování proxy klienta i pro služby s komplexní schématy.|Je různými způsoby k popisu webového rozhraní API od automaticky generovaný HTML stránky nápovědy popisující fragmenty na strukturovaných metadata pro OData integrované rozhraní API.|  
|Se dodává s rozhraním .NET framework.|Se dodává s verzí rozhraní .NET framework, ale je typu open source a je také k dispozici out-of-band nezávislé ke stažení.|  
  
 K vytvoření to přístupné spolehlivé, zabezpečené webové služby pro řadu přenosů použijte WCF. K vytvoření služby založené na protokolu HTTP, které jsou dostupné z různých klientů použijte rozhraní ASP.NET Web API. Webové rozhraní API ASP.NET použijte, pokud se vytváření a návrhu nové služby stylu REST. I když WCF poskytuje některé podporu pro zápis služby stylu REST, podpora v rozhraní ASP.NET Web API REST je obsáhlejší a všechna budoucí vylepšení funkce REST budou provedeny v rozhraní ASP.NET Web API. Pokud máte existující službu WCF a chcete vystavit další koncové body REST, použijte WCF a <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Viz také  
 [Co je Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Základní koncepty Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
