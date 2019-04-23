---
title: ICorProfilerInfo2::GetCodeInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1acf77c250b47bb32a83227a427dd3fe4f909a33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122483"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="acbdb-102">ICorProfilerInfo2::GetCodeInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="acbdb-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="acbdb-103">Získá rozsah nativního kódu přidružený k zadanému `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="acbdb-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acbdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acbdb-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acbdb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="acbdb-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="acbdb-106">[in] ID funkce, ke kterému je přidružen nativní kód.</span><span class="sxs-lookup"><span data-stu-id="acbdb-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="acbdb-107">[in] Velikost `codeInfos` pole.</span><span class="sxs-lookup"><span data-stu-id="acbdb-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="acbdb-108">[out] Ukazatel na celkový počet [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury k dispozici.</span><span class="sxs-lookup"><span data-stu-id="acbdb-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="acbdb-109">[out] Pokud volající vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="acbdb-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="acbdb-110">Po návratu metody obsahuje celou řadu `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="acbdb-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acbdb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acbdb-111">Remarks</span></span>  
 <span data-ttu-id="acbdb-112">Rozsahy jsou seřazeny v pořadí podle zvyšující posun Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="acbdb-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="acbdb-113">Po `GetCodeInfo2` vrátí, musíte ověřit, že `codeInfos` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny `COR_PRF_CODE_INFO` struktury.</span><span class="sxs-lookup"><span data-stu-id="acbdb-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="acbdb-114">K tomuto účelu porovnat hodnotu `cCodeInfos` s hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="acbdb-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="acbdb-115">Pokud `cCodeInfos` rozdělené podle velikosti `COR_PRF_CODE_INFO` struktura je menší než `pcCodeInfos`, přidělte větší `codeInfos` vyrovnávací paměti, aktualizujte `cCodeInfos` nové, větší velikosti a volání `GetCodeInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="acbdb-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="acbdb-116">Alternativně můžete nejprve volat `GetCodeInfo2` s nulovou délkou `codeInfos` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="acbdb-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="acbdb-117">Pak můžete nastavit `codeInfos` velikost k hodnotě vrácené ve vyrovnávací paměti `pcCodeInfos`, vynásobený velikostí `COR_PRF_CODE_INFO` strukturu a volání `GetCodeInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="acbdb-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acbdb-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="acbdb-118">Requirements</span></span>  
 <span data-ttu-id="acbdb-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acbdb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acbdb-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="acbdb-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="acbdb-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acbdb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acbdb-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acbdb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acbdb-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acbdb-123">See also</span></span>

- [<span data-ttu-id="acbdb-124">GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="acbdb-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="acbdb-125">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="acbdb-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="acbdb-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="acbdb-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="acbdb-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="acbdb-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
