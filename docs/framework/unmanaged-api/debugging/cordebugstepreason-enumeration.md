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
ms.openlocfilehash: 92aee981aca3bac32c0ef264799e486315ca5103
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789258"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="33e2a-102">CorDebugStepReason – výčet</span><span class="sxs-lookup"><span data-stu-id="33e2a-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="33e2a-103">Označuje výsledek jednotlivého kroku.</span><span class="sxs-lookup"><span data-stu-id="33e2a-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33e2a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="33e2a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="33e2a-105">Members</span></span>  
  
|<span data-ttu-id="33e2a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="33e2a-106">Member</span></span>|<span data-ttu-id="33e2a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="33e2a-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="33e2a-108">Krokování je normálně dokončeno v rámci stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="33e2a-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="33e2a-109">Krokování se normálně dostálo po vrácení funkce.</span><span class="sxs-lookup"><span data-stu-id="33e2a-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="33e2a-110">Krokování obvykle probíhá na začátku nově volané funkce.</span><span class="sxs-lookup"><span data-stu-id="33e2a-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="33e2a-111">Byla vygenerována výjimka a ovládací prvek byl předán filtru výjimky.</span><span class="sxs-lookup"><span data-stu-id="33e2a-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="33e2a-112">Byla vygenerována výjimka a ovládací prvek byl předán obslužné rutině výjimky.</span><span class="sxs-lookup"><span data-stu-id="33e2a-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="33e2a-113">Ovládací prvek byl předán do zachytávací.</span><span class="sxs-lookup"><span data-stu-id="33e2a-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="33e2a-114">Vlákno bylo ukončeno před dokončením kroku.</span><span class="sxs-lookup"><span data-stu-id="33e2a-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33e2a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33e2a-115">Requirements</span></span>  
 <span data-ttu-id="33e2a-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33e2a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33e2a-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33e2a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33e2a-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="33e2a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33e2a-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33e2a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e2a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33e2a-120">See also</span></span>

- [<span data-ttu-id="33e2a-121">StepComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="33e2a-121">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="33e2a-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="33e2a-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
