---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674775"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
Služba MSMQ zprávu odmítla.  
  
## <a name="description"></a>Popis  
 Toto trasování označuje, že zpráva služby MSMQ byla odmítnuta.  
  
 Zprávy služby MSMQ lze odmítnout, pokud je nelze zpracovat při službě WCF (wcf) systému Windows Communication Foundation (používané s vazací NetMsmqBinding nebo MsmqIntegrationBinding). Tyto zprávy jsou označovány jako poškozená zprávy. Poškozená zpráva je `ReceiveErrorHandling` odmítnuta, pokud je vlastnost na NetMsmqBinding `Reject`nebo MsmqIntegrationBinding nastavena na . Odmítnutá zpráva je doručena zpět do [fronty nedoručených zpráv odesílatele](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).  
  
 Další informace o tom, kdy se zprávy stanou jedovatými a jak nakonfigurovat službu tak, aby je správně zpracovávala, naleznete v [tématu Zpracování zpráv poison](../../feature-details/poison-message-handling.md).  
  
 Další informace o tom, co znamená odmítnutá zpráva v msmq, naleznete v [tématu MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).  
  
## <a name="see-also"></a>Viz také

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení potíží s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Zpracování poškozená zpráva](../../feature-details/poison-message-handling.md)
- [Zpráva MQMarkMessage byla odmítnuta.](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
