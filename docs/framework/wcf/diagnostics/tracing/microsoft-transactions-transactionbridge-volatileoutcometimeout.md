---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: dd2a0b67ec140aa2e6fe1abad8e85c0206abd8ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579018"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="b7276-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="b7276-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="b7276-103">Vypršel časový limit služby protokolu WS-AT při čekání na odpověď na zprávu o výsledku od nestálého účastníka.</span><span class="sxs-lookup"><span data-stu-id="b7276-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="b7276-104">Výsledek transakce může být nejistý, pokud účastník vrátí.</span><span class="sxs-lookup"><span data-stu-id="b7276-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b7276-105">Popis</span><span class="sxs-lookup"><span data-stu-id="b7276-105">Description</span></span>  
 <span data-ttu-id="b7276-106">Sledováno v případě, že se nestálý účastník rozhodl zapsat nebo přerušit, ale neodpověděl na žádost o potvrzení nebo vrácení zpět během daného časového intervalu.</span><span class="sxs-lookup"><span data-stu-id="b7276-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b7276-107">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="b7276-107">Troubleshooting</span></span>  
 <span data-ttu-id="b7276-108">Zajistěte, aby každý stálý účastník mohl reagovat v daném časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="b7276-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="b7276-109">Výchozí časové období je 180 sekund.</span><span class="sxs-lookup"><span data-stu-id="b7276-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="b7276-110">Pokud to nestačí, zvyšte `VolatileOutcomeDelay` zásady časovače pro WS-AT.</span><span class="sxs-lookup"><span data-stu-id="b7276-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7276-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7276-111">See also</span></span>

- [<span data-ttu-id="b7276-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="b7276-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="b7276-113">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="b7276-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b7276-114">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="b7276-114">Administration and Diagnostics</span></span>](../index.md)
