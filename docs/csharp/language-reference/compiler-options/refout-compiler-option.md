---
title: "-refout (možnosti kompilátoru C#)"
ms.date: 08/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc78165fc8f273948111c174ae0bf0af6591a8ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="refout-c-compiler-options"></a><span data-ttu-id="d7daa-102">/refout (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d7daa-102">/refout (C# Compiler Options)</span></span>

<span data-ttu-id="d7daa-103">**/Refout** možnost určuje cestu k souboru, kde referenční sestavení by měla být výstup.</span><span class="sxs-lookup"><span data-stu-id="d7daa-103">The **/refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="d7daa-104">To znamená, že k `metadataPeStream` v emitování rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d7daa-104">This translates to `metadataPeStream` in the Emit API.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7daa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7daa-105">Syntax</span></span>

```console
/refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="d7daa-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="d7daa-106">Arguments</span></span>

 <span data-ttu-id="d7daa-107">`filepath`Filepath pro referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7daa-107">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="d7daa-108">Obecně je by měl odpovídat u primárních sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7daa-108">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="d7daa-109">Doporučené konvence (používané MSBuild) je umístit referenční sestavení v "ref nebo" podsložky relativně k primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7daa-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7daa-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7daa-110">Remarks</span></span>

<span data-ttu-id="d7daa-111">Sestavení obsahující jenom metadata obsahovat jejich základní metoda nahradí jediný `throw null` textu, ale zahrnout všichni členové s výjimkou anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="d7daa-111">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="d7daa-112">Důvod použití `throw null` těla (na rozdíl od žádné těla) je, aby PEVerify může spouštět a předat (tedy ověření úplnost metadat).</span><span class="sxs-lookup"><span data-stu-id="d7daa-112">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="d7daa-113">Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut.</span><span class="sxs-lookup"><span data-stu-id="d7daa-113">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="d7daa-114">Tento atribut je možné zadat zdroj (pak kompilátor nebudete muset syntetizace ji).</span><span class="sxs-lookup"><span data-stu-id="d7daa-114">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="d7daa-115">Z důvodu tohoto atributu moduly runtime odmítne načíst odkaz na sestavení pro spuštění (ale stále může být načíst v režimu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="d7daa-115">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="d7daa-116">Nástroje, které odpovídala v sestavení je potřeba zajistit, aby že jejich načtení referenční sestavení jako pouze pro reflexi, jinak se se zobrazí chyba načtení typu z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d7daa-116">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="d7daa-117">Referenční sestavení další odebrání pouze metadata sestavení metadat (soukromé členy):</span><span class="sxs-lookup"><span data-stu-id="d7daa-117">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="d7daa-118">Referenční sestavení má jenom odkazy pro vše potřebné v plochy rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d7daa-118">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="d7daa-119">Skutečné sestavení může mít další odkazy týkající se konkrétní implementace.</span><span class="sxs-lookup"><span data-stu-id="d7daa-119">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="d7daa-120">Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na žádné typů nezbytných pro `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="d7daa-120">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="d7daa-121">V případech, kde jejich odebrání nebude mít vliv na viditelně kompilace se odeberou privátní funkce členy (metody, vlastnosti a události).</span><span class="sxs-lookup"><span data-stu-id="d7daa-121">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="d7daa-122">Pokud neexistují žádné `InternalsVisibleTo` atributy, proveďte pro vnitřní funkce členy stejné.</span><span class="sxs-lookup"><span data-stu-id="d7daa-122">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="d7daa-123">Ale všechny typy (včetně privátního nebo vnořené typy) jsou uchovávány v referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7daa-123">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="d7daa-124">Všechny atributy jsou uchovány (i interní ty).</span><span class="sxs-lookup"><span data-stu-id="d7daa-124">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="d7daa-125">Všechny virtuální metody jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="d7daa-125">All virtual methods are kept.</span></span> <span data-ttu-id="d7daa-126">Explicitní implementace rozhraní jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="d7daa-126">Explicit interface implementations are kept.</span></span> <span data-ttu-id="d7daa-127">– Explicitně implementovaná vlastností a událostí jsou zachovány, jako jsou virtuální jejich přístupových objektů (a jsou proto v).</span><span class="sxs-lookup"><span data-stu-id="d7daa-127">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="d7daa-128">Všechna pole struktury jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="d7daa-128">All fields of a struct are kept.</span></span> <span data-ttu-id="d7daa-129">(Toto je kandidátem pro metodu post-C#-7.1 upřesnění)</span><span class="sxs-lookup"><span data-stu-id="d7daa-129">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="d7daa-130">`/refout` a [ `/refonly` ](refonly-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="d7daa-130">The `/refout` and [`/refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7daa-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7daa-131">See Also</span></span>
 [<span data-ttu-id="d7daa-132">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="d7daa-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="d7daa-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="d7daa-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
