---
title: "Rozdíly funkcí front zpráv v systémech Windows Vista, Windows Server 2003 a Windows XP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f30ad7819a570f0149868502261f986f4dd8c0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Rozdíly funkcí front zpráv v systémech Windows Vista, Windows Server 2003 a Windows XP
Toto téma shrnuje rozdíly v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fronty funkci mezi [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
## <a name="application-specific-dead-letter-queue"></a>Fronty nedoručených zpráv specifické pro aplikaci  
 Zprávy ve frontě může zůstat ve frontě po neomezenou dobu Pokud přijímající aplikace nenačte je včas. Toto chování se nedoporučuje, pokud jsou náročné na čas zprávy. Zprávy náročné na čas `TimeToLive` vlastností nastavenou zařazených do fronty vazba. Tato vlastnost určuje, jak dlouho zprávy může být ve frontě před vypršením jejich platnosti. Zprávy s vypršenou platností jsou odesílány speciální fronty s názvem frontu nedoručených zpráv. Zprávu můžete také ukončit do fronty nedoručených zpráv z jiných důvodů, například překročení kvóty fronty nebo došlo k chybě ověřování.  
  
 Obvykle jediné fronty nedoručených zpráv systémové existuje pro všechny aplikace ve frontě, které sdílejí správce front. Frontu nedoručených zpráv pro každou aplikaci umožňuje lepší izolace mezi aplikacemi zařazených do fronty, které sdílejí správce front tím, že se tyto aplikace zadat své vlastní frontu nedoručených zpráv pro konkrétní aplikace. Procházet fronty najít zprávy, které se vztahují k němu má aplikace sdílející frontu nedoručených zpráv s jinými aplikacemi. S frontu nedoručených zpráv specifické pro aplikaci aplikace si být jistí, že se na něj vztahují všechny zprávy do fronty nedoručených zpráv.  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)]poskytuje pro fronty nedoručených zpráv specifické pro aplikaci. Fronty nedoručených zpráv specifické pro aplikaci nejsou k dispozici v [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)], a aplikace, musí používat systémové fronty nedoručených zpráv.  
  
## <a name="poison-message-handling"></a>Zpracování zpráv Poison  
 Nezpracovatelná zpráva je zprávu, která byla překročena maximální počet pokusů o doručení přijímající aplikaci. Tato situace mohou nastat při aplikaci, která čte zprávy z fronty transakcí nelze okamžitě zpracovat zprávu z důvodu chyb. Pokud aplikace zruší transakce, ve kterém byl přijat zpráv zařazených ve frontě, vrátí zprávu do fronty. Aplikace se pak pokusí se načíst zprávu znovu za novou transakci. Pokud není vyřešen problém, který způsobuje chybu, může být zablokován má přijímající aplikace ve smyčce přijímáním a přerušení stejná zpráva, dokud překračuje maximální počet pokusů o doručení a výsledky poškozená zpráva.  
  
 Hlavní rozdíly mezi řízení front zpráv (MSMQ) na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] , které jsou relevantní pro zpracování poškozených patří:  
  
-   Služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje podfronty, zatímco [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nepodporují podfronty. Podfronty se používají při zpracování poison zpráv. Fronty opakování a poškozených fronty jsou podfronty do fronty aplikace, která je vytvořena na základě nastavení zpracování poison zpráv. `MaxRetryCycles` Určuje, kolik opakujte podfronty k vytvoření. Proto při spuštění [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` jsou ignorovány a `ReceiveErrorHandling.Move` není povolen.  
  
-   Služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje zápornou potvrzení, zatímco [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nepodporují. Záporné potvrzení z přijímající správce front způsobí, že odesílání správce front k umístit odmítnuté zprávy do fronty nedoručených zpráv. Jako takový `ReceiveErrorHandling.Reject` není povolen u [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje dojde k pokusu o vlastnosti zprávy, která udržuje počet Počet doručení zpráv. Tato vlastnost počet přerušení není k dispozici na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udržuje počet přerušení v paměti, takže je možné, že tato vlastnost nesmí obsahovat přesné hodnoty přečtení stejné zprávy o více než jednu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby ve webové farmě.  
  
## <a name="remote-transactional-read"></a>Vzdálené transakcí pro čtení  
 MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje vzdálené transakční čtení. To umožňuje aplikaci, která je čtení z fronty pro hostování v počítači, který se liší od počítače, který je hostitelem fronty. Tím se zajistí možnost farma služby čtení z centrální fronty, která zvyšuje celkovou propustnost systému. Je taky zajišťuje, že pokud dojde k chybě při čtení a zpracování zprávy, transakce se vrátí zpět a zpráva zůstává ve frontě pro pozdější zpracování.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
