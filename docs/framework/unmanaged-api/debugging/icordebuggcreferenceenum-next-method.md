---
title: ICorDebugGCReferenceEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f76b727511ad604c407fb2998a5ecea26f91c49
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481358"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="b3dc1-102">ICorDebugGCReferenceEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b3dc1-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="b3dc1-103">Získá zadaný počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instancí, které obsahují informace o objektech, které bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="b3dc1-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3dc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3dc1-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3dc1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3dc1-105">Parameters</span></span>  
 <span data-ttu-id="b3dc1-106">celt</span><span class="sxs-lookup"><span data-stu-id="b3dc1-106">celt</span></span>  
 <span data-ttu-id="b3dc1-107">[in] Počet kořenových adresářů, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="b3dc1-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="b3dc1-108">kořeny</span><span class="sxs-lookup"><span data-stu-id="b3dc1-108">roots</span></span>  
 <span data-ttu-id="b3dc1-109">[out] Pole ukazatelů, každý z nich odkazuje [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekt, který reprezentuje kořenový objekt bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="b3dc1-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="b3dc1-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="b3dc1-110">pceltFetched</span></span>  
 <span data-ttu-id="b3dc1-111">[out] Ukazatel na počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objektů skutečně vrácených v `roots`.</span><span class="sxs-lookup"><span data-stu-id="b3dc1-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="b3dc1-112">Tato hodnota může být `null` Pokud `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="b3dc1-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3dc1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3dc1-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3dc1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3dc1-114">Requirements</span></span>  
 <span data-ttu-id="b3dc1-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3dc1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3dc1-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3dc1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3dc1-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3dc1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3dc1-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3dc1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3dc1-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3dc1-119">See also</span></span>
- [<span data-ttu-id="b3dc1-120">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3dc1-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="b3dc1-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b3dc1-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
