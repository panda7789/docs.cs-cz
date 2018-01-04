---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87eac8f0e3949ac47c7bb2915a87043bdc205b8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Nelze přesunout nebo zprávu odstranit.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že došlo k chybě při pokusu o přesunutí, odstraňte nebo odmítnout zprávu služby MSMQ.  
  
 Zaměstnává zpráv MSMQ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (při použití s – NetMsmqBinding nebo MsmqIntegrationBinding). Trasování se vztahuje k vybrané hodnotu `ReceiveErrorHandling` vlastnost na – NetMsmqBinding nebo – MsmqIntegrationBinding.  
  
 Trasování není určující pro chybu celkové systému. Však označuje, že zvolený škodlivých dispozice zpráva pro zprávu se nezdařilo. V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
