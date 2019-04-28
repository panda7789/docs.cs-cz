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
ms.openlocfilehash: 60d3b22d8dc140bf16af7f59781d5ed103dafbf4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765476"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="19e6f-102">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19e6f-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="19e6f-103">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="19e6f-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="19e6f-104">Toto rozhraní rozšiřuje ICorDebugHeapValue a icordebugheapvalue2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="19e6f-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19e6f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="19e6f-105">Methods</span></span>  
  
|<span data-ttu-id="19e6f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="19e6f-106">Method</span></span>|<span data-ttu-id="19e6f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="19e6f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19e6f-108">GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="19e6f-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="19e6f-109">Vrátí spravované vlákno, který vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="19e6f-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="19e6f-110">GetMonitorEventWaitList – metoda</span><span class="sxs-lookup"><span data-stu-id="19e6f-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="19e6f-111">Poskytuje seřazený seznam vláken, které jsou zařazeny do fronty na událost, která souvisí se zámkem monitorování.</span><span class="sxs-lookup"><span data-stu-id="19e6f-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19e6f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19e6f-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19e6f-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="19e6f-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19e6f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19e6f-114">Requirements</span></span>  
 <span data-ttu-id="19e6f-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19e6f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19e6f-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19e6f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19e6f-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19e6f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19e6f-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19e6f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e6f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19e6f-119">See also</span></span>

- [<span data-ttu-id="19e6f-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="19e6f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="19e6f-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="19e6f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
