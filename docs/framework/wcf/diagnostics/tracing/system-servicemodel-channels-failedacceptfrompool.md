---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: de0bdd9e5ab922b09249bf550fde745042be8e58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156478"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="8784d-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="8784d-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="8784d-103">Pokus o opakované použití připojení ve fondu se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="8784d-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="8784d-104">Další pokus se uskuteční v rámci určeného časového limitu.</span><span class="sxs-lookup"><span data-stu-id="8784d-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8784d-105">Popis</span><span class="sxs-lookup"><span data-stu-id="8784d-105">Description</span></span>  
 <span data-ttu-id="8784d-106">Tento informační trasování označuje, že došlo k chybě při pokusu o opakované použití ve fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="8784d-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="8784d-107">Může k tomu dojít, protože ve fondu připojení není kompatibilní, připravené nebo stále aktivní.</span><span class="sxs-lookup"><span data-stu-id="8784d-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="8784d-108">Další pokusy o opakované použití dalších klientů ve fondu připojení jsou provedeny v daném časovém limitu a v případě, že se nenašla žádná použitelná připojení, vytvoří se nové připojení.</span><span class="sxs-lookup"><span data-stu-id="8784d-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8784d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8784d-109">See also</span></span>

- [<span data-ttu-id="8784d-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="8784d-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8784d-111">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="8784d-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8784d-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="8784d-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
