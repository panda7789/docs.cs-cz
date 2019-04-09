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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 221752b537cd3a890ad646290a64a7022692f625
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173937"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="b9acc-102">ICorProfilerObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b9acc-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="b9acc-103">Získá zadaný počet souvislých objekty z sekvenční kolekcí objektů, od aktuální pozice čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="b9acc-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9acc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9acc-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9acc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9acc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b9acc-106">[in] Počet objektů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="b9acc-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="b9acc-107">[out] Pole `ObjectID` hodnot, z nichž každý představuje načtený objekt.</span><span class="sxs-lookup"><span data-stu-id="b9acc-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b9acc-108">[out] Ukazatel na počet skutečně vrácených v prvků `objects` pole.</span><span class="sxs-lookup"><span data-stu-id="b9acc-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9acc-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9acc-109">Requirements</span></span>  
 <span data-ttu-id="b9acc-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9acc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9acc-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9acc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9acc-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9acc-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b9acc-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b9acc-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b9acc-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9acc-114">See also</span></span>

- [<span data-ttu-id="b9acc-115">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9acc-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
