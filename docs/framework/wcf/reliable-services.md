---
title: "Spolehlivé služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 408801e28fec71f133c2dddd3f30b2509ab5896c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-services"></a>Spolehlivé služby
Fronty a spolehlivé relace jsou [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] funkce, které implementují spolehlivé zasílání zpráv. Toto téma popisuje funkce spolehlivého zasílání zpráv [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 *Spolehlivé zasílání zpráv* je způsob spolehlivého zasílání zpráv zdroje (volat *zdroj*) přenosu zpráv spolehlivě do cílového umístění spolehlivého zasílání zpráv (volat *cílové*).  
  
 Spolehlivé zasílání zpráv provádí následující funkce:  
  
-   Přenáší záruky pro zprávy odeslané ze zdroje do cílového umístění, bez ohledu na selhání přenos nebo přenosu zpráv.  
  
-   Odděluje zdroj a cíl od sebe navzájem. To poskytuje nezávislé selhání a obnovení zdroj a cíl, a taky přenosu spolehlivé a doručení zpráv, i v případě, že zdroj nebo cíl nedostupný.  
  
 Spolehlivé zasílání zpráv se často dodává za cenu vysokou latencí. *Latence* je doba potřebná pro zprávu, která se přenos dat ze zdroje do cíle. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], proto poskytuje následující typy spolehlivého zasílání zpráv:  
  
-   [Spolehlivé relace](../../../docs/framework/wcf/feature-details/reliable-sessions.md), který nabízí spolehlivé přenosu bez nákladů vysokou latencí.  
  
-   [Fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md), který nabízí spolehlivé přenosů a oddělení mezi zdrojovým a cílovým.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace zadejte začátku do konce spolehlivé přenosu zpráv mezi zdrojem a cílem pomocí protokolu WS-spolehlivé zasílání zpráv, bez ohledu na počet a typ prostředníci, které oddělují koncové body zasílání zpráv (zdrojové a cílové). To zahrnuje všechny prostředníci přenosu, které nepoužívají protokolu SOAP (například HTTP proxy) nebo prostředníci používající SOAP (například založený na protokolu SOAP směrovače nebo mosty), které jsou požadovány pro zprávy tok mezi koncových bodů. Spolehlivé relace použijte okno s přenosy v paměti na selhání úroveň zprávy protokolu SOAP maska a znovu vytvořte připojení v případě selhání přenosu.  
  
 Spolehlivé relace poskytují spolehlivé zpráv s nízkou latencí přenosů. Poskytují protokolu SOAP zprávy přes všechny proxy servery nebo prostředníci, ekvivalent jaké TCP poskytuje pro pakety prostřednictvím mostů IP. [!INCLUDE[crabout](../../../includes/crabout-md.md)]spolehlivé relace, najdete v části [spolehlivé relace](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Fronty  
 Fronty v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zadejte oba spolehlivé přenosu zpráv a oddělení mezi zdroje a cíle za cenu vysokou latencí. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]komunikace ve frontě je založený na řízení front zpráv (MSMQ).  
  
 MSMQ dodává jako volitelná komponenta s Windows. Služba MSMQ spouští jako služby systému Windows. Se zaznamená zprávy k přenosu v přenosové frontě jménem zdroji a doručí do cílové fronty. Cílová fronta přijímá zprávy jménem cíl pro pozdější doručení kdykoliv cíl zprávy. Správci služby MSMQ implementovat protokol spolehlivého přenos zpráv tak, aby zprávy nejsou ztrátě při přenosu. Protokol může být nativní nebo protokol založený na protokolu SOAP názvem protokol spolehlivého zasílání zpráv na protokolu SOAP (SRMP).  
  
 Oddělení, spolu s spolehlivé zpráva přenosy mezi front, umožňuje aplikacím, které jsou volně vázány spolehlivě komunikovat. Na rozdíl od spolehlivé relace zdrojové a cílové nemusí být spuštěna ve stejnou dobu. Implicitně to umožňuje scénáře, kde fronty, ve skutečnosti slouží jako vhodný mechanismus Vyrovnávání zatížení při míra zdroje provozních zpráv a cíle tempo spotřeby zpráva se neshodují. [!INCLUDE[crabout](../../../includes/crabout-md.md)]fronty, najdete v části [fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled spolehlivých relací](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)  
 [Zařazování do front ve WCF](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
