---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1385995165308cb1c2f2e6bd6c8a800a88b7b79e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Čekání na odpověď na zprávu o výsledek od volatile účastníka vypršel časový limit služby protokolu WS-AT. Výsledek transakce může mít nejistých účastník vrátí.  
  
## <a name="description"></a>Popis  
 Sledovat, když se rozhodla potvrzení nebo přerušení Volatile účastník, ale neodpověděl na žádost o potvrzení nebo vrácení změn v rámci dané množství času.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zajistěte, aby všichni účastníci Volatile schopné reagovat v rámci daného časového intervalu. Výchozí období je 180 sekund.  Pokud to není dostatečné, zvýšit `VolatileOutcomeDelay` časovače zásady pro služby WS-AT.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
