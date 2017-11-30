---
title: "ICorProfilerInfo4::GetCodeInfo3 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetCodeInfo3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87a93220bbaf3930f8ac2671efc0f19b2df8aee5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="fe090-102">ICorProfilerInfo4::GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="fe090-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="fe090-103">Získá rozsah nativního kódu přidružené verze překompilovat JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="fe090-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe090-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe090-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe090-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe090-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="fe090-106">[v] ID funkce, ke kterému je přiřazeno nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="fe090-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="fe090-107">[v] Identita překompilovat JIT funkce.</span><span class="sxs-lookup"><span data-stu-id="fe090-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="fe090-108">[v] Velikost `codeInfos` pole.</span><span class="sxs-lookup"><span data-stu-id="fe090-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="fe090-109">[out] Ukazatel na celkový počet [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fe090-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="fe090-110">[out] Zadaný volající vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fe090-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="fe090-111">Po návratu metody obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="fe090-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe090-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe090-112">Remarks</span></span>  
 <span data-ttu-id="fe090-113">`GetCodeInfo3` Metoda je podobná [getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)kromě toho, že se budou získávat překompilovat JIT ID funkce, která obsahuje zadaná IP adresa.</span><span class="sxs-lookup"><span data-stu-id="fe090-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe090-114">`GetCodeInfo3`můžete aktivovat uvolňování paměti, zatímco [getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) nikoli.</span><span class="sxs-lookup"><span data-stu-id="fe090-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="fe090-115">Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fe090-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="fe090-116">Rozsah jsou seřazeny v pořadí podle zvýšení posun Common mezilehlá jazyk (CIL).</span><span class="sxs-lookup"><span data-stu-id="fe090-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="fe090-117">Po `GetCodeInfo3` vrátí, musíte ověřit, že `codeInfos` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="fe090-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="fe090-118">K tomuto účelu porovnat hodnotu `cCodeInfos` s hodnotou `cchName` parametr.</span><span class="sxs-lookup"><span data-stu-id="fe090-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="fe090-119">Pokud `cCodeInfos` dělený velikost [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktura je menší než `pcCodeInfos`, přidělit větší `codeInfos` vyrovnávací paměti, aktualizujte `cCodeInfos` s novou, větší velikost a volání `GetCodeInfo3` znovu.</span><span class="sxs-lookup"><span data-stu-id="fe090-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="fe090-120">Alternativně můžete nejdřív volat `GetCodeInfo3` s nulovou délkou `codeInfos` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fe090-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="fe090-121">Pak můžete nastavit `codeInfos` velikost k hodnotě vrácené ve vyrovnávací paměti `pcCodeInfos`, násobenou velikost [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) strukturu a volání `GetCodeInfo3` znovu.</span><span class="sxs-lookup"><span data-stu-id="fe090-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe090-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe090-122">Requirements</span></span>  
 <span data-ttu-id="fe090-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe090-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe090-124">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe090-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe090-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe090-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe090-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe090-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe090-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe090-127">See Also</span></span>  
 [<span data-ttu-id="fe090-128">Getcodeinfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fe090-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
 [<span data-ttu-id="fe090-129">Icorprofilerinfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe090-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="fe090-130">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="fe090-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="fe090-131">Profilace</span><span class="sxs-lookup"><span data-stu-id="fe090-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
