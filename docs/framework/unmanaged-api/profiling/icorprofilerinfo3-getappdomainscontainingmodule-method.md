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
ms.openlocfilehash: 93c042d760eab4bcb1846701ad92ac38cb473c69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449733"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="5b397-102">ICorProfilerInfo3::GetAppDomainsContainingModule – metoda</span><span class="sxs-lookup"><span data-stu-id="5b397-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="5b397-103">Získá identifikátory domén aplikace, ve kterých byl daný modul načten.</span><span class="sxs-lookup"><span data-stu-id="5b397-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b397-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b397-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b397-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b397-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="5b397-106">pro ID načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="5b397-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="5b397-107">pro Velikost pole `appDomainIds`.</span><span class="sxs-lookup"><span data-stu-id="5b397-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="5b397-108">mimo Ukazatel na celkový počet vrácených elementů.</span><span class="sxs-lookup"><span data-stu-id="5b397-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="5b397-109">mimo Pole hodnot ID aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="5b397-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b397-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b397-110">Remarks</span></span>  
 <span data-ttu-id="5b397-111">Metoda používá vyrovnávací paměti přidělené volajícímu.</span><span class="sxs-lookup"><span data-stu-id="5b397-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b397-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b397-112">Requirements</span></span>  
 <span data-ttu-id="5b397-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b397-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b397-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5b397-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b397-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5b397-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b397-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b397-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b397-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b397-117">See also</span></span>

- [<span data-ttu-id="5b397-118">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b397-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="5b397-119">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b397-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="5b397-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5b397-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5b397-121">Profilace</span><span class="sxs-lookup"><span data-stu-id="5b397-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
