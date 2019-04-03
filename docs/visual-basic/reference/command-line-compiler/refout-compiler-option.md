---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: f2cdd228d8ce1912abbbe888c29c42f29299ebba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832733"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="f91e3-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f91e3-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="f91e3-103">**- Refout** možnost určuje, kde referenční sestavení by mělo být výstupní cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="f91e3-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="f91e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f91e3-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="f91e3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f91e3-105">Arguments</span></span>

 <span data-ttu-id="f91e3-106">`filepath` Cesta a název souboru referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="f91e3-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="f91e3-107">Obecně by měl být v dílčí složce primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="f91e3-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="f91e3-108">Doporučené konvence (používány nástrojem MSBuild), je umístit odkaz na sestavení v "ref /" podsložku vzhledem k primární sestavení.</span><span class="sxs-lookup"><span data-stu-id="f91e3-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="f91e3-109">Všechny složky v `filepath` musí existovat; kompilátor nevytvoří je.</span><span class="sxs-lookup"><span data-stu-id="f91e3-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="f91e3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f91e3-110">Remarks</span></span>

<span data-ttu-id="f91e3-111">Visual Basic podporuje `-refout` přepnout od verze 15.3.</span><span class="sxs-lookup"><span data-stu-id="f91e3-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="f91e3-112">Referenční sestavení jsou pouze metadata sestavení, která obsahují metadata, ale žádný implementační kód.</span><span class="sxs-lookup"><span data-stu-id="f91e3-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="f91e3-113">Patří mezi ně typů a členů informace pro všechno, co s výjimkou anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="f91e3-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="f91e3-114">Jejich těla metod jsou nahrazeny jednoho `throw null` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f91e3-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="f91e3-115">Důvod pro použití `throw null` těla metod (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).</span><span class="sxs-lookup"><span data-stu-id="f91e3-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="f91e3-116">Zahrnout odkaz na sestavení úrovni sestavení [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="f91e3-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="f91e3-117">Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho).</span><span class="sxs-lookup"><span data-stu-id="f91e3-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="f91e3-118">Z důvodu tohoto atributu moduly runtime odmítnout načíst referenční sestavení pro spuštění (ale stále může být načteny v kontextu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="f91e3-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="f91e3-119">Nástroje, které odpovídají na sestavení se muset ujistit, že se načítají referenční sestavení jako pouze pro reflexi; v opačném případě modul runtime vyvolá <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="f91e3-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="f91e3-120">`-refout` a [ `-refonly` ](refonly-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="f91e3-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="f91e3-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f91e3-121">See also</span></span>

- [<span data-ttu-id="f91e3-122">-refonly</span><span class="sxs-lookup"><span data-stu-id="f91e3-122">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="f91e3-123">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="f91e3-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f91e3-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="f91e3-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
