---
title: ICorDebugHeapValue3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
ms.openlocfilehash: b062faffc22e444bd4d3b4a0c67f2a08d7af3560
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131112"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="e1f63-102">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1f63-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="e1f63-103">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="e1f63-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="e1f63-104">Toto rozhraní rozšiřuje rozhraní ICorDebugHeapValue a ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="e1f63-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1f63-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e1f63-105">Methods</span></span>  
  
|<span data-ttu-id="e1f63-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e1f63-106">Method</span></span>|<span data-ttu-id="e1f63-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e1f63-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1f63-108">GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="e1f63-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="e1f63-109">Vrátí spravované vlákno, které vlastní zámek monitorování tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="e1f63-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="e1f63-110">GetMonitorEventWaitList – metoda</span><span class="sxs-lookup"><span data-stu-id="e1f63-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="e1f63-111">Poskytuje uspořádaný seznam vláken, která jsou zařazená do fronty pro událost přidruženou ke zámku monitoru.</span><span class="sxs-lookup"><span data-stu-id="e1f63-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1f63-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1f63-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1f63-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e1f63-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1f63-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1f63-114">Requirements</span></span>  
 <span data-ttu-id="e1f63-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1f63-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1f63-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e1f63-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1f63-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e1f63-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1f63-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1f63-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f63-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1f63-119">See also</span></span>

- [<span data-ttu-id="e1f63-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e1f63-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e1f63-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="e1f63-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
