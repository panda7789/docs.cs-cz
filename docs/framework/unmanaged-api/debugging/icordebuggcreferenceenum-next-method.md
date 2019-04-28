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
ms.openlocfilehash: 33ad221f2a05357484d0877b6306d78e3864eff6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651595"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="a01fd-102">ICorDebugGCReferenceEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a01fd-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="a01fd-103">Získá zadaný počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instancí, které obsahují informace o objektech, které bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="a01fd-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a01fd-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a01fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a01fd-105">Parameters</span></span>  
 <span data-ttu-id="a01fd-106">celt</span><span class="sxs-lookup"><span data-stu-id="a01fd-106">celt</span></span>  
 <span data-ttu-id="a01fd-107">[in] Počet kořenových adresářů, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="a01fd-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="a01fd-108">kořeny</span><span class="sxs-lookup"><span data-stu-id="a01fd-108">roots</span></span>  
 <span data-ttu-id="a01fd-109">[out] Pole ukazatelů, každý z nich odkazuje [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekt, který reprezentuje kořenový objekt bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="a01fd-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="a01fd-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="a01fd-110">pceltFetched</span></span>  
 <span data-ttu-id="a01fd-111">[out] Ukazatel na počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objektů skutečně vrácených v `roots`.</span><span class="sxs-lookup"><span data-stu-id="a01fd-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="a01fd-112">Tato hodnota může být `null` Pokud `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="a01fd-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a01fd-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a01fd-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a01fd-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a01fd-114">Requirements</span></span>  
 <span data-ttu-id="a01fd-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a01fd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a01fd-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a01fd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a01fd-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a01fd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a01fd-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a01fd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01fd-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a01fd-119">See also</span></span>

- [<span data-ttu-id="a01fd-120">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a01fd-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="a01fd-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a01fd-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
