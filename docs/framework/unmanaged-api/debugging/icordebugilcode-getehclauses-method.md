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
ms.openlocfilehash: e1fd68cd079b381d941d416831133c54e49ac48a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210381"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="b18ef-102">ICorDebugILCode::GetEHClauses – metoda</span><span class="sxs-lookup"><span data-stu-id="b18ef-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="b18ef-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="b18ef-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b18ef-104">Vrátí ukazatel na seznam klauzulí zpracování výjimek (EH), které jsou definovány pro tento převodní jazyk (IL).</span><span class="sxs-lookup"><span data-stu-id="b18ef-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b18ef-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b18ef-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b18ef-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b18ef-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="b18ef-107">pro Kapacita úložiště `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="b18ef-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="b18ef-108">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="b18ef-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="b18ef-109">mimo Počet klauzulí, o které se zapisují informace do `clauses` pole</span><span class="sxs-lookup"><span data-stu-id="b18ef-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="b18ef-110">platný</span><span class="sxs-lookup"><span data-stu-id="b18ef-110">clauses</span></span>  
 <span data-ttu-id="b18ef-111">mimo Pole objektů [CorDebugEHClause](cordebugehclause-structure.md) , které obsahují informace o klauzulích zpracování výjimek definovaných pro tento Il.</span><span class="sxs-lookup"><span data-stu-id="b18ef-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b18ef-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b18ef-112">Remarks</span></span>  
 <span data-ttu-id="b18ef-113">Pokud `cClauses` je 0 a `pcClauses` není**null**, `pcClauses` je nastaveno na počet dostupných klauzulí zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="b18ef-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="b18ef-114">Pokud `cClauses` je hodnota nenulová, představuje kapacitu úložiště `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="b18ef-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="b18ef-115">Když metoda vrátí, `clauses` obsahuje maximální počet `cClauses` položek a `pcClauses` je nastaven na počet klauzulí, které jsou ve skutečnosti zapsány do `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="b18ef-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b18ef-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b18ef-116">Requirements</span></span>  
 <span data-ttu-id="b18ef-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b18ef-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b18ef-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b18ef-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b18ef-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b18ef-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b18ef-120">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b18ef-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b18ef-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b18ef-121">See also</span></span>

- [<span data-ttu-id="b18ef-122">Rozhraní ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="b18ef-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="b18ef-123">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="b18ef-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="b18ef-124">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b18ef-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
