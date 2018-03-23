---
title: -refout (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6075b92efd1eec9797fca248e97a325bd5df4bb
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="4b1d1-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b1d1-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="4b1d1-103">**- Refout** možnost určuje cestu k souboru, kde referenční sestavení by měla být výstup.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="4b1d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b1d1-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="4b1d1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4b1d1-105">Arguments</span></span>

 <span data-ttu-id="4b1d1-106">`filepath` Cesta a název souboru referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="4b1d1-107">Obecně je nutné v dílčí složce primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="4b1d1-108">Doporučené konvence (používané MSBuild) je umístit referenční sestavení v "ref nebo" podsložky relativně k primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="4b1d1-109">Všechny složky v `filepath` musí existovat; kompilátor je nevytvoří.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="4b1d1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b1d1-110">Remarks</span></span>

<span data-ttu-id="4b1d1-111">Podporuje jazyka Visual Basic `-refout` přepínače, počínaje verzí 15.3.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="4b1d1-112">Referenční sestavení jsou pouze metadata sestavení, které obsahují metadata, ale žádný kód implementace.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="4b1d1-113">Obsahují informace o typu a členu pro všechno kromě anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="4b1d1-114">Jejich těla metody nahrazená s jedním `throw null` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="4b1d1-115">Důvod použití `throw null` těla metody (na rozdíl od žádné těla) je tak, aby PEVerify můžete spustit a předat (tedy ověření úplnost metadat).</span><span class="sxs-lookup"><span data-stu-id="4b1d1-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="4b1d1-116">Zahrnout odkaz na sestavení úrovni sestavení [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="4b1d1-117">Tento atribut je možné zadat zdroj (pak kompilátor nebudete muset syntetizace ji).</span><span class="sxs-lookup"><span data-stu-id="4b1d1-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="4b1d1-118">Z důvodu tohoto atributu moduly runtime odmítnout načíst odkaz na sestavení pro spuštění (ale stále může být načteno do kontextu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="4b1d1-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="4b1d1-119">Nástroje, které odráží sestavení potřeba zajistit, že se načíst odkaz na sestavení jako pouze pro reflexi; jinak, modul runtime vyvolá <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="4b1d1-120">`-refout` a [ `-refonly` ](refonly-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="4b1d1-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b1d1-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b1d1-121">See Also</span></span>
<span data-ttu-id="4b1d1-122">[-refonly](refonly-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="4b1d1-122">[-refonly](refonly-compiler-option.md) </span></span>  
[<span data-ttu-id="4b1d1-123">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="4b1d1-123">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="4b1d1-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="4b1d1-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)  

