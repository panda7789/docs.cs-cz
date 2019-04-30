---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67ae413ae8944757fc90bcde752b9a5fe53cc68f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948522"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="d9a4c-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="d9a4c-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="d9a4c-103">Vrátí enumerátor pro všechny metody, které jsou definovány v zadaném modulu NGen a vložené dané metody.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9a4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9a4c-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="d9a4c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9a4c-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="d9a4c-106">[in] Identifikátor modulu technologie NGen.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="d9a4c-107">[in] Identifikátor modulu, který definuje `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="d9a4c-108">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="d9a4c-109">[in] Identifikátor je vložená metoda.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="d9a4c-110">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="d9a4c-111">[out] Příznak označující, zda `ppEnum` obsahuje všechny metody vkládání dané metody.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="d9a4c-112">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="d9a4c-113">[out] Ukazatel na adresu enumerátor</span><span class="sxs-lookup"><span data-stu-id="d9a4c-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="d9a4c-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9a4c-114">Remarks</span></span>

<span data-ttu-id="d9a4c-115">`inlineeModuleId` a `inlineeMethodId` společně tvoří úplný identifikátor pro metodu, která mohou být vložená.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="d9a4c-116">Předpokládejme například, modul `A` definuje metodu `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="d9a4c-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="d9a4c-117">a modul B definuje `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="d9a4c-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="d9a4c-118">Umožňuje taky se předpokládá, že `Fancy.AddTwice` inlines volání do `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="d9a4c-119">Profiler může použít výčet najít všechny metody definované v modulu B které vložené `Simple.Add`, a výsledek by výčet `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="d9a4c-120">`inlineeModuleId` identifikátor modulu `A`, a `inlineeMethodId` je identifikátor `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="d9a4c-121">Pokud `incompleteData` platí za funkci vrací enumerátor neobsahuje všechny metody vkládání dané metody.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="d9a4c-122">K tomu může dojít v případě, že jedna nebo přímou nebo nepřímou závislostmi inliners modulu nebyly dosud načteny.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="d9a4c-123">Pokud profiler přesná data, je při další moduly se načítají, pokud možno na každého modulu zatížení opakovat později.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="d9a4c-124">`EnumNgenModuleMethodsInliningThisMethod` Metodu je možné obejít omezení na vkládání pro ReJIT.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="d9a4c-125">ReJIT umožňuje profileru, změňte implementaci metody a pak vytvořte nový kód pro něj v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="d9a4c-126">Můžeme například změnit `Simple.Add` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d9a4c-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="d9a4c-127">Ale protože `Fancy.AddTwice` má již vložených `Simple.Add`, nadále mají stejné chování jako předtím.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="d9a4c-128">Toto omezení obejít, volající musí vyhledat všechny metody ve všech modulech přímo tady `Simple.Add` a použít `ICorProfilerInfo5::RequestRejit` na každé z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="d9a4c-129">Pokud metody jsou znovu zkompilovány, mají nové chování `Simple.Add` místo staré chování.</span><span class="sxs-lookup"><span data-stu-id="d9a4c-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="d9a4c-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9a4c-130">Requirements</span></span>

<span data-ttu-id="d9a4c-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9a4c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="d9a4c-132">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d9a4c-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d9a4c-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9a4c-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d9a4c-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9a4c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d9a4c-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9a4c-135">See also</span></span>

- [<span data-ttu-id="d9a4c-136">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9a4c-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)