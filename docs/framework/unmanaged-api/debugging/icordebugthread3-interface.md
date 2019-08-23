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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9622716e3a2cca7e3af0b1e1b134458a50ad1bec
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962970"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="c4cc8-102">ICorDebugThread3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4cc8-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="c4cc8-103">Poskytuje vstupní bod pro [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4cc8-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4cc8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c4cc8-104">Methods</span></span>  
  
|<span data-ttu-id="c4cc8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4cc8-105">Method</span></span>|<span data-ttu-id="c4cc8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c4cc8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4cc8-107">CreateStackWalk – metoda</span><span class="sxs-lookup"><span data-stu-id="c4cc8-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="c4cc8-108">Vytvoří objekt [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) pro vlákno, jehož zásobník chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="c4cc8-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="c4cc8-109">GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="c4cc8-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="c4cc8-110">Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) ) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c4cc8-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4cc8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4cc8-111">Remarks</span></span>  
 <span data-ttu-id="c4cc8-112">`ICorDebugThread3`je logickým rozšířením rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c4cc8-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4cc8-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c4cc8-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4cc8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4cc8-114">Requirements</span></span>  
 <span data-ttu-id="c4cc8-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4cc8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4cc8-116">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4cc8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4cc8-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4cc8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4cc8-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4cc8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4cc8-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4cc8-119">See also</span></span>

- [<span data-ttu-id="c4cc8-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c4cc8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c4cc8-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="c4cc8-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
