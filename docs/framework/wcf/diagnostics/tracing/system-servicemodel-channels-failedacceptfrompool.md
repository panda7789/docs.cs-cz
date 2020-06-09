---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 5bfa31d0eaf3b00017512eddc60bfa99eda619e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582579"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="7b845-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="7b845-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="7b845-103">Pokus o opakované použití sdruženého připojení se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="7b845-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="7b845-104">V zadaném časovém limitu se provede další pokus.</span><span class="sxs-lookup"><span data-stu-id="7b845-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7b845-105">Popis</span><span class="sxs-lookup"><span data-stu-id="7b845-105">Description</span></span>  
 <span data-ttu-id="7b845-106">Toto informační trasování indikuje, že došlo k chybě při pokusu o opakované použití připojení ve fondu.</span><span class="sxs-lookup"><span data-stu-id="7b845-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="7b845-107">K tomu může dojít, protože připojení ve fondu není kompatibilní, připravené nebo pořád aktivní.</span><span class="sxs-lookup"><span data-stu-id="7b845-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="7b845-108">Další pokusy o opakované použití jiných sdružených připojení se provedou v daném časovém limitu a vytvoří se nové připojení pro případ, že se nenaleznou žádná použitelná připojení.</span><span class="sxs-lookup"><span data-stu-id="7b845-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b845-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b845-109">See also</span></span>

- [<span data-ttu-id="7b845-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="7b845-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="7b845-111">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="7b845-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7b845-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="7b845-112">Administration and Diagnostics</span></span>](../index.md)
