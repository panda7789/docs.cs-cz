---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 22992b4dfad4b4867adda0fcbbd8ecc5eb67d87e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160143"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="939ea-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="939ea-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="939ea-103">Služba protokolu WS-AT vypršel časový limit čekání na odpověď na zprávu z nestálého účastníka.</span><span class="sxs-lookup"><span data-stu-id="939ea-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="939ea-104">Výsledek transakce může mít nejistým výsledkem vrátí účastníka.</span><span class="sxs-lookup"><span data-stu-id="939ea-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="939ea-105">Popis</span><span class="sxs-lookup"><span data-stu-id="939ea-105">Description</span></span>  
 <span data-ttu-id="939ea-106">Trasovaná při nestálého účastníka se rozhodl potvrzení nebo přerušení, ale neodpověděl na požadavek na zápis nebo vrácení zpět v daném čase.</span><span class="sxs-lookup"><span data-stu-id="939ea-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="939ea-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="939ea-107">Troubleshooting</span></span>  
 <span data-ttu-id="939ea-108">Ujistěte se, že se všichni účastníci Volatile neodpoví v daném čase.</span><span class="sxs-lookup"><span data-stu-id="939ea-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="939ea-109">Výchozí časové období je 180 sekund.</span><span class="sxs-lookup"><span data-stu-id="939ea-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="939ea-110">Pokud to není dostatečné, zvýšit `VolatileOutcomeDelay` časovače zásady pro WS-AT.</span><span class="sxs-lookup"><span data-stu-id="939ea-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939ea-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="939ea-111">See also</span></span>

- [<span data-ttu-id="939ea-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="939ea-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="939ea-113">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="939ea-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="939ea-114">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="939ea-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
