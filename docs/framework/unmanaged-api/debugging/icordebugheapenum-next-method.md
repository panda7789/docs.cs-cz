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
ms.openlocfilehash: 5d0b231b4014e60a9e8778c6b9d6ed7758b2d8c5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208470"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="6ed30-102">ICorDebugHeapEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="6ed30-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="6ed30-103">Získá zadaný počet instancí [COR_HEAPOBJECT](cor-heapobject-structure.md) , které obsahují informace o objektech na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="6ed30-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ed30-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ed30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ed30-105">Parameters</span></span>  
 <span data-ttu-id="6ed30-106">celt</span><span class="sxs-lookup"><span data-stu-id="6ed30-106">celt</span></span>  
 <span data-ttu-id="6ed30-107">pro Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="6ed30-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="6ed30-108"> – objekty</span><span class="sxs-lookup"><span data-stu-id="6ed30-108">objects</span></span>  
 <span data-ttu-id="6ed30-109">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [COR_HEAPOBJECT](cor-heapobject-structure.md) , který poskytuje informace o objektu na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="6ed30-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="6ed30-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="6ed30-110">pceltFetched</span></span>  
 <span data-ttu-id="6ed30-111">mimo Ukazatel na počet skutečně vrácených objektů [COR_HEAPOBJECT](cor-heapobject-structure.md) `objects` .</span><span class="sxs-lookup"><span data-stu-id="6ed30-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="6ed30-112">Tato hodnota může být `null` `celt` , pokud je 1.</span><span class="sxs-lookup"><span data-stu-id="6ed30-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ed30-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ed30-113">Remarks</span></span>  
 <span data-ttu-id="6ed30-114">`COR_HEAPOBJECT.type`Pole je identifikátor vnořeného rozhraní COM se započítávající odkazy.</span><span class="sxs-lookup"><span data-stu-id="6ed30-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="6ed30-115">Tento odkaz musí být vydaný volajícím `ICorDebugHeapEnum::Next` .</span><span class="sxs-lookup"><span data-stu-id="6ed30-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed30-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ed30-116">Requirements</span></span>  
 <span data-ttu-id="6ed30-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ed30-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed30-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ed30-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ed30-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6ed30-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ed30-120">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed30-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed30-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ed30-121">See also</span></span>

- [<span data-ttu-id="6ed30-122">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ed30-122">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="6ed30-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ed30-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
