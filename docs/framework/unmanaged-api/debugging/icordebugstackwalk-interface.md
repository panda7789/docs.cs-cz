---
title: ICorDebugStackWalk – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e33e9be112a6a10f89b88005496ce2e63dff2d54
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080680"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="5d232-102">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d232-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="5d232-103">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="5d232-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d232-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5d232-104">Methods</span></span>  
  
|<span data-ttu-id="5d232-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d232-105">Method</span></span>|<span data-ttu-id="5d232-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5d232-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d232-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="5d232-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="5d232-108">Vrátí kontext pro aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="5d232-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="5d232-109">SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="5d232-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="5d232-110">Nastaví `ICorDebugStackWalk` aktuální kontext objektu na platný kontext pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="5d232-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="5d232-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="5d232-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="5d232-112">Přesune `ICorDebugStackWalk` objektu do dalšího snímku.</span><span class="sxs-lookup"><span data-stu-id="5d232-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="5d232-113">GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="5d232-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="5d232-114">Získá aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="5d232-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d232-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d232-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d232-116">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="5d232-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d232-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d232-117">Requirements</span></span>  
 <span data-ttu-id="5d232-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d232-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d232-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d232-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d232-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d232-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5d232-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5d232-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d232-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d232-122">See also</span></span>

- [<span data-ttu-id="5d232-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d232-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5d232-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="5d232-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
