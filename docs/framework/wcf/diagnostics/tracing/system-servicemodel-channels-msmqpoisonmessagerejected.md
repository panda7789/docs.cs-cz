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
ms.openlocfilehash: 55ae2ed6ac8a02218fa4c13063fb8b8a8c474fd8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Poškozená zpráva byla odmítnuta.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že byl nezpracovatelná zpráva došlo a následně odmítnuto. K tomu dojde při `ReceiveErrorHandling` – NetMsmqBinding nebo – MsmqIntegrationBinding je nastavena na `Reject`. Odmítnuté zprávy doručuje zpět do odesílatele [frontu nedoručených zpráv](http://go.microsoft.com/fwlink/?LinkId=99544).  
  
 V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkId=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat. V tématu [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) další podrobnosti o odmítnuté zprávy znamená služby MSMQ.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)
