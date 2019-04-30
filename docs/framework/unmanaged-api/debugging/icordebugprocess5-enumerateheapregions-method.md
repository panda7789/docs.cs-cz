---
title: ICorDebugProcess5::EnumerateHeapRegions – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61e30cf4ffe45578f7ad37de8295d227dbf313c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61930192"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="e7a9b-102">ICorDebugProcess5::EnumerateHeapRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="e7a9b-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="e7a9b-103">Získá enumerátor pro oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="e7a9b-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7a9b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7a9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7a9b-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="e7a9b-106">[out] Ukazatel na adresu [icordebugheapsegmentenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) rozhraní objektu, který je enumerátor pro oblasti paměti, ve kterém jsou umístěny objekty ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="e7a9b-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7a9b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7a9b-107">Remarks</span></span>  
 <span data-ttu-id="e7a9b-108">Před voláním `ICorDebugProcess5::EnumerateHeapRegions` metoda, měli byste zavolat [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda a zkoumat hodnoty `areGCStructuresValid` pole vráceného [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Ujistěte se, že haldě uvolňování paměti v jejím aktuálním stavu vyčíslitelný objekt.</span><span class="sxs-lookup"><span data-stu-id="e7a9b-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="e7a9b-109">Kromě toho `ICorDebugProcess5::EnumerateHeapRegions` vrátí metoda `E_FAIL` Pokud připojíte příliš brzy v doba života procesu, před paměti oblastech budou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="e7a9b-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="e7a9b-110">Tato metoda je zaručeno, že se vytvořit výčet všech oblastí paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že spravované objekty ve skutečnosti jsou umístěny v těchto oblastech.</span><span class="sxs-lookup"><span data-stu-id="e7a9b-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="e7a9b-111">[Icordebugheapsegmentenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objektu kolekce může zahrnovat oblasti prázdný nebo vyhrazené paměti.</span><span class="sxs-lookup"><span data-stu-id="e7a9b-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="e7a9b-112">[Icordebugheapsegmentenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objektu rozhraní je standardní výčet odvozený od icordebugenum – rozhraní, která umožňuje vytvořit výčet [cor_segment –](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="e7a9b-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="e7a9b-113">Každý [cor_segment –](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objekt poskytuje informace o rozsahu paměti konkrétního segmentu, spolu s generování objekty v daném segmentu.</span><span class="sxs-lookup"><span data-stu-id="e7a9b-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a9b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7a9b-114">Requirements</span></span>  
 <span data-ttu-id="e7a9b-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7a9b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a9b-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7a9b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7a9b-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7a9b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7a9b-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a9b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a9b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7a9b-119">See also</span></span>

- [<span data-ttu-id="e7a9b-120">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7a9b-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="e7a9b-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e7a9b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
