---
title: -Nepoužívejte refout (C# možnosti kompilátoru)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: eb62f98c5d548fe3583d3422eb7b6020a82c296a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606482"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="1d330-102">-Nepoužívejte refout (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="1d330-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="1d330-103">Možnost **-nepoužívejte refout** označuje, že referenční sestavení by měl být výstupem namísto sestavení implementace jako primární výstup.</span><span class="sxs-lookup"><span data-stu-id="1d330-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="1d330-104">`-refonly` Parametr tiše zakáže soubory PDB na výstupu, protože referenční sestavení nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="1d330-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="1d330-105">Tato možnost odpovídá vlastnosti projektu [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1d330-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d330-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d330-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="1d330-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d330-107">Remarks</span></span>

<span data-ttu-id="1d330-108">Sestavení pouze s metadaty mají své tělo metody nahrazené jediným `throw null` tělem, ale obsahují všechny členy kromě anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="1d330-108">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="1d330-109">Důvodem použití `throw null` těl (na rozdíl od žádného těla) je, že nástroj PEverify může běžet a předávat (čímž ověřuje úplnost metadat).</span><span class="sxs-lookup"><span data-stu-id="1d330-109">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="1d330-110">Referenční sestavení obsahují atribut na úrovni `ReferenceAssembly` sestavení.</span><span class="sxs-lookup"><span data-stu-id="1d330-110">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="1d330-111">Tento atribut může být zadán ve zdroji (pak ho kompilátor nebude muset syntetizovat).</span><span class="sxs-lookup"><span data-stu-id="1d330-111">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="1d330-112">Z důvodu tohoto atributu modul runtime odmítne načíst referenční sestavení ke spuštění (ale mohou být nadále načtena v režimu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="1d330-112">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="1d330-113">Nástroje, které reflektují sestavení, musí zajistit, aby načetly referenční sestavení pouze v případě reflexe, jinak obdrží chybu výjimek z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1d330-113">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="1d330-114">Referenční sestavení dále odstraňují metadata (soukromá členové) od sestavení, která jsou pouze metadata:</span><span class="sxs-lookup"><span data-stu-id="1d330-114">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="1d330-115">Referenční sestavení obsahuje pouze odkazy na to, co potřebuje na povrchu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1d330-115">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="1d330-116">Reálné sestavení může mít další odkazy týkající se konkrétních implementací.</span><span class="sxs-lookup"><span data-stu-id="1d330-116">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="1d330-117">Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na žádné typy, které jsou požadovány pro. `dynamic`</span><span class="sxs-lookup"><span data-stu-id="1d330-117">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="1d330-118">Soukromá funkce – členové (metody, vlastnosti a události) jsou odebrány v případech, kdy jejich odebrání nepozorovatelně ovlivní kompilaci.</span><span class="sxs-lookup"><span data-stu-id="1d330-118">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="1d330-119">Pokud neexistují žádné <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy, udělejte totéž pro členy vnitřní funkce.</span><span class="sxs-lookup"><span data-stu-id="1d330-119">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="1d330-120">Všechny typy (včetně privátních nebo vnořených typů) jsou však uloženy v referenčních sestaveních.</span><span class="sxs-lookup"><span data-stu-id="1d330-120">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="1d330-121">Všechny atributy jsou zachovány (i interní).</span><span class="sxs-lookup"><span data-stu-id="1d330-121">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="1d330-122">Všechny virtuální metody jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="1d330-122">All virtual methods are kept.</span></span> <span data-ttu-id="1d330-123">Explicitní implementace rozhraní jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="1d330-123">Explicit interface implementations are kept.</span></span> <span data-ttu-id="1d330-124">Explicitně implementované vlastnosti a události jsou zachované, protože jejich přistupující objekty jsou virtuální (a jsou proto zachované).</span><span class="sxs-lookup"><span data-stu-id="1d330-124">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="1d330-125">Všechna pole struktury jsou zachována.</span><span class="sxs-lookup"><span data-stu-id="1d330-125">All fields of a struct are kept.</span></span> <span data-ttu-id="1d330-126">(Toto je kandidát pro upřesnění poC#7,1)</span><span class="sxs-lookup"><span data-stu-id="1d330-126">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="1d330-127">Možnosti `-refonly` [a`-refout`](refout-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="1d330-127">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d330-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d330-128">See also</span></span>

- [<span data-ttu-id="1d330-129">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1d330-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1d330-130">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="1d330-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
