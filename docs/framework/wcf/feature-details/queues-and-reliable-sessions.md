---
title: Fronty a spolehlivé relace
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: 1fb7d7db36aa51c63789b6daf0ac3689c87ace5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946689"
---
# <a name="queues-and-reliable-sessions"></a>Fronty a spolehlivé relace
Fronty a spolehlivé relace jsou funkce Windows Communication Foundation (WCF), které implementují spolehlivé zasílání zpráv. Témata obsažené v této části popisují funkce spolehlivé zasílání zpráv WCF.  
  
 Spolehlivé zasílání zpráv je, jak zdroj spolehlivé zasílání zpráv (označované jako zdroj) přenáší zprávy spolehlivě do spolehlivého zasílání zpráv cíle (označované jako cíl).  
  
 Spolehlivé zasílání zpráv má následující klíčové aspekty:  
  
- Přenos záruky pro zprávy odeslané ze zdroje do cíle bez ohledu na selhání přenosu zpráv nebo selhání přenosu.  
  
- Oddělení zdroj a cíl z ostatních, které poskytuje nezávislé selhání a obnovení zdroje a cíle jako dobře spolehlivé doručování zpráv a přenosu i v případě, že zdroj nebo cíl nedostupný.  
  
 Spolehlivé zasílání zpráv je často za cenu vysokou latenci. Latence je doba, která je potřebná pro zprávy k dosažení cíle ze zdroje. WCF, proto poskytuje spolehlivé zasílání zpráv následující typy:  
  
- [Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), která nabízí spolehlivé přenos bez nákladů vysokou latencí  
  
- [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), která nabízí spolehlivé přenosů a oddělení mezi zdrojem a cílem.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace poskytují začátku do konce spolehlivé přenos zpráv mezi zdroj a cíl pomocí protokolu WS-ReliableMessaging bez ohledu na počet a typ zprostředkovatelů, které oddělují koncových bodů pro zasílání zpráv (zdrojové a cílové). To zahrnuje všechny přenosu zprostředkovatelů, které nevyužívají protokol SOAP (například proxy protokolu HTTP) nebo zprostředkovatelů, které používají protokol SOAP (například založený na protokolu SOAP směrovače nebo mosty), které jsou požadovány pro zprávy, které jsou předávány mezi koncovými body. Spolehlivé relace okno přenosu v paměti na selhání úroveň zprávy protokolu SOAP maska a znovu vytvořit připojení v případě selhání přenosu.  
  
 Spolehlivé relace poskytují spolehlivé zprávy s nízkou latencí přenosy. Poskytují pro zprávy protokolu SOAP přes všechny proxy servery nebo prostředníci, ekvivalent jaké TCP poskytuje pro pakety přes mosty IP. Další informace o spolehlivých relací najdete v tématu [spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>fronty  
 Fronty ve WCF poskytují obě reliable přenos zpráv a oddělení mezi zdroje a cíle za cenu vysokou latenci. Ve frontě WCF je nástavbou komunikaci služby Řízení front zpráv (MSMQ).  
  
 Služba MSMQ je dodáván jako možnost s Windows, na kterém běží jako služba NT. Zaznamenává zprávy pro předávání v přenosové frontě jménem zdroji a doručí ho do cílové fronty. Cílová fronta přijímá zprávy jménem cíl pro pozdější doručení pokaždé, když cíl žádosti o zprávy. Správci fronty MSMQ implementovat spolehlivé přenos zpráv protokolu, aby se zprávy nejsou ztraceno v přenosu. Protokol může být nativní nebo založený na protokolu SOAP, jako je například spolehlivé zasílání zpráv protokolu (SRMP Soap).  
  
 Oddělení, spolu s přenosy spolehlivých zpráv mezi front, umožňuje aplikacím, které jsou volně vázány spolehlivě komunikovat. Na rozdíl od spolehlivé relace zdrojových a cílových nemusí běžet ve stejnou dobu. To umožňuje implicitně scénáře, kde fronty, v důsledku toho slouží jako mechanismus pro vyrovnávání zatížení při došlo k neshodě mezi výroby zprávy ve zdroji a frekvence zpráv konzumace cíl. Další informace o frontách najdete v tématu [fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Viz také:

- [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
- [Přehled spolehlivých relací](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
