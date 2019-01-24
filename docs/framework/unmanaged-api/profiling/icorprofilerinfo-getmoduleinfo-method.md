---
title: ICorProfilerInfo::GetModuleInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9abe342a795f8f511fce0504c7839411079c1c75
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742537"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="042a3-102">ICorProfilerInfo::GetModuleInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="042a3-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="042a3-103">Dané ID modulu vrátí název souboru modulu a ID modulu nadřazené sestavení.</span><span class="sxs-lookup"><span data-stu-id="042a3-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="042a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="042a3-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="042a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="042a3-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="042a3-106">[in] ID modulu, pro kterou budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="042a3-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="042a3-107">[out] Základní adresa, načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="042a3-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="042a3-108">[in] Délka ve znacích, nástroje `szName` návratové vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="042a3-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="042a3-109">[out] Celkový počet znaků z modulů název souboru, který je vrácen ukazatel.</span><span class="sxs-lookup"><span data-stu-id="042a3-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="042a3-110">[out] Pokud volající širokého znaku vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="042a3-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="042a3-111">Po návratu metody obsahuje tuto vyrovnávací paměť názvu souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="042a3-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="042a3-112">[out] Ukazatel na ID nadřazeného sestavení modulu.</span><span class="sxs-lookup"><span data-stu-id="042a3-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="042a3-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="042a3-113">Remarks</span></span>  
 <span data-ttu-id="042a3-114">Pro dynamické moduly `szName` parametru je prázdný řetězec a je základní adresa 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="042a3-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="042a3-115">I když `GetModuleInfo` metoda může být volána jako ID modulu existuje, ID nadřazeného sestavení nebude k dispozici, dokud profiler obdrží [icorprofilercallback::moduleattachedtoassembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="042a3-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="042a3-116">Když `GetModuleInfo` vrátí, musíte ověřit, že `szName` vyrovnávací paměť je dostatečně velký, aby obsahovat úplný název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="042a3-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="042a3-117">K tomuto účelu porovnat hodnoty, které `pcchName` odkazuje na hodnotu `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="042a3-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="042a3-118">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší `szName` vyrovnávací paměti, aktualizujte `cchName` nové, větší velikosti a volání `GetModuleInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="042a3-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="042a3-119">Alternativně můžete nejprve volat `GetModuleInfo` s nulovou délkou `szName` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="042a3-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="042a3-120">Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcchName` a volat `GetModuleInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="042a3-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="042a3-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="042a3-121">Requirements</span></span>  
 <span data-ttu-id="042a3-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="042a3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="042a3-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="042a3-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="042a3-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="042a3-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="042a3-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="042a3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042a3-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="042a3-126">See also</span></span>
- [<span data-ttu-id="042a3-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="042a3-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="042a3-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="042a3-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="042a3-129">Profilace</span><span class="sxs-lookup"><span data-stu-id="042a3-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [<span data-ttu-id="042a3-130">GetModuleInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="042a3-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
