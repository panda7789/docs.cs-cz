---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: c388a9dc3569e20639de09abc5f4941b73c561ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578048"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
Služba MSMQ odmítla zprávu.  
  
## <a name="description"></a>Popis  
 Toto trasování indikuje, že zpráva služby MSMQ byla odmítnuta.  
  
 Zprávy služby MSMQ lze odmítat, pokud Windows Communication Foundation (WCF) (použité s NetMsmqBinding nebo MsmqIntegrationBinding) není schopen je zpracovat. Tyto zprávy se označují jako nepoškozené zprávy. Pokud `ReceiveErrorHandling` je vlastnost na NetMsmqBinding nebo MsmqIntegrationBinding nastavena na hodnotu, je nezpracovatelná zpráva odmítnuta `Reject` . Odmítnutá zpráva se doručí zpátky do [fronty nedoručených](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)zpráv odesilatele.  
  
 Další informace o tom, kdy se zprávy stanou neslušně a jak nakonfigurovat službu tak, aby byla správně zpracována, naleznete v tématu [manipulace s poškozením](../../feature-details/poison-message-handling.md).  
  
 Další informace o tom, co odmítnutá zpráva znamená v MSMQ, najdete v tématu [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
- [Zpracování nezpracovatelných zpráv](../../feature-details/poison-message-handling.md)
- [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
