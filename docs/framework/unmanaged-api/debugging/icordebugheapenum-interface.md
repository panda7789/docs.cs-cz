---
title: ICorDebugHeapEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e9f58a0bc51e8a22672df6ab9bd94009c00f9bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688077"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="66f78-102">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66f78-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="66f78-103">Poskytuje enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="66f78-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="66f78-104">Toto rozhraní je podtřídou třídy icordebugenum – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="66f78-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66f78-105">Metody</span><span class="sxs-lookup"><span data-stu-id="66f78-105">Methods</span></span>  
  
|<span data-ttu-id="66f78-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="66f78-106">Method</span></span>|<span data-ttu-id="66f78-107">Popis</span><span class="sxs-lookup"><span data-stu-id="66f78-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66f78-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="66f78-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="66f78-109">Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o objektech na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="66f78-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66f78-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66f78-110">Remarks</span></span>  
 <span data-ttu-id="66f78-111">`ICorDebugHeapEnum` Icordebugenum – rozhraní implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="66f78-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="66f78-112">`ICorDebugHeapEnum` Instance se vyplní [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance voláním [icordebugprocess5::enumerateheap –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="66f78-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="66f78-113">Každý [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance v kolekci představuje buď živých objektů na haldě, nebo objekt, který není uveden do kořene s jakýmkoli objektem, ale nebyl dosud shromažďuje systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="66f78-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="66f78-114">[Cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objektů v kolekci můžete vytvořit výčet voláním [icordebugheapenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="66f78-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66f78-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66f78-115">Requirements</span></span>  
 <span data-ttu-id="66f78-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66f78-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66f78-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66f78-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66f78-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66f78-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66f78-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66f78-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f78-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66f78-120">See also</span></span>
- [<span data-ttu-id="66f78-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="66f78-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
