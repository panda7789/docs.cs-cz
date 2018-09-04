---
title: -refout (možnosti kompilátoru C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: c15308d27b504f22b266e28f6db0caf837ae36c5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518387"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="6c1dd-102">-refout (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="6c1dd-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="6c1dd-103">**- Refout** možnost znamená, že referenční sestavení by měl být výstup místo provedení sestavení, jako primární výstup.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="6c1dd-104">`-refonly` Parametr tiše zakáže generování souborů pdb, jako referenční sestavení nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c1dd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c1dd-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="6c1dd-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c1dd-106">Remarks</span></span>

<span data-ttu-id="6c1dd-107">Obsahující jenom metadata sestavení mají jejich těl metod nahradit pomocí jediného `throw null` textu, ale zahrnout všichni členové s výjimkou anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="6c1dd-108">Důvod pro použití `throw null` subjektů (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).</span><span class="sxs-lookup"><span data-stu-id="6c1dd-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="6c1dd-109">Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="6c1dd-110">Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho).</span><span class="sxs-lookup"><span data-stu-id="6c1dd-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="6c1dd-111">Z důvodu tohoto atributu moduly runtime odmítne načíst referenční sestavení pro spuštění (ale stále může být načten v režimu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="6c1dd-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="6c1dd-112">Nástroje, které odpovídají na sestavení je potřeba zajistit, že se načítají referenční sestavení jako pouze pro reflexi, jinak se mu nepřidají chyby z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="6c1dd-113">Další referenční sestavení odebrání metadat (soukromé členy) obsahující jenom metadata sestavení:</span><span class="sxs-lookup"><span data-stu-id="6c1dd-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="6c1dd-114">Referenční sestavení má jenom odkazy na to, co potřebuje na povrchu API.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="6c1dd-115">Skutečné sestavení může mít další odkazy týkající se konkrétní implementace.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="6c1dd-116">Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na všechny typy vyžadované pro `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="6c1dd-117">V případech, kdy jejich odebrání nebude mít vliv na viditelně kompilace se odeberou soukromé funkce členy (metody, vlastnosti a události).</span><span class="sxs-lookup"><span data-stu-id="6c1dd-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="6c1dd-118">Pokud neexistují žádné `InternalsVisibleTo` atributy, provést totéž pro interní členy funkce.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="6c1dd-119">Ale všechny typy (včetně privátního nebo vnořené typy) jsou uloženy v referenčních sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="6c1dd-120">Všechny atributy jsou udržovány (pravidla i interní).</span><span class="sxs-lookup"><span data-stu-id="6c1dd-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="6c1dd-121">Všechny virtuální metody jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-121">All virtual methods are kept.</span></span> <span data-ttu-id="6c1dd-122">Explicitní implementace rozhraní zůstanou.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="6c1dd-123">Explicitně implementovaný vlastnosti a události se neodstraní jejich přístupových objektů jsou virtuální (a tedy uchovávají).</span><span class="sxs-lookup"><span data-stu-id="6c1dd-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="6c1dd-124">Všechna pole struktury jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-124">All fields of a struct are kept.</span></span> <span data-ttu-id="6c1dd-125">(Toto je Release candidate pro metodu post-C# – vylepšení 7.1)</span><span class="sxs-lookup"><span data-stu-id="6c1dd-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="6c1dd-126">`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="6c1dd-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c1dd-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c1dd-127">See also</span></span>

- [<span data-ttu-id="6c1dd-128">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6c1dd-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="6c1dd-129">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="6c1dd-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
