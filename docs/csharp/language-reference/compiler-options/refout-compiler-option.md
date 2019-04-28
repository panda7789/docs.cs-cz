---
title: -refout (možnosti kompilátoru C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 34f7b62c0d9a14c52dde0ddd4ac0d5c29a3b5b75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662462"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="99bac-102">-refout (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="99bac-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="99bac-103">**- Refout** možnost určuje, kde referenční sestavení by mělo být výstupní cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="99bac-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="99bac-104">To se přeloží na `metadataPeStream` v rozhraní API pro generování.</span><span class="sxs-lookup"><span data-stu-id="99bac-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="99bac-105">Tato možnost odpovídá nabídce [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) vlastnosti nástroje MSBuild projektu.</span><span class="sxs-lookup"><span data-stu-id="99bac-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="99bac-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99bac-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="99bac-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="99bac-107">Arguments</span></span>

 <span data-ttu-id="99bac-108">`filepath` Cesta k souboru pro referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="99bac-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="99bac-109">Obecně to by měla odpovídat hodnotě primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="99bac-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="99bac-110">Doporučené konvence (používány nástrojem MSBuild), je umístit odkaz na sestavení v "ref /" podsložku vzhledem k primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="99bac-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="99bac-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99bac-111">Remarks</span></span>

<span data-ttu-id="99bac-112">Obsahující jenom metadata sestavení mají jejich těl metod nahradit pomocí jediného `throw null` textu, ale zahrnout všichni členové s výjimkou anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="99bac-112">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="99bac-113">Důvod pro použití `throw null` subjektů (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).</span><span class="sxs-lookup"><span data-stu-id="99bac-113">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="99bac-114">Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut.</span><span class="sxs-lookup"><span data-stu-id="99bac-114">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="99bac-115">Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho).</span><span class="sxs-lookup"><span data-stu-id="99bac-115">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="99bac-116">Z důvodu tohoto atributu moduly runtime odmítne načíst referenční sestavení pro spuštění (ale stále může být načten v režimu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="99bac-116">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="99bac-117">Nástroje, které odpovídají na sestavení je potřeba zajistit, že se načítají referenční sestavení jako pouze pro reflexi, jinak se mu nepřidají chyby z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="99bac-117">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="99bac-118">Další referenční sestavení odebrání metadat (soukromé členy) obsahující jenom metadata sestavení:</span><span class="sxs-lookup"><span data-stu-id="99bac-118">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="99bac-119">Referenční sestavení má jenom odkazy na to, co potřebuje na povrchu API.</span><span class="sxs-lookup"><span data-stu-id="99bac-119">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="99bac-120">Skutečné sestavení může mít další odkazy týkající se konkrétní implementace.</span><span class="sxs-lookup"><span data-stu-id="99bac-120">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="99bac-121">Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na všechny typy vyžadované pro `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="99bac-121">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="99bac-122">V případech, kdy jejich odebrání nebude mít vliv na viditelně kompilace se odeberou soukromé funkce členy (metody, vlastnosti a události).</span><span class="sxs-lookup"><span data-stu-id="99bac-122">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="99bac-123">Pokud neexistují žádné <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy, provést totéž pro interní členy funkce.</span><span class="sxs-lookup"><span data-stu-id="99bac-123">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="99bac-124">Ale všechny typy (včetně privátního nebo vnořené typy) jsou uloženy v referenčních sestavení.</span><span class="sxs-lookup"><span data-stu-id="99bac-124">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="99bac-125">Všechny atributy jsou udržovány (pravidla i interní).</span><span class="sxs-lookup"><span data-stu-id="99bac-125">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="99bac-126">Všechny virtuální metody jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="99bac-126">All virtual methods are kept.</span></span> <span data-ttu-id="99bac-127">Explicitní implementace rozhraní zůstanou.</span><span class="sxs-lookup"><span data-stu-id="99bac-127">Explicit interface implementations are kept.</span></span> <span data-ttu-id="99bac-128">Explicitně implementovaný vlastnosti a události se neodstraní jejich přístupových objektů jsou virtuální (a tedy uchovávají).</span><span class="sxs-lookup"><span data-stu-id="99bac-128">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="99bac-129">Všechna pole struktury jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="99bac-129">All fields of a struct are kept.</span></span> <span data-ttu-id="99bac-130">(Toto je Release candidate pro metodu post-C# – vylepšení 7.1)</span><span class="sxs-lookup"><span data-stu-id="99bac-130">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="99bac-131">`-refout` a [ `-refonly` ](refonly-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="99bac-131">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="99bac-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99bac-132">See also</span></span>

- [<span data-ttu-id="99bac-133">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="99bac-133">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="99bac-134">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="99bac-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
