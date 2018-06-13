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
ms.openlocfilehash: 01e52385f1a94ffb9682bdbe92e5c95e9870611e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416800"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="28208-102">ICorDebugGCReferenceEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="28208-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="28208-103">Získá zadaný počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instancí, které obsahují informace o objektech, které budou uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="28208-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28208-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28208-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28208-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28208-105">Parameters</span></span>  
 <span data-ttu-id="28208-106">celt</span><span class="sxs-lookup"><span data-stu-id="28208-106">celt</span></span>  
 <span data-ttu-id="28208-107">[v] Počet kořeny mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="28208-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="28208-108">kořeny</span><span class="sxs-lookup"><span data-stu-id="28208-108">roots</span></span>  
 <span data-ttu-id="28208-109">[out] Ukazatele, každý z nich odkazuje na pole [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekt, který reprezentuje kořen objekt tak, aby se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="28208-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="28208-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="28208-110">pceltFetched</span></span>  
 <span data-ttu-id="28208-111">[out] Ukazatel na počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekty ve skutečnosti, vrátí se v `roots`.</span><span class="sxs-lookup"><span data-stu-id="28208-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="28208-112">Tato hodnota může být `null` Pokud `celt` je 1.</span><span class="sxs-lookup"><span data-stu-id="28208-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28208-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28208-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28208-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28208-114">Requirements</span></span>  
 <span data-ttu-id="28208-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28208-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28208-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28208-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28208-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28208-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28208-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28208-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28208-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="28208-119">See Also</span></span>  
 [<span data-ttu-id="28208-120">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28208-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [<span data-ttu-id="28208-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="28208-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
