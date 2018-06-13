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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: badd79926e8f039cf6b947dd6655e2cd679e3000
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406972"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="356e5-102">CorDebugSetContextFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="356e5-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="356e5-103">Určuje, zda kontext je z aktivní (nebo listu) s rámečkem v zásobníku nebo je poškozený podle unwinding z jiné rámce.</span><span class="sxs-lookup"><span data-stu-id="356e5-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="356e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="356e5-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="356e5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="356e5-105">Members</span></span>  
  
|<span data-ttu-id="356e5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="356e5-106">Member</span></span>|<span data-ttu-id="356e5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="356e5-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="356e5-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="356e5-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="356e5-109">Kontext není aktivní kontextu vlákna.</span><span class="sxs-lookup"><span data-stu-id="356e5-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="356e5-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="356e5-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="356e5-111">Kontext je poškozený podle unwinding z jiné rámce.</span><span class="sxs-lookup"><span data-stu-id="356e5-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="356e5-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="356e5-112">Remarks</span></span>  
 <span data-ttu-id="356e5-113">`CorDebugSetContextFlag` obsahuje hodnoty, které jsou používány [icordebugstackwalk::setcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="356e5-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="356e5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="356e5-114">Requirements</span></span>  
 <span data-ttu-id="356e5-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="356e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="356e5-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="356e5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="356e5-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="356e5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="356e5-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="356e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356e5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="356e5-119">See Also</span></span>  
 [<span data-ttu-id="356e5-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="356e5-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="356e5-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="356e5-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
