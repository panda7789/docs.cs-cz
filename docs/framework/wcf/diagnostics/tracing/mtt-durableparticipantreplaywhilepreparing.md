---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 375bb5902640ba0816217aec161834d79e9765ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Služba Protokol WS-AT přijala zprávu opětovného přehrání z trvalého účastníka, které neodpovídají na přípravu. V důsledku toho byla transakce přerušena.  
  
## <a name="description"></a>Popis  
 Trasovat, pokud bylo přijato formou opakovaného přehrávání zprávy trvalého účastníka stále připravuje. Tato zpráva neplatné pro tento stav je a transakce přerušena.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Tato chyba může indiate, že trvalého účastníka (včetně podřízených TransactionManagers) došlo k zotavení z chyby, ale je jistí výstup transakce a požádat o jeho stav.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
