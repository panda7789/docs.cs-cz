---
title: "ICorProfilerInfo::GetModuleInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8309b57f2940805e23010feac17b6d37f1a58af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="043e5-102">ICorProfilerInfo::GetModuleInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="043e5-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="043e5-103">Zadaný modul ID vrátí název souboru modulu a ID modulu nadřazené sestavení.</span><span class="sxs-lookup"><span data-stu-id="043e5-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="043e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="043e5-104">Syntax</span></span>  
  
```  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="043e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="043e5-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="043e5-106">[v] ID modulu, pro které budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="043e5-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="043e5-107">[out] Základní adresa, kdy je načíst modul.</span><span class="sxs-lookup"><span data-stu-id="043e5-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="043e5-108">[v] Délka ve znacích, nástroje `szName` návratové vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="043e5-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="043e5-109">[out] Ukazatel na celkový počet znaků názvu souboru modulu, která je vrácena.</span><span class="sxs-lookup"><span data-stu-id="043e5-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="043e5-110">[out] Zadaný volající široká znaková vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="043e5-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="043e5-111">Po návratu metody obsahuje tento vyrovnávací paměť názvu souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="043e5-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="043e5-112">[out] Ukazatel na ID nadřazeného sestavení modulu.</span><span class="sxs-lookup"><span data-stu-id="043e5-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="043e5-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="043e5-113">Remarks</span></span>  
 <span data-ttu-id="043e5-114">Pro dynamické moduly `szName` parametr je řetězec prázdný, a základní adresa je 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="043e5-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="043e5-115">I když `GetModuleInfo` metoda může být volána při ID modulu existuje, ID nadřazeného sestavení nebudete mít k dispozici, dokud neobdrží profileru [icorprofilercallback::moduleattachedtoassembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="043e5-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="043e5-116">Když `GetModuleInfo` vrátí, musíte ověřit, že `szName` vyrovnávací paměť byla dostatečně velký pro obsahovat úplný název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="043e5-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="043e5-117">K tomuto účelu porovnat hodnotu, `pcchName` body s hodnotou `cchName` parametr.</span><span class="sxs-lookup"><span data-stu-id="043e5-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="043e5-118">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělit větší `szName` vyrovnávací paměti, aktualizujte `cchName` s novou, větší velikost a volání `GetModuleInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="043e5-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="043e5-119">Alternativně můžete nejdřív volat `GetModuleInfo` s nulovou délkou `szName` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="043e5-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="043e5-120">Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcchName` a volání `GetModuleInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="043e5-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="043e5-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="043e5-121">Requirements</span></span>  
 <span data-ttu-id="043e5-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="043e5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="043e5-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="043e5-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="043e5-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="043e5-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="043e5-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="043e5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="043e5-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="043e5-126">See Also</span></span>  
 [<span data-ttu-id="043e5-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="043e5-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="043e5-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="043e5-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="043e5-129">Profilace</span><span class="sxs-lookup"><span data-stu-id="043e5-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [<span data-ttu-id="043e5-130">GetModuleInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="043e5-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
