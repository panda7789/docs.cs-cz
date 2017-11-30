---
title: "Fronty a spolehlivé relace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfd81e1b2290f1ed2c4e2400516ce0d23c7588f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="queues-and-reliable-sessions"></a>Fronty a spolehlivé relace
Fronty a spolehlivé relace jsou [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkce, které implementují spolehlivé zasílání zpráv. Témata obsažené v této části popisují [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce spolehlivého zasílání zpráv.  
  
 Spolehlivé zasílání zpráv je, jak zdroj spolehlivého zasílání zpráv (označovaný jako zdroj) přenáší zprávy spolehlivě do spolehlivého zasílání zpráv cíl (označované jako cíl).  
  
 Spolehlivé zasílání zpráv má následující klíčové aspekty:  
  
-   Záruky přenosu zpráv odeslaných z zdroje do cílového umístění, bez ohledu na to, chyba přenosu zprávy nebo přenosu chyb.  
  
-   Oddělení zdroj a cíl z vzájemně, která poskytuje nezávislé selhání a obnovení zdroj a cíl jako dobře stejně spolehlivá přenos a doručování zpráv Přestože zdroj nebo cíl nedostupný.  
  
 Spolehlivé zasílání zpráv se často dodává za cenu vysokou latencí. Latence je doba, která je potřebná pro zprávu, která se přenos dat ze zdroje do cíle. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], proto poskytuje následující typy spolehlivého zasílání zpráv:  
  
-   [Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), která nabízí spolehlivé přenosu bez nákladů vysokou latencí  
  
-   [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), která nabízí spolehlivé přenosů a oddělení mezi zdrojovým a cílovým.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace zadejte začátku do konce spolehlivé přenosu zpráv mezi zdrojem a cílem pomocí protokolu WS-ReliableMessaging bez ohledu na počet a typ prostředníci, které oddělují koncové body zasílání zpráv (zdrojové a cílové). To zahrnuje všechny prostředníci přenosu, které nepoužívají protokolu SOAP (například HTTP proxy) nebo prostředníci používající SOAP (například založený na protokolu SOAP směrovače nebo mosty), které jsou požadovány pro zprávy tok mezi koncových bodů. Spolehlivé relace použijte okno s přenosy v paměti na selhání úroveň zprávy protokolu SOAP maska a znovu vytvořte připojení v případě selhání přenosu.  
  
 Spolehlivé relace poskytují spolehlivé zpráv s nízkou latencí přenosů. Poskytují protokolu SOAP zprávy přes všechny proxy servery nebo prostředníci, ekvivalent jaké TCP poskytuje pro pakety prostřednictvím mostů IP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]spolehlivé relace, najdete v části [spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Fronty  
 Fronty v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zadejte oba spolehlivé přenosu zpráv a oddělení mezi zdroje a cíle za cenu vysokou latencí. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]komunikace ve frontě je postavená na služby Řízení front zpráv (MSMQ).  
  
 MSMQ je dodáván jako možnost s Windows, který běží jako služba NT. Se zaznamená zprávy k přenosu v přenosové frontě jménem zdroji a doručí do cílové fronty. Cílová fronta přijímá zprávy jménem cíl pro pozdější doručení vždy, když cíl požadavky pro zprávy. Správci frontu MSMQ implementovat protokol spolehlivého přenos zpráv tak, aby zprávy nejsou ztrátě při přenosu. Protokol může být nativní nebo založený na protokolu SOAP, jako je například Soap spolehlivého zasílání zpráv SRMP (Protocol).  
  
 Oddělení, spolu s spolehlivé zpráva přenosy mezi front, umožňuje aplikacím, které jsou volně vázány spolehlivě komunikovat. Na rozdíl od spolehlivé relace zdrojové a cílové nemusí být spuštěna ve stejnou dobu. Implicitně to umožňuje scénáře, kde fronty, ve skutečnosti slouží jako vhodný mechanismus Vyrovnávání zatížení při došlo k neshodě mezi zpráva výroby zdrojem a rychlost spotřeby zpráva podle cílové. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]fronty, najdete v části [fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Viz také  
 [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Spolehlivé relace – přehled](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
