---
title: 'Postupy: Sbalení a skrytí sekcí kódu'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: c11affe9c4dd4251ba8ff4b87029d314970b5fcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404846"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="e9024-102">Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9024-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="e9024-103">`#Region`Direktiva umožňuje sbalit a skrýt části kódu v souborech Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e9024-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="e9024-104">`#Region`Direktiva umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9024-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="e9024-105">Možnost selektivně skrývat kód usnadňuje správu a snazší čtení souborů.</span><span class="sxs-lookup"><span data-stu-id="e9024-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="e9024-106">Další informace najdete v tématu [popisujícím sbalení](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="e9024-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="e9024-107">`#Region`direktivy podporují sémantiku bloků kódu, jako je `#If...#End If` .</span><span class="sxs-lookup"><span data-stu-id="e9024-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="e9024-108">To znamená, že nemohou začít v jednom bloku a končit jiným. počátek a konec musí být ve stejném bloku.</span><span class="sxs-lookup"><span data-stu-id="e9024-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="e9024-109">`#Region`direktivy nejsou v rámci funkcí podporovány.</span><span class="sxs-lookup"><span data-stu-id="e9024-109">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="e9024-110">Sbalení a skrytí oddílu kódu</span><span class="sxs-lookup"><span data-stu-id="e9024-110">To collapse and hide a section of code</span></span>

<span data-ttu-id="e9024-111">Umístěte oddíl kódu mezi `#Region` `#End Region` příkazy a, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e9024-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="e9024-112">`#Region`Blok lze použít několikrát v souboru kódu; proto mohou uživatelé definovat vlastní bloky procedur a tříd, které mohou být následně sbaleny.</span><span class="sxs-lookup"><span data-stu-id="e9024-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="e9024-113">`#Region`bloky je také možné vnořit do jiných `#Region` bloků.</span><span class="sxs-lookup"><span data-stu-id="e9024-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="e9024-114">Skrytí kódu nebrání jeho zkompilování a nemá vliv na `#If...#End If` příkazy.</span><span class="sxs-lookup"><span data-stu-id="e9024-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9024-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9024-115">See also</span></span>

- [<span data-ttu-id="e9024-116">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="e9024-116">Conditional Compilation</span></span>](conditional-compilation.md)
- [<span data-ttu-id="e9024-117">#Region direktiva</span><span class="sxs-lookup"><span data-stu-id="e9024-117">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="e9024-118">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="e9024-118">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="e9024-119">Sbalování</span><span class="sxs-lookup"><span data-stu-id="e9024-119">Outlining</span></span>](/visualstudio/ide/outlining)
