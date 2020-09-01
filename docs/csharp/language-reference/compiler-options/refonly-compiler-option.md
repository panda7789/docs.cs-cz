---
description: -Nepoužívejte refout (možnosti kompilátoru C#)
title: -Nepoužívejte refout (možnosti kompilátoru C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: f9a92462203bedff93a4a711ca8742465b7a561c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124744"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="72239-103">-Nepoužívejte refout (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="72239-103">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="72239-104">Možnost **-nepoužívejte refout** označuje, že referenční sestavení by měl být výstupem namísto sestavení implementace jako primární výstup.</span><span class="sxs-lookup"><span data-stu-id="72239-104">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="72239-105">`-refonly`Parametr tiše zakáže soubory PDB na výstupu, protože referenční sestavení nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="72239-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="72239-106">Tato možnost odpovídá vlastnosti projektu [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="72239-106">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="72239-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="72239-107">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="72239-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72239-108">Remarks</span></span>

<span data-ttu-id="72239-109">Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny.</span><span class="sxs-lookup"><span data-stu-id="72239-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="72239-110">Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="72239-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="72239-111">Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.</span><span class="sxs-lookup"><span data-stu-id="72239-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="72239-112">`-refonly`Možnosti a [`-refout`](refout-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="72239-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="72239-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="72239-113">See also</span></span>

- [<span data-ttu-id="72239-114">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="72239-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="72239-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="72239-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
