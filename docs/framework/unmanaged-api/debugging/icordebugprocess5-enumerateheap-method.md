---
title: "ICorDebugProcess5::EnumerateHeap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fabe3d70b493427f3845b5752946b00097c1e78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="009c9-102">ICorDebugProcess5::EnumerateHeap – metoda</span><span class="sxs-lookup"><span data-stu-id="009c9-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="009c9-103">Získá enumerátor pro objekty v haldě spravované.</span><span class="sxs-lookup"><span data-stu-id="009c9-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="009c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="009c9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="009c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="009c9-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="009c9-106">[out] Ukazatel na adresu [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) rozhraní objekt, který je enumerátor pro objekty, které jsou umístěné na spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="009c9-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="009c9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="009c9-107">Remarks</span></span>  
 <span data-ttu-id="009c9-108">Před voláním `ICorDebugProcess5::EnumerateHeap` metody by měly volat [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda a zkontrolujte hodnotu `areGCStructuresValid` pole vráceného objektu [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objekt, který chcete zkontrolujte, zda je vyčíslitelná kolekce halda paměti v jejím aktuálním stavu.</span><span class="sxs-lookup"><span data-stu-id="009c9-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="009c9-109">Kromě toho `ICorDebugProcess5::EnumerateHeap` vrátí `E_FAIL` Pokud připojíte příliš brzy v doba platnosti procesu před paměti, pro spravovaná halda je přidělen.</span><span class="sxs-lookup"><span data-stu-id="009c9-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="009c9-110">[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objekt rozhraní je standardní enumerátor odvozen z rozhraní ICorDebugEnum, který umožňuje vytvořit výčet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="009c9-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="009c9-111">Naplní tuto metodu [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objektu kolekce s [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o všech objektech.</span><span class="sxs-lookup"><span data-stu-id="009c9-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="009c9-112">Kolekce může také zahrnovat [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o objektech, které nejsou root podle objektu, ale nebyly dosud shromážděných modulem garbage collector.</span><span class="sxs-lookup"><span data-stu-id="009c9-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="009c9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="009c9-113">Requirements</span></span>  
 <span data-ttu-id="009c9-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="009c9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="009c9-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="009c9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="009c9-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="009c9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="009c9-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="009c9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009c9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="009c9-118">See Also</span></span>  
 [<span data-ttu-id="009c9-119">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="009c9-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="009c9-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="009c9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
