---
title: Rozdíly funkcí front zpráv v systémech Windows Vista, Windows Server 2003 a Windows XP
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: d13cb3e732d0276902def5de6ca7c007f61b0ec9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039725"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Rozdíly funkcí front zpráv v systémech Windows Vista, Windows Server 2003 a Windows XP
Toto téma shrnuje rozdíly ve funkci Windows Communication Foundation (WCF) fronty mezi [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
## <a name="application-specific-dead-letter-queue"></a>Fronta nedoručených specifické pro aplikaci  
 Zprávy ve frontě může zůstat ve frontě po neomezenou dobu Pokud přijímající aplikace nenačítá je včas. Toto chování není žádoucí, pokud zprávy jsou náročné na čas. Mají časově zprávy `TimeToLive` nastavenou v vazbu s frontou. Tato vlastnost určuje, jak dlouho zprávy může být ve frontě před vypršením jejich platnosti. Zprávy s vypršenou platností se odesílají do speciální fronty s názvem fronty nedoručených zpráv. Zprávy mohou také ukládaly do fronty nedoručených zpráv z jiných důvodů, jako je například překročení kvóty fronty nebo dochází k selhání ověřování.  
  
 Obvykle existuje jeden systémová fronty nedoručených zpráv pro všechny ve frontě aplikace, které sdílejí správce fronty. Fronty nedoručených zpráv pro každou aplikaci umožňuje lepší izolace mezi zařazených do fronty aplikacemi, které sdílejí správce fronty tím, že tyto aplikace zadat své vlastní fronty nedoručených zpráv pro konkrétní aplikaci. Aplikace, která sdílí s jinými aplikacemi fronty nedoručených zpráv musí procházet fronty k vyhledání zpráv, které se dají použít k němu. Pomocí fronty nedoručených zpráv služby specifické pro aplikaci si být jistí aplikace, že se na něj vztahují všechny zprávy do fronty nedoručených zpráv.  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] poskytuje pro konkrétní aplikaci fronty nedoručených zpráv. Fronty nedoručených zpráv specifické pro aplikaci nejsou k dispozici v [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)], a aplikace musí používat fronty nedoručených zpráv celý systém.  
  
## <a name="poison-message-handling"></a>Zpracování zpráv Poison  
 Nezpracovatelná zpráva se zpráva, která byla překročena maximální počet pokusů o doručení do přijímající aplikace. Tato situace může nastat, když aplikaci, která čte zprávy z transakční fronty nemůže okamžitě zpracovat zprávu z důvodu chyby. Pokud aplikace zruší transakce, ve kterém byla přijata zpráv zařazených ve frontě, vrátí zprávu do fronty. Aplikace se pak pokusí se načetla tuto zprávu znovu za novou transakci. Pokud není opraven problém, který způsobuje chybu, můžete získat přijímající aplikace zablokované ve smyčce přijímáním a přerušení stejné zprávy, dokud překračuje maximální počet pokusů o doručení a výsledky nezpracovatelná zpráva.  
  
 Hlavní rozdíly mezi řízení front zpráv (MSMQ) na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] , které jsou relevantní pro zpracování nezpracovatelných patří následující:  
  
- Služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje podfrontách, zatímco [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nepodporují podfrontách. Podfrontách se používají při zpracování poison zpráv. Fronty opakovaných a nezpracovatelných fronty jsou podfronty do aplikace fronty, který je vytvořen na základě nastavení zpracování poison zpráv. `MaxRetryCycles` Určuje, kolik opakování podfrontách vytvořit. Proto při spuštění na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` jsou ignorovány a `ReceiveErrorHandling.Move` není povolený.  
  
- Služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje negativní potvrzení, zatímco [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nepodporují. Negativní potvrzení z využívá správce fronty způsobí, že odesílání správce front k umístění odmítnuté zprávy do fronty nedoručených zpráv. V důsledku toho `ReceiveErrorHandling.Reject` není povolen u [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- Služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje dojde k pokusu o vlastnost zprávy, který udržuje počet určený počet pokusů o doručení zpráv. Tato vlastnost počet přerušení není k dispozici na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. WCF udržuje počet přerušení v paměti, takže je možné, že tato vlastnost nesmí obsahovat přesné hodnoty, když přečte stejné zprávy více než jedné služby WCF ve webové farmě.  
  
## <a name="remote-transactional-read"></a>Vzdálené transakční čtení  
 MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje vzdálené transakční operace čtení. To umožňuje aplikaci, která čte z fronty zajistit také jejich hostování v počítači, který se liší od počítače, který je hostitelem fronty. Tím se zajistí možnost používat farmu služby čtení z centrální fronty, který zlepšuje celkovou propustnost systému. Je také zajišťuje, že pokud dojde k chybě při čtení a zpracování zprávy, transakce se vrátí zpět a zpráva zůstane ve frontě pro pozdější zpracování.  
  
## <a name="see-also"></a>Viz také:

- [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
