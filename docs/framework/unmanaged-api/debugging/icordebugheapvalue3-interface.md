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
ms.openlocfilehash: ddfe8cee8fdbca910ffa4f6989b1359ae5f7b11f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794373"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="905e3-102">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="905e3-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="905e3-103">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="905e3-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="905e3-104">Toto rozhraní rozšiřuje rozhraní ICorDebugHeapValue a ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="905e3-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="905e3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="905e3-105">Methods</span></span>  
  
|<span data-ttu-id="905e3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="905e3-106">Method</span></span>|<span data-ttu-id="905e3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="905e3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="905e3-108">GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="905e3-108">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="905e3-109">Vrátí spravované vlákno, které vlastní zámek monitorování tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="905e3-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="905e3-110">GetMonitorEventWaitList – metoda</span><span class="sxs-lookup"><span data-stu-id="905e3-110">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="905e3-111">Poskytuje uspořádaný seznam vláken, která jsou zařazená do fronty pro událost přidruženou ke zámku monitoru.</span><span class="sxs-lookup"><span data-stu-id="905e3-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="905e3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="905e3-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="905e3-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="905e3-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="905e3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="905e3-114">Requirements</span></span>  
 <span data-ttu-id="905e3-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="905e3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="905e3-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="905e3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="905e3-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="905e3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="905e3-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="905e3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="905e3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="905e3-119">See also</span></span>

- [<span data-ttu-id="905e3-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="905e3-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="905e3-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="905e3-121">Debugging</span></span>](index.md)
