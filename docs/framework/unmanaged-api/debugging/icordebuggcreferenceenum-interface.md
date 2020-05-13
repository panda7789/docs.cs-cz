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
ms.openlocfilehash: 5650a7e6e6cb0108f0d043914ea94debe2b703bf
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213098"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="c2d48-102">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2d48-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="c2d48-103">Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="c2d48-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2d48-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c2d48-104">Methods</span></span>  
  
|<span data-ttu-id="c2d48-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c2d48-105">Method</span></span>|<span data-ttu-id="c2d48-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c2d48-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2d48-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="c2d48-107">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="c2d48-108">Získá zadaný počet instancí [COR_GC_REFERENCE](cor-gc-reference-structure.md) , které obsahují informace o objektech, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="c2d48-108">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2d48-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2d48-109">Remarks</span></span>  
 <span data-ttu-id="c2d48-110">`ICorDebugGCReferenceEnum`Rozhraní implementuje rozhraní "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="c2d48-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="c2d48-111">`ICorDebugGCReferenceEnum`Instance je naplněna instancí [COR_GC_REFERENCE](cor-gc-reference-structure.md) voláním metody [ICorDebugProcess5:: EnumerateGCReferences –](icordebugprocess5-enumerategcreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c2d48-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="c2d48-112">Objekty [COR_GC_REFERENCE](cor-gc-reference-structure.md) lze vyčíslit voláním metody [ICorDebugGCReference:: Next](icordebuggcreferenceenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c2d48-112">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="c2d48-113">Objekty [COR_GC_REFERENCE](cor-gc-reference-structure.md) v kolekci, které jsou vyplněny touto metodou, reprezentují tři druhy objektů:</span><span class="sxs-lookup"><span data-stu-id="c2d48-113">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="c2d48-114">Objekty ze všech spravovaných zásobníků.</span><span class="sxs-lookup"><span data-stu-id="c2d48-114">Objects from all managed stacks.</span></span> <span data-ttu-id="c2d48-115">To zahrnuje živé odkazy ve spravovaném kódu a také objekty vytvořené modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="c2d48-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="c2d48-116">Objekty z tabulky popisovačů.</span><span class="sxs-lookup"><span data-stu-id="c2d48-116">Objects from the handle table.</span></span> <span data-ttu-id="c2d48-117">To zahrnuje silné odkazy ( `HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT` ) a statické proměnné v modulu.</span><span class="sxs-lookup"><span data-stu-id="c2d48-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="c2d48-118">Objekty z fronty finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="c2d48-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="c2d48-119">Objekty kořene fronty finalizační metody, dokud není spuštěn finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="c2d48-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d48-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2d48-120">Requirements</span></span>  
 <span data-ttu-id="c2d48-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d48-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d48-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2d48-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2d48-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2d48-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2d48-124">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d48-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d48-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2d48-125">See also</span></span>

- [<span data-ttu-id="c2d48-126">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2d48-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
