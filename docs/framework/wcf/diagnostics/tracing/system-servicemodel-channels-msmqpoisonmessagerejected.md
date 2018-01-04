---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28924f04dc83387f49c2369c2598c028f9b8d4bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Poškozená zpráva byla odmítnuta.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že byl nezpracovatelná zpráva došlo a následně odmítnuto. K tomu dojde při `ReceiveErrorHandling` – NetMsmqBinding nebo – MsmqIntegrationBinding je nastavena na `Reject`. Odmítnuté zprávy doručuje zpět do odesílatele [frontu nedoručených zpráv](http://go.microsoft.com/fwlink/?LinkId=99544).  
  
 V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkId=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat. V tématu [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) další podrobnosti o odmítnuté zprávy znamená služby MSMQ.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)
