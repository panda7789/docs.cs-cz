---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 59bba87095931c80a7ce347def2656a7a1f6f949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479311"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="ac5be-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="ac5be-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="ac5be-103">Pokus o opakované použití ve fondu připojení se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="ac5be-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="ac5be-104">Další pokus se uskuteční během zadaného časového limitu.</span><span class="sxs-lookup"><span data-stu-id="ac5be-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ac5be-105">Popis</span><span class="sxs-lookup"><span data-stu-id="ac5be-105">Description</span></span>  
 <span data-ttu-id="ac5be-106">Informační trasování označuje, že došlo k chybě při pokusu o opakované použití ve fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="ac5be-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="ac5be-107">Toto může nastat, protože ve fondu připojení není kompatibilní, připraveno nebo stále aktivní.</span><span class="sxs-lookup"><span data-stu-id="ac5be-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="ac5be-108">Další pokusy o znovu použít jiné ve fondu připojení jsou vytvářeny v daném časovém limitu a v případě, že nebyly nalezeny žádné použitelné připojení k vytvoření nového připojení.</span><span class="sxs-lookup"><span data-stu-id="ac5be-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5be-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac5be-109">See Also</span></span>  
 [<span data-ttu-id="ac5be-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="ac5be-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ac5be-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="ac5be-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ac5be-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="ac5be-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
