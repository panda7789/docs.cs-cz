---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582876"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="b3afd-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3afd-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="b3afd-103">Možnost **-refout** Určuje cestu k souboru, kde by měl být výstup referenčního sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3afd-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="b3afd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3afd-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="b3afd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b3afd-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="b3afd-106">Cesta a název souboru referenčního sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3afd-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="b3afd-107">Obvykle by měla být v podsložce primárního sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3afd-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="b3afd-108">Doporučená konvence (používaná nástrojem MSBuild) slouží k umístění referenčního sestavení do podsložky ref/v relativní vzhledem k primárnímu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3afd-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="b3afd-109">Musí existovat všechny složky v `filepath`. kompilátor je nevytváří.</span><span class="sxs-lookup"><span data-stu-id="b3afd-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3afd-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3afd-110">Remarks</span></span>

<span data-ttu-id="b3afd-111">Visual Basic podporuje přepínač `-refout` počínaje verzí 15,3.</span><span class="sxs-lookup"><span data-stu-id="b3afd-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="b3afd-112">Referenční sestavení jsou pouze metadata sestavení, která obsahují metadata, ale nemají kód implementace.</span><span class="sxs-lookup"><span data-stu-id="b3afd-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="b3afd-113">Zahrnují informace o typu a členu pro vše kromě anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="b3afd-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="b3afd-114">Jejich těla metod jsou nahrazeny jediným příkazem `throw null`.</span><span class="sxs-lookup"><span data-stu-id="b3afd-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="b3afd-115">Důvodem použití `throw null` tělo metody (na rozdíl od žádného těla) je, aby bylo možné spustit a předat nástroj PEverify (čímž se ověří úplnost metadat).</span><span class="sxs-lookup"><span data-stu-id="b3afd-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="b3afd-116">Referenční sestavení obsahují atribut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3afd-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="b3afd-117">Tento atribut může být zadán ve zdroji (pak ho kompilátor nebude muset syntetizovat).</span><span class="sxs-lookup"><span data-stu-id="b3afd-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="b3afd-118">Z důvodu tohoto atributu modul runtime odmítne načíst referenční sestavení ke spuštění (ale mohou být i nadále načteny v kontextu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="b3afd-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="b3afd-119">Nástroje, které reflektují sestavení, musí zajistit, aby načetly referenční sestavení pouze pro reflexi. v opačném případě modul runtime vyvolá <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="b3afd-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="b3afd-120">Možnosti `-refout` a [`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="b3afd-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3afd-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3afd-121">See also</span></span>

- [<span data-ttu-id="b3afd-122">-refonly</span><span class="sxs-lookup"><span data-stu-id="b3afd-122">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="b3afd-123">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="b3afd-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b3afd-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="b3afd-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
