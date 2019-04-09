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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191702"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="54d91-102">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54d91-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="54d91-103">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="54d91-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="54d91-104">Toto rozhraní rozšiřuje ICorDebugHeapValue a icordebugheapvalue2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="54d91-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54d91-105">Metody</span><span class="sxs-lookup"><span data-stu-id="54d91-105">Methods</span></span>  
  
|<span data-ttu-id="54d91-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="54d91-106">Method</span></span>|<span data-ttu-id="54d91-107">Popis</span><span class="sxs-lookup"><span data-stu-id="54d91-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54d91-108">GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="54d91-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="54d91-109">Vrátí spravované vlákno, který vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="54d91-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="54d91-110">GetMonitorEventWaitList – metoda</span><span class="sxs-lookup"><span data-stu-id="54d91-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="54d91-111">Poskytuje seřazený seznam vláken, které jsou zařazeny do fronty na událost, která souvisí se zámkem monitorování.</span><span class="sxs-lookup"><span data-stu-id="54d91-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54d91-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54d91-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54d91-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="54d91-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54d91-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54d91-114">Requirements</span></span>  
 <span data-ttu-id="54d91-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54d91-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54d91-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54d91-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54d91-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54d91-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="54d91-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="54d91-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54d91-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54d91-119">See also</span></span>

- [<span data-ttu-id="54d91-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54d91-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="54d91-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="54d91-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
