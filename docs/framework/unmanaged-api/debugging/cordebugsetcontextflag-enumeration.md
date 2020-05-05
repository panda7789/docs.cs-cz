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
ms.openlocfilehash: a3214fc4e52918716f183720c7c616b1fff74bdb
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795674"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="10cf1-102">CorDebugSetContextFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="10cf1-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="10cf1-103">Označuje, zda je kontext z aktivního (nebo koncového) rámce v zásobníku nebo byl vypočítán odvinutím z jiného rámce.</span><span class="sxs-lookup"><span data-stu-id="10cf1-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10cf1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10cf1-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="10cf1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="10cf1-105">Members</span></span>  
  
|<span data-ttu-id="10cf1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="10cf1-106">Member</span></span>|<span data-ttu-id="10cf1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="10cf1-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="10cf1-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="10cf1-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="10cf1-109">Kontext je aktivní kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="10cf1-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="10cf1-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="10cf1-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="10cf1-111">Kontext byl vypočítán odvinutím z jiného rámce.</span><span class="sxs-lookup"><span data-stu-id="10cf1-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10cf1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10cf1-112">Remarks</span></span>  
 <span data-ttu-id="10cf1-113">`CorDebugSetContextFlag`poskytuje hodnoty, které jsou používány metodou [ICorDebugStackWalk:: SetContext](icordebugstackwalk-setcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="10cf1-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10cf1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10cf1-114">Requirements</span></span>  
 <span data-ttu-id="10cf1-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10cf1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10cf1-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="10cf1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10cf1-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="10cf1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10cf1-118">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10cf1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10cf1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="10cf1-119">See also</span></span>

- [<span data-ttu-id="10cf1-120">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="10cf1-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="10cf1-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="10cf1-121">Debugging</span></span>](index.md)
