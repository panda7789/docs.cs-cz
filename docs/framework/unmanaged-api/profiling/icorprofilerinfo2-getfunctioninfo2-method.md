---
title: ICorProfilerInfo2::GetFunctionInfo2 – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45a7e0c793baa31d9efde2763570cd46a072fe86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546316"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="183ce-102">ICorProfilerInfo2::GetFunctionInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="183ce-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="183ce-103">Získá na nadřazenou třídu tokenu metadat a `ClassID` každý typ argumentu, pokud jsou k dispozici funkce.</span><span class="sxs-lookup"><span data-stu-id="183ce-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="183ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="183ce-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="183ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="183ce-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="183ce-106">[in] ID funkce, pro které chcete-li získat nadřazené třídu a další informace.</span><span class="sxs-lookup"><span data-stu-id="183ce-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="183ce-107">[in] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="183ce-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="183ce-108">[out] Ukazatel na nadřazené třídy funkce.</span><span class="sxs-lookup"><span data-stu-id="183ce-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="183ce-109">[out] Ukazatel na modul, ve kterém je definována funkce nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="183ce-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="183ce-110">[out] Ukazatel na token metadat pro funkci.</span><span class="sxs-lookup"><span data-stu-id="183ce-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="183ce-111">[in] Velikost `typeArgs` pole.</span><span class="sxs-lookup"><span data-stu-id="183ce-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="183ce-112">[out] Ukazatel na celkový počet `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="183ce-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="183ce-113">[out] Pole `ClassID` hodnot, z nichž každý je ID argument typu funkce.</span><span class="sxs-lookup"><span data-stu-id="183ce-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="183ce-114">Po návratu metody `typeArgs` bude obsahovat některé nebo všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="183ce-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="183ce-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="183ce-115">Remarks</span></span>  
 <span data-ttu-id="183ce-116">Profiler kódu může volat [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získat [metadat](../../../../docs/framework/unmanaged-api/metadata/index.md) rozhraní pro daný modul.</span><span class="sxs-lookup"><span data-stu-id="183ce-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="183ce-117">Token metadat, který je vrácen do umístění odkazuje `pToken` lze použít k přístupu k metadatům pro funkci.</span><span class="sxs-lookup"><span data-stu-id="183ce-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="183ce-118">Třída ID a typ argumentů, které jsou vráceny prostřednictvím `pClassId` a `typeArgs` parametry záviset na hodnotě předané `frameInfo` parametru, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="183ce-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="183ce-119">Hodnota `frameInfo` parametr</span><span class="sxs-lookup"><span data-stu-id="183ce-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="183ce-120">Výsledek</span><span class="sxs-lookup"><span data-stu-id="183ce-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="183ce-121">A `COR_PRF_FRAME_INFO` hodnoty, který byl získán z `FunctionEnter2` zpětného volání</span><span class="sxs-lookup"><span data-stu-id="183ce-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="183ce-122">`ClassID`, Vracet v umístění odkazuje `pClassId`, a všechny argumenty, vrácené v typu `typeArgs` pole, nebudou přesné.</span><span class="sxs-lookup"><span data-stu-id="183ce-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="183ce-123">A `COR_PRF_FRAME_INFO` , který byl získán ze zdroje jiné než `FunctionEnter2` zpětného volání</span><span class="sxs-lookup"><span data-stu-id="183ce-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="183ce-124">Přesné `ClassID` a argumenty typu nelze určit.</span><span class="sxs-lookup"><span data-stu-id="183ce-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="183ce-125">To znamená `ClassID` může mít hodnotu null a některé argumenty typu by mohl pocházet zpět jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="183ce-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="183ce-126">Nula</span><span class="sxs-lookup"><span data-stu-id="183ce-126">Zero</span></span>|<span data-ttu-id="183ce-127">Přesné `ClassID` a argumenty typu nelze určit.</span><span class="sxs-lookup"><span data-stu-id="183ce-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="183ce-128">To znamená `ClassID` může mít hodnotu null a některé argumenty typu by mohl pocházet zpět jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="183ce-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="183ce-129">Po `GetFunctionInfo2` vrátí, musíte ověřit, že `typeArgs` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="183ce-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="183ce-130">K tomuto účelu porovnat hodnoty, které `pcTypeArgs` odkazuje na hodnotu `cTypeArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="183ce-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="183ce-131">Pokud `pcTypeArgs` odkazuje na hodnotu, která je větší než `cTypeArgs` rozdělené podle velikosti `ClassID` hodnoty, přidělte větší `pcTypeArgs` vyrovnávací paměti, aktualizujte `cTypeArgs` nové, větší velikosti a volání `GetFunctionInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="183ce-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="183ce-132">Alternativně můžete nejprve volat `GetFunctionInfo2` s nulovou délkou `pcTypeArgs` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="183ce-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="183ce-133">Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcTypeArgs` rozdělené podle velikosti `ClassID` hodnotu a volání `GetFunctionInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="183ce-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="183ce-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="183ce-134">Requirements</span></span>  
 <span data-ttu-id="183ce-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="183ce-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="183ce-136">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="183ce-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="183ce-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="183ce-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="183ce-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="183ce-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183ce-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="183ce-139">See also</span></span>
- [<span data-ttu-id="183ce-140">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="183ce-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="183ce-141">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="183ce-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="183ce-142">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="183ce-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="183ce-143">Profilace</span><span class="sxs-lookup"><span data-stu-id="183ce-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
