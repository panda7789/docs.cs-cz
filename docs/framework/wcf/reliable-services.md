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
ms.openlocfilehash: f98da5db34686e3bf09cc14c42a2ff6b693201f6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803751"
---
# <a name="reliable-services"></a>Spolehlivé služby
Fronty a spolehlivé relace jsou funkce Windows Communication Foundation (WCF), které implementují spolehlivé zasílání zpráv. Toto téma popisuje funkce spolehlivého zasílání zpráv služby WCF.  
  
 *Spolehlivé zasílání zpráv* je způsob spolehlivého zasílání zpráv zdroje (volat *zdroj*) přenosu zpráv spolehlivě do cílového umístění spolehlivého zasílání zpráv (volat *cílové*).  
  
 Spolehlivé zasílání zpráv provádí následující funkce:  
  
-   Přenáší záruky pro zprávy odeslané ze zdroje do cílového umístění, bez ohledu na selhání přenos nebo přenosu zpráv.  
  
-   Odděluje zdroj a cíl od sebe navzájem. To poskytuje nezávislé selhání a obnovení zdroj a cíl, a taky přenosu spolehlivé a doručení zpráv, i v případě, že zdroj nebo cíl nedostupný.  
  
 Spolehlivé zasílání zpráv se často dodává za cenu vysokou latencí. *Latence* je doba potřebná pro zprávu, která se přenos dat ze zdroje do cíle. WCF, proto poskytuje následující typy spolehlivého zasílání zpráv:  
  
-   [Spolehlivé relace](../../../docs/framework/wcf/feature-details/reliable-sessions.md), který nabízí spolehlivé přenosu bez nákladů vysokou latencí.  
  
-   [Fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md), který nabízí spolehlivé přenosů a oddělení mezi zdrojovým a cílovým.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace zadejte začátku do konce spolehlivé přenosu zpráv mezi zdrojem a cílem pomocí protokolu WS-spolehlivé zasílání zpráv, bez ohledu na počet a typ prostředníci, které oddělují koncové body zasílání zpráv (zdrojové a cílové). To zahrnuje všechny prostředníci přenosu, které nepoužívají protokolu SOAP (například HTTP proxy) nebo prostředníci používající SOAP (například založený na protokolu SOAP směrovače nebo mosty), které jsou požadovány pro zprávy tok mezi koncových bodů. Spolehlivé relace použijte okno s přenosy v paměti na selhání úroveň zprávy protokolu SOAP maska a znovu vytvořte připojení v případě selhání přenosu.  
  
 Spolehlivé relace poskytují spolehlivé zpráv s nízkou latencí přenosů. Poskytují protokolu SOAP zprávy přes všechny proxy servery nebo prostředníci, ekvivalent jaké TCP poskytuje pro pakety prostřednictvím mostů IP. Další informace o spolehlivé relace najdete v tématu [spolehlivé relace](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Fronty  
 Fronty ve WCF zadejte oba spolehlivé přenosu zpráv a oddělení mezi zdroje a cíle za cenu vysokou latencí. Ve frontě WCF komunikace je založený na řízení front zpráv (MSMQ).  
  
 MSMQ dodává jako volitelná komponenta s Windows. Služba MSMQ spouští jako služby systému Windows. Se zaznamená zprávy k přenosu v přenosové frontě jménem zdroji a doručí do cílové fronty. Cílová fronta přijímá zprávy jménem cíl pro pozdější doručení kdykoliv cíl zprávy. Správci služby MSMQ implementovat protokol spolehlivého přenos zpráv tak, aby zprávy nejsou ztrátě při přenosu. Protokol může být nativní nebo protokol založený na protokolu SOAP názvem protokol spolehlivého zasílání zpráv na protokolu SOAP (SRMP).  
  
 Oddělení, spolu s spolehlivé zpráva přenosy mezi front, umožňuje aplikacím, které jsou volně vázány spolehlivě komunikovat. Na rozdíl od spolehlivé relace zdrojové a cílové nemusí být spuštěna ve stejnou dobu. Implicitně to umožňuje scénáře, kde fronty, ve skutečnosti slouží jako vhodný mechanismus Vyrovnávání zatížení při míra zdroje provozních zpráv a cíle tempo spotřeby zpráva se neshodují. Další informace o frontách najdete v tématu [fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled spolehlivých relací](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)  
 [Zařazování do front ve WCF](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
