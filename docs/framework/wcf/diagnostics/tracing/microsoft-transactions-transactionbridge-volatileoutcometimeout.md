---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: fac3682a955ed0caf21fdb1dea48672bf3bdea77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704573"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="bd4eb-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="bd4eb-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="bd4eb-103">Služba protokolu WS-AT vypršel časový limit čekání na odpověď na zprávu z nestálého účastníka.</span><span class="sxs-lookup"><span data-stu-id="bd4eb-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="bd4eb-104">Výsledek transakce může mít nejistým výsledkem vrátí účastníka.</span><span class="sxs-lookup"><span data-stu-id="bd4eb-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bd4eb-105">Popis</span><span class="sxs-lookup"><span data-stu-id="bd4eb-105">Description</span></span>  
 <span data-ttu-id="bd4eb-106">Trasovaná při nestálého účastníka se rozhodl potvrzení nebo přerušení, ale neodpověděl na požadavek na zápis nebo vrácení zpět v daném čase.</span><span class="sxs-lookup"><span data-stu-id="bd4eb-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="bd4eb-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="bd4eb-107">Troubleshooting</span></span>  
 <span data-ttu-id="bd4eb-108">Ujistěte se, že se všichni účastníci Volatile neodpoví v daném čase.</span><span class="sxs-lookup"><span data-stu-id="bd4eb-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="bd4eb-109">Výchozí časové období je 180 sekund.</span><span class="sxs-lookup"><span data-stu-id="bd4eb-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="bd4eb-110">Pokud to není dostatečné, zvýšit `VolatileOutcomeDelay` časovače zásady pro WS-AT.</span><span class="sxs-lookup"><span data-stu-id="bd4eb-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd4eb-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd4eb-111">See also</span></span>
- [<span data-ttu-id="bd4eb-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="bd4eb-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="bd4eb-113">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="bd4eb-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bd4eb-114">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="bd4eb-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
