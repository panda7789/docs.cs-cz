---
title: "Fronty ve službě Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dfc78d355db4bd8c9d43541545e6fac35086b39
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="queues-in-windows-communication-foundation"></a>Fronty ve službě Windows Communication Foundation
Témata v této části popisují [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporu pro fronty. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje podporu pro službu Řízení front s využitím Microsoft služby Řízení front zpráv (dříve označované jako MSMQ) jako přenosového mechanismu a umožňuje následující scénáře:  
  
-   Volně párované aplikace. Odeslání aplikace mohou zasílat zprávy do fronty, aniž by museli vědět, zda má přijímající aplikace je k dispozici pro zpracování zprávy. Fronty poskytuje nezávislost zpracování, který umožňuje aplikacím k odesílání zpráv do fronty s rychlostí, která není závislá na rychlost přijímací aplikace dokáže zpracovat zprávy. Celkové dostupnosti systému zvýší při odesílání zpráv do fronty není pevně pro zpracování zprávy.  
  
-   Selhání izolace. Aplikace odesílání nebo přijímání zprávy do fronty může selhat, aniž by to ovlivnilo navzájem. Pokud například přijímající aplikace selže, můžete k odesílání zpráv do fronty pokračovat odesílající aplikací. Pokud příjemce je znovu nahoru, může zpracovat zprávy z fronty. Selhání izolace zvyšuje celkovou spolehlivost systému a dostupnosti.  
  
-   Vyrovnávání zátěže. Odeslání aplikace můžete zahlcovat přijímající aplikace s zprávy. Fronty můžete spravovat počty výroby a spotřeby neodpovídající zpráv, tak, aby přijímač není obávat přílišné složitosti.  
  
-   Odpojené operace. Odesílání, příjem a operace zpracování může odpojují při komunikaci přes s vysokou latencí sítě nebo omezené dostupnosti sítě, například v případě mobilních zařízení. Fronty mohly tyto operace pokračovat, i když jsou odpojené koncových bodů. Když je znovu navázat připojení, fronty přeposílá zprávy na přijímající aplikace.  
  
 Použití funkce fronty v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, můžete použít jednu standardní vazby, nebo můžete vytvořit vlastní vytvoření vazby, pokud jedna z vazeb standardní nevyhovuje vašim požadavkům. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]relevantní standardní vazby a jak zvolit jednu, najdete v části [postup: Exchange zpráv pomocí koncových bodů WCF a aplikace služby Řízení front zpráv](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vytváření vlastních vazeb, najdete v části [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Přehled konceptů služby Řízení front zpráv.  
  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Přehled [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fronty podpory.  
  
 [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Vysvětluje, jak používat <xref:System.ServiceModel.NetMsmqBinding> třídy ke komunikaci mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
 [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Vysvětluje, jak používat <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ke komunikaci mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a aplikace služby Řízení front zpráv.  
  
 [Seskupování zpráv zařazených do fronty v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Vysvětluje, jak chcete seskupit zprávy ve frontě pro usnadnění zpracování korelační zprávy jeden přijímající aplikací.  
  
 [Dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Vysvětluje, jak dávky zpráv v transakci.  
  
 [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Popisuje způsob zpracování chyb přenosu a doručování zpráv pomocí front nedoručených zpráv a postupy zpracování zpráv z fronty nedoručených zpráv.  
  
 [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Vysvětluje, jak pro zpracování poškozených zpráv (zpráv, které překročily maximální počet pokusů o doručení přijímající aplikaci).  
  
 [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Shrnuje rozdíly v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fronty funkci mezi [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Popisuje, jak zabezpečit zprávy ve frontě pomocí zabezpečení přenosu.  
  
 [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Popisuje, jak používat zabezpečení zpráv zabezpečit zprávy ve frontě.  
  
 [Řešení problémů se zasíláním zpráv zařazovaných do front](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Vysvětluje, jak řešit běžné problémy s front zpráv.  
  
 [Osvědčené postupy pro komunikaci ve frontě](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Popisuje osvědčené postupy pro použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikace ve frontě.  
  
## <a name="see-also"></a>Viz také  
 [Služba Řízení front zpráv](http://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)
