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
ms.openlocfilehash: 49f89f7d36e74b1fa5921230d7dc6d271d4c0883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134635"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="b4942-102">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4942-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="b4942-103">Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="b4942-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4942-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b4942-104">Methods</span></span>  
  
|<span data-ttu-id="b4942-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b4942-105">Method</span></span>|<span data-ttu-id="b4942-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b4942-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4942-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b4942-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="b4942-108">Získá zadaný počet instancí [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) , které obsahují informace o objektech, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="b4942-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4942-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4942-109">Remarks</span></span>  
 <span data-ttu-id="b4942-110">Rozhraní `ICorDebugGCReferenceEnum` implementuje rozhraní "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="b4942-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="b4942-111">Instance `ICorDebugGCReferenceEnum` se naplní instancemi [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) voláním metody [ICorDebugProcess5:: EnumerateGCReferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b4942-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="b4942-112">Objekty [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) lze vyčíslit voláním metody [ICorDebugGCReference:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b4942-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="b4942-113">Objekty [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) v kolekci, které jsou vyplněny touto metodou, reprezentují tři druhy objektů:</span><span class="sxs-lookup"><span data-stu-id="b4942-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="b4942-114">Objekty ze všech spravovaných zásobníků.</span><span class="sxs-lookup"><span data-stu-id="b4942-114">Objects from all managed stacks.</span></span> <span data-ttu-id="b4942-115">To zahrnuje živé odkazy ve spravovaném kódu a také objekty vytvořené modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b4942-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="b4942-116">Objekty z tabulky popisovačů.</span><span class="sxs-lookup"><span data-stu-id="b4942-116">Objects from the handle table.</span></span> <span data-ttu-id="b4942-117">To zahrnuje silné odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.</span><span class="sxs-lookup"><span data-stu-id="b4942-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="b4942-118">Objekty z fronty finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="b4942-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="b4942-119">Objekty kořene fronty finalizační metody, dokud není spuštěn finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="b4942-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4942-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4942-120">Requirements</span></span>  
 <span data-ttu-id="b4942-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4942-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4942-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b4942-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4942-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4942-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4942-124">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4942-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4942-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4942-125">See also</span></span>

- [<span data-ttu-id="b4942-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b4942-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
