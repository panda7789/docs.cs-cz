---
description: -refout (možnosti kompilátoru C#)
title: -refout (možnosti kompilátoru C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 424782e4607fea63130e95ab09a671c75fe1404d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128711"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="4d5be-103">-refout (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="4d5be-103">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="4d5be-104">Možnost **-refout** Určuje cestu k souboru, kde by měl být výstup referenčního sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d5be-104">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="4d5be-105">To se týká `metadataPeStream` v rozhraní API Emit.</span><span class="sxs-lookup"><span data-stu-id="4d5be-105">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="4d5be-106">Tato možnost odpovídá vlastnosti projektu [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="4d5be-106">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d5be-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d5be-107">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="4d5be-108">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4d5be-108">Arguments</span></span>

 <span data-ttu-id="4d5be-109">`filepath` FilePath pro referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d5be-109">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="4d5be-110">Obecně se musí shodovat s primárním sestavením.</span><span class="sxs-lookup"><span data-stu-id="4d5be-110">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="4d5be-111">Doporučená konvence (používaná nástrojem MSBuild) slouží k umístění referenčního sestavení do podsložky ref/v relativní vzhledem k primárnímu sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d5be-111">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d5be-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d5be-112">Remarks</span></span>

<span data-ttu-id="4d5be-113">Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny.</span><span class="sxs-lookup"><span data-stu-id="4d5be-113">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="4d5be-114">Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4d5be-114">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="4d5be-115">Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.</span><span class="sxs-lookup"><span data-stu-id="4d5be-115">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="4d5be-116">`-refout`Možnosti a [`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="4d5be-116">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d5be-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d5be-117">See also</span></span>

- [<span data-ttu-id="4d5be-118">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="4d5be-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4d5be-119">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="4d5be-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
