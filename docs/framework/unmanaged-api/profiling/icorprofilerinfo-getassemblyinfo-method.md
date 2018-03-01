---
title: "ICorProfilerInfo::GetAssemblyInfo – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3ac5bd35d12bb4c9d9308dcdff3e1fb8385f6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="fbcfe-102">ICorProfilerInfo::GetAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="fbcfe-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="fbcfe-103">Přijímá ID sestavení a vrátí název sestavení a ID jeho manifestu modul.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbcfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbcfe-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="fbcfe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbcfe-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="fbcfe-106">[v] Identifikátor sestavení.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="fbcfe-107">[v] Délka ve znacích, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fbcfe-108">[out] Ukazatel na celkový počet znaků názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="fbcfe-109">[out] Zadaný volající široká znaková vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="fbcfe-110">Když funkce vrátí hodnotu, bude obsahovat název sestavení.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="fbcfe-111">[out] Ukazatel na ID doménu aplikace, který obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="fbcfe-112">[out] Ukazatel na ID manifestu modulu sestavení.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbcfe-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbcfe-113">Remarks</span></span>  
 <span data-ttu-id="fbcfe-114">Po návratu tato metoda, musíte se ověřit, že `szName` vyrovnávací paměť byla dostatečně velký pro obsahovat úplný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="fbcfe-115">K tomuto účelu porovnat hodnotu, `pcchName` body s hodnotou `cchName` parametr.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="fbcfe-116">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělit větší `szName` vyrovnávací paměti, aktualizujte `cchName` s novou, větší velikost a volání `GetAssemblyInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="fbcfe-117">Alternativně můžete nejdřív volat `GetAssemblyInfo` s nulovou délkou `szName` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="fbcfe-118">Potom můžete upravit velikost vyrovnávací paměti na základě hodnoty, vrátí se v `pcchName` a volání `GetAssemblyInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="fbcfe-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbcfe-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbcfe-119">Requirements</span></span>  
 <span data-ttu-id="fbcfe-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbcfe-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbcfe-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fbcfe-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fbcfe-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbcfe-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbcfe-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbcfe-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbcfe-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbcfe-124">See Also</span></span>  
 [<span data-ttu-id="fbcfe-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbcfe-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="fbcfe-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="fbcfe-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="fbcfe-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="fbcfe-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
