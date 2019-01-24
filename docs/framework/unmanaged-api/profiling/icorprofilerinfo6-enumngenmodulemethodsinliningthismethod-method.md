---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b1c905e587708336ce690bbf3d187b2d21e5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568150"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="56b64-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span><span class="sxs-lookup"><span data-stu-id="56b64-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="56b64-103">[Podporované v rozhraní .NET Framework 4.6 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="56b64-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="56b64-104">Vrátí enumerátor pro všechny metody, které jsou definovány v zadaném modulu NGen a vložené dané metody.</span><span class="sxs-lookup"><span data-stu-id="56b64-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b64-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56b64-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56b64-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="56b64-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="56b64-107">[in] Identifikátor modulu technologie NGen.</span><span class="sxs-lookup"><span data-stu-id="56b64-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="56b64-108">[in] Identifikátor modulu, který definuje `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="56b64-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="56b64-109">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="56b64-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="56b64-110">[in] Identifikátor je vložená metoda.</span><span class="sxs-lookup"><span data-stu-id="56b64-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="56b64-111">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="56b64-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="56b64-112">[out] Příznak označující, zda `ppEnum` obsahuje všechny metody vkládání dané metody.</span><span class="sxs-lookup"><span data-stu-id="56b64-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="56b64-113">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="56b64-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="56b64-114">[out] Ukazatel na adresu enumerátor</span><span class="sxs-lookup"><span data-stu-id="56b64-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56b64-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56b64-115">Remarks</span></span>  
 <span data-ttu-id="56b64-116">`inlineeModuleId` a `inlineeMethodId` společně tvoří úplný identifikátor pro metodu, která mohou být vložená.</span><span class="sxs-lookup"><span data-stu-id="56b64-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="56b64-117">Předpokládejme například, modul `A` definuje metodu `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="56b64-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="56b64-118">modul Bdefines a `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="56b64-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="56b64-119">Umožňuje taky se předpokládá, že `Fancy.AddTwice` inlines volání do `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="56b64-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="56b64-120">Profiler může použít výčet najít všechny metody definované v modulu B které vložené `Simple.Add`, a výsledek by výčet `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="56b64-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="56b64-121">`inlineeModuleId` identifikátor modulu `A`, a `inlineeeMethodId` je identifikátor `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="56b64-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="56b64-122">Pokud `incompleteData` platí za funkci vrací enumerátor neobsahuje všechny metody vkládání dané metody.</span><span class="sxs-lookup"><span data-stu-id="56b64-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="56b64-123">K tomu může dojít v případě, že jedna nebo přímou nebo nepřímou závislostmi inliners modulu nebyly dosud načteny.</span><span class="sxs-lookup"><span data-stu-id="56b64-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="56b64-124">Pokud profiler přesná data, je při další moduly se načítají, pokud možno na každého modulu zatížení opakovat později.</span><span class="sxs-lookup"><span data-stu-id="56b64-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="56b64-125">`EnumNgenModuleMethodsInliningThisMethod` Metodu je možné obejít omezení na vkládání pro ReJIT.</span><span class="sxs-lookup"><span data-stu-id="56b64-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="56b64-126">ReJIT umožňuje profileru, změňte implementaci metody a pak vytvořte nový kód pro něj v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="56b64-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="56b64-127">Můžeme například změnit `Simple.Add` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="56b64-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="56b64-128">Ale protože `Fancy.AddTwice` má již vložených `Simple.Add`, nadále mají stejné chování jako předtím.</span><span class="sxs-lookup"><span data-stu-id="56b64-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="56b64-129">Toto omezení obejít, volající musí vyhledat všechny metody ve všech modulech přímo tady `Simple.Add` a použít `ICorProfilerInfo5::RequestRejit` na každé z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="56b64-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="56b64-130">Pokud metody jsou znovu zkompilovány, mají nové chování `Simple.Add` místo staré chování.</span><span class="sxs-lookup"><span data-stu-id="56b64-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56b64-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56b64-131">Requirements</span></span>  
 <span data-ttu-id="56b64-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56b64-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56b64-133">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="56b64-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56b64-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56b64-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56b64-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56b64-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b64-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56b64-136">See also</span></span>
- [<span data-ttu-id="56b64-137">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56b64-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
