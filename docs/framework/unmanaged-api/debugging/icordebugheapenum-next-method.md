---
title: ICorDebugHeapEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 2c84112984e9cb7dec2a492ac16af00e14770806
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782485"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="f3367-102">ICorDebugHeapEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f3367-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="f3367-103">Získá zadaný počet instancí [COR_HEAPOBJECT](cor-heapobject-structure.md) , které obsahují informace o objektech na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="f3367-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3367-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3367-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3367-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3367-105">Parameters</span></span>  
 <span data-ttu-id="f3367-106">celt</span><span class="sxs-lookup"><span data-stu-id="f3367-106">celt</span></span>  
 <span data-ttu-id="f3367-107">pro Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="f3367-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="f3367-108">– objekty</span><span class="sxs-lookup"><span data-stu-id="f3367-108">objects</span></span>  
 <span data-ttu-id="f3367-109">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [COR_HEAPOBJECT](cor-heapobject-structure.md) , který poskytuje informace o objektu na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="f3367-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="f3367-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="f3367-110">pceltFetched</span></span>  
 <span data-ttu-id="f3367-111">mimo Ukazatel na počet objektů [COR_HEAPOBJECT](cor-heapobject-structure.md) ve skutečnosti vrácených v `objects`.</span><span class="sxs-lookup"><span data-stu-id="f3367-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="f3367-112">Tato hodnota může být `null`, pokud `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="f3367-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3367-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3367-113">Remarks</span></span>  
 <span data-ttu-id="f3367-114">Pole `COR_HEAPOBJECT.type` je identifikátor vnořeného rozhraní COM s vypočítaným odkazem.</span><span class="sxs-lookup"><span data-stu-id="f3367-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="f3367-115">Tento odkaz musí být vydaný volajícím `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="f3367-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3367-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3367-116">Requirements</span></span>  
 <span data-ttu-id="f3367-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3367-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3367-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3367-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3367-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3367-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3367-120">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3367-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3367-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3367-121">See also</span></span>

- [<span data-ttu-id="f3367-122">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3367-122">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="f3367-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f3367-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
