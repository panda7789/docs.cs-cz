---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: a6b4e369d2d22d2441b3896321b7c152e21d967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33483328"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="d35e2-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="d35e2-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="d35e2-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="d35e2-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="d35e2-104">Popis</span><span class="sxs-lookup"><span data-stu-id="d35e2-104">Description</span></span>  
 <span data-ttu-id="d35e2-105">Systém dosažen limit nastavený pro ManualFlowControlLimit omezení.</span><span class="sxs-lookup"><span data-stu-id="d35e2-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="d35e2-106">Hodnota omezení lze změnit úpravou vlastnosti ManualFlowControlLimit na hostiteli služby nebo objekt InstanceContext, podle vhodnosti.</span><span class="sxs-lookup"><span data-stu-id="d35e2-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="d35e2-107">Trasování jsou vydávány po limit ruční toku řízení původně zmenšení na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="d35e2-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="d35e2-108">Následné změny 0 nejsou trasovat.</span><span class="sxs-lookup"><span data-stu-id="d35e2-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="d35e2-109">Tok řízení limit pro daný kontext instance trasovaný jednou pro každý kontext.</span><span class="sxs-lookup"><span data-stu-id="d35e2-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35e2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d35e2-110">See Also</span></span>  
 [<span data-ttu-id="d35e2-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="d35e2-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d35e2-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="d35e2-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d35e2-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="d35e2-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
