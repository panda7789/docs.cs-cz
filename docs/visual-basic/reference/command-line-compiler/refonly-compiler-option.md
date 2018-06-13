---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8f6c15084ac9b1a07aef8a0311edfcc4a93337c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653043"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="3ce26-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ce26-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="3ce26-103">**- Refonly** možnost znamená, že primární výstup kompilace by měl být referenční sestavení místo implementace sestavení.</span><span class="sxs-lookup"><span data-stu-id="3ce26-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="3ce26-104">`-refonly` Parametr bezobslužně zakáže výstup vytvořeného soubory PDB, jako referenční sestavení nelze provést.</span><span class="sxs-lookup"><span data-stu-id="3ce26-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="3ce26-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ce26-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="3ce26-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ce26-106">Remarks</span></span>

<span data-ttu-id="3ce26-107">Podporuje jazyka Visual Basic `-refout` přepínače, počínaje verzí 15.3.</span><span class="sxs-lookup"><span data-stu-id="3ce26-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="3ce26-108">Referenční sestavení jsou pouze metadata sestavení, které obsahují metadata, ale žádný kód implementace.</span><span class="sxs-lookup"><span data-stu-id="3ce26-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="3ce26-109">Obsahují informace o typu a členu pro všechno kromě anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="3ce26-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="3ce26-110">Důvod použití `throw null` těla (na rozdíl od žádné těla) je, aby PEVerify může spouštět a předat (tedy ověření úplnost metadat).</span><span class="sxs-lookup"><span data-stu-id="3ce26-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="3ce26-111">Zahrnout odkaz na sestavení úrovni sestavení [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="3ce26-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="3ce26-112">Tento atribut je možné zadat zdroj (pak kompilátor nebudete muset syntetizace ji).</span><span class="sxs-lookup"><span data-stu-id="3ce26-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="3ce26-113">Z důvodu tohoto atributu moduly runtime odmítne načíst odkaz na sestavení pro spuštění (ale stále může být načteno do kontextu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="3ce26-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="3ce26-114">Nástroje, které odráží sestavení potřeba zajistit, že se načíst odkaz na sestavení jako pouze pro reflexi; jinak, modul runtime vyvolá <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="3ce26-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="3ce26-115">`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="3ce26-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ce26-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ce26-116">See also</span></span>
<span data-ttu-id="3ce26-117">[-refout](refout-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="3ce26-117">[-refout](refout-compiler-option.md) </span></span>  
[<span data-ttu-id="3ce26-118">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="3ce26-118">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="3ce26-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="3ce26-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)   
