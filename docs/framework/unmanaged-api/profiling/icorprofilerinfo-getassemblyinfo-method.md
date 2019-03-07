---
title: ICorProfilerInfo::GetAssemblyInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06594b2c369f02cfecb555af173284b094935c46
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490096"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="5cbcb-102">ICorProfilerInfo::GetAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="5cbcb-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="5cbcb-103">Přijímá ID sestavení a vrátí název sestavení a ID jeho manifestu modulu.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cbcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cbcb-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cbcb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cbcb-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="5cbcb-106">[in] Identifikátor sestavení.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5cbcb-107">[in] Délka ve znacích, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5cbcb-108">[out] Ukazatel na celkový počet znaků názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="5cbcb-109">[out] Pokud volající širokého znaku vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="5cbcb-110">Po návratu funkce bude obsahovat název sestavení.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="5cbcb-111">[out] Ukazatel na ID domény aplikace, který obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="5cbcb-112">[out] Ukazatel na ID modul manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cbcb-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cbcb-113">Remarks</span></span>  
 <span data-ttu-id="5cbcb-114">Po návratu tato metoda je nutné ověřit, `szName` vyrovnávací paměť je dostatečně velký, aby obsahoval úplný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="5cbcb-115">K tomuto účelu porovnat hodnoty, které `pcchName` odkazuje na hodnotu `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="5cbcb-116">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší `szName` vyrovnávací paměti, aktualizujte `cchName` nové, větší velikosti a volání `GetAssemblyInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="5cbcb-117">Alternativně můžete nejprve volat `GetAssemblyInfo` s nulovou délkou `szName` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="5cbcb-118">Potom můžete upravit velikost vyrovnávací paměti na základě hodnoty vráceny v `pcchName` a volat `GetAssemblyInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="5cbcb-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cbcb-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cbcb-119">Requirements</span></span>  
 <span data-ttu-id="5cbcb-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cbcb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cbcb-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5cbcb-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5cbcb-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cbcb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cbcb-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cbcb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cbcb-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cbcb-124">See also</span></span>
- [<span data-ttu-id="5cbcb-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cbcb-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5cbcb-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5cbcb-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5cbcb-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="5cbcb-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
