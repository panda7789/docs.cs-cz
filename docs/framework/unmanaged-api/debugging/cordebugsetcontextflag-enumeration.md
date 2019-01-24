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
ms.openlocfilehash: 572087bd6f14c43b439910be32fca54af66a2e8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585533"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="e436b-102">CorDebugSetContextFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="e436b-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="e436b-103">Určuje, zda je kontext z aktivního (nebo listu) rámce v zásobníku nebo byl vypočítán pomocí návrat zpět z jiného snímku.</span><span class="sxs-lookup"><span data-stu-id="e436b-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e436b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e436b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="e436b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e436b-105">Members</span></span>  
  
|<span data-ttu-id="e436b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e436b-106">Member</span></span>|<span data-ttu-id="e436b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e436b-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e436b-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="e436b-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="e436b-109">Kontext je aktivní kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="e436b-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="e436b-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="e436b-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="e436b-111">Kontext obsahuje se počítají tak, že návrat zpět z jiného snímku.</span><span class="sxs-lookup"><span data-stu-id="e436b-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e436b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e436b-112">Remarks</span></span>  
 <span data-ttu-id="e436b-113">`CorDebugSetContextFlag` obsahuje hodnoty, které jsou používány [icordebugstackwalk::setcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e436b-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e436b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e436b-114">Requirements</span></span>  
 <span data-ttu-id="e436b-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e436b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e436b-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e436b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e436b-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e436b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e436b-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e436b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e436b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e436b-119">See also</span></span>
- [<span data-ttu-id="e436b-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="e436b-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="e436b-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="e436b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
