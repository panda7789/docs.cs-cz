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
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="07d3b-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="07d3b-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="07d3b-103">Čekání na odpověď na zprávu o výsledek od volatile účastníka vypršel časový limit služby protokolu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="07d3b-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="07d3b-104">Výsledek transakce může mít nejistých účastník vrátí.</span><span class="sxs-lookup"><span data-stu-id="07d3b-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="07d3b-105">Popis</span><span class="sxs-lookup"><span data-stu-id="07d3b-105">Description</span></span>  
 <span data-ttu-id="07d3b-106">Sledovat, když se rozhodla potvrzení nebo přerušení Volatile účastník, ale neodpověděl na žádost o potvrzení nebo vrácení změn v rámci dané množství času.</span><span class="sxs-lookup"><span data-stu-id="07d3b-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="07d3b-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="07d3b-107">Troubleshooting</span></span>  
 <span data-ttu-id="07d3b-108">Zajistěte, aby všichni účastníci Volatile schopné reagovat v rámci daného časového intervalu.</span><span class="sxs-lookup"><span data-stu-id="07d3b-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="07d3b-109">Výchozí období je 180 sekund.</span><span class="sxs-lookup"><span data-stu-id="07d3b-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="07d3b-110">Pokud to není dostatečné, zvýšit `VolatileOutcomeDelay` časovače zásady pro služby WS-AT.</span><span class="sxs-lookup"><span data-stu-id="07d3b-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d3b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="07d3b-111">See Also</span></span>  
 [<span data-ttu-id="07d3b-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="07d3b-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="07d3b-113">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="07d3b-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="07d3b-114">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="07d3b-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
