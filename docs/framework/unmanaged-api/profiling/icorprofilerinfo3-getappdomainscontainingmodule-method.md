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
ms.openlocfilehash: 56221c6b3ac40595e999f2a2a3739f023441c46d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862407"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="ff60c-102">ICorProfilerInfo3::GetAppDomainsContainingModule – metoda</span><span class="sxs-lookup"><span data-stu-id="ff60c-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="ff60c-103">Získá identifikátory domén aplikace, ve kterých byl daný modul načten.</span><span class="sxs-lookup"><span data-stu-id="ff60c-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff60c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff60c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff60c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff60c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ff60c-106">pro ID načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="ff60c-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="ff60c-107">pro Velikost pole `appDomainIds`.</span><span class="sxs-lookup"><span data-stu-id="ff60c-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="ff60c-108">mimo Ukazatel na celkový počet vrácených elementů.</span><span class="sxs-lookup"><span data-stu-id="ff60c-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="ff60c-109">mimo Pole hodnot ID aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="ff60c-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff60c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff60c-110">Remarks</span></span>  
 <span data-ttu-id="ff60c-111">Metoda používá vyrovnávací paměti přidělené volajícímu.</span><span class="sxs-lookup"><span data-stu-id="ff60c-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff60c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff60c-112">Requirements</span></span>  
 <span data-ttu-id="ff60c-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff60c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff60c-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ff60c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff60c-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ff60c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff60c-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff60c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff60c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff60c-117">See also</span></span>

- [<span data-ttu-id="ff60c-118">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff60c-118">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="ff60c-119">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff60c-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ff60c-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ff60c-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ff60c-121">Profilace</span><span class="sxs-lookup"><span data-stu-id="ff60c-121">Profiling</span></span>](index.md)
