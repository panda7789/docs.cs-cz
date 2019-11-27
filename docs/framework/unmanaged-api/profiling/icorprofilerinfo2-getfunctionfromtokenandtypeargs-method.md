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
ms.openlocfilehash: 41021a524142afe34727584265aee578e31a64b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433210"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="69c42-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda</span><span class="sxs-lookup"><span data-stu-id="69c42-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="69c42-103">Získá `FunctionID` funkce pomocí zadaného tokenu metadat, obsahující třídy a hodnot `ClassID` jakýchkoli argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="69c42-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69c42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69c42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69c42-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="69c42-106">pro ID modulu, ve kterém je funkce umístěna.</span><span class="sxs-lookup"><span data-stu-id="69c42-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="69c42-107">pro Token metadat `mdMethodDef`, který odkazuje na funkci.</span><span class="sxs-lookup"><span data-stu-id="69c42-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="69c42-108">pro ID obsahující třídy funkce</span><span class="sxs-lookup"><span data-stu-id="69c42-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="69c42-109">pro Počet parametrů typu pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="69c42-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="69c42-110">Pro neobecné funkce musí být tato hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="69c42-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="69c42-111">pro Pole hodnot `ClassID`, z nichž každý je argumentem funkce.</span><span class="sxs-lookup"><span data-stu-id="69c42-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="69c42-112">Hodnota `typeArgs` může mít hodnotu NULL, pokud je `cTypeArgs` nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="69c42-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="69c42-113">mimo Ukazatel na `FunctionID` zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="69c42-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69c42-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69c42-114">Remarks</span></span>  
 <span data-ttu-id="69c42-115">Volání metody `GetFunctionFromTokenAndTypeArgs` s metadaty `mdMethodRef` namísto tokenu metadat `mdMethodDef` může mít nepředvídatelné výsledky.</span><span class="sxs-lookup"><span data-stu-id="69c42-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="69c42-116">Volající by při předávání měli `mdMethodDef` `mdMethodRef` vyřešit.</span><span class="sxs-lookup"><span data-stu-id="69c42-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="69c42-117">Není-li funkce již načtena, volání `GetFunctionFromTokenAndTypeArgs` způsobí nasazování, což je nebezpečná operace v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="69c42-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="69c42-118">Například volání této metody během načítání modulů nebo typů může vést k nekonečné smyčce, protože modul runtime se pokusí cyklicky načíst věci.</span><span class="sxs-lookup"><span data-stu-id="69c42-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="69c42-119">Obecně platí, že použití `GetFunctionFromTokenAndTypeArgs` se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="69c42-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="69c42-120">Pokud jsou profilery zajímat události pro konkrétní funkci, měly by uložit `ModuleID` a `mdMethodDef` této funkce a pomocí [ICorProfilerInfo2:: GetFunctionInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) ověřit, zda daný `FunctionID` má požadovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="69c42-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69c42-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69c42-121">Requirements</span></span>  
 <span data-ttu-id="69c42-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69c42-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69c42-123">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="69c42-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69c42-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="69c42-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69c42-125">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69c42-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c42-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69c42-126">See also</span></span>

- [<span data-ttu-id="69c42-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69c42-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="69c42-128">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69c42-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
