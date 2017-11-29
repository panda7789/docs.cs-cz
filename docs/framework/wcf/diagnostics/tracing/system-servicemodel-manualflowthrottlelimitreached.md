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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 556afe035697ee35d7ba86185b5b768a645c32c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="7c764-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="7c764-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="7c764-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="7c764-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="7c764-104">Popis</span><span class="sxs-lookup"><span data-stu-id="7c764-104">Description</span></span>  
 <span data-ttu-id="7c764-105">Systém dosažen limit nastavený pro ManualFlowControlLimit omezení.</span><span class="sxs-lookup"><span data-stu-id="7c764-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="7c764-106">Hodnota omezení lze změnit úpravou vlastnosti ManualFlowControlLimit na hostiteli služby nebo objekt InstanceContext, podle vhodnosti.</span><span class="sxs-lookup"><span data-stu-id="7c764-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="7c764-107">Trasování jsou vydávány po limit ruční toku řízení původně zmenšení na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="7c764-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="7c764-108">Následné změny 0 nejsou trasovat.</span><span class="sxs-lookup"><span data-stu-id="7c764-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="7c764-109">Tok řízení limit pro daný kontext instance trasovaný jednou pro každý kontext.</span><span class="sxs-lookup"><span data-stu-id="7c764-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c764-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c764-110">See Also</span></span>  
 [<span data-ttu-id="7c764-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="7c764-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7c764-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="7c764-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="7c764-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="7c764-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
