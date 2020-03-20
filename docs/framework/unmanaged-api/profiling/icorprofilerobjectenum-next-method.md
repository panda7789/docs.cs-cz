---
title: ICorProfilerObjectEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type:
- apiref
ms.openlocfilehash: b6e26d1538cab30db66e887aee89b8fbae501bdb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177004"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="58cbc-102">ICorProfilerObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="58cbc-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="58cbc-103">Získá zadaný počet souvislých objektů z sekvenční kolekce objektů, počínaje aktuální pozici čítače v pořadí.</span><span class="sxs-lookup"><span data-stu-id="58cbc-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58cbc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58cbc-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58cbc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58cbc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="58cbc-106">[v] Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="58cbc-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="58cbc-107">[out] Pole `ObjectID` hodnot, z nichž každá představuje načtený objekt.</span><span class="sxs-lookup"><span data-stu-id="58cbc-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="58cbc-108">[out] Ukazatel na počet prvků skutečně vrácených v `objects` poli.</span><span class="sxs-lookup"><span data-stu-id="58cbc-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58cbc-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58cbc-109">Requirements</span></span>  
 <span data-ttu-id="58cbc-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58cbc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58cbc-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58cbc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58cbc-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58cbc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58cbc-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58cbc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58cbc-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="58cbc-114">See also</span></span>

- [<span data-ttu-id="58cbc-115">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58cbc-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
