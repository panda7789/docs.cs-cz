---
title: "ICorDebugStackWalk – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk
helpviewer_keywords: ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 018ed69e52efd21ca25029284c70f1c8493d877f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="8496f-102">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8496f-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="8496f-103">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="8496f-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8496f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8496f-104">Methods</span></span>  
  
|<span data-ttu-id="8496f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8496f-105">Method</span></span>|<span data-ttu-id="8496f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8496f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8496f-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8496f-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="8496f-108">Vrátí kontext pro aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="8496f-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="8496f-109">SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8496f-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="8496f-110">Nastaví `ICorDebugStackWalk` aktuální kontext objektu, který má platný kontext pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="8496f-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="8496f-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="8496f-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="8496f-112">Přesune `ICorDebugStackWalk` objektu na další snímek.</span><span class="sxs-lookup"><span data-stu-id="8496f-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="8496f-113">GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="8496f-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="8496f-114">Získá aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="8496f-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8496f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8496f-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8496f-116">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8496f-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8496f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8496f-117">Requirements</span></span>  
 <span data-ttu-id="8496f-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8496f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8496f-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8496f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8496f-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8496f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8496f-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8496f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8496f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8496f-122">See Also</span></span>  
 [<span data-ttu-id="8496f-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8496f-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8496f-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="8496f-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
