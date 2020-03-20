---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674815"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Poškozená zpráva byla odmítnuta.  
  
## <a name="description"></a>Popis  

 Trasování označuje, že poškozená zpráva byla zjištěna a následně odmítnuta. K tomu dochází, `ReceiveErrorHandling` když je vlastnost na NetMsmqBinding nebo `Reject`MsmqIntegrationBinding nastavena na . Odmítnutá zpráva je doručena zpět do [fronty nedoručených zpráv odesílatele](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
 Další informace o tom, kdy se zprávy stanou jedovatými a jak nakonfigurovat službu tak, aby je správně zpracovávala, naleznete v [tématu Zpracování zpráv poison](../../feature-details/poison-message-handling.md). Další informace o tom, co znamená odmítnutá zpráva v msmq, naleznete v [tématu MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).  
  
## <a name="see-also"></a>Viz také

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení potíží s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Zpracování poškozená zpráva](../../feature-details/poison-message-handling.md)
- [Zpráva MQMarkMessage byla odmítnuta.](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
