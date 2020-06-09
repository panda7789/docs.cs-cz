---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: bffa6361df5a50748f45aa3004f7a307ad516d7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580486"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="6ac5e-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="6ac5e-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="6ac5e-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="6ac5e-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="6ac5e-104">Popis</span><span class="sxs-lookup"><span data-stu-id="6ac5e-104">Description</span></span>  
 <span data-ttu-id="6ac5e-105">Systém dosáhl limitu nastaveného pro omezení ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="6ac5e-106">Hodnotu omezení lze změnit úpravou vlastnosti ManualFlowControlLimit u třídy ServiceHost nebo InstanceContext, jak je to možné.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="6ac5e-107">Toto trasování je generováno, pokud je limit ručního řízení toku zpočátku snížen na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="6ac5e-108">Následné změny 0 nejsou trasovány.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="6ac5e-109">Limit řízení toku v kontextu instance je pro každý kontext sledován jednou.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac5e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ac5e-110">See also</span></span>

- [<span data-ttu-id="6ac5e-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="6ac5e-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="6ac5e-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="6ac5e-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6ac5e-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="6ac5e-113">Administration and Diagnostics</span></span>](../index.md)
