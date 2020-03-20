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
ms.openlocfilehash: f5af8e559b4fbfeb60530372185ca10104ade987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178854"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="758d5-102">ICorDebugHeapEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="758d5-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="758d5-103">Získá zadaný počet [COR_HEAPOBJECT](cor-heapobject-structure.md) instancí, které obsahují informace o objektech na spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="758d5-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="758d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="758d5-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="758d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="758d5-105">Parameters</span></span>  
 <span data-ttu-id="758d5-106">celt</span><span class="sxs-lookup"><span data-stu-id="758d5-106">celt</span></span>  
 <span data-ttu-id="758d5-107">[v] Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="758d5-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="758d5-108"> – objekty</span><span class="sxs-lookup"><span data-stu-id="758d5-108">objects</span></span>  
 <span data-ttu-id="758d5-109">[out] Pole ukazatelů, z nichž každý odkazuje na [COR_HEAPOBJECT](cor-heapobject-structure.md) objekt, který poskytuje informace o objektu na spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="758d5-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="758d5-110">pceltnačten</span><span class="sxs-lookup"><span data-stu-id="758d5-110">pceltFetched</span></span>  
 <span data-ttu-id="758d5-111">[out] Ukazatel na počet [objektů COR_HEAPOBJECT](cor-heapobject-structure.md) skutečně `objects`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="758d5-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="758d5-112">Tato hodnota `null` může `celt` být, pokud je 1.</span><span class="sxs-lookup"><span data-stu-id="758d5-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="758d5-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="758d5-113">Remarks</span></span>  
 <span data-ttu-id="758d5-114">Toto `COR_HEAPOBJECT.type` pole je identifikátorem vnořeného rozhraní COM s počítaného odkazem.</span><span class="sxs-lookup"><span data-stu-id="758d5-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="758d5-115">Tento odkaz musí být uvolněn `ICorDebugHeapEnum::Next`volajícím .</span><span class="sxs-lookup"><span data-stu-id="758d5-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="758d5-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="758d5-116">Requirements</span></span>  
 <span data-ttu-id="758d5-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="758d5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="758d5-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="758d5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="758d5-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="758d5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="758d5-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="758d5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="758d5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="758d5-121">See also</span></span>

- [<span data-ttu-id="758d5-122">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="758d5-122">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="758d5-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="758d5-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
