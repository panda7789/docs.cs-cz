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
ms.openlocfilehash: 5add6da1ace372ecf6e513902bbf98f5f79c6778
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210394"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="00685-102">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00685-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="00685-103">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="00685-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="00685-104">Toto rozhraní rozšiřuje rozhraní ICorDebugHeapValue a ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="00685-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00685-105">Metody</span><span class="sxs-lookup"><span data-stu-id="00685-105">Methods</span></span>  
  
|<span data-ttu-id="00685-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="00685-106">Method</span></span>|<span data-ttu-id="00685-107">Popis</span><span class="sxs-lookup"><span data-stu-id="00685-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00685-108">GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="00685-108">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="00685-109">Vrátí spravované vlákno, které vlastní zámek monitorování tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="00685-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="00685-110">GetMonitorEventWaitList – metoda</span><span class="sxs-lookup"><span data-stu-id="00685-110">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="00685-111">Poskytuje uspořádaný seznam vláken, která jsou zařazená do fronty pro událost přidruženou ke zámku monitoru.</span><span class="sxs-lookup"><span data-stu-id="00685-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00685-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00685-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00685-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="00685-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00685-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00685-114">Requirements</span></span>  
 <span data-ttu-id="00685-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00685-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00685-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="00685-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00685-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="00685-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00685-118">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00685-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00685-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="00685-119">See also</span></span>

- [<span data-ttu-id="00685-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00685-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="00685-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="00685-121">Debugging</span></span>](index.md)
