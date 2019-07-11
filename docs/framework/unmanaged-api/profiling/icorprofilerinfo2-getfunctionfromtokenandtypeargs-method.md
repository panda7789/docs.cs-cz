---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31fad9e82d0b93360f92676f6357c136ae60634a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771126"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="8d667-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda</span><span class="sxs-lookup"><span data-stu-id="8d667-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="8d667-103">Získá `FunctionID` funkce s použitím Zadaná metadata token, který obsahuje třídy, a `ClassID` hodnot ve všech argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="8d667-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d667-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d667-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d667-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d667-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="8d667-106">[in] ID modulu, ve kterém se funkce nachází.</span><span class="sxs-lookup"><span data-stu-id="8d667-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="8d667-107">[in] `mdMethodDef` Token metadat, který odkazuje na funkci.</span><span class="sxs-lookup"><span data-stu-id="8d667-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="8d667-108">[in] ID funkce obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="8d667-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="8d667-109">[in] Počet parametrů typu pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="8d667-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="8d667-110">Tato hodnota musí být nula pro funkce, který není obecný.</span><span class="sxs-lookup"><span data-stu-id="8d667-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="8d667-111">[in] Pole `ClassID` hodnot, z nichž každý je argument funkce.</span><span class="sxs-lookup"><span data-stu-id="8d667-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="8d667-112">Hodnota `typeArgs` může mít hodnotu NULL, pokud `cTypeArgs` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="8d667-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="8d667-113">[out] Ukazatel `FunctionID` zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="8d667-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d667-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d667-114">Remarks</span></span>  
 <span data-ttu-id="8d667-115">Volání `GetFunctionFromTokenAndTypeArgs` metodou `mdMethodRef` metadat místo `mdMethodDef` tokenu metadat může mít nepředvídatelné výsledky.</span><span class="sxs-lookup"><span data-stu-id="8d667-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="8d667-116">Volající musí se překládat `mdMethodRef` do `mdMethodDef` při předávání ho.</span><span class="sxs-lookup"><span data-stu-id="8d667-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="8d667-117">Pokud funkce dosud není načtený, volání `GetFunctionFromTokenAndTypeArgs` způsobí, že načítání pravděpodobnější, což je nebezpečné operace v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="8d667-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="8d667-118">Například volání této metody při načítání modulů nebo typy může vést k nekonečné smyčce jak modul runtime pokusí se načíst cyklicky věci.</span><span class="sxs-lookup"><span data-stu-id="8d667-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="8d667-119">Obecně platí, využívání `GetFunctionFromTokenAndTypeArgs` se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="8d667-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="8d667-120">Pokud profilery zajímají události pro určitou funkci, měli uložit `ModuleID` a `mdMethodDef` této funkce a použití [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) ke kontrole, jestli daný `FunctionID` je který požadované funkce.</span><span class="sxs-lookup"><span data-stu-id="8d667-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d667-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d667-121">Requirements</span></span>  
 <span data-ttu-id="8d667-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d667-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d667-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d667-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d667-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d667-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d667-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d667-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d667-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d667-126">See also</span></span>

- [<span data-ttu-id="8d667-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d667-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="8d667-128">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d667-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
