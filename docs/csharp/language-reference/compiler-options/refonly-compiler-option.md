---
title: -refonly (Možnosti kompilátoru Jazyka C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773854"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="897f2-102">-refonly (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="897f2-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="897f2-103">Možnost **-refonly** označuje, že referenční sestavení by mělo být výstupní místo sestavení implementace jako primární výstup.</span><span class="sxs-lookup"><span data-stu-id="897f2-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="897f2-104">Parametr `-refonly` tiše zakáže odchozí pdb, jako referenční sestavení nelze provést.</span><span class="sxs-lookup"><span data-stu-id="897f2-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="897f2-105">Tato možnost odpovídá vlastnosti [projektu ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) msbuild.</span><span class="sxs-lookup"><span data-stu-id="897f2-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="897f2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="897f2-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="897f2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="897f2-107">Remarks</span></span>

<span data-ttu-id="897f2-108">Referenční sestavení jsou zvláštní typ sestavení, které obsahují pouze minimální množství metadat, které jsou nutné k reprezentaci veřejného povrchu rozhraní API knihovny.</span><span class="sxs-lookup"><span data-stu-id="897f2-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="897f2-109">Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučit všechny implementace členů a deklarace soukromých členů, které nemají žádný pozorovatelný dopad na jejich smlouvy rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="897f2-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="897f2-110">Další informace naleznete [v tématu Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span><span class="sxs-lookup"><span data-stu-id="897f2-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="897f2-111">A `-refonly` [`-refout`](refout-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="897f2-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="897f2-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="897f2-112">See also</span></span>

- [<span data-ttu-id="897f2-113">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="897f2-113">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="897f2-114">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="897f2-114">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
