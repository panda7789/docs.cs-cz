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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aef821c10b8b44e54967245aaab3956c16ea15b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757382"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="f5d96-102">ICorDebugHeapEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f5d96-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="f5d96-103">Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o objektech na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="f5d96-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5d96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5d96-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5d96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5d96-105">Parameters</span></span>  
 <span data-ttu-id="f5d96-106">celt</span><span class="sxs-lookup"><span data-stu-id="f5d96-106">celt</span></span>  
 <span data-ttu-id="f5d96-107">[in] Počet objektů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="f5d96-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="f5d96-108">– objekty</span><span class="sxs-lookup"><span data-stu-id="f5d96-108">objects</span></span>  
 <span data-ttu-id="f5d96-109">[out] Pole ukazatelů, každý z nich odkazuje [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekt, který poskytuje informace o objektu na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="f5d96-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="f5d96-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="f5d96-110">pceltFetched</span></span>  
 <span data-ttu-id="f5d96-111">[out] Ukazatel na počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objektů skutečně vrácených v `objects`.</span><span class="sxs-lookup"><span data-stu-id="f5d96-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="f5d96-112">Tato hodnota může být `null` Pokud `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="f5d96-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5d96-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5d96-113">Remarks</span></span>  
 <span data-ttu-id="f5d96-114">`COR_HEAPOBJECT.type` Pole je identifikátor vnořené rozhraní modelu COM počítaného odkazy.</span><span class="sxs-lookup"><span data-stu-id="f5d96-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="f5d96-115">Tento odkaz musí být vydán volající `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="f5d96-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5d96-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5d96-116">Requirements</span></span>  
 <span data-ttu-id="f5d96-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5d96-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5d96-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5d96-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5d96-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5d96-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5d96-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5d96-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d96-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5d96-121">See also</span></span>

- [<span data-ttu-id="f5d96-122">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5d96-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [<span data-ttu-id="f5d96-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f5d96-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
