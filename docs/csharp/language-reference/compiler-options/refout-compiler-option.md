---
title: -refout (C# možnosti kompilátoru)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771763"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="8e7d3-102">-refout (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="8e7d3-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="8e7d3-103">Možnost **-refout** Určuje cestu k souboru, kde by měl být výstup referenčního sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="8e7d3-104">To se týká `metadataPeStream` v rozhraní API pro generování.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="8e7d3-105">Tato možnost odpovídá vlastnosti projektu [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e7d3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e7d3-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="8e7d3-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="8e7d3-107">Arguments</span></span>

 <span data-ttu-id="8e7d3-108">`filepath` FilePath pro referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="8e7d3-109">Obecně se musí shodovat s primárním sestavením.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="8e7d3-110">Doporučená konvence (používaná nástrojem MSBuild) slouží k umístění referenčního sestavení do podsložky ref/v relativní vzhledem k primárnímu sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e7d3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e7d3-111">Remarks</span></span>

<span data-ttu-id="8e7d3-112">Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="8e7d3-113">Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="8e7d3-114">Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="8e7d3-115">Možnosti `-refout` a [`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="8e7d3-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e7d3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e7d3-116">See also</span></span>

- [<span data-ttu-id="8e7d3-117">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e7d3-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="8e7d3-118">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="8e7d3-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
