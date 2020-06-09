---
title: Rozdíly funkcí front zpráv v systémech Windows Vista, Windows Server 2003 a Windows XP
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: abd81b5e7bf611fc6b4f446a82628b83130f2d54
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599201"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Rozdíly funkcí front zpráv v systémech Windows Vista, Windows Server 2003 a Windows XP
Toto téma shrnuje rozdíly mezi funkcí fronty Windows Communication Foundation (WCF) mezi systémy Windows Vista, Windows Server 2003 a Windows XP.  
  
## <a name="application-specific-dead-letter-queue"></a>Fronta nedoručených zpráv specifická pro aplikaci  
 Zprávy ve frontě mohou zůstat ve frontě po neomezenou dobu, pokud přijímající aplikace je nepřečte včas. Toto chování není vhodné, pokud jsou zprávy citlivé na čas. Zprávy s časovým rozlišením mají `TimeToLive` v vazbě zařazené do fronty nastavenou vlastnost. Tato vlastnost určuje, jak dlouho mohou být zprávy ve frontě, než vyprší jejich platnost. Zprávy s vypršenou platností se odesílají do speciální fronty označované jako fronta nedoručených zpráv. Zpráva může také končit nedoručenou frontou z jiných důvodů, například překročení kvóty fronty nebo selhání ověřování.  
  
 Pro všechny aplikace zařazené do fronty, které sdílejí správce front, existuje obvykle jedna fronta nedoručených zpráv v celém systému. Fronta nedoručených zpráv pro každou aplikaci umožňuje lepší izolaci mezi aplikacemi zařazenými do fronty, které sdílejí správce front. umožňuje těmto aplikacím zadat vlastní frontu nedoručených zpráv specifickou pro danou aplikaci. Aplikace, která sdílí frontu nedoručených zpráv s jinými aplikacemi, musí procházet frontu a vyhledat tak zprávy, které se na ně vztahují. U fronty nedoručených zpráv konkrétní aplikace je možné zajistit, že se na ni vztahují všechny zprávy ve frontě nedoručených zpráv.  
  
 Systém Windows Vista poskytuje pro fronty nedoručených zpráv specifické pro aplikaci. Fronty nedoručených zpráv specifické pro aplikaci nejsou k dispozici v systémech Windows Server 2003 a Windows XP a aplikace musí používat frontu nedoručených zpráv v rámci systému.  
  
## <a name="poison-message-handling"></a>Zpracování nezpracovatelných zpráv  
 Nezpracovatelná zpráva je zpráva, že překročila maximální počet pokusů o doručení přijímající aplikace. K této situaci může dojít, když aplikace, která čte zprávu z transakční fronty, nemůže zprávu zpracovat okamžitě kvůli chybám. Pokud aplikace přeruší transakci, ve které byla zpráva ve frontě přijata, vrátí zprávu do fronty. Aplikace se pak pokusí znovu načíst zprávu v nové transakci. Pokud problém, který způsobí chybu, se neopraví, přijímající aplikace může zablokovat ve smyčce příjem a přerušit stejnou zprávu, dokud nepřekračuje maximální počet pokusů o doručení a výsledky nepoškozené zprávy.  
  
 Mezi hlavní rozdíly mezi službou Řízení front zpráv (MSMQ) v systému Windows Vista, Windows Server 2003 a Windows XP, které jsou relevantní pro zpracování poškození, patří následující:  
  
- Služba MSMQ v systému Windows Vista podporuje dílčí fronty, přičemž systémy Windows Server 2003 a Windows XP nepodporují dílčí fronty. Podfronty se používají při zpracování nezpracovatelných zpráv. Fronty opakování a nepoškozená fronta jsou podfronty aplikací, které jsou vytvořeny na základě nastavení zpracování nezpracovatelných zpráv. Určuje, kolik `MaxRetryCycles` opakovaných podfront se má vytvořit. Proto se při spuštění v systému Windows Server 2003 nebo Windows XP `MaxRetryCycles` ignoruje a není `ReceiveErrorHandling.Move` povolená.  
  
- Služba MSMQ v systému Windows Vista podporuje negativní potvrzení, ale systémy Windows Server 2003 a Windows XP ne. Negativní potvrzení od přijímacího správce fronty způsobí, že odesílajícímu správci fronty umístí odmítnutou zprávu do fronty nedoručených zpráv. Tato možnost není `ReceiveErrorHandling.Reject` povolena v systémech Windows Server 2003 a Windows XP.  
  
- Služba MSMQ v systému Windows Vista podporuje vlastnost zprávy, která udržuje počet pokusů o doručení zprávy. Tato vlastnost počet přerušení není k dispozici v systémech Windows Server 2003 a Windows XP. Služba WCF udržuje počet přerušení v paměti, takže je možné, že tato vlastnost nesmí obsahovat přesnou hodnotu, pokud je stejná zpráva čtena více než jednou službou WCF ve webové farmě.  
  
## <a name="remote-transactional-read"></a>Vzdálená transakční čtení  
 Služba MSMQ v systému Windows Vista podporuje vzdálená transakční čtení. To umožňuje aplikaci, která je čtena z fronty, hostovat na počítači, který se liší od počítače, ve kterém je fronta hostovaná. Tím je zajištěno, že bude mít možnost načítat farmu služeb z centrální fronty, čímž se zvýší celková propustnost systému. Také zajišťuje, že pokud při čtení a zpracování zprávy dojde k selhání, transakce se vrátí zpět a zpráva zůstane ve frontě pro pozdější zpracování.  
  
## <a name="see-also"></a>Viz také

- [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Zpracování škodlivých zpráv](poison-message-handling.md)
