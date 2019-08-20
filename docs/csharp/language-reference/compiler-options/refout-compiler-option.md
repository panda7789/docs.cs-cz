---
title: -refout (C# možnosti kompilátoru)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 97cbf540527d0449387b71bb1d97df95b6a4aba4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602513"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="24772-102">-refout (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="24772-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="24772-103">Možnost **-refout** Určuje cestu k souboru, kde by měl být výstup referenčního sestavení.</span><span class="sxs-lookup"><span data-stu-id="24772-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="24772-104">To se týká `metadataPeStream` v rozhraní API Emit.</span><span class="sxs-lookup"><span data-stu-id="24772-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="24772-105">Tato možnost odpovídá vlastnosti projektu [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="24772-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="24772-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24772-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="24772-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="24772-107">Arguments</span></span>

 <span data-ttu-id="24772-108">`filepath`FilePath pro referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="24772-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="24772-109">Obecně se musí shodovat s primárním sestavením.</span><span class="sxs-lookup"><span data-stu-id="24772-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="24772-110">Doporučená konvence (používaná nástrojem MSBuild) slouží k umístění referenčního sestavení do podsložky ref/v relativní vzhledem k primárnímu sestavení.</span><span class="sxs-lookup"><span data-stu-id="24772-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="24772-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24772-111">Remarks</span></span>

<span data-ttu-id="24772-112">Sestavení pouze s metadaty mají své tělo metody nahrazené jediným `throw null` tělem, ale obsahují všechny členy kromě anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="24772-112">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="24772-113">Důvodem použití `throw null` těl (na rozdíl od žádného těla) je, že nástroj PEverify může běžet a předávat (čímž ověřuje úplnost metadat).</span><span class="sxs-lookup"><span data-stu-id="24772-113">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="24772-114">Referenční sestavení obsahují atribut na úrovni `ReferenceAssembly` sestavení.</span><span class="sxs-lookup"><span data-stu-id="24772-114">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="24772-115">Tento atribut může být zadán ve zdroji (pak ho kompilátor nebude muset syntetizovat).</span><span class="sxs-lookup"><span data-stu-id="24772-115">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="24772-116">Z důvodu tohoto atributu modul runtime odmítne načíst referenční sestavení ke spuštění (ale mohou být nadále načtena v režimu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="24772-116">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="24772-117">Nástroje, které reflektují sestavení, musí zajistit, aby načetly referenční sestavení pouze v případě reflexe, jinak obdrží chybu výjimek z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="24772-117">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="24772-118">Referenční sestavení dále odstraňují metadata (soukromá členové) od sestavení, která jsou pouze metadata:</span><span class="sxs-lookup"><span data-stu-id="24772-118">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="24772-119">Referenční sestavení obsahuje pouze odkazy na to, co potřebuje na povrchu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="24772-119">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="24772-120">Reálné sestavení může mít další odkazy týkající se konkrétních implementací.</span><span class="sxs-lookup"><span data-stu-id="24772-120">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="24772-121">Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na žádné typy, které jsou požadovány pro. `dynamic`</span><span class="sxs-lookup"><span data-stu-id="24772-121">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="24772-122">Soukromá funkce – členové (metody, vlastnosti a události) jsou odebrány v případech, kdy jejich odebrání nepozorovatelně ovlivní kompilaci.</span><span class="sxs-lookup"><span data-stu-id="24772-122">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="24772-123">Pokud neexistují žádné <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy, udělejte totéž pro členy vnitřní funkce.</span><span class="sxs-lookup"><span data-stu-id="24772-123">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="24772-124">Všechny typy (včetně privátních nebo vnořených typů) jsou však uloženy v referenčních sestaveních.</span><span class="sxs-lookup"><span data-stu-id="24772-124">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="24772-125">Všechny atributy jsou zachovány (i interní).</span><span class="sxs-lookup"><span data-stu-id="24772-125">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="24772-126">Všechny virtuální metody jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="24772-126">All virtual methods are kept.</span></span> <span data-ttu-id="24772-127">Explicitní implementace rozhraní jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="24772-127">Explicit interface implementations are kept.</span></span> <span data-ttu-id="24772-128">Explicitně implementované vlastnosti a události jsou zachované, protože jejich přistupující objekty jsou virtuální (a jsou proto zachované).</span><span class="sxs-lookup"><span data-stu-id="24772-128">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="24772-129">Všechna pole struktury jsou zachována.</span><span class="sxs-lookup"><span data-stu-id="24772-129">All fields of a struct are kept.</span></span> <span data-ttu-id="24772-130">(Toto je kandidát pro upřesnění poC#7,1)</span><span class="sxs-lookup"><span data-stu-id="24772-130">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="24772-131">Možnosti `-refout` [a`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="24772-131">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="24772-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24772-132">See also</span></span>

- [<span data-ttu-id="24772-133">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="24772-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="24772-134">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="24772-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
