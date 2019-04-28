---
title: ICorDebugGCReferenceEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f83d2ac9ca96145fa89b283fec42c71858097f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651620"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="74b0a-102">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74b0a-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="74b0a-103">Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="74b0a-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74b0a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="74b0a-104">Methods</span></span>  
  
|<span data-ttu-id="74b0a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="74b0a-105">Method</span></span>|<span data-ttu-id="74b0a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="74b0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74b0a-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="74b0a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="74b0a-108">Získá zadaný počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instancí, které obsahují informace o objektech, které bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="74b0a-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74b0a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74b0a-109">Remarks</span></span>  
 <span data-ttu-id="74b0a-110">`ICorDebugGCReferenceEnum` Rozhraní implementuje rozhraní "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="74b0a-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="74b0a-111">`ICorDebugGCReferenceEnum` Instance se vyplní [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instance voláním [icordebugprocess5::enumerategcreferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="74b0a-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="74b0a-112">[Cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekty mohou být uvedené voláním [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="74b0a-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="74b0a-113">[Cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekty v kolekci vyplněn prostředkem tato metoda představují tři typy objektů:</span><span class="sxs-lookup"><span data-stu-id="74b0a-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="74b0a-114">Objekty ze všech spravovaných zásobníků.</span><span class="sxs-lookup"><span data-stu-id="74b0a-114">Objects from all managed stacks.</span></span> <span data-ttu-id="74b0a-115">To zahrnuje živé odkazy ve spravovaném kódu, jakož i objekty vytvořené modulem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="74b0a-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="74b0a-116">Objekty z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="74b0a-116">Objects from the handle table.</span></span> <span data-ttu-id="74b0a-117">Jedná se o silná odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.</span><span class="sxs-lookup"><span data-stu-id="74b0a-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="74b0a-118">Objekty ve frontě finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="74b0a-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="74b0a-119">Fronta finalizační metody kořeny objekty, dokud finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="74b0a-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74b0a-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74b0a-120">Requirements</span></span>  
 <span data-ttu-id="74b0a-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74b0a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74b0a-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74b0a-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74b0a-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74b0a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74b0a-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74b0a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b0a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74b0a-125">See also</span></span>

- [<span data-ttu-id="74b0a-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="74b0a-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
