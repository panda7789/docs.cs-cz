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
ms.openlocfilehash: 7f1276e1adeece086ca7b6791eb6e870faf4d010
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502870"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="299f1-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda</span><span class="sxs-lookup"><span data-stu-id="299f1-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="299f1-103">Získá `FunctionID` funkci pomocí zadaného tokenu metadat obsahujícího třídu a `ClassID` hodnot libovolných argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="299f1-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="299f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="299f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="299f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="299f1-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="299f1-106">pro ID modulu, ve kterém je funkce umístěna.</span><span class="sxs-lookup"><span data-stu-id="299f1-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="299f1-107">pro `mdMethodDef`Token metadat, který odkazuje na funkci.</span><span class="sxs-lookup"><span data-stu-id="299f1-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="299f1-108">pro ID obsahující třídy funkce</span><span class="sxs-lookup"><span data-stu-id="299f1-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="299f1-109">pro Počet parametrů typu pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="299f1-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="299f1-110">Pro neobecné funkce musí být tato hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="299f1-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="299f1-111">pro Pole `ClassID` hodnot, z nichž každý je argumentem funkce.</span><span class="sxs-lookup"><span data-stu-id="299f1-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="299f1-112">Hodnota `typeArgs` může být null, pokud `cTypeArgs` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="299f1-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="299f1-113">mimo Ukazatel na `FunctionID` určenou funkci.</span><span class="sxs-lookup"><span data-stu-id="299f1-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="299f1-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="299f1-114">Remarks</span></span>  
 <span data-ttu-id="299f1-115">Volání `GetFunctionFromTokenAndTypeArgs` metody s `mdMethodRef` metadaty namísto `mdMethodDef` tokenu metadat může mít nepředvídatelné výsledky.</span><span class="sxs-lookup"><span data-stu-id="299f1-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="299f1-116">Volající by při předávání měli metodu vyřešit `mdMethodRef` na `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="299f1-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="299f1-117">Pokud funkce ještě není načtená, volání `GetFunctionFromTokenAndTypeArgs` způsobí nasazování, což je nebezpečná operace v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="299f1-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="299f1-118">Například volání této metody během načítání modulů nebo typů může vést k nekonečné smyčce, protože modul runtime se pokusí cyklicky načíst věci.</span><span class="sxs-lookup"><span data-stu-id="299f1-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="299f1-119">Obecně platí, že použití `GetFunctionFromTokenAndTypeArgs` se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="299f1-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="299f1-120">Pokud se profilery zajímá o události pro konkrétní funkci, měly by uložit `ModuleID` a příslušné `mdMethodDef` funkce a pomocí [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) ověřit, zda daná `FunctionID` funkce má požadovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="299f1-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="299f1-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="299f1-121">Requirements</span></span>  
 <span data-ttu-id="299f1-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="299f1-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="299f1-123">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="299f1-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="299f1-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="299f1-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="299f1-125">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="299f1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="299f1-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="299f1-126">See also</span></span>

- [<span data-ttu-id="299f1-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="299f1-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="299f1-128">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="299f1-128">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
