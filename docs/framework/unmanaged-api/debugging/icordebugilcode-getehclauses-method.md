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
ms.openlocfilehash: 6e890629f307e3d3cff11dabdb2db90a5e88ece5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105051"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="7e55e-102">ICorDebugILCode::GetEHClauses – metoda</span><span class="sxs-lookup"><span data-stu-id="7e55e-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="7e55e-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="7e55e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7e55e-104">Vrací ukazatel na seznam klauzulí (EH), které jsou definovány pro tento (IL intermediate language) pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="7e55e-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e55e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e55e-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e55e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e55e-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="7e55e-107">[in] Kapacita úložiště `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="7e55e-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="7e55e-108">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="7e55e-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="7e55e-109">[out] Počet klauzule, které informace jsou zapsány do `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="7e55e-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="7e55e-110">Klauzule</span><span class="sxs-lookup"><span data-stu-id="7e55e-110">clauses</span></span>  
 <span data-ttu-id="7e55e-111">[out] Pole [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objektů, které obsahují informace o definovaných pro tento IL klauzulím zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="7e55e-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e55e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e55e-112">Remarks</span></span>  
 <span data-ttu-id="7e55e-113">Pokud `cClauses` je 0 a `pcClauses` jinou hodnotu než**null**, `pcClauses` je nastavena na počet dostupných klauzulím zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="7e55e-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="7e55e-114">Pokud `cClauses` je nenulová, představuje kapacitu úložiště `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="7e55e-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="7e55e-115">Po návratu metody `clauses` obsahuje určitý počet `cClauses` položky, a `pcClauses` je nastavena na počet aktuálně zapsaných do klauzule `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="7e55e-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e55e-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e55e-116">Requirements</span></span>  
 <span data-ttu-id="7e55e-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e55e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e55e-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e55e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e55e-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e55e-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7e55e-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7e55e-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e55e-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e55e-121">See also</span></span>

- [<span data-ttu-id="7e55e-122">Rozhraní ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="7e55e-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="7e55e-123">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="7e55e-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [<span data-ttu-id="7e55e-124">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e55e-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
