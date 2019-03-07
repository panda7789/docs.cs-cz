---
title: ICorDebugILCode::GetEHClauses – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d9ae1abc97d348dced9e4a21236c70658a9141
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488133"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="1931f-102">ICorDebugILCode::GetEHClauses – metoda</span><span class="sxs-lookup"><span data-stu-id="1931f-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="1931f-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="1931f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1931f-104">Vrací ukazatel na seznam klauzulí (EH), které jsou definovány pro tento (IL intermediate language) pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="1931f-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1931f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1931f-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1931f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1931f-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="1931f-107">[in] Kapacita úložiště `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="1931f-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="1931f-108">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="1931f-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="1931f-109">[out] Počet klauzule, které informace jsou zapsány do `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="1931f-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="1931f-110">Klauzule</span><span class="sxs-lookup"><span data-stu-id="1931f-110">clauses</span></span>  
 <span data-ttu-id="1931f-111">[out] Pole [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objektů, které obsahují informace o definovaných pro tento IL klauzulím zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="1931f-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1931f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1931f-112">Remarks</span></span>  
 <span data-ttu-id="1931f-113">Pokud `cClauses` je 0 a `pcClauses` jinou hodnotu než**null**, `pcClauses` je nastavena na počet dostupných klauzulím zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="1931f-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="1931f-114">Pokud `cClauses` je nenulová, představuje kapacitu úložiště `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="1931f-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="1931f-115">Po návratu metody `clauses` obsahuje určitý počet `cClauses` položky, a `pcClauses` je nastavena na počet aktuálně zapsaných do klauzule `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="1931f-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1931f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1931f-116">Requirements</span></span>  
 <span data-ttu-id="1931f-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1931f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1931f-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1931f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1931f-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1931f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1931f-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1931f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1931f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1931f-121">See also</span></span>
- [<span data-ttu-id="1931f-122">ICorDebugILCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1931f-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="1931f-123">CorDebugEHClause – struktura</span><span class="sxs-lookup"><span data-stu-id="1931f-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [<span data-ttu-id="1931f-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1931f-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
