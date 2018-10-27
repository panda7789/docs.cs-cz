---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b22fb9ae24a04d9fe530811bf764352199c31813
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50036057"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="25a24-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25a24-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="25a24-103">**- Refout** možnost znamená, že primární výstup tohoto sestavení by měl být referenční sestavení místo sestavení implementace.</span><span class="sxs-lookup"><span data-stu-id="25a24-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="25a24-104">`-refonly` Parametr tiše zakáže generování souborů pdb, jako referenční sestavení nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="25a24-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="25a24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25a24-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="25a24-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25a24-106">Remarks</span></span>

<span data-ttu-id="25a24-107">Visual Basic podporuje `-refout` přepnout od verze 15.3.</span><span class="sxs-lookup"><span data-stu-id="25a24-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="25a24-108">Referenční sestavení jsou pouze metadata sestavení, která obsahují metadata, ale žádný implementační kód.</span><span class="sxs-lookup"><span data-stu-id="25a24-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="25a24-109">Patří mezi ně typů a členů informace pro všechno, co s výjimkou anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="25a24-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="25a24-110">Důvod pro použití `throw null` subjektů (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).</span><span class="sxs-lookup"><span data-stu-id="25a24-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="25a24-111">Zahrnout odkaz na sestavení úrovni sestavení [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="25a24-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="25a24-112">Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho).</span><span class="sxs-lookup"><span data-stu-id="25a24-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="25a24-113">Z důvodu tohoto atributu moduly runtime odmítne načíst referenční sestavení pro spuštění (ale stále může být načteny v kontextu pouze pro reflexi).</span><span class="sxs-lookup"><span data-stu-id="25a24-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="25a24-114">Nástroje, které odpovídají na sestavení se muset ujistit, že se načítají referenční sestavení jako pouze pro reflexi; v opačném případě modul runtime vyvolá <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="25a24-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="25a24-115">`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="25a24-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="25a24-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25a24-116">See also</span></span>
<span data-ttu-id="25a24-117">[-refout](refout-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="25a24-117">[-refout](refout-compiler-option.md) </span></span>  
[<span data-ttu-id="25a24-118">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25a24-118">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="25a24-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="25a24-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)   
