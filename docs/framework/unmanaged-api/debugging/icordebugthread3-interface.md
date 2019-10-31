---
title: ICorDebugThread3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 7cddf860f044e8493a0fdf6023b2853ac16c5b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137506"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="5550d-102">ICorDebugThread3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5550d-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="5550d-103">Poskytuje vstupní bod pro [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5550d-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5550d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5550d-104">Methods</span></span>  
  
|<span data-ttu-id="5550d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5550d-105">Method</span></span>|<span data-ttu-id="5550d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5550d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5550d-107">CreateStackWalk – metoda</span><span class="sxs-lookup"><span data-stu-id="5550d-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="5550d-108">Vytvoří objekt [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) pro vlákno, jehož zásobník chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="5550d-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="5550d-109">GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="5550d-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="5550d-110">Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) ) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5550d-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5550d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5550d-111">Remarks</span></span>  
 <span data-ttu-id="5550d-112">`ICorDebugThread3` je logické rozšíření rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="5550d-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5550d-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="5550d-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5550d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5550d-114">Requirements</span></span>  
 <span data-ttu-id="5550d-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5550d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5550d-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5550d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5550d-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5550d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5550d-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5550d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5550d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5550d-119">See also</span></span>

- [<span data-ttu-id="5550d-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5550d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5550d-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="5550d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
