---
title: ICorProfilerInfo4::GetCodeInfo3 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 64382f0d405e84b2be78aac982b085fec35cb37b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675093"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="a382b-102">ICorProfilerInfo4::GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="a382b-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="a382b-103">Získá rozsah nativního kódu přidružené verze překompilován JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="a382b-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a382b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a382b-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a382b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a382b-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="a382b-106">[in] ID funkce, ke kterému je přidružen nativní kód.</span><span class="sxs-lookup"><span data-stu-id="a382b-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="a382b-107">[in] Identita funkce překompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="a382b-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="a382b-108">[in] Velikost `codeInfos` pole.</span><span class="sxs-lookup"><span data-stu-id="a382b-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="a382b-109">[out] Ukazatel na celkový počet [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a382b-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="a382b-110">[out] Pokud volající vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a382b-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="a382b-111">Po návratu metody obsahuje celou řadu `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a382b-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a382b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a382b-112">Remarks</span></span>  
 <span data-ttu-id="a382b-113">`GetCodeInfo3` Metoda je podobná [getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), s tím rozdílem, že se budou získávat překompilován JIT ID funkce, která obsahuje zadaná IP adresa.</span><span class="sxs-lookup"><span data-stu-id="a382b-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a382b-114">`GetCodeInfo3` můžete aktivovat kolekce uvolnění paměti, že [getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) se tak nestane.</span><span class="sxs-lookup"><span data-stu-id="a382b-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="a382b-115">Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a382b-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="a382b-116">Rozsahy jsou seřazeny v pořadí podle zvýšení posun Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="a382b-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="a382b-117">Po `GetCodeInfo3` vrátí, musíte ověřit, že `codeInfos` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="a382b-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="a382b-118">K tomuto účelu porovnat hodnotu `cCodeInfos` s hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="a382b-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="a382b-119">Pokud `cCodeInfos` rozdělené podle velikosti [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktura je menší než `pcCodeInfos`, přidělte větší `codeInfos` vyrovnávací paměti, aktualizujte `cCodeInfos` nové, větší velikosti a volání `GetCodeInfo3` znovu.</span><span class="sxs-lookup"><span data-stu-id="a382b-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="a382b-120">Alternativně můžete nejprve volat `GetCodeInfo3` s nulovou délkou `codeInfos` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="a382b-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a382b-121">Pak můžete nastavit `codeInfos` velikost k hodnotě vrácené ve vyrovnávací paměti `pcCodeInfos`, vynásobený velikostí [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) strukturu a volání `GetCodeInfo3` znovu.</span><span class="sxs-lookup"><span data-stu-id="a382b-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a382b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a382b-122">Requirements</span></span>  
 <span data-ttu-id="a382b-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a382b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a382b-124">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a382b-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a382b-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a382b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a382b-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a382b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a382b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a382b-127">See also</span></span>
- [<span data-ttu-id="a382b-128">GetCodeInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a382b-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="a382b-129">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a382b-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="a382b-130">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a382b-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a382b-131">Profilace</span><span class="sxs-lookup"><span data-stu-id="a382b-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
