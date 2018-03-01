---
title: "ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda"
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
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a459f8e9ec6d63dc42d6a0a8f752c129d278524
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="21712-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda</span><span class="sxs-lookup"><span data-stu-id="21712-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="21712-103">Získá `ClassID` typu pomocí tokenu Zadaná metadata a `ClassID` argumentů hodnoty libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="21712-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21712-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21712-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21712-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21712-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="21712-106">[v] ID modulu, ve které je umístěn typu.</span><span class="sxs-lookup"><span data-stu-id="21712-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="21712-107">[v] `mdTypeDef` Metadata token, který odkazuje na typ.</span><span class="sxs-lookup"><span data-stu-id="21712-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="21712-108">[v] Počet parametrů typu pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="21712-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="21712-109">Tato hodnota musí být nula pro neobecný typy.</span><span class="sxs-lookup"><span data-stu-id="21712-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="21712-110">[v] Pole `ClassID` hodnoty, z nichž každý je argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="21712-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="21712-111">Hodnota `typeArgs` může mít hodnotu NULL, pokud `cTypeArgs` je nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="21712-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="21712-112">[out] Ukazatel `ClassID` zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="21712-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21712-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21712-113">Remarks</span></span>  
 <span data-ttu-id="21712-114">Volání `GetClassFromTokenAndTypeArgs` metoda s `mdTypeRef` místo `mdTypeDef` metadata token může mít nepředvídatelné výsledky; volající musí se překládat `mdTypeRef` k `mdTypeDef` při předání.</span><span class="sxs-lookup"><span data-stu-id="21712-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="21712-115">Pokud dosud není načtený typ, voláním `GetClassFromTokenAndTypeArgs` aktivují načítání, což je nebezpečné operace v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="21712-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="21712-116">Například voláním této metody během načítání moduly nebo jiné typy může vést k nekonečné smyčce jako modul runtime, pokusí se načíst pravidelného věcí.</span><span class="sxs-lookup"><span data-stu-id="21712-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="21712-117">Obecně platí, použití `GetClassFromTokenAndTypeArgs` se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="21712-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="21712-118">Pokud události pro určitý typ zajímá profilery, měli uložit `ModuleID` a `mdTypeDef` tohoto typu a použití [ICorProfilerInfo2::getclassidinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) zkontrolujte zda daný `ClassID` , je požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="21712-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21712-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21712-119">Requirements</span></span>  
 <span data-ttu-id="21712-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21712-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21712-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21712-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21712-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21712-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21712-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21712-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21712-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="21712-124">See Also</span></span>  
 [<span data-ttu-id="21712-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21712-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="21712-126">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21712-126">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
