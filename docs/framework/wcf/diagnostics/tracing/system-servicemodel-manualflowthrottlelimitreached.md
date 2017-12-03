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
ms.openlocfilehash: 49b41e27847005c7187435229e030994df10df26
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="5d029-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="5d029-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="5d029-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="5d029-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="5d029-104">Popis</span><span class="sxs-lookup"><span data-stu-id="5d029-104">Description</span></span>  
 <span data-ttu-id="5d029-105">Systém dosažen limit nastavený pro ManualFlowControlLimit omezení.</span><span class="sxs-lookup"><span data-stu-id="5d029-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="5d029-106">Hodnota omezení lze změnit úpravou vlastnosti ManualFlowControlLimit na hostiteli služby nebo objekt InstanceContext, podle vhodnosti.</span><span class="sxs-lookup"><span data-stu-id="5d029-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="5d029-107">Trasování jsou vydávány po limit ruční toku řízení původně zmenšení na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="5d029-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="5d029-108">Následné změny 0 nejsou trasovat.</span><span class="sxs-lookup"><span data-stu-id="5d029-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="5d029-109">Tok řízení limit pro daný kontext instance trasovaný jednou pro každý kontext.</span><span class="sxs-lookup"><span data-stu-id="5d029-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d029-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d029-110">See Also</span></span>  
 [<span data-ttu-id="5d029-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="5d029-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5d029-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="5d029-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5d029-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="5d029-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
