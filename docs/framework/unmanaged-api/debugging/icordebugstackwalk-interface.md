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
ms.openlocfilehash: 48f1b485b6dfa8fd898f6ea00eee2d7b397deba6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131859"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="ac6b3-102">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac6b3-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="ac6b3-103">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="ac6b3-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac6b3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ac6b3-104">Methods</span></span>  
  
|<span data-ttu-id="ac6b3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ac6b3-105">Method</span></span>|<span data-ttu-id="ac6b3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ac6b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac6b3-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="ac6b3-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="ac6b3-108">Vrátí kontext pro aktuální rámec v objektu `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="ac6b3-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="ac6b3-109">SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="ac6b3-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="ac6b3-110">Nastaví aktuální kontext objektu `ICorDebugStackWalk` na platný kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="ac6b3-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="ac6b3-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="ac6b3-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="ac6b3-112">Přesune objekt `ICorDebugStackWalk` k dalšímu snímku.</span><span class="sxs-lookup"><span data-stu-id="ac6b3-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="ac6b3-113">GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="ac6b3-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="ac6b3-114">Získá aktuální rámec v objektu `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="ac6b3-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac6b3-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac6b3-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac6b3-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ac6b3-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac6b3-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac6b3-117">Requirements</span></span>  
 <span data-ttu-id="ac6b3-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac6b3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac6b3-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ac6b3-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac6b3-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ac6b3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac6b3-121">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac6b3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac6b3-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac6b3-122">See also</span></span>

- [<span data-ttu-id="ac6b3-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ac6b3-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ac6b3-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="ac6b3-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
