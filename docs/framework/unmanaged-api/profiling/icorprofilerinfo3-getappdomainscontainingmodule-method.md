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
ms.openlocfilehash: b5658ac87c7a938381639442216df03853f02998
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195784"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="892e9-102">ICorProfilerInfo3::GetAppDomainsContainingModule – metoda</span><span class="sxs-lookup"><span data-stu-id="892e9-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="892e9-103">Získá identifikátory aplikační domény, ve kterých daný modul byl načten.</span><span class="sxs-lookup"><span data-stu-id="892e9-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="892e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="892e9-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="892e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="892e9-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="892e9-106">[in] ID načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="892e9-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="892e9-107">[in] Velikost `appDomainIds` pole.</span><span class="sxs-lookup"><span data-stu-id="892e9-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="892e9-108">[out] Ukazatel na celkový počet vrácených prvků.</span><span class="sxs-lookup"><span data-stu-id="892e9-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="892e9-109">[out] Pole hodnoty ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="892e9-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="892e9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="892e9-110">Remarks</span></span>  
 <span data-ttu-id="892e9-111">Metoda používá volající přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="892e9-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="892e9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="892e9-112">Requirements</span></span>  
 <span data-ttu-id="892e9-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="892e9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="892e9-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="892e9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="892e9-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="892e9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="892e9-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="892e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="892e9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="892e9-117">See also</span></span>

- [<span data-ttu-id="892e9-118">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="892e9-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="892e9-119">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="892e9-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="892e9-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="892e9-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="892e9-121">Profilace</span><span class="sxs-lookup"><span data-stu-id="892e9-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
