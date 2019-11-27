---
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 3649a24a52cc6a448ea7cf4d850915adf02147fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348655"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="69159-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69159-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="69159-103">Možnost **-refout** Určuje cestu k souboru, kde by měl být výstup referenčního sestavení.</span><span class="sxs-lookup"><span data-stu-id="69159-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="69159-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69159-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="69159-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="69159-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="69159-106">Cesta a název souboru referenčního sestavení.</span><span class="sxs-lookup"><span data-stu-id="69159-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="69159-107">Obvykle by měla být v podsložce primárního sestavení.</span><span class="sxs-lookup"><span data-stu-id="69159-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="69159-108">Doporučená konvence (používaná nástrojem MSBuild) slouží k umístění referenčního sestavení do podsložky ref/v relativní vzhledem k primárnímu sestavení.</span><span class="sxs-lookup"><span data-stu-id="69159-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="69159-109">Musí existovat všechny složky v `filepath`. kompilátor je nevytváří.</span><span class="sxs-lookup"><span data-stu-id="69159-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="69159-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69159-110">Remarks</span></span>

<span data-ttu-id="69159-111">Visual Basic podporuje přepínač `-refout` počínaje verzí 15,3.</span><span class="sxs-lookup"><span data-stu-id="69159-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="69159-112">Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny.</span><span class="sxs-lookup"><span data-stu-id="69159-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="69159-113">Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="69159-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="69159-114">Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.</span><span class="sxs-lookup"><span data-stu-id="69159-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="69159-115">Možnosti `-refout` a [`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="69159-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="69159-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69159-116">See also</span></span>

- [<span data-ttu-id="69159-117">-refonly</span><span class="sxs-lookup"><span data-stu-id="69159-117">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="69159-118">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="69159-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="69159-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="69159-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
