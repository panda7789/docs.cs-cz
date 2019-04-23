---
title: -refout (možnosti kompilátoru C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 97245b50881d687572c1ae1df649651831822094
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978481"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="875b2-102">-refout (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="875b2-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="875b2-103">**- Refout** možnost znamená, že referenční sestavení by měl být výstup místo provedení sestavení, jako primární výstup.</span><span class="sxs-lookup"><span data-stu-id="875b2-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="875b2-104">`-refonly` Parametr tiše zakáže generování souborů pdb, jako referenční sestavení nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="875b2-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="875b2-105">Tato možnost odpovídá nabídce [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) vlastnosti nástroje MSBuild projektu.</span><span class="sxs-lookup"><span data-stu-id="875b2-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="875b2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="875b2-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="875b2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="875b2-107">Remarks</span></span>

<span data-ttu-id="875b2-108">Obsahující jenom metadata sestavení mají jejich těl metod nahradit pomocí jediného `throw null` textu, ale zahrnout všichni členové s výjimkou anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="875b2-108">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="875b2-109">Důvod pro použití `throw null` subjektů (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).</span><span class="sxs-lookup"><span data-stu-id="875b2-109">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="875b2-110">Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut.</span><span class="sxs-lookup"><span data-stu-id="875b2-110">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="875b2-111">Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho).</span><span class="sxs-lookup"><span data-stu-id="875b2-111">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="875b2-112">Z důvodu tohoto atributu moduly runtime odmítne načíst referenční sestavení pro spuštění (ale stále může být načten v režimu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="875b2-112">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="875b2-113">Nástroje, které odpovídají na sestavení je potřeba zajistit, že se načítají referenční sestavení jako pouze pro reflexi, jinak se mu nepřidají chyby z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="875b2-113">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="875b2-114">Další referenční sestavení odebrání metadat (soukromé členy) obsahující jenom metadata sestavení:</span><span class="sxs-lookup"><span data-stu-id="875b2-114">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="875b2-115">Referenční sestavení má jenom odkazy na to, co potřebuje na povrchu API.</span><span class="sxs-lookup"><span data-stu-id="875b2-115">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="875b2-116">Skutečné sestavení může mít další odkazy týkající se konkrétní implementace.</span><span class="sxs-lookup"><span data-stu-id="875b2-116">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="875b2-117">Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na všechny typy vyžadované pro `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="875b2-117">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="875b2-118">V případech, kdy jejich odebrání nebude mít vliv na viditelně kompilace se odeberou soukromé funkce členy (metody, vlastnosti a události).</span><span class="sxs-lookup"><span data-stu-id="875b2-118">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="875b2-119">Pokud neexistují žádné <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy, provést totéž pro interní členy funkce.</span><span class="sxs-lookup"><span data-stu-id="875b2-119">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="875b2-120">Ale všechny typy (včetně privátního nebo vnořené typy) jsou uloženy v referenčních sestavení.</span><span class="sxs-lookup"><span data-stu-id="875b2-120">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="875b2-121">Všechny atributy jsou udržovány (pravidla i interní).</span><span class="sxs-lookup"><span data-stu-id="875b2-121">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="875b2-122">Všechny virtuální metody jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="875b2-122">All virtual methods are kept.</span></span> <span data-ttu-id="875b2-123">Explicitní implementace rozhraní zůstanou.</span><span class="sxs-lookup"><span data-stu-id="875b2-123">Explicit interface implementations are kept.</span></span> <span data-ttu-id="875b2-124">Explicitně implementovaný vlastnosti a události se neodstraní jejich přístupových objektů jsou virtuální (a tedy uchovávají).</span><span class="sxs-lookup"><span data-stu-id="875b2-124">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="875b2-125">Všechna pole struktury jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="875b2-125">All fields of a struct are kept.</span></span> <span data-ttu-id="875b2-126">(Toto je Release candidate pro metodu post-C# – vylepšení 7.1)</span><span class="sxs-lookup"><span data-stu-id="875b2-126">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="875b2-127">`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="875b2-127">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="875b2-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="875b2-128">See also</span></span>

- [<span data-ttu-id="875b2-129">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="875b2-129">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="875b2-130">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="875b2-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
