---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 4feeb1b57d79c7445d51f5d688b0a9f55e761542
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997504"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ odmítl zprávu.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že zprávy MSMQ byla odmítnuta.  
  
 Když (používá se NetMsmqBinding nebo vazbu MsmqIntegrationBinding) Windows Communication Foundation (WCF) není schopen se jejich zpracování může být odmítnutá zprávy služby MSMQ. Tyto zprávy jsou označovány jako počet nezpracovatelných zpráv. Nezpracovatelná zpráva zamítá při `ReceiveErrorHandling` NetMsmqBinding nebo vazbu MsmqIntegrationBinding je nastavena na `Reject`. Odmítnuté zprávy se doručí zpět do odesílatele [fronty nedoručených zpráv](https://go.microsoft.com/fwlink/?LinkID=99544).  
  
 Zobrazit [zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkID=99546) podrobné informace o při stát nezpracovatelných zpráv a způsob konfigurace vaší služby k odpovídajícím způsobem zpracovat.  
  
 Zobrazit [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) pro další podrobnosti o tom, co znamená odmítnuté zprávy služby MSMQ.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkID=99546)
- [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548)
