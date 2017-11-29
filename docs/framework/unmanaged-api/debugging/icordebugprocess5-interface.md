---
title: "ICorDebugProcess5 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5
helpviewer_keywords: ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0f0a46e18121a222ee62fec207dde938d1e967b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="609d1-102">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="609d1-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="609d1-103">Rozšiřuje rozhraní ICorDebugProcess podporující přístup k spravovaná halda k zadání informací o uvolňování paměti spravovaných objektů, a k určení, zda ladicí program načte bitové kopie z mezipaměti místní nativních bitových kopií aplikace.</span><span class="sxs-lookup"><span data-stu-id="609d1-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="609d1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="609d1-104">Methods</span></span>  
  
|<span data-ttu-id="609d1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-105">Method</span></span>|<span data-ttu-id="609d1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="609d1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="609d1-107">Enablengenpolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="609d1-108">Nastaví hodnotu, která určuje, jak aplikace načte nativní bitové kopie při spuštění pod spravované ladicí program.</span><span class="sxs-lookup"><span data-stu-id="609d1-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="609d1-109">Enumerategcreferences – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="609d1-110">Získá enumerátor pro všechny objekty, které mají být uklizeny v procesu.</span><span class="sxs-lookup"><span data-stu-id="609d1-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="609d1-111">Enumeratehandles – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="609d1-112">Získá enumerátor pro objekt popisovače v procesu.</span><span class="sxs-lookup"><span data-stu-id="609d1-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="609d1-113">Enumerateheap – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="609d1-114">Získá enumerátor pro objekty v haldě spravované.</span><span class="sxs-lookup"><span data-stu-id="609d1-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="609d1-115">Enumerateheapregions – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="609d1-116">Získá enumerátor pro oblasti spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="609d1-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="609d1-117">Getarraylayout – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="609d1-118">Získá informace o rozložení pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="609d1-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="609d1-119">Getgcheapinformation – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="609d1-120">Získá odkazy [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) struktura, která obsahuje informace o objektech, které mají být uklizeny na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="609d1-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="609d1-121">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="609d1-122">Získá ukazatel na objekt spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="609d1-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="609d1-123">Gettypefields – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="609d1-124">Získá ukazatel na pole obsahující informace z pole pro typ podle jeho typ identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="609d1-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="609d1-125">Gettypefortypeid – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="609d1-126">Získá typ objektu, která poskytuje informace o objektu na základě jeho typu identifikátory.</span><span class="sxs-lookup"><span data-stu-id="609d1-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="609d1-127">GetTypeId – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="609d1-128">Získá typ identifikátor pro objekt na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="609d1-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="609d1-129">Gettypelayout – metoda</span><span class="sxs-lookup"><span data-stu-id="609d1-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="609d1-130">Získá informace o rozložení objektu v paměti podle jeho typ identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="609d1-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="609d1-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="609d1-131">Remarks</span></span>  
 <span data-ttu-id="609d1-132">Toto rozhraní logicky rozšiřuje ICorDebugProcess, icordebugprocess2 –, a [icordebugprocess3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="609d1-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="609d1-133">Toto rozhraní nepodporuje volané vzdáleně z jiného počítače nebo z jiného procesu.</span><span class="sxs-lookup"><span data-stu-id="609d1-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="609d1-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="609d1-134">Requirements</span></span>  
 <span data-ttu-id="609d1-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="609d1-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="609d1-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="609d1-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="609d1-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="609d1-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="609d1-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="609d1-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609d1-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="609d1-139">See Also</span></span>  
 [<span data-ttu-id="609d1-140">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="609d1-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="609d1-141">Ladění</span><span class="sxs-lookup"><span data-stu-id="609d1-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
