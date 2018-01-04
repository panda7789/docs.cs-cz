---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35f149423fc8c0cd2a25834742d7c8b79ad8d8c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="844e8-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="844e8-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="844e8-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="844e8-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="844e8-104">Popis</span><span class="sxs-lookup"><span data-stu-id="844e8-104">Description</span></span>  
 <span data-ttu-id="844e8-105">Systém dosažen limit nastavený pro ManualFlowControlLimit omezení.</span><span class="sxs-lookup"><span data-stu-id="844e8-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="844e8-106">Hodnota omezení lze změnit úpravou vlastnosti ManualFlowControlLimit na hostiteli služby nebo objekt InstanceContext, podle vhodnosti.</span><span class="sxs-lookup"><span data-stu-id="844e8-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="844e8-107">Trasování jsou vydávány po limit ruční toku řízení původně zmenšení na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="844e8-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="844e8-108">Následné změny 0 nejsou trasovat.</span><span class="sxs-lookup"><span data-stu-id="844e8-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="844e8-109">Tok řízení limit pro daný kontext instance trasovaný jednou pro každý kontext.</span><span class="sxs-lookup"><span data-stu-id="844e8-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="844e8-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="844e8-110">See Also</span></span>  
 [<span data-ttu-id="844e8-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="844e8-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="844e8-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="844e8-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="844e8-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="844e8-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
