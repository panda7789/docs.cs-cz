---
title: Fronty ve službě Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: e921084ed28cb4e846cb269e57e58a194e9437a5
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837334"
---
# <a name="queues-in-windows-communication-foundation"></a>Fronty ve službě Windows Communication Foundation
Témata v této části popisují podporu Windows Communication Foundation (WCF) pro fronty. Služba WCF poskytuje podporu pro řazení do fronty tím, že využije služby Řízení front zpráv (dříve označované jako MSMQ) jako přenos a umožňuje následující scénáře:  
  
- Volně spárované aplikace. Odesílání aplikací může odesílat zprávy do front bez nutnosti zjistit, zda je přijímající aplikace k dispozici pro zpracování zprávy. Fronta zajišťuje nezávislost zpracování, která umožňuje odesílající aplikaci odesílat zprávy do fronty za rychlostí, která nezávisí na tom, jak rychle přijímající aplikace můžou zprávy zpracovávat. Celková dostupnost systému se zvyšuje při odesílání zpráv do fronty, která není pevně spojena se zpracováním zpráv.  
  
- Izolace selhání. Aplikace, které odesílají nebo přijímají zprávy do fronty, můžou selhat, aniž by to mělo vliv na sebe. Pokud například přijímající aplikace nebude úspěšná, odesílající aplikace může dál odesílat zprávy do fronty. Po opětovném přihlášení může příjemce zpracovat zprávy z fronty. Při izolaci selhání se zvyšuje celková spolehlivost a dostupnost systému.  
  
- Vyrovnávání zátěže. Posílání aplikací může obdržet nenáročný příjem aplikací se zprávami. Fronty mohou spravovat neshodné provozní nároky a sazby za spotřebu, takže příjemce není zahlcený.  
  
- Odpojené operace. Operace odesílání, přijímání a zpracování se můžou odpojit při komunikaci v sítích s vysokou latencí nebo v sítích s omezeným dostupností, jako třeba v případě mobilních zařízení. Fronty umožňují, aby tyto operace pokračovaly i po odpojení koncových bodů. Když se připojení znovu naváže, zařadí se zprávy do přijímající aplikace.  
  
 Chcete-li použít funkci Queues v aplikaci WCF, můžete použít jednu ze standardních vazeb, nebo můžete vytvořit vlastní vazbu, pokud jedna ze standardních vazeb nevyhovuje vašim požadavkům. Další informace o relevantních standardních vazbách a o tom, jak zvolit jednu, najdete v tématu [How to: Exchange with a Applications služby Řízení front zpráv (WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)). Další informace o vytváření vlastních vazeb najdete v tématu [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Přehled konceptů služby Řízení front zpráv.  
  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Přehled podpory fronty WCF.  
  
 [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Vysvětluje, jak použít třídu <xref:System.ServiceModel.NetMsmqBinding> ke komunikaci mezi klientem WCF a službou WCF.  
  
 [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Vysvětluje, jak použít <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ke komunikaci mezi aplikacemi WCF a službou Řízení front zpráv.  
  
 [Seskupování zpráv zařazených do fronty v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Vysvětluje, jak seskupit zprávy ve frontě a usnadnit tak zpracování korelační zprávy jedinou přijímající aplikací.  
  
 [Dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Vysvětluje, jak Batch zprávy v transakci.  
  
 [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Vysvětluje, jak zpracovávat selhání přenosu zpráv a doručení pomocí front nedoručených zpráv a jak zpracovávat zprávy z fronty nedoručených zpráv.  
  
 [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Vysvětluje, jak zpracovávat poškozené zprávy (zprávy, které překročily maximální počet pokusů o doručení do přijímající aplikace).  
  
 [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Shrnuje rozdíly ve funkci fronty WCF mezi systémy Windows Vista, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Popisuje, jak používat zabezpečení přenosu k zabezpečení zpráv ve frontě.  
  
 [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Popisuje, jak používat zabezpečení zpráv k zabezpečení zpráv ve frontě.  
  
 [Řešení problémů se zasíláním zpráv zařazovaných do front](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Vysvětluje, jak řešit běžné problémy s řazením do fronty.  
  
 [Osvědčené postupy pro komunikaci ve frontě](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Vysvětluje osvědčené postupy pro použití komunikace ve frontě WCF.  
