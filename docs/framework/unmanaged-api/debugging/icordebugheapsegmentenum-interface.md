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
ms.openlocfilehash: cac4ddc33bcaf07d615fd186a63d96b1f4f6464c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417729"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="111bb-102">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="111bb-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="111bb-103">Poskytuje enumerátor pro oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="111bb-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="111bb-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="111bb-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="111bb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="111bb-105">Methods</span></span>  
  
|<span data-ttu-id="111bb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="111bb-106">Method</span></span>|<span data-ttu-id="111bb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="111bb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="111bb-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="111bb-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="111bb-109">Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o oblastech spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="111bb-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="111bb-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="111bb-110">Remarks</span></span>  
 <span data-ttu-id="111bb-111">`ICorDebugHeapSegmentEnum` Rozhraní implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="111bb-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="111bb-112">`ICorDebugHeapSegmentEnum` Se zobrazí v instanci [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance voláním [icordebugprocess5::enumerateheapregions –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="111bb-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="111bb-113">[Cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) voláním mohou být uvedené v kolekci objektů [icordebugheapsegmentenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="111bb-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="111bb-114">`ICorDebugHeapSegmentEnum` Objektu kolekce zobrazí všechny oblasti paměti, které mohou obsahovat spravovaných objektů, ale nezaručí, že spravované objekty skutečně nacházejí v těchto oblastech.</span><span class="sxs-lookup"><span data-stu-id="111bb-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="111bb-115">Může zahrnovat informace o oblastech prázdná nebo vyhrazené paměti.</span><span class="sxs-lookup"><span data-stu-id="111bb-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="111bb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="111bb-116">Requirements</span></span>  
 <span data-ttu-id="111bb-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="111bb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="111bb-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="111bb-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="111bb-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="111bb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="111bb-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="111bb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="111bb-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="111bb-121">See Also</span></span>  
 [<span data-ttu-id="111bb-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="111bb-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
