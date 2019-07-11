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
ms.openlocfilehash: 8c938c7c51c867d8e8d8d23390a3c16a23084fbc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775019"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="6d30d-102">ICorProfilerObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="6d30d-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="6d30d-103">Získá zadaný počet souvislých objekty z sekvenční kolekcí objektů, od aktuální pozice čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="6d30d-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d30d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d30d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d30d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d30d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6d30d-106">[in] Počet objektů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="6d30d-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6d30d-107">[out] Pole `ObjectID` hodnot, z nichž každý představuje načtený objekt.</span><span class="sxs-lookup"><span data-stu-id="6d30d-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6d30d-108">[out] Ukazatel na počet skutečně vrácených v prvků `objects` pole.</span><span class="sxs-lookup"><span data-stu-id="6d30d-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d30d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d30d-109">Requirements</span></span>  
 <span data-ttu-id="6d30d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d30d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d30d-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d30d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d30d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d30d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d30d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d30d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d30d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d30d-114">See also</span></span>

- [<span data-ttu-id="6d30d-115">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d30d-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
