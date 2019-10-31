---
title: CorDebugStepReason – výčet
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 6c73afb00cbd104cff3d310d1369097b459c131e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133679"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="1338e-102">CorDebugStepReason – výčet</span><span class="sxs-lookup"><span data-stu-id="1338e-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="1338e-103">Označuje výsledek jednotlivého kroku.</span><span class="sxs-lookup"><span data-stu-id="1338e-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1338e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1338e-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="1338e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1338e-105">Members</span></span>  
  
|<span data-ttu-id="1338e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1338e-106">Member</span></span>|<span data-ttu-id="1338e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1338e-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="1338e-108">Krokování je normálně dokončeno v rámci stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="1338e-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="1338e-109">Krokování se normálně dostálo po vrácení funkce.</span><span class="sxs-lookup"><span data-stu-id="1338e-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="1338e-110">Krokování obvykle probíhá na začátku nově volané funkce.</span><span class="sxs-lookup"><span data-stu-id="1338e-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="1338e-111">Byla vygenerována výjimka a ovládací prvek byl předán filtru výjimky.</span><span class="sxs-lookup"><span data-stu-id="1338e-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="1338e-112">Byla vygenerována výjimka a ovládací prvek byl předán obslužné rutině výjimky.</span><span class="sxs-lookup"><span data-stu-id="1338e-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="1338e-113">Ovládací prvek byl předán do zachytávací.</span><span class="sxs-lookup"><span data-stu-id="1338e-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="1338e-114">Vlákno bylo ukončeno před dokončením kroku.</span><span class="sxs-lookup"><span data-stu-id="1338e-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1338e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1338e-115">Requirements</span></span>  
 <span data-ttu-id="1338e-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1338e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1338e-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1338e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1338e-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1338e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1338e-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1338e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1338e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1338e-120">See also</span></span>

- [<span data-ttu-id="1338e-121">StepComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="1338e-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="1338e-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="1338e-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
