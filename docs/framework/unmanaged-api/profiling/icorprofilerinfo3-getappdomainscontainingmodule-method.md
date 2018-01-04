---
title: "ICorProfilerInfo3::GetAppDomainsContainingModule – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa0aa6620f8465154ac31586618af3fe36f3dfe4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="57ab2-102">ICorProfilerInfo3::GetAppDomainsContainingModule – metoda</span><span class="sxs-lookup"><span data-stu-id="57ab2-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="57ab2-103">Získá identifikátory aplikační domény, ve kterých byl načten daného modulu.</span><span class="sxs-lookup"><span data-stu-id="57ab2-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ab2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57ab2-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57ab2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57ab2-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="57ab2-106">[v] ID modulu načíst.</span><span class="sxs-lookup"><span data-stu-id="57ab2-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="57ab2-107">[v] Velikost `appDomainIds` pole.</span><span class="sxs-lookup"><span data-stu-id="57ab2-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="57ab2-108">[out] Ukazatel na celkový počet vrácených elementy.</span><span class="sxs-lookup"><span data-stu-id="57ab2-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="57ab2-109">[out] Pole hodnoty ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="57ab2-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57ab2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57ab2-110">Remarks</span></span>  
 <span data-ttu-id="57ab2-111">Metoda používá volající přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="57ab2-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57ab2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57ab2-112">Requirements</span></span>  
 <span data-ttu-id="57ab2-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57ab2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57ab2-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="57ab2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57ab2-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57ab2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57ab2-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57ab2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ab2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="57ab2-117">See Also</span></span>  
 [<span data-ttu-id="57ab2-118">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57ab2-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="57ab2-119">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57ab2-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="57ab2-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="57ab2-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="57ab2-121">Profilace</span><span class="sxs-lookup"><span data-stu-id="57ab2-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
