---
title: ICorDebugHeapSegmentEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: e9679029cd54ac44832add9bc4f47f8c8e9a26a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138452"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="31d0a-102">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31d0a-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="31d0a-103">Poskytuje enumerátor pro oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="31d0a-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="31d0a-104">Toto rozhraní je podtřídou rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="31d0a-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31d0a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="31d0a-105">Methods</span></span>  
  
|<span data-ttu-id="31d0a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="31d0a-106">Method</span></span>|<span data-ttu-id="31d0a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="31d0a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31d0a-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="31d0a-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="31d0a-109">Získá zadaný počet instancí [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , které obsahují informace o oblastech spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="31d0a-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31d0a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31d0a-110">Remarks</span></span>  
 <span data-ttu-id="31d0a-111">Rozhraní `ICorDebugHeapSegmentEnum` implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="31d0a-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="31d0a-112">Instance `ICorDebugHeapSegmentEnum` se naplní instancemi [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) voláním metody [ICorDebugProcess5:: EnumerateHeapRegions –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="31d0a-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="31d0a-113">Objekty [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) v kolekci lze vyčíslit voláním metody [ICorDebugHeapSegmentEnum –:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="31d0a-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="31d0a-114">Objekt `ICorDebugHeapSegmentEnum` Collection vypíše všechny oblasti paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že se v těchto oblastech skutečně nacházejí spravované objekty.</span><span class="sxs-lookup"><span data-stu-id="31d0a-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="31d0a-115">Může obsahovat informace o prázdných nebo rezervovaných oblastech paměti.</span><span class="sxs-lookup"><span data-stu-id="31d0a-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d0a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31d0a-116">Requirements</span></span>  
 <span data-ttu-id="31d0a-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31d0a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d0a-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="31d0a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31d0a-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="31d0a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31d0a-120">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d0a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d0a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31d0a-121">See also</span></span>

- [<span data-ttu-id="31d0a-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="31d0a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
