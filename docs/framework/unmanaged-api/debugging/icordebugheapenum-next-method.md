---
title: "ICorDebugHeapEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9869542b04b26fdf343b4112c2f84a26a3061c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="4fda4-102">ICorDebugHeapEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="4fda4-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="4fda4-103">Získá zadaný počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o objektech v haldě spravované.</span><span class="sxs-lookup"><span data-stu-id="4fda4-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fda4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fda4-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fda4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fda4-105">Parameters</span></span>  
 <span data-ttu-id="4fda4-106">celt</span><span class="sxs-lookup"><span data-stu-id="4fda4-106">celt</span></span>  
 <span data-ttu-id="4fda4-107">[v] Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="4fda4-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="4fda4-108">– objekty</span><span class="sxs-lookup"><span data-stu-id="4fda4-108">objects</span></span>  
 <span data-ttu-id="4fda4-109">[out] Ukazatele, každý z nich odkazuje na pole [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekt, který obsahuje informace o objekt na spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="4fda4-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="4fda4-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="4fda4-110">pceltFetched</span></span>  
 <span data-ttu-id="4fda4-111">[out] Ukazatel na počet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty ve skutečnosti, vrátí se v `objects`.</span><span class="sxs-lookup"><span data-stu-id="4fda4-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="4fda4-112">Tato hodnota může být `null` Pokud `celt` je 1.</span><span class="sxs-lookup"><span data-stu-id="4fda4-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fda4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fda4-113">Remarks</span></span>  
 <span data-ttu-id="4fda4-114">`COR_HEAPOBJECT.type` Pole je identifikátor vnořené rozhraní modelu COM počítá odkaz.</span><span class="sxs-lookup"><span data-stu-id="4fda4-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="4fda4-115">Tento odkaz musí být vydán volající `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="4fda4-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fda4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fda4-116">Requirements</span></span>  
 <span data-ttu-id="4fda4-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fda4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fda4-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fda4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fda4-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fda4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fda4-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fda4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fda4-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fda4-121">See Also</span></span>  
 [<span data-ttu-id="4fda4-122">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fda4-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 [<span data-ttu-id="4fda4-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4fda4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
