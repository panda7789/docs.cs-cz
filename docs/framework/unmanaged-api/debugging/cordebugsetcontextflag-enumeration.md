---
title: "CorDebugSetContextFlag – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugSetContextFlag
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugSetContextFlag
helpviewer_keywords: CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 958ed303fab3dcb01fad2040dd06381e76fe5a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="b1bb7-102">CorDebugSetContextFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="b1bb7-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="b1bb7-103">Určuje, zda kontext je z aktivní (nebo listu) s rámečkem v zásobníku nebo je poškozený podle unwinding z jiné rámce.</span><span class="sxs-lookup"><span data-stu-id="b1bb7-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1bb7-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="b1bb7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b1bb7-105">Members</span></span>  
  
|<span data-ttu-id="b1bb7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b1bb7-106">Member</span></span>|<span data-ttu-id="b1bb7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b1bb7-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b1bb7-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="b1bb7-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="b1bb7-109">Kontext není aktivní kontextu vlákna.</span><span class="sxs-lookup"><span data-stu-id="b1bb7-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="b1bb7-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="b1bb7-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="b1bb7-111">Kontext je poškozený podle unwinding z jiné rámce.</span><span class="sxs-lookup"><span data-stu-id="b1bb7-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1bb7-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1bb7-112">Remarks</span></span>  
 <span data-ttu-id="b1bb7-113">`CorDebugSetContextFlag`obsahuje hodnoty, které jsou používány [icordebugstackwalk::setcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="b1bb7-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1bb7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1bb7-114">Requirements</span></span>  
 <span data-ttu-id="b1bb7-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1bb7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1bb7-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1bb7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1bb7-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1bb7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1bb7-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1bb7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bb7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1bb7-119">See Also</span></span>  
 [<span data-ttu-id="b1bb7-120">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="b1bb7-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="b1bb7-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="b1bb7-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
