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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e50e104816567927f53673f9b1da9c3c5beac3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="be3cf-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="be3cf-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="be3cf-103">Pokus o opakované použití ve fondu připojení se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="be3cf-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="be3cf-104">Další pokus se uskuteční během zadaného časového limitu.</span><span class="sxs-lookup"><span data-stu-id="be3cf-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="be3cf-105">Popis</span><span class="sxs-lookup"><span data-stu-id="be3cf-105">Description</span></span>  
 <span data-ttu-id="be3cf-106">Informační trasování označuje, že došlo k chybě při pokusu o opakované použití ve fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="be3cf-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="be3cf-107">Toto může nastat, protože ve fondu připojení není kompatibilní, připraveno nebo stále aktivní.</span><span class="sxs-lookup"><span data-stu-id="be3cf-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="be3cf-108">Další pokusy o znovu použít jiné ve fondu připojení jsou vytvářeny v daném časovém limitu a v případě, že nebyly nalezeny žádné použitelné připojení k vytvoření nového připojení.</span><span class="sxs-lookup"><span data-stu-id="be3cf-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be3cf-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="be3cf-109">See Also</span></span>  
 [<span data-ttu-id="be3cf-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="be3cf-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="be3cf-111">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="be3cf-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="be3cf-112">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="be3cf-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
