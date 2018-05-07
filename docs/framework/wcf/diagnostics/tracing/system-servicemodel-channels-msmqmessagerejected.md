---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 2bd64263a2374c10a3514cbed75f9224542051dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ odmítl zprávu.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že služby MSMQ zpráva byla odmítnuta.  
  
 Zprávy služby MSMQ může být odmítnutá při Windows Communication Foundation (WCF) (používá se s – NetMsmqBinding nebo – MsmqIntegrationBinding) se nepodařilo zpracovat. Takové zprávy se označují jako poškozených zpráv. Byl odmítnut nezpracovatelná zpráva při `ReceiveErrorHandling` – NetMsmqBinding nebo – MsmqIntegrationBinding je nastavena na `Reject`. Odmítnuté zprávy doručuje zpět do odesílatele [frontu nedoručených zpráv](http://go.microsoft.com/fwlink/?LinkID=99544).  
  
 V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.  
  
 V tématu [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) další podrobnosti o odmítnuté zprávy znamená služby MSMQ.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)
