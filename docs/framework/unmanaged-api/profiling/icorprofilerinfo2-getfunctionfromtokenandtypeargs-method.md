---
title: "ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda"
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
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b225b87eab6e65055618c8b6659459637e8a01be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="4f94a-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda</span><span class="sxs-lookup"><span data-stu-id="4f94a-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="4f94a-103">Získá `FunctionID` funkce pomocí Zadaná metadata token, který obsahuje třídy, a `ClassID` argumentů hodnoty libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="4f94a-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f94a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f94a-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f94a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f94a-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="4f94a-106">[v] ID modulu, ve kterém se funkce nachází.</span><span class="sxs-lookup"><span data-stu-id="4f94a-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="4f94a-107">[v] `mdMethodDef` Metadata token, který odkazuje na funkci.</span><span class="sxs-lookup"><span data-stu-id="4f94a-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="4f94a-108">[v] ID třídy obsahující funkce.</span><span class="sxs-lookup"><span data-stu-id="4f94a-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="4f94a-109">[v] Počet typů parametrů pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="4f94a-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="4f94a-110">Tato hodnota musí být nula pro neobecný funkce.</span><span class="sxs-lookup"><span data-stu-id="4f94a-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="4f94a-111">[v] Pole `ClassID` hodnoty, z nichž každý je argument funkce.</span><span class="sxs-lookup"><span data-stu-id="4f94a-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="4f94a-112">Hodnota `typeArgs` může mít hodnotu NULL, pokud `cTypeArgs` je nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="4f94a-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="4f94a-113">[out] Ukazatel `FunctionID` zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="4f94a-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f94a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f94a-114">Remarks</span></span>  
 <span data-ttu-id="4f94a-115">Volání `GetFunctionFromTokenAndTypeArgs` metoda s `mdMethodRef` metadata místo `mdMethodDef` metadata token může mít vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="4f94a-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="4f94a-116">Volající musí se překládat `mdMethodRef` k `mdMethodDef` při předání.</span><span class="sxs-lookup"><span data-stu-id="4f94a-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="4f94a-117">Pokud funkce dosud není načtený, volání `GetFunctionFromTokenAndTypeArgs` způsobí, že dojde k, načítání, což je nebezpečné operace v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="4f94a-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="4f94a-118">Například voláním této metody během načítání moduly nebo typů může vést k nekonečné smyčce jako modul runtime, pokusí se načíst pravidelného věcí.</span><span class="sxs-lookup"><span data-stu-id="4f94a-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="4f94a-119">Obecně platí, použití `GetFunctionFromTokenAndTypeArgs` se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="4f94a-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="4f94a-120">Pokud profilery zájem o události pro určitou funkci, měli uložit `ModuleID` a `mdMethodDef` této funkce a použití [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) zkontrolujte zda danou `FunctionID` je který požadované funkce.</span><span class="sxs-lookup"><span data-stu-id="4f94a-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f94a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f94a-121">Requirements</span></span>  
 <span data-ttu-id="4f94a-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f94a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f94a-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f94a-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f94a-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f94a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f94a-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f94a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f94a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f94a-126">See Also</span></span>  
 [<span data-ttu-id="4f94a-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f94a-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="4f94a-128">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f94a-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
