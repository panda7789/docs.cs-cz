---
title: Spolehlivé služby
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
ms.openlocfilehash: a617100e46d4bcafb9325efa99c255f2f8ee5981
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216766"
---
# <a name="reliable-services"></a>Spolehlivé služby
Fronty a spolehlivé relace jsou funkce Windows Communication Foundation (WCF), které implementují spolehlivé zasílání zpráv. Toto téma popisuje funkce spolehlivé zasílání zpráv služby WCF.  
  
 *Spolehlivé zasílání zpráv* je způsob spolehlivého zasílání zpráv zdroje (volá se *zdroj*) přenosu zpráv spolehlivě do spolehlivého zasílání zpráv cíle (volá *cílové*).  
  
 Spolehlivé zasílání zpráv zajišťuje následující funkce:  
  
-   Přenese záruky pro zprávy odeslané ze zdroje do cíle bez ohledu na selhání přenosu nebo přenos zpráv.  
  
-   Odděluje zdroj a cíl od sebe navzájem. To poskytuje nezávislé selhání a obnovení zdroji a cíl, stejně jako reliable přenos a doručování zpráv, i v případě, že zdroj nebo cíl nedostupný.  
  
 Spolehlivé zasílání zpráv je často za cenu vysokou latenci. *Latence* je čas potřebný pro zprávu pro přenos dat ze zdroje do cíle. WCF, proto poskytuje spolehlivé zasílání zpráv následující typy:  
  
-   [Spolehlivé relace](../../../docs/framework/wcf/feature-details/reliable-sessions.md), která nabízí spolehlivé přenos bez nákladů na vysokou latenci.  
  
-   [Fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md), která nabízí spolehlivé přenosů a oddělení mezi zdrojem a cílem.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace poskytují začátku do konce spolehlivé přenos zpráv mezi zdrojem a cílem pomocí protokolu WS-Reliable zasílání zpráv bez ohledu na počet a typ zprostředkovatelů, které oddělují koncových bodů pro zasílání zpráv (zdrojové a cílové). To zahrnuje všechny přenosu zprostředkovatelů, které nevyužívají protokol SOAP (například proxy protokolu HTTP) nebo zprostředkovatelů, které používají protokol SOAP (například založený na protokolu SOAP směrovače nebo mosty), které jsou požadovány pro zprávy, které jsou předávány mezi koncovými body. Spolehlivé relace okno přenosu v paměti na selhání úroveň zprávy protokolu SOAP maska a znovu vytvořit připojení v případě selhání přenosu.  
  
 Spolehlivé relace poskytují spolehlivé zprávy s nízkou latencí přenosy. Poskytují pro zprávy protokolu SOAP přes všechny proxy servery nebo prostředníci, ekvivalent jaké TCP poskytuje pro pakety přes mosty IP. Další informace o spolehlivých relací najdete v tématu [spolehlivé relace](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>fronty  
 Fronty ve WCF poskytují obě reliable přenos zpráv a oddělení mezi zdroje a cíle za cenu vysokou latenci. Ve frontě WCF komunikace je postavená na řízení front zpráv (MSMQ).  
  
 MSMQ se dodává jako volitelnou komponentu s Windows. Služba MSMQ běží jako služba Windows. Zaznamenává zprávy pro předávání v přenosové frontě jménem zdroji a doručí ho do cílové fronty. Cílová fronta přijímá zprávy jménem cíl pro pozdější doručení pokaždé, když cíl požadavků zprávy. Správci služby MSMQ implementovat spolehlivé přenos zpráv protokolu, aby se zprávy nejsou ztraceno v přenosu. Protokol může být nativní nebo názvem protokol spolehlivého zasílání zpráv na SOAP (SRMP) protokol založený na protokolu SOAP.  
  
 Oddělení, spolu s přenosy spolehlivých zpráv mezi front, umožňuje aplikacím, které jsou volně vázány spolehlivě komunikovat. Na rozdíl od spolehlivé relace zdrojových a cílových nemusí běžet ve stejnou dobu. To umožňuje implicitně scénáře, kde fronty, v důsledku toho slouží jako mechanismus pro vyrovnávání zatížení při zdroje na počet zpráv produkční a míra cíle spotřeby zprávy se neshodují. Další informace o frontách najdete v tématu [fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled spolehlivých relací](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
- [Zařazování do front ve WCF](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
