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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ce2b23306e7e38f3982f8d5a4b377aa2f9547c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723157"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="ef9d8-102">CorDebugStepReason – výčet</span><span class="sxs-lookup"><span data-stu-id="ef9d8-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="ef9d8-103">Určuje výsledek jednotlivé kroky.</span><span class="sxs-lookup"><span data-stu-id="ef9d8-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef9d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef9d8-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ef9d8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ef9d8-105">Members</span></span>  
  
|<span data-ttu-id="ef9d8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ef9d8-106">Member</span></span>|<span data-ttu-id="ef9d8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ef9d8-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="ef9d8-108">Krokování dokončit za normálních okolností v rámci stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="ef9d8-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="ef9d8-109">Krokování pokračuje za normálních okolností se po vrácení funkce.</span><span class="sxs-lookup"><span data-stu-id="ef9d8-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="ef9d8-110">Krokování za normálních okolností pokračovat na začátku nově volané funkce.</span><span class="sxs-lookup"><span data-stu-id="ef9d8-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="ef9d8-111">Byla generována výjimka a ovládací prvek předaný funkci filtru výjimky.</span><span class="sxs-lookup"><span data-stu-id="ef9d8-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="ef9d8-112">Byla generována výjimka a ovládací prvek předaný funkci obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="ef9d8-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="ef9d8-113">Ovládací prvek byl předán zachycování.</span><span class="sxs-lookup"><span data-stu-id="ef9d8-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="ef9d8-114">Vlákno se ukončil před krok byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="ef9d8-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef9d8-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef9d8-115">Requirements</span></span>  
 <span data-ttu-id="ef9d8-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef9d8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef9d8-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef9d8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef9d8-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef9d8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef9d8-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef9d8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef9d8-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef9d8-120">See also</span></span>

- [<span data-ttu-id="ef9d8-121">StepComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="ef9d8-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="ef9d8-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="ef9d8-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
