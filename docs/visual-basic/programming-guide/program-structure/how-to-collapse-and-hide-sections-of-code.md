---
title: 'Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4497c9586182cca9e2be97dc39e5ccb242725d25
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="870c8-102">Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="870c8-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="870c8-103">`#Region` – Direktiva umožňuje sbalení a skrytí sekcí kódu v souborech jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="870c8-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="870c8-104">`#Region` Umožňuje zadat blok kódu, které můžete rozbalit nebo sbalit při použití editoru kódu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="870c8-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="870c8-105">Umožňuje selektivně skrýt kódu umožňuje vaše soubory lépe spravovat a snadněji číst.</span><span class="sxs-lookup"><span data-stu-id="870c8-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="870c8-106">Další informace najdete v tématu [Osnova](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="870c8-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="870c8-107">`#Region` direktivy podporují sémantiku bloku kódu, jako například `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="870c8-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="870c8-108">To znamená, že nelze začít v jeden blok a končit počáteční a koncová musí být ve stejné bloku.</span><span class="sxs-lookup"><span data-stu-id="870c8-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="870c8-109">`#Region` direktivy nejsou podporovány v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="870c8-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="870c8-110">Chcete-li sbalení a skrytí části kódu</span><span class="sxs-lookup"><span data-stu-id="870c8-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="870c8-111">Umístěte části kódu mezi `#Region` a `#End Region` příkazy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="870c8-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     <span data-ttu-id="870c8-112">`#Region` Bloku můžete použít více než jednou v souboru kódu; proto uživatelé mohou definovat vlastní bloky postupů a třídy, které lze, pak sbalit.</span><span class="sxs-lookup"><span data-stu-id="870c8-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="870c8-113">`#Region` bloky mohou být také vnořené v jiných `#Region` bloky.</span><span class="sxs-lookup"><span data-stu-id="870c8-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="870c8-114">Skrytí kódu nezabrání z kompiluje a nemá vliv na `#If...#End If` příkazy.</span><span class="sxs-lookup"><span data-stu-id="870c8-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870c8-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="870c8-115">See Also</span></span>  
 [<span data-ttu-id="870c8-116">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="870c8-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="870c8-117">Direktiva #Region</span><span class="sxs-lookup"><span data-stu-id="870c8-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="870c8-118">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="870c8-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="870c8-119">Sbalení</span><span class="sxs-lookup"><span data-stu-id="870c8-119">Outlining</span></span>](/visualstudio/ide/outlining)
