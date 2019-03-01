---
title: 'Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: bbce0e4a2427843ed9d9d51b25684db8c54ba69a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980123"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="a8a46-102">Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8a46-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="a8a46-103">`#Region` – Direktiva umožňuje sbalit a skrýt části kódu v souborech Visual Basicu.</span><span class="sxs-lookup"><span data-stu-id="a8a46-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="a8a46-104">`#Region` Umožňuje určit blok kódu, které můžete rozbalit nebo sbalit při použití editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a8a46-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="a8a46-105">Možnost Skrýt kódu selektivně díky soubory spravovatelné a snadněji čitelné.</span><span class="sxs-lookup"><span data-stu-id="a8a46-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="a8a46-106">Další informace najdete v tématu [Osnova](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="a8a46-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="a8a46-107">`#Region` direktivy podporují sémantiku bloku kódu, jako je například `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="a8a46-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="a8a46-108">To znamená, že nemůže začínat v jedné bloku a končit v jiné; spuštění a ukončení musí být ve stejném bloku.</span><span class="sxs-lookup"><span data-stu-id="a8a46-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="a8a46-109">`#Region` direktivy nejsou podporovány v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="a8a46-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="a8a46-110">Pokud chcete sbalit a skrýt části kódu</span><span class="sxs-lookup"><span data-stu-id="a8a46-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="a8a46-111">Umístit části kódu mezi `#Region` a `#End Region` příkazy jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a8a46-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     <span data-ttu-id="a8a46-112">`#Region` Bloku lze použít více než jednou v souboru kódu; proto uživatelé mohou definovat vlastní bloky postupů a třídy, které můžou zase, sbalit.</span><span class="sxs-lookup"><span data-stu-id="a8a46-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="a8a46-113">`#Region` bloky také může být vnořena v jiné `#Region` bloky.</span><span class="sxs-lookup"><span data-stu-id="a8a46-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8a46-114">Skrytí kódu nebrání je kompilovaná a nemá vliv na `#If...#End If` příkazy.</span><span class="sxs-lookup"><span data-stu-id="a8a46-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a46-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8a46-115">See also</span></span>
- [<span data-ttu-id="a8a46-116">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="a8a46-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="a8a46-117">Direktiva #Region</span><span class="sxs-lookup"><span data-stu-id="a8a46-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="a8a46-118">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="a8a46-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="a8a46-119">Sbalení</span><span class="sxs-lookup"><span data-stu-id="a8a46-119">Outlining</span></span>](/visualstudio/ide/outlining)
