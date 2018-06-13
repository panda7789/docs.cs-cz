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
ms.openlocfilehash: 3b63646b54b73c30abf0ddb9a06a982f1364ef87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417021"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="b5161-102">ICorDebugHeapSegmentEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b5161-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="b5161-103">Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o oblasti paměti spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="b5161-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5161-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5161-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5161-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5161-105">Parameters</span></span>  
 <span data-ttu-id="b5161-106">celt</span><span class="sxs-lookup"><span data-stu-id="b5161-106">celt</span></span>  
 <span data-ttu-id="b5161-107">[v] Počet segmentů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="b5161-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="b5161-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="b5161-108">segments</span></span>  
 <span data-ttu-id="b5161-109">[out] Ukazatele, každý z nich odkazuje na pole [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekt, který obsahuje informace o oblasti spravovaná halda paměti.</span><span class="sxs-lookup"><span data-stu-id="b5161-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="b5161-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="b5161-110">pceltFetched</span></span>  
 <span data-ttu-id="b5161-111">[out] Ukazatel na počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty ve skutečnosti, vrátí se v `segments`.</span><span class="sxs-lookup"><span data-stu-id="b5161-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="b5161-112">Tato hodnota může být `null` Pokud `celt` je 1.</span><span class="sxs-lookup"><span data-stu-id="b5161-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5161-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5161-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5161-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5161-114">Requirements</span></span>  
 <span data-ttu-id="b5161-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5161-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5161-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5161-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5161-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5161-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5161-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5161-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5161-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5161-119">See Also</span></span>  
 [<span data-ttu-id="b5161-120">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5161-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 [<span data-ttu-id="b5161-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b5161-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
