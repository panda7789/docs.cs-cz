---
title: "ICorDebugHeapValue3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3
helpviewer_keywords: ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5531689a3a4ba66fddfc98cadec7dc8d51c8629a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="b1209-102">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1209-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="b1209-103">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="b1209-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="b1209-104">Toto rozhraní rozšiřuje icordebugheapvalue – a icordebugheapvalue2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b1209-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1209-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b1209-105">Methods</span></span>  
  
|<span data-ttu-id="b1209-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b1209-106">Method</span></span>|<span data-ttu-id="b1209-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b1209-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1209-108">Getthreadowningmonitorlock – metoda</span><span class="sxs-lookup"><span data-stu-id="b1209-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="b1209-109">Vrátí spravované vlákno, které vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="b1209-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="b1209-110">Getmonitoreventwaitlist – metoda</span><span class="sxs-lookup"><span data-stu-id="b1209-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="b1209-111">Poskytuje seřazený seznam vláken, které jsou zařazeny do fronty na událost, která souvisí s monitorování zámku.</span><span class="sxs-lookup"><span data-stu-id="b1209-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1209-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1209-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1209-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b1209-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1209-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1209-114">Requirements</span></span>  
 <span data-ttu-id="b1209-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1209-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1209-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1209-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1209-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1209-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1209-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1209-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1209-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1209-119">See Also</span></span>  
 [<span data-ttu-id="b1209-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1209-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b1209-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="b1209-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
