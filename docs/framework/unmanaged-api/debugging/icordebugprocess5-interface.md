---
title: ICorDebugProcess5 – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: 64fb60abf4f5730dbc15204dbc034b08cacefab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121249"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="ab466-102">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab466-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="ab466-103">Rozšiřuje rozhraní ICorDebugProcess pro podporu přístupu ke spravované haldě, k poskytnutí informací o uvolnění paměti spravovaných objektů a určení, zda ladicí program načítá obrázky z místní mezipaměti nativní bitové kopie aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab466-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab466-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab466-104">Methods</span></span>  
  
|<span data-ttu-id="ab466-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-105">Method</span></span>|<span data-ttu-id="ab466-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ab466-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab466-107">EnableNGenPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="ab466-108">Nastaví hodnotu, která určuje, jak aplikace načítá nativní bitové kopie při spuštění pod spravovaným ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="ab466-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="ab466-109">EnumerateGCReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="ab466-110">Získá enumerátor pro všechny objekty, které mají být v procesu shromažďovány jako uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ab466-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="ab466-111">EnumerateHandles – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="ab466-112">Získá enumerátor pro popisovače objektů v procesu.</span><span class="sxs-lookup"><span data-stu-id="ab466-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="ab466-113">EnumerateHeap – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="ab466-114">Získá enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="ab466-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="ab466-115">EnumerateHeapRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="ab466-116">Získá enumerátor pro oblasti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="ab466-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="ab466-117">GetArrayLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="ab466-118">Získá informace o rozložení pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="ab466-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="ab466-119">GetGCHeapInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="ab466-120">Získá ukazatel na strukturu [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) , která obsahuje informace o objektech, které mají být ve spravované haldě shromážděny paměti.</span><span class="sxs-lookup"><span data-stu-id="ab466-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="ab466-121">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="ab466-122">Získá ukazatel na objekt na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="ab466-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="ab466-123">GetTypeFields – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="ab466-124">Získá ukazatel na pole, které obsahuje informace o poli pro typ založený na jeho identifikátoru typu.</span><span class="sxs-lookup"><span data-stu-id="ab466-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="ab466-125">GetTypeForTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="ab466-126">Získá objekt typu, který poskytuje informace o objektu na základě jeho identifikátorů typu.</span><span class="sxs-lookup"><span data-stu-id="ab466-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="ab466-127">GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="ab466-128">Získá identifikátor typu objektu na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="ab466-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="ab466-129">GetTypeLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="ab466-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="ab466-130">Načte informace o rozložení objektu v paměti na základě jeho identifikátoru typu.</span><span class="sxs-lookup"><span data-stu-id="ab466-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab466-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab466-131">Remarks</span></span>  
 <span data-ttu-id="ab466-132">Toto rozhraní logicky rozšiřuje rozhraní ICorDebugProcess, ICorDebugProcess2 a [ICorDebugProcess3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ab466-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab466-133">Toto rozhraní nepodporuje vzdálené volání, a to buď z jiného počítače, nebo z jiného procesu.</span><span class="sxs-lookup"><span data-stu-id="ab466-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab466-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab466-134">Requirements</span></span>  
 <span data-ttu-id="ab466-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab466-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab466-136">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab466-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab466-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ab466-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab466-138">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab466-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab466-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab466-139">See also</span></span>

- [<span data-ttu-id="ab466-140">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ab466-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ab466-141">Ladění</span><span class="sxs-lookup"><span data-stu-id="ab466-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
