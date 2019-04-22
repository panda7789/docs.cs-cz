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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080680"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="25ea2-102">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25ea2-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="25ea2-103">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="25ea2-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25ea2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="25ea2-104">Methods</span></span>  
  
|<span data-ttu-id="25ea2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="25ea2-105">Method</span></span>|<span data-ttu-id="25ea2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="25ea2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25ea2-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="25ea2-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="25ea2-108">Vrátí kontext pro aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="25ea2-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="25ea2-109">SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="25ea2-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="25ea2-110">Nastaví `ICorDebugStackWalk` aktuální kontext objektu na platný kontext pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="25ea2-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="25ea2-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="25ea2-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="25ea2-112">Přesune `ICorDebugStackWalk` objektu do dalšího snímku.</span><span class="sxs-lookup"><span data-stu-id="25ea2-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="25ea2-113">GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="25ea2-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="25ea2-114">Získá aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="25ea2-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25ea2-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25ea2-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25ea2-116">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="25ea2-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ea2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25ea2-117">Requirements</span></span>  
 <span data-ttu-id="25ea2-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25ea2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25ea2-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25ea2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25ea2-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25ea2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25ea2-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25ea2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ea2-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25ea2-122">See also</span></span>

- [<span data-ttu-id="25ea2-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="25ea2-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="25ea2-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="25ea2-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
