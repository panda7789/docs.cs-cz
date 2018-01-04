---
title: "ICorDebugHeapSegmentEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f8e197bb5d31635e4abc8e8bc6e3d62eb7632be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="003db-102">ICorDebugHeapSegmentEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="003db-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="003db-103">Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o oblasti paměti spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="003db-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="003db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="003db-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="003db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="003db-105">Parameters</span></span>  
 <span data-ttu-id="003db-106">celt</span><span class="sxs-lookup"><span data-stu-id="003db-106">celt</span></span>  
 <span data-ttu-id="003db-107">[v] Počet segmentů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="003db-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="003db-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="003db-108">segments</span></span>  
 <span data-ttu-id="003db-109">[out] Ukazatele, každý z nich odkazuje na pole [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekt, který obsahuje informace o oblasti spravovaná halda paměti.</span><span class="sxs-lookup"><span data-stu-id="003db-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="003db-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="003db-110">pceltFetched</span></span>  
 <span data-ttu-id="003db-111">[out] Ukazatel na počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty ve skutečnosti, vrátí se v `segments`.</span><span class="sxs-lookup"><span data-stu-id="003db-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="003db-112">Tato hodnota může být `null` Pokud `celt` je 1.</span><span class="sxs-lookup"><span data-stu-id="003db-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="003db-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="003db-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="003db-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="003db-114">Requirements</span></span>  
 <span data-ttu-id="003db-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="003db-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="003db-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="003db-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="003db-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="003db-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="003db-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="003db-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="003db-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="003db-119">See Also</span></span>  
 [<span data-ttu-id="003db-120">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="003db-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 [<span data-ttu-id="003db-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="003db-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
