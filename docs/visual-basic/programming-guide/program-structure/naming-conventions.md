---
title: Konvence vytváření názvů
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 98fdda2934c9df1b33f41b6e0442a39246efe168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347310"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="00677-102">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00677-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="00677-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span><span class="sxs-lookup"><span data-stu-id="00677-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="00677-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="00677-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="00677-105">The following suggestions apply to naming.</span><span class="sxs-lookup"><span data-stu-id="00677-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="00677-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="00677-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="00677-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="00677-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="00677-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="00677-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="00677-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="00677-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="00677-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span><span class="sxs-lookup"><span data-stu-id="00677-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="00677-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="00677-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="00677-112">In names of event argument classes, include the "`EventArgs`" suffix.</span><span class="sxs-lookup"><span data-stu-id="00677-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="00677-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="00677-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="00677-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span><span class="sxs-lookup"><span data-stu-id="00677-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="00677-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span><span class="sxs-lookup"><span data-stu-id="00677-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="00677-116">Also, make sure your abbreviations are consistent throughout the entire application.</span><span class="sxs-lookup"><span data-stu-id="00677-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="00677-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span><span class="sxs-lookup"><span data-stu-id="00677-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="00677-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span><span class="sxs-lookup"><span data-stu-id="00677-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="00677-119">Errors can result if the wrong variable is accessed.</span><span class="sxs-lookup"><span data-stu-id="00677-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="00677-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span><span class="sxs-lookup"><span data-stu-id="00677-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="00677-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="00677-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00677-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00677-122">See also</span></span>

- [<span data-ttu-id="00677-123">Klíčová slova jako názvy elementů v kódu</span><span class="sxs-lookup"><span data-stu-id="00677-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [<span data-ttu-id="00677-124">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="00677-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="00677-125">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="00677-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="00677-126">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="00677-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="00677-127">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00677-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
