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
ms.openlocfilehash: 1d34a3395605505ca0ebda072e33d8083d51123a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902418"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="cdc76-102">ICorDebugThread3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cdc76-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="cdc76-103">Poskytuje vstupní bod, který [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cdc76-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cdc76-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cdc76-104">Methods</span></span>  
  
|<span data-ttu-id="cdc76-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cdc76-105">Method</span></span>|<span data-ttu-id="cdc76-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cdc76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cdc76-107">CreateStackWalk – metoda</span><span class="sxs-lookup"><span data-stu-id="cdc76-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="cdc76-108">Vytvoří [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu pro vlákno, jehož zásobníku, které chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="cdc76-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="cdc76-109">GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="cdc76-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="cdc76-110">Vrátí pole vnitřních rámcích ([icordebuginternalframe2 –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objektů) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cdc76-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdc76-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cdc76-111">Remarks</span></span>  
 <span data-ttu-id="cdc76-112">`ICorDebugThread3` je logickým rozšířením icordebugthread – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cdc76-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdc76-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="cdc76-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdc76-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cdc76-114">Requirements</span></span>  
 <span data-ttu-id="cdc76-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdc76-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdc76-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdc76-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdc76-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdc76-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdc76-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdc76-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc76-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdc76-119">See also</span></span>

- [<span data-ttu-id="cdc76-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cdc76-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cdc76-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="cdc76-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
