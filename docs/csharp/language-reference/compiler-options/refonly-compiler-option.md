---
title: -refonly (možnosti kompilátoru C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: c380df1cb473fcd187e56bb0a338a909dd3ac894
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217344"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="6cb09-102">-refonly (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="6cb09-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="6cb09-103">**- Refonly** možnost označuje, že referenční sestavení by se měly zobrazovat místo implementace sestavení, jako primární výstup.</span><span class="sxs-lookup"><span data-stu-id="6cb09-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="6cb09-104">`-refonly` Parametr bezobslužně zakáže výstup vytvořeného soubory PDB, jako referenční sestavení nelze provést.</span><span class="sxs-lookup"><span data-stu-id="6cb09-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="6cb09-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cb09-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="6cb09-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cb09-106">Remarks</span></span>

<span data-ttu-id="6cb09-107">Sestavení obsahující jenom metadata obsahovat jejich základní metoda nahradí jediný `throw null` textu, ale zahrnout všichni členové s výjimkou anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="6cb09-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="6cb09-108">Důvod použití `throw null` těla (na rozdíl od žádné těla) je, aby PEVerify může spouštět a předat (tedy ověření úplnost metadat).</span><span class="sxs-lookup"><span data-stu-id="6cb09-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="6cb09-109">Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut.</span><span class="sxs-lookup"><span data-stu-id="6cb09-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="6cb09-110">Tento atribut je možné zadat zdroj (pak kompilátor nebudete muset syntetizace ji).</span><span class="sxs-lookup"><span data-stu-id="6cb09-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="6cb09-111">Z důvodu tohoto atributu moduly runtime odmítne načíst odkaz na sestavení pro spuštění (ale stále může být načíst v režimu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="6cb09-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="6cb09-112">Nástroje, které odpovídala v sestavení je potřeba zajistit, aby že jejich načtení referenční sestavení jako pouze pro reflexi, jinak se se zobrazí chyba načtení typu z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6cb09-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="6cb09-113">Referenční sestavení další odebrání pouze metadata sestavení metadat (soukromé členy):</span><span class="sxs-lookup"><span data-stu-id="6cb09-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="6cb09-114">Referenční sestavení má jenom odkazy pro vše potřebné v plochy rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6cb09-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="6cb09-115">Skutečné sestavení může mít další odkazy týkající se konkrétní implementace.</span><span class="sxs-lookup"><span data-stu-id="6cb09-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="6cb09-116">Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na žádné typů nezbytných pro `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="6cb09-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="6cb09-117">V případech, kde jejich odebrání nebude mít vliv na viditelně kompilace se odeberou privátní funkce členy (metody, vlastnosti a události).</span><span class="sxs-lookup"><span data-stu-id="6cb09-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="6cb09-118">Pokud neexistují žádné `InternalsVisibleTo` atributy, proveďte pro vnitřní funkce členy stejné.</span><span class="sxs-lookup"><span data-stu-id="6cb09-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="6cb09-119">Ale všechny typy (včetně privátního nebo vnořené typy) jsou uchovávány v referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="6cb09-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="6cb09-120">Všechny atributy jsou uchovány (i interní ty).</span><span class="sxs-lookup"><span data-stu-id="6cb09-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="6cb09-121">Všechny virtuální metody jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="6cb09-121">All virtual methods are kept.</span></span> <span data-ttu-id="6cb09-122">Explicitní implementace rozhraní jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="6cb09-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="6cb09-123">– Explicitně implementovaná vlastností a událostí jsou zachovány, jako jsou virtuální jejich přístupových objektů (a jsou proto v).</span><span class="sxs-lookup"><span data-stu-id="6cb09-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="6cb09-124">Všechna pole struktury jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="6cb09-124">All fields of a struct are kept.</span></span> <span data-ttu-id="6cb09-125">(Toto je kandidátem pro metodu post-C#-7.1 upřesnění)</span><span class="sxs-lookup"><span data-stu-id="6cb09-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="6cb09-126">`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="6cb09-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cb09-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cb09-127">See also</span></span>
 [<span data-ttu-id="6cb09-128">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6cb09-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="6cb09-129">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="6cb09-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
