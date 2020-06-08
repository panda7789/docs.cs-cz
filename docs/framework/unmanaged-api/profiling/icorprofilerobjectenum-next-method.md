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
ms.openlocfilehash: 850f05520e4146b5016bb574f02aa800dfcaaf32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494576"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="bb6ec-102">ICorProfilerObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="bb6ec-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="bb6ec-103">Získá zadaný počet souvislých objektů ze sekvenční kolekce objektů počínaje aktuální pozicí čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="bb6ec-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb6ec-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb6ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb6ec-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bb6ec-106">pro Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="bb6ec-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="bb6ec-107">mimo Pole `ObjectID` hodnot, z nichž každý představuje načtený objekt.</span><span class="sxs-lookup"><span data-stu-id="bb6ec-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bb6ec-108">mimo Ukazatel na počet prvků skutečně vrácených v `objects` poli.</span><span class="sxs-lookup"><span data-stu-id="bb6ec-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb6ec-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb6ec-109">Requirements</span></span>  
 <span data-ttu-id="bb6ec-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb6ec-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6ec-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bb6ec-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb6ec-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bb6ec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb6ec-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6ec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6ec-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb6ec-114">See also</span></span>

- [<span data-ttu-id="bb6ec-115">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb6ec-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
