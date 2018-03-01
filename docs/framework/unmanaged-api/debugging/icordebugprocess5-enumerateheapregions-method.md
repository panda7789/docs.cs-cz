---
title: "ICorDebugProcess5::EnumerateHeapRegions – metoda"
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
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 478a8490e57946a08670d9f86e1f6ebcc67703a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="dbbee-102">ICorDebugProcess5::EnumerateHeapRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="dbbee-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="dbbee-103">Získá enumerátor pro rozsahy spravovaná halda paměti.</span><span class="sxs-lookup"><span data-stu-id="dbbee-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbbee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbbee-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbbee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbbee-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="dbbee-106">[out] Ukazatel na adresu [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) rozhraní objekt, který je enumerátor pro rozsahy, ve které objekty jsou umístěny v spravovaná halda paměti.</span><span class="sxs-lookup"><span data-stu-id="dbbee-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbbee-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbbee-107">Remarks</span></span>  
 <span data-ttu-id="dbbee-108">Před voláním `ICorDebugProcess5::EnumerateHeapRegions` metody by měly volat [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda a zkontrolujte hodnotu `areGCStructuresValid` pole vráceného objektu [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objekt, který chcete zkontrolujte, zda je vyčíslitelná kolekce halda paměti v jejím aktuálním stavu.</span><span class="sxs-lookup"><span data-stu-id="dbbee-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="dbbee-109">Kromě toho `ICorDebugProcess5::EnumerateHeapRegions` metoda vrátí `E_FAIL` Pokud připojíte příliš brzy v doba platnosti procesu, před paměti oblasti budou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="dbbee-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="dbbee-110">Tato metoda záruku, že se vytvořit výčet všech oblastech paměti, které mohou obsahovat spravovaných objektů, ale nezaručí, že spravované objekty skutečně nacházejí v těchto oblastech.</span><span class="sxs-lookup"><span data-stu-id="dbbee-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="dbbee-111">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objektu kolekce může zahrnovat oblasti prázdná nebo vyhrazené paměti.</span><span class="sxs-lookup"><span data-stu-id="dbbee-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="dbbee-112">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objekt rozhraní je standardní enumerátor odvozen z rozhraní ICorDebugEnum, který umožňuje vytvořit výčet [cor_segment –](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="dbbee-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="dbbee-113">Každý [cor_segment –](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objekt poskytuje informace o paměti rozsah určitý segment, společně s generování objektů v tomto segmentu.</span><span class="sxs-lookup"><span data-stu-id="dbbee-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbbee-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbbee-114">Requirements</span></span>  
 <span data-ttu-id="dbbee-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbbee-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbbee-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbbee-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbbee-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbbee-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbbee-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbbee-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbee-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbbee-119">See Also</span></span>  
 [<span data-ttu-id="dbbee-120">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbbee-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="dbbee-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dbbee-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
