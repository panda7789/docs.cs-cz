---
title: "ICorDebugProcess5 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e26f50967f0fb70e0593584e3f175d20a7b213e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="dde02-102">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dde02-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="dde02-103">Rozšiřuje rozhraní ICorDebugProcess podporující přístup k spravovaná halda k zadání informací o uvolňování paměti spravovaných objektů, a k určení, zda ladicí program načte bitové kopie z mezipaměti místní nativních bitových kopií aplikace.</span><span class="sxs-lookup"><span data-stu-id="dde02-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dde02-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dde02-104">Methods</span></span>  
  
|<span data-ttu-id="dde02-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-105">Method</span></span>|<span data-ttu-id="dde02-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dde02-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dde02-107">EnableNGenPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="dde02-108">Nastaví hodnotu, která určuje, jak aplikace načte nativní bitové kopie při spuštění pod spravované ladicí program.</span><span class="sxs-lookup"><span data-stu-id="dde02-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="dde02-109">EnumerateGCReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="dde02-110">Získá enumerátor pro všechny objekty, které mají být uklizeny v procesu.</span><span class="sxs-lookup"><span data-stu-id="dde02-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="dde02-111">EnumerateHandles – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="dde02-112">Získá enumerátor pro objekt popisovače v procesu.</span><span class="sxs-lookup"><span data-stu-id="dde02-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="dde02-113">EnumerateHeap – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="dde02-114">Získá enumerátor pro objekty v haldě spravované.</span><span class="sxs-lookup"><span data-stu-id="dde02-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="dde02-115">EnumerateHeapRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="dde02-116">Získá enumerátor pro oblasti spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="dde02-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="dde02-117">GetArrayLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="dde02-118">Získá informace o rozložení pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="dde02-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="dde02-119">GetGCHeapInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="dde02-120">Získá odkazy [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) struktura, která obsahuje informace o objektech, které mají být uklizeny na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="dde02-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="dde02-121">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="dde02-122">Získá ukazatel na objekt spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="dde02-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="dde02-123">GetTypeFields – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="dde02-124">Získá ukazatel na pole obsahující informace z pole pro typ podle jeho typ identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="dde02-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="dde02-125">GetTypeForTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="dde02-126">Získá typ objektu, která poskytuje informace o objektu na základě jeho typu identifikátory.</span><span class="sxs-lookup"><span data-stu-id="dde02-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="dde02-127">GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="dde02-128">Získá typ identifikátor pro objekt na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="dde02-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="dde02-129">GetTypeLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="dde02-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="dde02-130">Získá informace o rozložení objektu v paměti podle jeho typ identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="dde02-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dde02-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dde02-131">Remarks</span></span>  
 <span data-ttu-id="dde02-132">Toto rozhraní logicky rozšiřuje ICorDebugProcess, icordebugprocess2 –, a [icordebugprocess3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dde02-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dde02-133">Toto rozhraní nepodporuje volané vzdáleně z jiného počítače nebo z jiného procesu.</span><span class="sxs-lookup"><span data-stu-id="dde02-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dde02-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dde02-134">Requirements</span></span>  
 <span data-ttu-id="dde02-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dde02-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dde02-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dde02-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dde02-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dde02-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dde02-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dde02-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde02-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="dde02-139">See Also</span></span>  
 [<span data-ttu-id="dde02-140">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dde02-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="dde02-141">Ladění</span><span class="sxs-lookup"><span data-stu-id="dde02-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
