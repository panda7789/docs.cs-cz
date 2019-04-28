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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73036d1c12c46cbfda8031073a005bc9b376040e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756207"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="e48ce-102">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e48ce-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="e48ce-103">Poskytuje enumerátor pro oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="e48ce-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="e48ce-104">Toto rozhraní je podtřídou třídy icordebugenum – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e48ce-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e48ce-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e48ce-105">Methods</span></span>  
  
|<span data-ttu-id="e48ce-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e48ce-106">Method</span></span>|<span data-ttu-id="e48ce-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e48ce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e48ce-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="e48ce-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="e48ce-109">Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o oblastech spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="e48ce-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e48ce-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e48ce-110">Remarks</span></span>  
 <span data-ttu-id="e48ce-111">`ICorDebugHeapSegmentEnum` Icordebugenum – rozhraní implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e48ce-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="e48ce-112">`ICorDebugHeapSegmentEnum` Instance se vyplní [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance voláním [icordebugprocess5::enumerateheapregions –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e48ce-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="e48ce-113">[Cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objektů v kolekci můžete vytvořit výčet voláním [icordebugheapsegmentenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e48ce-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="e48ce-114">`ICorDebugHeapSegmentEnum` Objektu kolekce vytvoří výčet všech oblastí paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že spravované objekty ve skutečnosti jsou umístěny v těchto oblastech.</span><span class="sxs-lookup"><span data-stu-id="e48ce-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="e48ce-115">Může zahrnovat informace o oblastech prázdný nebo vyhrazené paměti.</span><span class="sxs-lookup"><span data-stu-id="e48ce-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e48ce-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e48ce-116">Requirements</span></span>  
 <span data-ttu-id="e48ce-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e48ce-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e48ce-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e48ce-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e48ce-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e48ce-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e48ce-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e48ce-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48ce-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e48ce-121">See also</span></span>

- [<span data-ttu-id="e48ce-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e48ce-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
