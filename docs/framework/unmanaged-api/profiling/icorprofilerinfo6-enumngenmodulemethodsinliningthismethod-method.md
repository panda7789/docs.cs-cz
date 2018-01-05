---
title: "ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e11dd1c24001c764c82ed3f11336873ee57b2e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="3abf1-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="3abf1-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="3abf1-103">[Podporované v rozhraní .NET Framework 4.6 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="3abf1-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="3abf1-104">Vrátí enumerátor pro všechny metody, které jsou definovány v daném modulu NGen a vložené dané metody.</span><span class="sxs-lookup"><span data-stu-id="3abf1-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3abf1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3abf1-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3abf1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3abf1-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="3abf1-107">[v] Identifikátor modul NGen.</span><span class="sxs-lookup"><span data-stu-id="3abf1-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="3abf1-108">[v] Identifikátor modul, který definuje `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="3abf1-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="3abf1-109">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="3abf1-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="3abf1-110">[v] Identifikátor vložená metoda.</span><span class="sxs-lookup"><span data-stu-id="3abf1-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="3abf1-111">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="3abf1-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="3abf1-112">[out] Příznak, který určuje, zda `ppEnum` obsahuje všechny metody vložené dané metody.</span><span class="sxs-lookup"><span data-stu-id="3abf1-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="3abf1-113">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="3abf1-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="3abf1-114">[out] Ukazatel na adresu enumerátor</span><span class="sxs-lookup"><span data-stu-id="3abf1-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3abf1-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3abf1-115">Remarks</span></span>  
 <span data-ttu-id="3abf1-116">`inlineeModuleId`a `inlineeMethodId` společně tvoří úplný identifikátor metodu, která může být vložená.</span><span class="sxs-lookup"><span data-stu-id="3abf1-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="3abf1-117">Předpokládejme například, modul `A` definuje metodu `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="3abf1-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="3abf1-118">modul Bdefines a `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="3abf1-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="3abf1-119">Umožňuje také předpokládají, že `Fancy.AddTwice` inlines volání do `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="3abf1-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="3abf1-120">Profileru použít tento enumerátor najít všechny metody definované v modulu B, který vložené `Simple.Add`, a výsledkem by výčet `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="3abf1-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="3abf1-121">`inlineeModuleId`je identifikátor modulu `A`, a `inlineeeMethodId` je identifikátor `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="3abf1-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="3abf1-122">Pokud `incompleteData` platí po funkce vrátí enumerátor neobsahuje všechny metody vložené dané metody.</span><span class="sxs-lookup"><span data-stu-id="3abf1-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="3abf1-123">K tomu může dojít, pokud jeden nebo dosud nebyla načtena přímý nebo nepřímý závislosti inliners modulu.</span><span class="sxs-lookup"><span data-stu-id="3abf1-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="3abf1-124">Pokud profileru potřebuje přesná data, jeho pokus opakovat později. Pokud další moduly jsou načteny, pokud možno na každém načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="3abf1-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="3abf1-125">`EnumNgenModuleMethodsInliningThisMethod` Metoda lze obejít omezení na vložené pro ReJIT.</span><span class="sxs-lookup"><span data-stu-id="3abf1-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="3abf1-126">ReJIT umožňuje profileru změňte implementaci metody a pak vytvořte nový kód pro něj za chodu.</span><span class="sxs-lookup"><span data-stu-id="3abf1-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="3abf1-127">Například nám změnit `Simple.Add` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3abf1-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="3abf1-128">Ale protože `Fancy.AddTwice` má již vložená `Simple.Add`, pokračuje tak, aby měl stejné chování jako předtím.</span><span class="sxs-lookup"><span data-stu-id="3abf1-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="3abf1-129">Toto omezení obejít, má vyhledat všechny metody ve všech modulech přímo tady volající `Simple.Add` a používat `ICorProfilerInfo5::RequestRejit` na každé z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="3abf1-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="3abf1-130">Pokud se metody znovu kompilované, budou mít nové chování `Simple.Add` místo staré chování.</span><span class="sxs-lookup"><span data-stu-id="3abf1-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3abf1-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3abf1-131">Requirements</span></span>  
 <span data-ttu-id="3abf1-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3abf1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3abf1-133">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3abf1-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3abf1-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3abf1-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3abf1-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3abf1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3abf1-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="3abf1-136">See Also</span></span>  
 [<span data-ttu-id="3abf1-137">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3abf1-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
