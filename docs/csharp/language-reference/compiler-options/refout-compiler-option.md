---
title: -refout (Možnosti kompilátoru Jazyka C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771763"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="575d8-102">-refout (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="575d8-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="575d8-103">Volba **-refout** určuje cestu k souboru, kde by mělo být výstupní sestavení odkazu.</span><span class="sxs-lookup"><span data-stu-id="575d8-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="575d8-104">To se `metadataPeStream` promítá do v rozhraní EMIT API.</span><span class="sxs-lookup"><span data-stu-id="575d8-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="575d8-105">Tato možnost odpovídá vlastnosti [projektu ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) msbuild.</span><span class="sxs-lookup"><span data-stu-id="575d8-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="575d8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="575d8-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="575d8-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="575d8-107">Arguments</span></span>

 <span data-ttu-id="575d8-108">`filepath`Cesta souboru pro referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="575d8-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="575d8-109">Obecně by měl odpovídat primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="575d8-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="575d8-110">Doporučená konvence (používá MSBuild) je umístit referenční sestavení v podsložce "ref/" vzhledem k primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="575d8-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="575d8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="575d8-111">Remarks</span></span>

<span data-ttu-id="575d8-112">Referenční sestavení jsou zvláštní typ sestavení, které obsahují pouze minimální množství metadat, které jsou nutné k reprezentaci veřejného povrchu rozhraní API knihovny.</span><span class="sxs-lookup"><span data-stu-id="575d8-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="575d8-113">Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučit všechny implementace členů a deklarace soukromých členů, které nemají žádný pozorovatelný dopad na jejich smlouvy rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="575d8-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="575d8-114">Další informace naleznete [v tématu Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span><span class="sxs-lookup"><span data-stu-id="575d8-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="575d8-115">A `-refout` [`-refonly`](refonly-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="575d8-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="575d8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="575d8-116">See also</span></span>

- [<span data-ttu-id="575d8-117">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="575d8-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="575d8-118">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="575d8-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
