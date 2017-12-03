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
ms.openlocfilehash: 2a4bbaca70954e5aa89dbcfd14723551de7848f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Čekání na odpověď na zprávu o výsledek od volatile účastníka vypršel časový limit služby protokolu WS-AT. Výsledek transakce může mít nejistých účastník vrátí.  
  
## <a name="description"></a>Popis  
 Sledovat, když se rozhodla potvrzení nebo přerušení Volatile účastník, ale neodpověděl na žádost o potvrzení nebo vrácení změn v rámci dané množství času.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zajistěte, aby všichni účastníci Volatile schopné reagovat v rámci daného časového intervalu. Výchozí období je 180 sekund.  Pokud to není dostatečné, zvýšit `VolatileOutcomeDelay` časovače zásady pro služby WS-AT.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
