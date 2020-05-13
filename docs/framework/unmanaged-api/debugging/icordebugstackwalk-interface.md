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
ms.openlocfilehash: 5f71dfcdffaaa683ca4f2abebaa99115ef90e0ff
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378910"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="12f47-102">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12f47-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="12f47-103">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="12f47-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12f47-104">Metody</span><span class="sxs-lookup"><span data-stu-id="12f47-104">Methods</span></span>  
  
|<span data-ttu-id="12f47-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="12f47-105">Method</span></span>|<span data-ttu-id="12f47-106">Popis</span><span class="sxs-lookup"><span data-stu-id="12f47-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12f47-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="12f47-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="12f47-108">Vrátí kontext pro aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="12f47-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="12f47-109">SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="12f47-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="12f47-110">Nastaví `ICorDebugStackWalk` aktuální kontext objektu na platný kontext pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="12f47-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="12f47-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="12f47-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="12f47-112">Přesune `ICorDebugStackWalk` objekt k dalšímu snímku.</span><span class="sxs-lookup"><span data-stu-id="12f47-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="12f47-113">GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="12f47-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="12f47-114">Získá aktuální rámec v `ICorDebugStackWalk` objektu.</span><span class="sxs-lookup"><span data-stu-id="12f47-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12f47-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12f47-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12f47-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="12f47-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f47-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12f47-117">Requirements</span></span>  
 <span data-ttu-id="12f47-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f47-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f47-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="12f47-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12f47-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="12f47-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12f47-121">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f47-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f47-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="12f47-122">See also</span></span>

- [<span data-ttu-id="12f47-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12f47-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="12f47-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="12f47-124">Debugging</span></span>](index.md)
