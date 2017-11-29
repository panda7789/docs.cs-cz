---
title: "ICorDebugGCReferenceEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGCReferenceEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55a02b88076d6097415d108d58f74565d1f426de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="22830-102">ICorDebugGCReferenceEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="22830-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="22830-103">Získá zadaný počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instancí, které obsahují informace o objektech, které budou uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="22830-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22830-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22830-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22830-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22830-105">Parameters</span></span>  
 <span data-ttu-id="22830-106">celt</span><span class="sxs-lookup"><span data-stu-id="22830-106">celt</span></span>  
 <span data-ttu-id="22830-107">[v] Počet kořeny mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="22830-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="22830-108">kořeny</span><span class="sxs-lookup"><span data-stu-id="22830-108">roots</span></span>  
 <span data-ttu-id="22830-109">[out] Ukazatele, každý z nich odkazuje na pole [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekt, který reprezentuje kořen objekt tak, aby se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="22830-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="22830-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="22830-110">pceltFetched</span></span>  
 <span data-ttu-id="22830-111">[out] Ukazatel na počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekty ve skutečnosti, vrátí se v `roots`.</span><span class="sxs-lookup"><span data-stu-id="22830-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="22830-112">Tato hodnota může být `null` Pokud `celt` je 1.</span><span class="sxs-lookup"><span data-stu-id="22830-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22830-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22830-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22830-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22830-114">Requirements</span></span>  
 <span data-ttu-id="22830-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22830-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22830-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22830-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22830-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22830-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22830-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22830-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22830-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="22830-119">See Also</span></span>  
 [<span data-ttu-id="22830-120">ICorDebugGCReferenceEnum – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="22830-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [<span data-ttu-id="22830-121">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="22830-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
