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
ms.openlocfilehash: ac9a4e4b54b302afeae4ede1dd574c15ded3ff12
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788604"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="f4b7b-102">ICorDebugILCode::GetEHClauses – metoda</span><span class="sxs-lookup"><span data-stu-id="f4b7b-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="f4b7b-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="f4b7b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f4b7b-104">Vrátí ukazatel na seznam klauzulí zpracování výjimek (EH), které jsou definovány pro tento převodní jazyk (IL).</span><span class="sxs-lookup"><span data-stu-id="f4b7b-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4b7b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4b7b-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4b7b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4b7b-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="f4b7b-107">pro Kapacita úložiště pole `clauses`.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="f4b7b-108">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="f4b7b-109">mimo Počet klauzulí, o které se zapisují informace do pole `clauses`.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="f4b7b-110">platný</span><span class="sxs-lookup"><span data-stu-id="f4b7b-110">clauses</span></span>  
 <span data-ttu-id="f4b7b-111">mimo Pole objektů [CorDebugEHClause](cordebugehclause-structure.md) , které obsahují informace o klauzulích zpracování výjimek definovaných pro tento Il.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4b7b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4b7b-112">Remarks</span></span>  
 <span data-ttu-id="f4b7b-113">Pokud je `cClauses` 0 a `pcClauses` není**null**, `pcClauses` je nastaveno na počet dostupných klauzulí zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="f4b7b-114">Pokud `cClauses` není nula, představuje kapacitu úložiště `clauses` pole.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="f4b7b-115">Když metoda vrátí, `clauses` obsahuje maximálně `cClauses` položek a `pcClauses` je nastaveno na počet klauzulí vlastněných v poli `clauses`.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4b7b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4b7b-116">Requirements</span></span>  
 <span data-ttu-id="f4b7b-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4b7b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4b7b-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f4b7b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4b7b-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f4b7b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4b7b-120">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4b7b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b7b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-121">See also</span></span>

- [<span data-ttu-id="f4b7b-122">ICorDebugILCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4b7b-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="f4b7b-123">CorDebugEHClause – struktura</span><span class="sxs-lookup"><span data-stu-id="f4b7b-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="f4b7b-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f4b7b-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
