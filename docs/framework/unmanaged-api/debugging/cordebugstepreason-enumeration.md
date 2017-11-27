---
title: "CorDebugStepReason – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStepReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugStepReason
helpviewer_keywords: CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32892a14de820e8add38654cef92aa44930aec62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="7efb0-102">CorDebugStepReason – výčet</span><span class="sxs-lookup"><span data-stu-id="7efb0-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="7efb0-103">Určuje výsledek jednotlivé kroky.</span><span class="sxs-lookup"><span data-stu-id="7efb0-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7efb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7efb0-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="7efb0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7efb0-105">Members</span></span>  
  
|<span data-ttu-id="7efb0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7efb0-106">Member</span></span>|<span data-ttu-id="7efb0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7efb0-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="7efb0-108">Krokování s dokončit za normálních okolností v rámci stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="7efb0-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="7efb0-109">Krokování s dál za normálních okolností po funkce vrátila.</span><span class="sxs-lookup"><span data-stu-id="7efb0-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="7efb0-110">Krokování s dál za normálních okolností na začátku nově volaná funkce.</span><span class="sxs-lookup"><span data-stu-id="7efb0-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="7efb0-111">Vygenerovalo výjimku a byla předána ovládací prvek filtru výjimek.</span><span class="sxs-lookup"><span data-stu-id="7efb0-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="7efb0-112">Vygenerovalo výjimku a řízení byl předán obslužnou rutinu výjimky.</span><span class="sxs-lookup"><span data-stu-id="7efb0-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="7efb0-113">Ovládací prvek byl předán interceptoru.</span><span class="sxs-lookup"><span data-stu-id="7efb0-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="7efb0-114">Vlákno byl ukončen před krok bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="7efb0-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7efb0-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7efb0-115">Requirements</span></span>  
 <span data-ttu-id="7efb0-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7efb0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7efb0-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7efb0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7efb0-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7efb0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7efb0-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7efb0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7efb0-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7efb0-120">See Also</span></span>  
 [<span data-ttu-id="7efb0-121">Stepcomplete – metoda</span><span class="sxs-lookup"><span data-stu-id="7efb0-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [<span data-ttu-id="7efb0-122">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="7efb0-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
