---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 103fe1b6845edfe0a364db979557db63511f6ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130376"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="a1e39-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="a1e39-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="a1e39-103">Vrátí enumerátor pro všechny metody, které jsou definovány v daném modulu NGen a vloží danou metodu.</span><span class="sxs-lookup"><span data-stu-id="a1e39-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1e39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1e39-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="a1e39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1e39-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="a1e39-106">pro Identifikátor modulu NGen.</span><span class="sxs-lookup"><span data-stu-id="a1e39-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="a1e39-107">pro Identifikátor modulu, který definuje `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="a1e39-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="a1e39-108">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="a1e39-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="a1e39-109">pro Identifikátor vložené metody.</span><span class="sxs-lookup"><span data-stu-id="a1e39-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="a1e39-110">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="a1e39-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="a1e39-111">mimo Příznak, který označuje, zda `ppEnum` obsahuje všechny metody pro vkládání dané metody.</span><span class="sxs-lookup"><span data-stu-id="a1e39-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="a1e39-112">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="a1e39-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="a1e39-113">mimo Ukazatel na adresu čítače výčtu</span><span class="sxs-lookup"><span data-stu-id="a1e39-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="a1e39-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1e39-114">Remarks</span></span>

<span data-ttu-id="a1e39-115">`inlineeModuleId` a `inlineeMethodId` dohromady tvoří úplný identifikátor pro metodu, která může být vložena.</span><span class="sxs-lookup"><span data-stu-id="a1e39-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="a1e39-116">Předpokládejme například, že modul `A` definuje metodu `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="a1e39-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="a1e39-117">a modul B definuje `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="a1e39-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="a1e39-118">Umožňuje také předpokládat, že `Fancy.AddTwice` zadává volání `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="a1e39-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="a1e39-119">Profiler může tento enumerátor použít k vyhledání všech metod definovaných v modulu B, které obsahují vložené `Simple.Add`a výsledek by měl vytvořit výčet `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="a1e39-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="a1e39-120">`inlineeModuleId` je identifikátor `A`modulu a `inlineeMethodId` je identifikátor `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="a1e39-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="a1e39-121">Pokud `incompleteData` má hodnotu true poté, co funkce vrátí, enumerátor neobsahuje všechny metody pro vkládání dané metody.</span><span class="sxs-lookup"><span data-stu-id="a1e39-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="a1e39-122">K tomu může dojít v případě, že není ještě načtena jedna nebo více přímých nebo nepřímých závislostí modulu inlinie.</span><span class="sxs-lookup"><span data-stu-id="a1e39-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="a1e39-123">Pokud profiler potřebuje přesná data, zkuste to znovu později, až se načtou další moduly, nejlépe při každém načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="a1e39-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="a1e39-124">Metodu `EnumNgenModuleMethodsInliningThisMethod` lze použít k obejít omezení pro vkládání pro ReJIT.</span><span class="sxs-lookup"><span data-stu-id="a1e39-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="a1e39-125">ReJIT umožňuje profileru změnit implementaci metody a pak za běhu vytvořit nový kód.</span><span class="sxs-lookup"><span data-stu-id="a1e39-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="a1e39-126">Například můžeme změnit `Simple.Add` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a1e39-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="a1e39-127">Vzhledem k tomu, že `Fancy.AddTwice` již byl vložen `Simple.Add`, bude nadále mít stejné chování jako předtím.</span><span class="sxs-lookup"><span data-stu-id="a1e39-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="a1e39-128">Chcete-li toto omezení obejít, volající musí vyhledat všechny metody ve všech modulech, které jsou vloženy `Simple.Add` a použít `ICorProfilerInfo5::RequestRejit` na každou z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="a1e39-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="a1e39-129">Když jsou metody znovu zkompilovány, budou mít nové chování `Simple.Add` místo starého chování.</span><span class="sxs-lookup"><span data-stu-id="a1e39-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1e39-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1e39-130">Requirements</span></span>

<span data-ttu-id="a1e39-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1e39-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a1e39-132">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a1e39-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a1e39-133">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a1e39-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a1e39-134">**Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1e39-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a1e39-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1e39-135">See also</span></span>

- [<span data-ttu-id="a1e39-136">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1e39-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
