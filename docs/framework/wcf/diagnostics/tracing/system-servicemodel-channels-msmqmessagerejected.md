---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3194409ef6daf417d3643eed20afa18944e29ad3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ odmítl zprávu.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že služby MSMQ zpráva byla odmítnuta.  
  
 MSMQ zprávy mohou být odmítnuty při [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (používá se s – NetMsmqBinding nebo – MsmqIntegrationBinding) se nepodařilo zpracovat. Takové zprávy se označují jako poškozených zpráv. Byl odmítnut nezpracovatelná zpráva při `ReceiveErrorHandling` – NetMsmqBinding nebo – MsmqIntegrationBinding je nastavena na `Reject`. Odmítnuté zprávy doručuje zpět do odesílatele [frontu nedoručených zpráv](http://go.microsoft.com/fwlink/?LinkID=99544).  
  
 V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.  
  
 V tématu [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) další podrobnosti o odmítnuté zprávy znamená služby MSMQ.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)
