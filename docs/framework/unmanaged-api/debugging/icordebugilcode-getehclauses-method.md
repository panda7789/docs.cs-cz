---
title: "ICorDebugILCode::GetEHClauses – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32b3a7bf7edaf15e44ea65e2d3b4f5037add8d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="84f0f-102">ICorDebugILCode::GetEHClauses – metoda</span><span class="sxs-lookup"><span data-stu-id="84f0f-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="84f0f-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="84f0f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="84f0f-104">Vrací ukazatel na seznam klauzule (EH), které jsou definované pro tento zprostředkující jazyk (IL) zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="84f0f-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f0f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84f0f-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84f0f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="84f0f-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="84f0f-107">[v] Úložnou kapacitu `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="84f0f-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="84f0f-108">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="84f0f-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="84f0f-109">[out] Číslo, pro které informace jsou zapsány do klauzule `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="84f0f-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="84f0f-110">klauzule</span><span class="sxs-lookup"><span data-stu-id="84f0f-110">clauses</span></span>  
 <span data-ttu-id="84f0f-111">[out] Pole [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objekty, které obsahují informace o zpracování klauzule definované pro tento IL výjimek.</span><span class="sxs-lookup"><span data-stu-id="84f0f-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84f0f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84f0f-112">Remarks</span></span>  
 <span data-ttu-id="84f0f-113">Pokud `cClauses` je 0 a `pcClauses` jinou hodnotu než**null**, `pcClauses` je nastaven na počet dostupných zpracování klauzule výjimek.</span><span class="sxs-lookup"><span data-stu-id="84f0f-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="84f0f-114">Pokud `cClauses` je nulová, představuje kapacitu úložiště `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="84f0f-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="84f0f-115">Po návratu metody `clauses` obsahuje maximálně `cClauses` položky, a `pcClauses` je nastaven na počet klauzulí ve skutečnosti zapsána do `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="84f0f-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84f0f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84f0f-116">Requirements</span></span>  
 <span data-ttu-id="84f0f-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84f0f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84f0f-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84f0f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84f0f-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84f0f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84f0f-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84f0f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f0f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="84f0f-121">See Also</span></span>  
 [<span data-ttu-id="84f0f-122">ICorDebugILCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84f0f-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="84f0f-123">CorDebugEHClause – struktura</span><span class="sxs-lookup"><span data-stu-id="84f0f-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [<span data-ttu-id="84f0f-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="84f0f-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
