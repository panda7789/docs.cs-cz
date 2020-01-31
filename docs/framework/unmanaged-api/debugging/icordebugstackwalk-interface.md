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
ms.openlocfilehash: a6283d699263dc9b79e457010f31923f77443129
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791881"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="918e5-102">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="918e5-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="918e5-103">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="918e5-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="918e5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="918e5-104">Methods</span></span>  
  
|<span data-ttu-id="918e5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="918e5-105">Method</span></span>|<span data-ttu-id="918e5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="918e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="918e5-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="918e5-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="918e5-108">Vrátí kontext pro aktuální rámec v objektu `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="918e5-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="918e5-109">SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="918e5-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="918e5-110">Nastaví aktuální kontext objektu `ICorDebugStackWalk` na platný kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="918e5-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="918e5-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="918e5-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="918e5-112">Přesune objekt `ICorDebugStackWalk` k dalšímu snímku.</span><span class="sxs-lookup"><span data-stu-id="918e5-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="918e5-113">GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="918e5-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="918e5-114">Získá aktuální rámec v objektu `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="918e5-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="918e5-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="918e5-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="918e5-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="918e5-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="918e5-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="918e5-117">Requirements</span></span>  
 <span data-ttu-id="918e5-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="918e5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="918e5-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="918e5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="918e5-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="918e5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="918e5-121">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="918e5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="918e5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="918e5-122">See also</span></span>

- [<span data-ttu-id="918e5-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="918e5-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="918e5-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="918e5-124">Debugging</span></span>](index.md)
