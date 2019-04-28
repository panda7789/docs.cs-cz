---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: fb69c3c737a0e77b05e08ab8d8282069feb069bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761517"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="80ac2-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="80ac2-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="80ac2-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="80ac2-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="80ac2-104">Popis</span><span class="sxs-lookup"><span data-stu-id="80ac2-104">Description</span></span>  
 <span data-ttu-id="80ac2-105">Systém dosáhl limitu nastaveného pro omezení ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="80ac2-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="80ac2-106">Hodnotu omezení lze změnit upravením vlastnosti ManualFlowControlLimit ServiceHost nebo třída InstanceContext, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="80ac2-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="80ac2-107">Trasování je vygenerován při limit ruční toku řízení je zpočátku omezená na 0.</span><span class="sxs-lookup"><span data-stu-id="80ac2-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="80ac2-108">Následné změny 0 nebudou trasovány.</span><span class="sxs-lookup"><span data-stu-id="80ac2-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="80ac2-109">Tok řízení omezený kontext instance trasován jednou pro každý kontext.</span><span class="sxs-lookup"><span data-stu-id="80ac2-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ac2-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80ac2-110">See also</span></span>

- [<span data-ttu-id="80ac2-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="80ac2-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="80ac2-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="80ac2-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="80ac2-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="80ac2-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
