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
ms.openlocfilehash: 8a267ec7123edb73ad51f0781a78344119ec6f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178894"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="e105b-102">ICorDebugHeapSegmentEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="e105b-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="e105b-103">Získá zadaný počet [COR_HEAPOBJECT](cor-heapobject-structure.md) instancí, které obsahují informace o oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="e105b-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e105b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e105b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e105b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e105b-105">Parameters</span></span>  
 <span data-ttu-id="e105b-106">celt</span><span class="sxs-lookup"><span data-stu-id="e105b-106">celt</span></span>  
 <span data-ttu-id="e105b-107">[v] Počet segmentů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="e105b-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="e105b-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="e105b-108">segments</span></span>  
 <span data-ttu-id="e105b-109">[out] Pole ukazatelů, z nichž každý odkazuje na [COR_HEAPOBJECT](cor-heapobject-structure.md) objekt, který poskytuje informace o oblasti paměti ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="e105b-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="e105b-110">pceltnačten</span><span class="sxs-lookup"><span data-stu-id="e105b-110">pceltFetched</span></span>  
 <span data-ttu-id="e105b-111">[out] Ukazatel na počet [objektů COR_HEAPOBJECT](cor-heapobject-structure.md) skutečně `segments`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="e105b-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="e105b-112">Tato hodnota `null` může `celt` být, pokud je 1.</span><span class="sxs-lookup"><span data-stu-id="e105b-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e105b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e105b-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e105b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e105b-114">Requirements</span></span>  
 <span data-ttu-id="e105b-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e105b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e105b-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e105b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e105b-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e105b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e105b-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e105b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e105b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e105b-119">See also</span></span>

- [<span data-ttu-id="e105b-120">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e105b-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="e105b-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e105b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
