---
title: "ICorProfilerModuleEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fca8a0f999ccc497c1929faa6cead04a1ec2774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="b6483-102">ICorProfilerModuleEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b6483-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="b6483-103">Získá zadaný počet souvislý moduly z sekvenční kolekce modulů, začínající na enumerátor na aktuální pozici v pořadí.</span><span class="sxs-lookup"><span data-stu-id="b6483-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6483-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6483-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6483-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6483-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b6483-106">[v] Počet modulů pro načtení.</span><span class="sxs-lookup"><span data-stu-id="b6483-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="b6483-107">[out] Pole `ModuleID` hodnoty, z nichž každý představuje modul načtena.</span><span class="sxs-lookup"><span data-stu-id="b6483-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b6483-108">[out] Ukazatel na počet elementů ve skutečnosti, vrátí se v `ids` pole.</span><span class="sxs-lookup"><span data-stu-id="b6483-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6483-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b6483-109">Return Value</span></span>  
 <span data-ttu-id="b6483-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="b6483-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b6483-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6483-111">HRESULT</span></span>|<span data-ttu-id="b6483-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b6483-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6483-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6483-113">S_OK</span></span>|<span data-ttu-id="b6483-114">`celt`elementy byly vráceny.</span><span class="sxs-lookup"><span data-stu-id="b6483-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="b6483-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b6483-115">S_FALSE</span></span>|<span data-ttu-id="b6483-116">Méně než `celt` byly vráceny elementy, které označuje, že výčtu je kompletní.</span><span class="sxs-lookup"><span data-stu-id="b6483-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6483-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6483-117">Requirements</span></span>  
 <span data-ttu-id="b6483-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6483-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6483-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6483-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6483-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6483-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6483-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6483-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6483-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6483-122">See Also</span></span>  
 [<span data-ttu-id="b6483-123">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6483-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="b6483-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b6483-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
