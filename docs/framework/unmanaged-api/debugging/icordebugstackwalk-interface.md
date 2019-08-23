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
ms.openlocfilehash: 06ce2da435df9458ca59d76fa426becbede2e619
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959677"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="5b127-102">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b127-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="5b127-103">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="5b127-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b127-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5b127-104">Methods</span></span>  
  
|<span data-ttu-id="5b127-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5b127-105">Method</span></span>|<span data-ttu-id="5b127-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5b127-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b127-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="5b127-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="5b127-108">Vrátí kontext pro aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="5b127-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="5b127-109">SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="5b127-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="5b127-110">Nastaví aktuální kontext objektu na platný kontext pro vlákno. `ICorDebugStackWalk`</span><span class="sxs-lookup"><span data-stu-id="5b127-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="5b127-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="5b127-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="5b127-112">`ICorDebugStackWalk` Přesune objekt k dalšímu snímku.</span><span class="sxs-lookup"><span data-stu-id="5b127-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="5b127-113">GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="5b127-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="5b127-114">Získá aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="5b127-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b127-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b127-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b127-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="5b127-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b127-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b127-117">Requirements</span></span>  
 <span data-ttu-id="5b127-118">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b127-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b127-119">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5b127-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b127-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b127-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b127-121">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b127-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b127-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b127-122">See also</span></span>

- [<span data-ttu-id="5b127-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5b127-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5b127-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="5b127-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
