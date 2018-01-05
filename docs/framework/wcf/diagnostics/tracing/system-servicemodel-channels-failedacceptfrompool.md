---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df0f983d646ea89eeef338b9742843e9fa50487b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="835e5-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="835e5-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="835e5-103">Pokus o opakované použití ve fondu připojení se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="835e5-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="835e5-104">Další pokus se uskuteční během zadaného časového limitu.</span><span class="sxs-lookup"><span data-stu-id="835e5-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="835e5-105">Popis</span><span class="sxs-lookup"><span data-stu-id="835e5-105">Description</span></span>  
 <span data-ttu-id="835e5-106">Informační trasování označuje, že došlo k chybě při pokusu o opakované použití ve fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="835e5-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="835e5-107">Toto může nastat, protože ve fondu připojení není kompatibilní, připraveno nebo stále aktivní.</span><span class="sxs-lookup"><span data-stu-id="835e5-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="835e5-108">Další pokusy o znovu použít jiné ve fondu připojení jsou vytvářeny v daném časovém limitu a v případě, že nebyly nalezeny žádné použitelné připojení k vytvoření nového připojení.</span><span class="sxs-lookup"><span data-stu-id="835e5-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835e5-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="835e5-109">See Also</span></span>  
 [<span data-ttu-id="835e5-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="835e5-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="835e5-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="835e5-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="835e5-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="835e5-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
