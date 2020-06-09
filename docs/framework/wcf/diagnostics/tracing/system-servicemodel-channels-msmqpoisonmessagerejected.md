---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: f0e49fcfa13bb9932a88a4e79d617343c080bb3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598369"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Nezpracovatelná zpráva byla odmítnuta.  
  
## <a name="description"></a>Popis  

 Trasování indikuje, že byla zjištěna nezpracovatelná zpráva a následně zamítnuta. K tomu dochází, pokud `ReceiveErrorHandling` je vlastnost na NetMsmqBinding nebo MsmqIntegrationBinding nastavena na `Reject` . Odmítnutá zpráva se doručí zpátky do [fronty nedoručených](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)zpráv odesilatele.  
  
 Další informace o tom, kdy se zprávy stanou neslušně a jak nakonfigurovat službu tak, aby byla správně zpracována, naleznete v tématu [manipulace s poškozením](../../feature-details/poison-message-handling.md). Další informace o tom, co odmítnutá zpráva znamená v MSMQ, najdete v tématu [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
- [Zpracování nezpracovatelných zpráv](../../feature-details/poison-message-handling.md)
- [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
