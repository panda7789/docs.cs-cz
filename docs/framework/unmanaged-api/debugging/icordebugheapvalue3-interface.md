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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a59d8bce6ae565687e7ed906f6c14332f0c5c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416829"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="3fca1-102">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fca1-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="3fca1-103">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="3fca1-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="3fca1-104">Toto rozhraní rozšiřuje icordebugheapvalue – a icordebugheapvalue2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3fca1-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3fca1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3fca1-105">Methods</span></span>  
  
|<span data-ttu-id="3fca1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3fca1-106">Method</span></span>|<span data-ttu-id="3fca1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3fca1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3fca1-108">GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="3fca1-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="3fca1-109">Vrátí spravované vlákno, které vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="3fca1-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="3fca1-110">GetMonitorEventWaitList – metoda</span><span class="sxs-lookup"><span data-stu-id="3fca1-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="3fca1-111">Poskytuje seřazený seznam vláken, které jsou zařazeny do fronty na událost, která souvisí s monitorování zámku.</span><span class="sxs-lookup"><span data-stu-id="3fca1-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fca1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fca1-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fca1-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3fca1-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fca1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fca1-114">Requirements</span></span>  
 <span data-ttu-id="3fca1-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fca1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fca1-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fca1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fca1-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fca1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fca1-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fca1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fca1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fca1-119">See Also</span></span>  
 [<span data-ttu-id="3fca1-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3fca1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3fca1-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="3fca1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
