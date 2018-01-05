---
title: "ICorDebugGCReferenceEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGCReferenceEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGCReferenceEnum
helpviewer_keywords: ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afe52c3df8f61b234b3c68ee819ba8389593c82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="47034-102">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47034-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="47034-103">Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="47034-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47034-104">Metody</span><span class="sxs-lookup"><span data-stu-id="47034-104">Methods</span></span>  
  
|<span data-ttu-id="47034-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="47034-105">Method</span></span>|<span data-ttu-id="47034-106">Popis</span><span class="sxs-lookup"><span data-stu-id="47034-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47034-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="47034-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="47034-108">Získá zadaný počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instancí, které obsahují informace o objektech, které budou uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="47034-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47034-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47034-109">Remarks</span></span>  
 <span data-ttu-id="47034-110">`ICorDebugGCReferenceEnum` Rozhraní implementuje rozhraní "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="47034-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="47034-111">`ICorDebugGCReferenceEnum` Se zobrazí v instanci [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instance voláním [icordebugprocess5::enumerategcreferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="47034-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="47034-112">[Cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekty mohou být uvedené voláním [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="47034-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="47034-113">[Cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objektů v kolekcích naplněno touto metodou představují tři typy objektů:</span><span class="sxs-lookup"><span data-stu-id="47034-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="47034-114">Objekty z všechny spravované zásobníky.</span><span class="sxs-lookup"><span data-stu-id="47034-114">Objects from all managed stacks.</span></span> <span data-ttu-id="47034-115">To zahrnuje za provozu odkazy ve spravovaném kódu a také objekty vytvořené modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="47034-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="47034-116">Objekty z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="47034-116">Objects from the handle table.</span></span> <span data-ttu-id="47034-117">To zahrnuje silné odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.</span><span class="sxs-lookup"><span data-stu-id="47034-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="47034-118">Objekty z fronty finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="47034-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="47034-119">Fronty finalizační metodu kořeny objekty, dokud finalizační metodu byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="47034-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47034-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47034-120">Requirements</span></span>  
 <span data-ttu-id="47034-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47034-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47034-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47034-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47034-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47034-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47034-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47034-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47034-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="47034-125">See Also</span></span>  
 [<span data-ttu-id="47034-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="47034-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
