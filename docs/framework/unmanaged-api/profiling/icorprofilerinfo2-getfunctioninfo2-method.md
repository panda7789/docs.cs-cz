---
title: "ICorProfilerInfo2::GetFunctionInfo2 – metoda"
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
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e7a48f109c22ae768e636a7f6b57e4e10ac76012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="f3321-102">ICorProfilerInfo2::GetFunctionInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="f3321-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="f3321-103">Získá nadřazené třídy, metadata token a `ClassID` každý typ argumentu, pokud je k dispozici funkce.</span><span class="sxs-lookup"><span data-stu-id="f3321-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3321-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3321-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3321-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3321-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="f3321-106">[v] ID funkce, pro které chcete získat nadřazené třídy a další informace.</span><span class="sxs-lookup"><span data-stu-id="f3321-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="f3321-107">[v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f3321-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="f3321-108">[out] Ukazatel na nadřazené třídy funkce.</span><span class="sxs-lookup"><span data-stu-id="f3321-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="f3321-109">[out] Ukazatel na modul, ve kterém je definovaný funkce nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="f3321-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="f3321-110">[out] Ukazatel na token metadata pro funkci.</span><span class="sxs-lookup"><span data-stu-id="f3321-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="f3321-111">[v] Velikost `typeArgs` pole.</span><span class="sxs-lookup"><span data-stu-id="f3321-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="f3321-112">[out] Ukazatel na celkový počet `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f3321-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="f3321-113">[out] Pole `ClassID` hodnoty, z nichž každý je ID argumentu typu funkce.</span><span class="sxs-lookup"><span data-stu-id="f3321-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="f3321-114">Po návratu metody `typeArgs` bude obsahovat některé nebo všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f3321-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3321-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3321-115">Remarks</span></span>  
 <span data-ttu-id="f3321-116">Můžete volat kód profileru [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získat [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) rozhraní pro daného modulu.</span><span class="sxs-lookup"><span data-stu-id="f3321-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="f3321-117">Metadata token, který je vrácen do umístění odkazuje `pToken` pak lze získat přístup k metadatům pro funkci.</span><span class="sxs-lookup"><span data-stu-id="f3321-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="f3321-118">Třída ID a zadejte argumenty, které jsou vráceny prostřednictvím `pClassId` a `typeArgs` parametry závisí na hodnota, je předaná `frameInfo` parametr, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f3321-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f3321-119">Hodnota `frameInfo` parametr</span><span class="sxs-lookup"><span data-stu-id="f3321-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="f3321-120">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f3321-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="f3321-121">A `COR_PRF_FRAME_INFO` hodnotu, který byl získán z `FunctionEnter2` zpětného volání</span><span class="sxs-lookup"><span data-stu-id="f3321-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="f3321-122">`ClassID`, Vrácený v umístění odkazuje `pClassId`, a všechny argumenty, vrátí se v typů `typeArgs` pole, bude přesný.</span><span class="sxs-lookup"><span data-stu-id="f3321-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="f3321-123">A `COR_PRF_FRAME_INFO` který byl získán z zdroje jiné než `FunctionEnter2` zpětného volání</span><span class="sxs-lookup"><span data-stu-id="f3321-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="f3321-124">Přesné `ClassID` a argumenty typu nelze určit.</span><span class="sxs-lookup"><span data-stu-id="f3321-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="f3321-125">To znamená `ClassID` může mít hodnotu null a může mít některé argumenty typu zpět jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="f3321-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="f3321-126">Nula</span><span class="sxs-lookup"><span data-stu-id="f3321-126">Zero</span></span>|<span data-ttu-id="f3321-127">Přesné `ClassID` a argumenty typu nelze určit.</span><span class="sxs-lookup"><span data-stu-id="f3321-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="f3321-128">To znamená `ClassID` může mít hodnotu null a může mít některé argumenty typu zpět jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="f3321-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="f3321-129">Po `GetFunctionInfo2` vrátí, musíte ověřit, že `typeArgs` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f3321-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="f3321-130">K tomuto účelu porovnat hodnotu, `pcTypeArgs` body s hodnotou `cTypeArgs` parametr.</span><span class="sxs-lookup"><span data-stu-id="f3321-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="f3321-131">Pokud `pcTypeArgs` odkazuje na hodnotu, která je větší než `cTypeArgs` dělený velikost `ClassID` hodnotu, přidělit větší `pcTypeArgs` vyrovnávací paměti, aktualizujte `cTypeArgs` s novou, větší velikost a volání `GetFunctionInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="f3321-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="f3321-132">Alternativně můžete nejdřív volat `GetFunctionInfo2` s nulovou délkou `pcTypeArgs` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f3321-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f3321-133">Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcTypeArgs` dělený velikost `ClassID` hodnota a volání `GetFunctionInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="f3321-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3321-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3321-134">Requirements</span></span>  
 <span data-ttu-id="f3321-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3321-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3321-136">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3321-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3321-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3321-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3321-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3321-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3321-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3321-139">See Also</span></span>  
 [<span data-ttu-id="f3321-140">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3321-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="f3321-141">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3321-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="f3321-142">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f3321-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f3321-143">Profilace</span><span class="sxs-lookup"><span data-stu-id="f3321-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
