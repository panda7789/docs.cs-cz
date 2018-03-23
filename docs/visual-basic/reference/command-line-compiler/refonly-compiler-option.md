---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5135ef4d33ddde27416e48c28425aa5b029237b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="961b9-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="961b9-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="961b9-103">**- Refonly** možnost znamená, že primární výstup kompilace by měl být referenční sestavení místo implementace sestavení.</span><span class="sxs-lookup"><span data-stu-id="961b9-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="961b9-104">`-refonly` Parametr bezobslužně zakáže výstup vytvořeného soubory PDB, jako referenční sestavení nelze provést.</span><span class="sxs-lookup"><span data-stu-id="961b9-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="961b9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="961b9-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="961b9-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="961b9-106">Remarks</span></span>

<span data-ttu-id="961b9-107">Podporuje jazyka Visual Basic `-refout` přepínače, počínaje verzí 15.3.</span><span class="sxs-lookup"><span data-stu-id="961b9-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="961b9-108">Referenční sestavení jsou pouze metadata sestavení, které obsahují metadata, ale žádný kód implementace.</span><span class="sxs-lookup"><span data-stu-id="961b9-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="961b9-109">Obsahují informace o typu a členu pro všechno kromě anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="961b9-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="961b9-110">Důvod použití `throw null` těla (na rozdíl od žádné těla) je, aby PEVerify může spouštět a předat (tedy ověření úplnost metadat).</span><span class="sxs-lookup"><span data-stu-id="961b9-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="961b9-111">Zahrnout odkaz na sestavení úrovni sestavení [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="961b9-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="961b9-112">Tento atribut je možné zadat zdroj (pak kompilátor nebudete muset syntetizace ji).</span><span class="sxs-lookup"><span data-stu-id="961b9-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="961b9-113">Z důvodu tohoto atributu moduly runtime odmítne načíst odkaz na sestavení pro spuštění (ale stále může být načteno do kontextu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="961b9-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="961b9-114">Nástroje, které odráží sestavení potřeba zajistit, že se načíst odkaz na sestavení jako pouze pro reflexi; jinak, modul runtime vyvolá <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="961b9-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="961b9-115">`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="961b9-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="961b9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="961b9-116">See also</span></span>
<span data-ttu-id="961b9-117">[-refout](refout-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="961b9-117">[-refout](refout-compiler-option.md) </span></span>  
[<span data-ttu-id="961b9-118">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="961b9-118">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="961b9-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="961b9-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)   
