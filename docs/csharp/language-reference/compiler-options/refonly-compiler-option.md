---
title: -Nepoužívejte refout (C# možnosti kompilátoru)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773854"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="8289c-102">-Nepoužívejte refout (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="8289c-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="8289c-103">Možnost **-nepoužívejte refout** označuje, že referenční sestavení by měl být výstupem namísto sestavení implementace jako primární výstup.</span><span class="sxs-lookup"><span data-stu-id="8289c-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="8289c-104">Parametr `-refonly` tiše zakáže soubory pdbí výstupu, protože referenční sestavení nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="8289c-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="8289c-105">Tato možnost odpovídá vlastnosti projektu [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8289c-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="8289c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8289c-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="8289c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8289c-107">Remarks</span></span>

<span data-ttu-id="8289c-108">Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny.</span><span class="sxs-lookup"><span data-stu-id="8289c-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="8289c-109">Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8289c-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="8289c-110">Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.</span><span class="sxs-lookup"><span data-stu-id="8289c-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="8289c-111">Možnosti `-refonly` a [`-refout`](refout-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="8289c-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="8289c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8289c-112">See also</span></span>

- [<span data-ttu-id="8289c-113">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8289c-113">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="8289c-114">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="8289c-114">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
