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
ms.openlocfilehash: 263124db75abdc058d26ffb606a13fc711aed8bf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792291"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="6a4d4-102">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a4d4-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="6a4d4-103">Rozšiřuje rozhraní ICorDebugProcess pro podporu přístupu ke spravované haldě, k poskytnutí informací o uvolnění paměti spravovaných objektů a určení, zda ladicí program načítá obrázky z místní mezipaměti nativní bitové kopie aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a4d4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6a4d4-104">Methods</span></span>  
  
|<span data-ttu-id="6a4d4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-105">Method</span></span>|<span data-ttu-id="6a4d4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6a4d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a4d4-107">EnableNGenPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-107">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="6a4d4-108">Nastaví hodnotu, která určuje, jak aplikace načítá nativní bitové kopie při spuštění pod spravovaným ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="6a4d4-109">EnumerateGCReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-109">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="6a4d4-110">Získá enumerátor pro všechny objekty, které mají být v procesu shromažďovány jako uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="6a4d4-111">EnumerateHandles – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-111">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="6a4d4-112">Získá enumerátor pro popisovače objektů v procesu.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="6a4d4-113">EnumerateHeap – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-113">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="6a4d4-114">Získá enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="6a4d4-115">EnumerateHeapRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-115">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="6a4d4-116">Získá enumerátor pro oblasti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="6a4d4-117">GetArrayLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-117">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="6a4d4-118">Získá informace o rozložení pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="6a4d4-119">GetGCHeapInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-119">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="6a4d4-120">Získá ukazatel na strukturu [COR_HEAPINFO](cor-heapinfo-structure.md) , která obsahuje informace o objektech, které mají být uvolňovány paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-120">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="6a4d4-121">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-121">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="6a4d4-122">Získá ukazatel na objekt na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="6a4d4-123">GetTypeFields – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-123">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="6a4d4-124">Získá ukazatel na pole, které obsahuje informace o poli pro typ založený na jeho identifikátoru typu.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="6a4d4-125">GetTypeForTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-125">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="6a4d4-126">Získá objekt typu, který poskytuje informace o objektu na základě jeho identifikátorů typu.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="6a4d4-127">GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-127">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="6a4d4-128">Získá identifikátor typu objektu na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="6a4d4-129">GetTypeLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="6a4d4-129">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="6a4d4-130">Načte informace o rozložení objektu v paměti na základě jeho identifikátoru typu.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a4d4-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a4d4-131">Remarks</span></span>  
 <span data-ttu-id="6a4d4-132">Toto rozhraní logicky rozšiřuje rozhraní ICorDebugProcess, ICorDebugProcess2 a [ICorDebugProcess3 –](icordebugprocess3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6a4d4-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a4d4-133">Toto rozhraní nepodporuje vzdálené volání, a to buď z jiného počítače, nebo z jiného procesu.</span><span class="sxs-lookup"><span data-stu-id="6a4d4-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a4d4-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a4d4-134">Requirements</span></span>  
 <span data-ttu-id="6a4d4-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a4d4-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a4d4-136">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a4d4-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a4d4-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6a4d4-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a4d4-138">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a4d4-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a4d4-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a4d4-139">See also</span></span>

- [<span data-ttu-id="6a4d4-140">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6a4d4-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6a4d4-141">Ladění</span><span class="sxs-lookup"><span data-stu-id="6a4d4-141">Debugging</span></span>](index.md)
