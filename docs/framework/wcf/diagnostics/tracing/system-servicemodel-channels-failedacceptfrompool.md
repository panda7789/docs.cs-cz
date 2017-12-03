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
ms.openlocfilehash: 339ba8df7e782281fcec962ff6c6f01988122b3a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="c3a66-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="c3a66-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="c3a66-103">Pokus o opakované použití ve fondu připojení se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="c3a66-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="c3a66-104">Další pokus se uskuteční během zadaného časového limitu.</span><span class="sxs-lookup"><span data-stu-id="c3a66-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c3a66-105">Popis</span><span class="sxs-lookup"><span data-stu-id="c3a66-105">Description</span></span>  
 <span data-ttu-id="c3a66-106">Informační trasování označuje, že došlo k chybě při pokusu o opakované použití ve fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="c3a66-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="c3a66-107">Toto může nastat, protože ve fondu připojení není kompatibilní, připraveno nebo stále aktivní.</span><span class="sxs-lookup"><span data-stu-id="c3a66-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="c3a66-108">Další pokusy o znovu použít jiné ve fondu připojení jsou vytvářeny v daném časovém limitu a v případě, že nebyly nalezeny žádné použitelné připojení k vytvoření nového připojení.</span><span class="sxs-lookup"><span data-stu-id="c3a66-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a66-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3a66-109">See Also</span></span>  
 [<span data-ttu-id="c3a66-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="c3a66-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c3a66-111">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="c3a66-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c3a66-112">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="c3a66-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
