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
ms.openlocfilehash: 25f352a3a6dfae69116d6cda2497d55485b951cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417060"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="73c5b-102">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73c5b-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="73c5b-103">Poskytuje enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="73c5b-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="73c5b-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="73c5b-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73c5b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="73c5b-105">Methods</span></span>  
  
|<span data-ttu-id="73c5b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="73c5b-106">Method</span></span>|<span data-ttu-id="73c5b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="73c5b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73c5b-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="73c5b-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="73c5b-109">Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o objektech v haldě spravované.</span><span class="sxs-lookup"><span data-stu-id="73c5b-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73c5b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73c5b-110">Remarks</span></span>  
 <span data-ttu-id="73c5b-111">`ICorDebugHeapEnum` Rozhraní implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="73c5b-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="73c5b-112">`ICorDebugHeapEnum` Se zobrazí v instanci [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance voláním [icordebugprocess5::enumerateheap –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="73c5b-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="73c5b-113">Každý [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance v kolekci reprezentuje buď objekt za provozu v haldě nebo objekt, který není root pomocí libovolného objektu, ale nebyla ještě zjištěna modulem garbage collector.</span><span class="sxs-lookup"><span data-stu-id="73c5b-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="73c5b-114">[Cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) voláním mohou být uvedené v kolekci objektů [icordebugheapenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="73c5b-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73c5b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73c5b-115">Requirements</span></span>  
 <span data-ttu-id="73c5b-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73c5b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73c5b-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73c5b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73c5b-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73c5b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73c5b-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73c5b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c5b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="73c5b-120">See Also</span></span>  
 [<span data-ttu-id="73c5b-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="73c5b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
