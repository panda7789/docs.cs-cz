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
ms.openlocfilehash: 897fb56cacb51e98cf8f1778c3529617decb5ecb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138445"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="70164-102">ICorDebugHeapSegmentEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="70164-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="70164-103">Získá zadaný počet instancí [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , které obsahují informace o oblastech paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="70164-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70164-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70164-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70164-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70164-105">Parameters</span></span>  
 <span data-ttu-id="70164-106">celt</span><span class="sxs-lookup"><span data-stu-id="70164-106">celt</span></span>  
 <span data-ttu-id="70164-107">pro Počet segmentů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="70164-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="70164-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="70164-108">segments</span></span>  
 <span data-ttu-id="70164-109">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , který poskytuje informace o oblasti paměti ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="70164-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="70164-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="70164-110">pceltFetched</span></span>  
 <span data-ttu-id="70164-111">mimo Ukazatel na počet [COR_HEAPOBJECTch](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objektů, které jsou ve skutečnosti vráceny v `segments`.</span><span class="sxs-lookup"><span data-stu-id="70164-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="70164-112">Tato hodnota může být `null`, pokud `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="70164-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70164-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70164-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70164-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70164-114">Requirements</span></span>  
 <span data-ttu-id="70164-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70164-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70164-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="70164-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70164-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="70164-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70164-118">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70164-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70164-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70164-119">See also</span></span>

- [<span data-ttu-id="70164-120">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70164-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="70164-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="70164-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
