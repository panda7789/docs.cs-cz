---
title: CorDebugSetContextFlag – výčet
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
ms.openlocfilehash: 251c96042e8e56112015fb869176c708322267f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097269"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="731a7-102">CorDebugSetContextFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="731a7-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="731a7-103">Označuje, zda je kontext z aktivního (nebo koncového) rámce v zásobníku nebo byl vypočítán odvinutím z jiného rámce.</span><span class="sxs-lookup"><span data-stu-id="731a7-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="731a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="731a7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="731a7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="731a7-105">Members</span></span>  
  
|<span data-ttu-id="731a7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="731a7-106">Member</span></span>|<span data-ttu-id="731a7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="731a7-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="731a7-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="731a7-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="731a7-109">Kontext je aktivní kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="731a7-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="731a7-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="731a7-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="731a7-111">Kontext byl vypočítán odvinutím z jiného rámce.</span><span class="sxs-lookup"><span data-stu-id="731a7-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="731a7-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="731a7-112">Remarks</span></span>  
 <span data-ttu-id="731a7-113">`CorDebugSetContextFlag` poskytuje hodnoty, které jsou používány metodou [ICorDebugStackWalk:: SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="731a7-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="731a7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="731a7-114">Requirements</span></span>  
 <span data-ttu-id="731a7-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="731a7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="731a7-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="731a7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="731a7-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="731a7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="731a7-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="731a7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="731a7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="731a7-119">See also</span></span>

- [<span data-ttu-id="731a7-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="731a7-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="731a7-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="731a7-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
