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
ms.openlocfilehash: 8615deb2e42b039120d97b3eb5af23beb31b0808
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502844"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="703b6-102">ICorProfilerInfo3::GetAppDomainsContainingModule – metoda</span><span class="sxs-lookup"><span data-stu-id="703b6-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="703b6-103">Získá identifikátory domén aplikace, ve kterých byl daný modul načten.</span><span class="sxs-lookup"><span data-stu-id="703b6-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="703b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="703b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="703b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="703b6-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="703b6-106">pro ID načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="703b6-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="703b6-107">pro Velikost `appDomainIds` pole.</span><span class="sxs-lookup"><span data-stu-id="703b6-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="703b6-108">mimo Ukazatel na celkový počet vrácených elementů.</span><span class="sxs-lookup"><span data-stu-id="703b6-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="703b6-109">mimo Pole hodnot ID aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="703b6-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="703b6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="703b6-110">Remarks</span></span>  
 <span data-ttu-id="703b6-111">Metoda používá vyrovnávací paměti přidělené volajícímu.</span><span class="sxs-lookup"><span data-stu-id="703b6-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="703b6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="703b6-112">Requirements</span></span>  
 <span data-ttu-id="703b6-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="703b6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="703b6-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="703b6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="703b6-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="703b6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="703b6-116">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="703b6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703b6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="703b6-117">See also</span></span>

- [<span data-ttu-id="703b6-118">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="703b6-118">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="703b6-119">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="703b6-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="703b6-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="703b6-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="703b6-121">Profilace</span><span class="sxs-lookup"><span data-stu-id="703b6-121">Profiling</span></span>](index.md)
