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
ms.openlocfilehash: ff290cd8ad331ff109c3bbbf87638d22b9b183bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208535"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="87024-102">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87024-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="87024-103">Poskytuje enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="87024-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="87024-104">Toto rozhraní je podtřídou rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="87024-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87024-105">Metody</span><span class="sxs-lookup"><span data-stu-id="87024-105">Methods</span></span>  
  
|<span data-ttu-id="87024-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="87024-106">Method</span></span>|<span data-ttu-id="87024-107">Popis</span><span class="sxs-lookup"><span data-stu-id="87024-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87024-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="87024-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="87024-109">Získá zadaný počet instancí [COR_HEAPOBJECT](cor-heapobject-structure.md) , které obsahují informace o objektech na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="87024-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87024-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87024-110">Remarks</span></span>  
 <span data-ttu-id="87024-111">`ICorDebugHeapEnum`Rozhraní implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="87024-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="87024-112">`ICorDebugHeapEnum`Instance je naplněna instancí [COR_HEAPOBJECT](cor-heapobject-structure.md) voláním metody [ICorDebugProcess5:: EnumerateHeap –](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="87024-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="87024-113">Každá instance [COR_HEAPOBJECT](cor-heapobject-structure.md) v kolekci představuje buď živý objekt na haldě, nebo objekt, který není rootem žádného objektu, ale ještě nebyl shromážděn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="87024-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="87024-114">Objekty [COR_HEAPOBJECT](cor-heapobject-structure.md) v kolekci lze vyčíslit voláním metody [ICorDebugHeapEnum –:: Next](icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="87024-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87024-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87024-115">Requirements</span></span>  
 <span data-ttu-id="87024-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87024-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87024-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87024-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87024-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="87024-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87024-119">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87024-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87024-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="87024-120">See also</span></span>

- [<span data-ttu-id="87024-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87024-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
