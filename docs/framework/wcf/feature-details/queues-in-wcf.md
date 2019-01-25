---
title: Fronty ve službě Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: 13bc401647612c982eb13a3b607e41c6afa61716
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742744"
---
# <a name="queues-in-windows-communication-foundation"></a>Fronty ve službě Windows Communication Foundation
Témata v této části popisují podpora Windows Communication Foundation (WCF) fronty. WCF poskytuje podporu pro službu Řízení front ve využívání Microsoft služby Řízení front zpráv (dříve označovanou jako MSMQ) jako přenosového mechanismu a podporuje následující scénáře:  
  
-   Volně propojených aplikací. Odesílání aplikace mohou odesílat zprávy do front, aniž by museli vědět, jestli je k dispozici pro zpracování zprávy přijímající aplikace. Fronta obsahuje nezávislost zpracování, který umožňuje odeslání aplikace pro odesílání zpráv do fronty s rychlostí, která nezávisí na rychlost přijímací aplikace dokáže zpracovat zprávy. Celková dostupnost systému zvýší při odesílání zpráv do fronty není pevně pro zpracování zpráv.  
  
-   Selhání izolace. Aplikace, odesílání a příjem zpráv do fronty může selhat a vzájemného ovlivnění. Pokud například přijímající aplikace selže, odesílací aplikace nadále odesílat zprávy do fronty. Když příjemce opět nahoru, dokáže zpracovat zprávy z fronty. Selhání izolace zvyšuje celkovou spolehlivost systému a dostupnost.  
  
-   Vyrovnávání zátěže. Odeslání aplikace můžou zahlcovat přijímající aplikace pomocí zpráv. Fronty můžete spravovat počty produkčního prostředí a spotřebu neodpovídající zpráv tak, aby není předešla zahlcení příjemce.  
  
-   Odpojené operace. Odesílání, příjem a zpracování může odpojují při komunikaci přes vysokou latencí sítě nebo omezená dostupnost sítě, jako například v případě mobilních zařízení. Fronty umožní tyto operace pokračovat, i když nejste připojení koncových bodů. Když se obnoví připojení, předává fronty zpráv do přijímající aplikace.  
  
 Chcete-li použít funkci fronty ve WCF aplikaci, můžete použít jednu standardní vazby nebo můžete vytvořit vlastní vazby, pokud jedna z vazeb standardní nevyhovuje vašim požadavkům. Další informace o příslušné standardní vazby a jak zvolit jednu, naleznete v tématu [jak: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Další informace o vytváření vlastních vazeb naleznete v tématu [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Přehled konceptů řízení front zpráv.  
  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Přehled podpory fronty WCF.  
  
 [Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Vysvětluje způsob používání <xref:System.ServiceModel.NetMsmqBinding> třídy ke komunikaci mezi klienta WCF a služby WCF.  
  
 [Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Vysvětluje způsob používání <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ke komunikaci mezi aplikacemi, WCF a služby Řízení front zpráv.  
  
 [Seskupování zpráv zařazených do fronty v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Vysvětluje, jak seskupit zprávy ve frontě pro usnadnění zpracování zprávy pro korelační jedné přijímající aplikace.  
  
 [Dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Vysvětluje, jak batch zpráv v transakci.  
  
 [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Vysvětluje, jak zpracovat selhání přenosu a doručování zpráv pomocí fronty nedoručených zpráv a postupy zpracování zpráv z fronty nedoručených zpráv.  
  
 [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Vysvětluje, jak zpracovat počet nezpracovatelných zpráv (zprávy, které překročily maximální počet pokusů o doručení do přijímající aplikace).  
  
 [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Shrnuje rozdíly ve funkci WCF fronty mezi [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Popisuje způsob použití zabezpečení přenosu pro zabezpečené zprávy ve frontě.  
  
 [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Popisuje způsob použití zpráv zabezpečení pro zabezpečené zprávy ve frontě.  
  
 [Řešení problémů se zasíláním zpráv zařazovaných do front](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Vysvětluje, jak řešit běžné problémy s zařazování do fronty.  
  
 [Osvědčené postupy pro komunikaci ve frontě](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Vysvětluje, komunikace ve frontě doporučené postupy pro používání WCF.  
  
## <a name="see-also"></a>Viz také:
- [Služba Řízení front zpráv](https://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)
