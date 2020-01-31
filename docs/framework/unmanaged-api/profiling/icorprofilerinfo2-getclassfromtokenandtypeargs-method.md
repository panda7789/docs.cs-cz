---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: e0663ff122397ba639a0a219e513be2f3f0cbbef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862760"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="396fa-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda</span><span class="sxs-lookup"><span data-stu-id="396fa-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="396fa-103">Získá `ClassID` typu pomocí zadaného tokenu metadat a hodnot `ClassID` jakýchkoli argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="396fa-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="396fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="396fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="396fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="396fa-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="396fa-106">pro ID modulu, ve kterém se nachází typ</span><span class="sxs-lookup"><span data-stu-id="396fa-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="396fa-107">pro Token metadat `mdTypeDef`, který odkazuje na typ.</span><span class="sxs-lookup"><span data-stu-id="396fa-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="396fa-108">pro Počet parametrů typu pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="396fa-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="396fa-109">Tato hodnota musí být nula pro neobecné typy.</span><span class="sxs-lookup"><span data-stu-id="396fa-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="396fa-110">pro Pole hodnot `ClassID`, z nichž každý je argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="396fa-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="396fa-111">Hodnota `typeArgs` může mít hodnotu NULL, pokud je `cTypeArgs` nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="396fa-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="396fa-112">mimo Ukazatel na `ClassID` zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="396fa-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="396fa-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="396fa-113">Remarks</span></span>  
 <span data-ttu-id="396fa-114">Volání metody `GetClassFromTokenAndTypeArgs` s `mdTypeRef` namísto tokenu metadat `mdTypeDef` může mít nepředvídatelné výsledky; Volající by při předávání měli `mdTypeDef` `mdTypeRef` vyřešit.</span><span class="sxs-lookup"><span data-stu-id="396fa-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="396fa-115">Pokud tento typ ještě není načtený, volání `GetClassFromTokenAndTypeArgs` spustí načítání, což je nebezpečná operace v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="396fa-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="396fa-116">Například volání této metody během načítání modulů nebo jiných typů může vést k nekonečné smyčce, protože modul runtime se pokusí cyklicky načíst věci.</span><span class="sxs-lookup"><span data-stu-id="396fa-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="396fa-117">Obecně platí, že použití `GetClassFromTokenAndTypeArgs` se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="396fa-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="396fa-118">Pokud jsou profilery zajímat události pro určitý typ, měly by uložit `ModuleID` a `mdTypeDef` tohoto typu a pomocí [ICorProfilerInfo2:: GetClassIDInfo2 –](icorprofilerinfo2-getclassidinfo2-method.md) ověřit, zda je daný `ClassID`, který je požadovaného typu.</span><span class="sxs-lookup"><span data-stu-id="396fa-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="396fa-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="396fa-119">Requirements</span></span>  
 <span data-ttu-id="396fa-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="396fa-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="396fa-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="396fa-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="396fa-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="396fa-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="396fa-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="396fa-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="396fa-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="396fa-124">See also</span></span>

- [<span data-ttu-id="396fa-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="396fa-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="396fa-126">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="396fa-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
