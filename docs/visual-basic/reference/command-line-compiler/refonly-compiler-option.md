---
title: -Nepoužívejte refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 8e64989ac1410b51991027ffcb33e8dae0c0284b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775568"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="b954b-102">-Nepoužívejte refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b954b-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="b954b-103">Možnost **-nepoužívejte refout** označuje, že primární výstup kompilace by měl být referenční sestavení namísto sestavení implementace.</span><span class="sxs-lookup"><span data-stu-id="b954b-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="b954b-104">Parametr `-refonly` tiše zakáže soubory pdbí výstupu, protože referenční sestavení nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="b954b-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="b954b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b954b-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="b954b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b954b-106">Remarks</span></span>

<span data-ttu-id="b954b-107">Visual Basic podporuje přepínač `-refonly` počínaje verzí 15,3.</span><span class="sxs-lookup"><span data-stu-id="b954b-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="b954b-108">Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny.</span><span class="sxs-lookup"><span data-stu-id="b954b-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="b954b-109">Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b954b-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="b954b-110">Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.</span><span class="sxs-lookup"><span data-stu-id="b954b-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="b954b-111">Možnosti `-refonly` a [`-refout`](refout-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="b954b-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="b954b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b954b-112">See also</span></span>

- [<span data-ttu-id="b954b-113">-refout</span><span class="sxs-lookup"><span data-stu-id="b954b-113">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="b954b-114">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="b954b-114">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b954b-115">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="b954b-115">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
