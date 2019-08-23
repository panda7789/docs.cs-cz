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
ms.openlocfilehash: 084007bd7ab20449c28d2c5e6125cbacfa280526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912706"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="6a2e2-102">ICorProfilerInfo4::GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="6a2e2-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="6a2e2-103">Získá rozsahy nativního kódu přidruženého k Rekompilované verzi JIT zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a2e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a2e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a2e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a2e2-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="6a2e2-106">pro ID funkce, ke které je přidružen nativní kód.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="6a2e2-107">pro Identita funkce Rekompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="6a2e2-108">pro Velikost `codeInfos` pole.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="6a2e2-109">mimo Ukazatel na celkový počet dostupných struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)</span><span class="sxs-lookup"><span data-stu-id="6a2e2-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="6a2e2-110">mimo Vyrovnávací paměť poskytnutá volajícím.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="6a2e2-111">Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a2e2-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a2e2-112">Remarks</span></span>  
 <span data-ttu-id="6a2e2-113">Metoda je podobná GetCodeInfo2 –, s tím rozdílem, že získá znovu zkompilované ID JIT funkce, která obsahuje zadanou IP adresu. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) `GetCodeInfo3`</span><span class="sxs-lookup"><span data-stu-id="6a2e2-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a2e2-114">`GetCodeInfo3`může aktivovat uvolňování paměti, zatímco [GetCodeInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) nebude.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="6a2e2-115">Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="6a2e2-116">Rozsahy jsou seřazené v pořadí zvyšování Common Intermediate Language (CIL) posun.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="6a2e2-117">Po `GetCodeInfo3` návratu je nutné ověřit `codeInfos` , zda byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2e2-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="6a2e2-118">Chcete-li to provést, porovnejte `cCodeInfos` hodnotu s hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="6a2e2-119">Je `cCodeInfos` -li děleno velikostí struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) menší než `pcCodeInfos`, přidělte větší `codeInfos` vyrovnávací paměť, aktualizujte `cCodeInfos` novou, větší velikost a zavolejte `GetCodeInfo3` znovu.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="6a2e2-120">Případně můžete pro získání správné velikosti `GetCodeInfo3` vyrovnávací paměti nejprve zavolat s `codeInfos` nulovou délkou vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="6a2e2-121">Pak můžete `codeInfos` nastavit velikost vyrovnávací paměti na hodnotu vrácenou `pcCodeInfos`v, vynásobenou velikostí [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury a volat `GetCodeInfo3` znovu.</span><span class="sxs-lookup"><span data-stu-id="6a2e2-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a2e2-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a2e2-122">Requirements</span></span>  
 <span data-ttu-id="6a2e2-123">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a2e2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a2e2-124">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6a2e2-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a2e2-125">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a2e2-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a2e2-126">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a2e2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a2e2-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a2e2-127">See also</span></span>

- [<span data-ttu-id="6a2e2-128">GetCodeInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6a2e2-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="6a2e2-129">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a2e2-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="6a2e2-130">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6a2e2-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6a2e2-131">Profilace</span><span class="sxs-lookup"><span data-stu-id="6a2e2-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
