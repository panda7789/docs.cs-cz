---
title: "ICorProfilerInfo2::GetFunctionInfo2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b0c288b88c868bc6e324ec57b3956344f03f34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="5e3c6-102">ICorProfilerInfo2::GetFunctionInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5e3c6-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="5e3c6-103">Získá nadřazené třídy, metadata token a `ClassID` každý typ argumentu, pokud je k dispozici funkce.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e3c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e3c6-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="5e3c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e3c6-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="5e3c6-106">[v] ID funkce, pro které chcete získat nadřazené třídy a další informace.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="5e3c6-107">[v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="5e3c6-108">[out] Ukazatel na nadřazené třídy funkce.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="5e3c6-109">[out] Ukazatel na modul, ve kterém je definovaný funkce nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="5e3c6-110">[out] Ukazatel na token metadata pro funkci.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="5e3c6-111">[v] Velikost `typeArgs` pole.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="5e3c6-112">[out] Ukazatel na celkový počet `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="5e3c6-113">[out] Pole `ClassID` hodnoty, z nichž každý je ID argumentu typu funkce.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="5e3c6-114">Po návratu metody `typeArgs` bude obsahovat některé nebo všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e3c6-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e3c6-115">Remarks</span></span>  
 <span data-ttu-id="5e3c6-116">Můžete volat kód profileru [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získat [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) rozhraní pro daného modulu.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="5e3c6-117">Metadata token, který je vrácen do umístění odkazuje `pToken` pak lze získat přístup k metadatům pro funkci.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="5e3c6-118">Třída ID a zadejte argumenty, které jsou vráceny prostřednictvím `pClassId` a `typeArgs` parametry závisí na hodnota, je předaná `frameInfo` parametr, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="5e3c6-119">Hodnota `frameInfo` parametr</span><span class="sxs-lookup"><span data-stu-id="5e3c6-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="5e3c6-120">Výsledek</span><span class="sxs-lookup"><span data-stu-id="5e3c6-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="5e3c6-121">A `COR_PRF_FRAME_INFO` hodnotu, který byl získán z `FunctionEnter2` zpětného volání</span><span class="sxs-lookup"><span data-stu-id="5e3c6-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="5e3c6-122">`ClassID`, Vrácený v umístění odkazuje `pClassId`, a všechny argumenty, vrátí se v typů `typeArgs` pole, bude přesný.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="5e3c6-123">A `COR_PRF_FRAME_INFO` který byl získán z zdroje jiné než `FunctionEnter2` zpětného volání</span><span class="sxs-lookup"><span data-stu-id="5e3c6-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="5e3c6-124">Přesné `ClassID` a argumenty typu nelze určit.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="5e3c6-125">To znamená `ClassID` může mít hodnotu null a může mít některé argumenty typu zpět jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="5e3c6-126">Nula</span><span class="sxs-lookup"><span data-stu-id="5e3c6-126">Zero</span></span>|<span data-ttu-id="5e3c6-127">Přesné `ClassID` a argumenty typu nelze určit.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="5e3c6-128">To znamená `ClassID` může mít hodnotu null a může mít některé argumenty typu zpět jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="5e3c6-129">Po `GetFunctionInfo2` vrátí, musíte ověřit, že `typeArgs` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="5e3c6-130">K tomuto účelu porovnat hodnotu, `pcTypeArgs` body s hodnotou `cTypeArgs` parametr.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="5e3c6-131">Pokud `pcTypeArgs` odkazuje na hodnotu, která je větší než `cTypeArgs` dělený velikost `ClassID` hodnotu, přidělit větší `pcTypeArgs` vyrovnávací paměti, aktualizujte `cTypeArgs` s novou, větší velikost a volání `GetFunctionInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="5e3c6-132">Alternativně můžete nejdřív volat `GetFunctionInfo2` s nulovou délkou `pcTypeArgs` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="5e3c6-133">Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcTypeArgs` dělený velikost `ClassID` hodnota a volání `GetFunctionInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="5e3c6-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e3c6-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e3c6-134">Requirements</span></span>  
 <span data-ttu-id="5e3c6-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e3c6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e3c6-136">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e3c6-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e3c6-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e3c6-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e3c6-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e3c6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3c6-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e3c6-139">See Also</span></span>  
 [<span data-ttu-id="5e3c6-140">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e3c6-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="5e3c6-141">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e3c6-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="5e3c6-142">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5e3c6-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5e3c6-143">Profilace</span><span class="sxs-lookup"><span data-stu-id="5e3c6-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
