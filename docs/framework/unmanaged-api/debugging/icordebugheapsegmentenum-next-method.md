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
ms.openlocfilehash: c9999961ec20a31cf82d5ad60104bcdd04c340d1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210173"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="22aff-102">ICorDebugHeapSegmentEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="22aff-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="22aff-103">Získá zadaný počet instancí [COR_HEAPOBJECT](cor-heapobject-structure.md) , které obsahují informace o oblastech paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="22aff-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22aff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22aff-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22aff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22aff-105">Parameters</span></span>  
 <span data-ttu-id="22aff-106">celt</span><span class="sxs-lookup"><span data-stu-id="22aff-106">celt</span></span>  
 <span data-ttu-id="22aff-107">pro Počet segmentů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="22aff-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="22aff-108">segmenty</span><span class="sxs-lookup"><span data-stu-id="22aff-108">segments</span></span>  
 <span data-ttu-id="22aff-109">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [COR_HEAPOBJECT](cor-heapobject-structure.md) , který poskytuje informace o oblasti paměti ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="22aff-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="22aff-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="22aff-110">pceltFetched</span></span>  
 <span data-ttu-id="22aff-111">mimo Ukazatel na počet skutečně vrácených objektů [COR_HEAPOBJECT](cor-heapobject-structure.md) `segments` .</span><span class="sxs-lookup"><span data-stu-id="22aff-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="22aff-112">Tato hodnota může být `null` `celt` , pokud je 1.</span><span class="sxs-lookup"><span data-stu-id="22aff-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22aff-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22aff-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22aff-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22aff-114">Requirements</span></span>  
 <span data-ttu-id="22aff-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22aff-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22aff-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="22aff-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22aff-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="22aff-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22aff-118">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22aff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22aff-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="22aff-119">See also</span></span>

- [<span data-ttu-id="22aff-120">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22aff-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="22aff-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22aff-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
