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
ms.openlocfilehash: b7db9b5af9b8bb8419573ef90ddf8beef697cb5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457497"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="592a4-102">ICorProfilerInfo2::GetCodeInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="592a4-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="592a4-103">Získá rozsah nativní kód spojený se zadaným `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="592a4-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="592a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="592a4-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="592a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="592a4-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="592a4-106">[v] ID funkce, ke kterému je přiřazeno nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="592a4-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="592a4-107">[v] Velikost `codeInfos` pole.</span><span class="sxs-lookup"><span data-stu-id="592a4-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="592a4-108">[out] Ukazatel na celkový počet [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="592a4-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="592a4-109">[out] Zadaný volající vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="592a4-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="592a4-110">Po návratu metody obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="592a4-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="592a4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="592a4-111">Remarks</span></span>  
 <span data-ttu-id="592a4-112">Rozsah jsou seřazeny v pořadí podle zvyšující posun (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="592a4-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="592a4-113">Po `GetCodeInfo2` vrátí, musíte ověřit, že `codeInfos` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `COR_PRF_CODE_INFO` struktury.</span><span class="sxs-lookup"><span data-stu-id="592a4-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="592a4-114">K tomuto účelu porovnat hodnotu `cCodeInfos` s hodnotou `cchName` parametr.</span><span class="sxs-lookup"><span data-stu-id="592a4-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="592a4-115">Pokud `cCodeInfos` dělený velikost `COR_PRF_CODE_INFO` struktura je menší než `pcCodeInfos`, přidělit větší `codeInfos` vyrovnávací paměti, aktualizujte `cCodeInfos` s novou, větší velikost a volání `GetCodeInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="592a4-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="592a4-116">Alternativně můžete nejdřív volat `GetCodeInfo2` s nulovou délkou `codeInfos` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="592a4-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="592a4-117">Pak můžete nastavit `codeInfos` velikost k hodnotě vrácené ve vyrovnávací paměti `pcCodeInfos`, násobenou velikost `COR_PRF_CODE_INFO` strukturu a volání `GetCodeInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="592a4-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="592a4-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="592a4-118">Requirements</span></span>  
 <span data-ttu-id="592a4-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="592a4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="592a4-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="592a4-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="592a4-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="592a4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="592a4-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="592a4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="592a4-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="592a4-123">See Also</span></span>  
 [<span data-ttu-id="592a4-124">GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="592a4-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)  
 [<span data-ttu-id="592a4-125">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="592a4-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="592a4-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="592a4-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="592a4-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="592a4-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
