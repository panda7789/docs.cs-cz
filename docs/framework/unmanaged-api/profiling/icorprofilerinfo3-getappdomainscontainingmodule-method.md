---
title: ICorProfilerInfo3::GetAppDomainsContainingModule – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ed9a9a91f4e802e6251add965306cf13f19139e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494230"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="342f8-102">ICorProfilerInfo3::GetAppDomainsContainingModule – metoda</span><span class="sxs-lookup"><span data-stu-id="342f8-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="342f8-103">Získá identifikátory aplikační domény, ve kterých daný modul byl načten.</span><span class="sxs-lookup"><span data-stu-id="342f8-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="342f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="342f8-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="342f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="342f8-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="342f8-106">[in] ID načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="342f8-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="342f8-107">[in] Velikost `appDomainIds` pole.</span><span class="sxs-lookup"><span data-stu-id="342f8-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="342f8-108">[out] Ukazatel na celkový počet vrácených prvků.</span><span class="sxs-lookup"><span data-stu-id="342f8-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="342f8-109">[out] Pole hodnoty ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="342f8-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="342f8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="342f8-110">Remarks</span></span>  
 <span data-ttu-id="342f8-111">Metoda používá volající přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="342f8-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="342f8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="342f8-112">Requirements</span></span>  
 <span data-ttu-id="342f8-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="342f8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="342f8-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="342f8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="342f8-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="342f8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="342f8-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="342f8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="342f8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="342f8-117">See also</span></span>
- [<span data-ttu-id="342f8-118">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="342f8-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="342f8-119">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="342f8-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="342f8-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="342f8-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="342f8-121">Profilace</span><span class="sxs-lookup"><span data-stu-id="342f8-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
