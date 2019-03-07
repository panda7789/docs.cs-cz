---
title: ICorDebugHeapSegmentEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c3b99936315c949fa9920c7d17dc01d9bcc53b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485041"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="af1af-102">ICorDebugHeapSegmentEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="af1af-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="af1af-103">Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="af1af-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af1af-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af1af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af1af-105">Parameters</span></span>  
 <span data-ttu-id="af1af-106">celt</span><span class="sxs-lookup"><span data-stu-id="af1af-106">celt</span></span>  
 <span data-ttu-id="af1af-107">[in] Počet segmentů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="af1af-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="af1af-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="af1af-108">segments</span></span>  
 <span data-ttu-id="af1af-109">[out] Pole ukazatelů, každý z nich odkazuje [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekt, který poskytuje informace o oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="af1af-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="af1af-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="af1af-110">pceltFetched</span></span>  
 <span data-ttu-id="af1af-111">[out] Ukazatel na počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objektů skutečně vrácených v `segments`.</span><span class="sxs-lookup"><span data-stu-id="af1af-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="af1af-112">Tato hodnota může být `null` Pokud `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="af1af-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af1af-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af1af-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af1af-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af1af-114">Requirements</span></span>  
 <span data-ttu-id="af1af-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af1af-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af1af-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af1af-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af1af-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af1af-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af1af-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af1af-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af1af-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af1af-119">See also</span></span>
- [<span data-ttu-id="af1af-120">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af1af-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="af1af-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="af1af-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
