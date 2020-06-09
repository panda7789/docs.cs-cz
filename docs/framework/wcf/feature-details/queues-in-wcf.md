---
title: Fronty ve službě Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: d1fee4fdde18563ec6ccce4f0675d8581184be08
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596731"
---
# <a name="queues-in-windows-communication-foundation"></a>Fronty ve službě Windows Communication Foundation
Témata v této části popisují podporu Windows Communication Foundation (WCF) pro fronty. Služba WCF poskytuje podporu pro řazení do fronty tím, že využije služby Řízení front zpráv (dříve označované jako MSMQ) jako přenos a umožňuje následující scénáře:  
  
- Volně spárované aplikace. Odesílání aplikací může odesílat zprávy do front bez nutnosti zjistit, zda je přijímající aplikace k dispozici pro zpracování zprávy. Fronta zajišťuje nezávislost zpracování, která umožňuje odesílající aplikaci odesílat zprávy do fronty za rychlostí, která nezávisí na tom, jak rychle přijímající aplikace můžou zprávy zpracovávat. Celková dostupnost systému se zvyšuje při odesílání zpráv do fronty, která není pevně spojena se zpracováním zpráv.  
  
- Izolace selhání. Aplikace, které odesílají nebo přijímají zprávy do fronty, můžou selhat, aniž by to mělo vliv na sebe. Pokud například přijímající aplikace nebude úspěšná, odesílající aplikace může dál odesílat zprávy do fronty. Po opětovném přihlášení může příjemce zpracovat zprávy z fronty. Při izolaci selhání se zvyšuje celková spolehlivost a dostupnost systému.  
  
- Vyrovnávání zátěže. Posílání aplikací může obdržet nenáročný příjem aplikací se zprávami. Fronty mohou spravovat neshodné provozní nároky a sazby za spotřebu, takže příjemce není zahlcený.  
  
- Odpojené operace. Operace odesílání, přijímání a zpracování se můžou odpojit při komunikaci v sítích s vysokou latencí nebo v sítích s omezeným dostupností, jako třeba v případě mobilních zařízení. Fronty umožňují, aby tyto operace pokračovaly i po odpojení koncových bodů. Když se připojení znovu naváže, zařadí se zprávy do přijímající aplikace.  
  
 Chcete-li použít funkci Queues v aplikaci WCF, můžete použít jednu ze standardních vazeb, nebo můžete vytvořit vlastní vazbu, pokud jedna ze standardních vazeb nevyhovuje vašim požadavkům. Další informace o relevantních standardních vazbách a o tom, jak zvolit jednu, najdete v tématu [How to: Exchange with a Applications služby Řízení front zpráv (WCF](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)). Další informace o vytváření vlastních vazeb najdete v tématu [Custom Bindings](../extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled front](queues-overview.md)  
 Přehled konceptů služby Řízení front zpráv.  
  
 [Fronty ve WCF](queuing-in-wcf.md)  
 Přehled podpory fronty WCF.  
  
 [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Vysvětluje, jak použít <xref:System.ServiceModel.NetMsmqBinding> třídu ke komunikaci mezi klientem WCF a službou WCF.  
  
 [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Vysvětluje, jak používat <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ke komunikaci mezi WCF a aplikacemi služby Řízení front zpráv.  
  
 [Seskupování zpráv zařazených do fronty v relaci](grouping-queued-messages-in-a-session.md)  
 Vysvětluje, jak seskupit zprávy ve frontě a usnadnit tak zpracování korelační zprávy jedinou přijímající aplikací.  
  
 [Dávkování zpráv v transakci](batching-messages-in-a-transaction.md)  
 Vysvětluje, jak Batch zprávy v transakci.  
  
 [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Vysvětluje, jak zpracovávat selhání přenosu zpráv a doručení pomocí front nedoručených zpráv a jak zpracovávat zprávy z fronty nedoručených zpráv.  
  
 [Zpracování škodlivých zpráv](poison-message-handling.md)  
 Vysvětluje, jak zpracovávat poškozené zprávy (zprávy, které překročily maximální počet pokusů o doručení do přijímající aplikace).  
  
 [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Shrnuje rozdíly ve funkci fronty WCF mezi systémy Windows Vista, Windows Server 2003 a Windows XP.  
  
 [Zabezpečení zpráv pomocí zabezpečení přenosu](securing-messages-using-transport-security.md)  
 Popisuje, jak používat zabezpečení přenosu k zabezpečení zpráv ve frontě.  
  
 [Zabezpečení zpráv](securing-messages-using-message-security.md)  
 Popisuje, jak používat zabezpečení zpráv k zabezpečení zpráv ve frontě.  
  
 [Řešení potíží se zasíláním zpráv zařazovaných do front](troubleshooting-queued-messaging.md)  
 Vysvětluje, jak řešit běžné problémy s řazením do fronty.  
  
 [Doporučené postupy pro komunikaci ve frontě](best-practices-for-queued-communication.md)  
 Vysvětluje osvědčené postupy pro použití komunikace ve frontě WCF.  
