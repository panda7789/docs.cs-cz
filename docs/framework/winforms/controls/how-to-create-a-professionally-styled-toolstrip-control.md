---
title: 'Postupy: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 6da6e113867efed79dfcd02f3b89ee1f9ae13c4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104584"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="95872-102">Postupy: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem</span><span class="sxs-lookup"><span data-stu-id="95872-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="95872-103">Aplikace můžete udělit <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled a chování (vzhled a chování) zápisem vlastní třídy odvozené od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.</span><span class="sxs-lookup"><span data-stu-id="95872-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="95872-104">Není k dispozici rozsáhlou podporu pro tuto funkci v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="95872-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="95872-105">Zobrazit [názorný postup: Vytvoření ovládacího prvku ToolStrip s profesionálním](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="95872-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95872-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="95872-106">Example</span></span>  
 <span data-ttu-id="95872-107">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStrip> ovládací prvky pro vytvoření složeného ovládacího prvku, který napodobuje **navigačním podokně** poskytované Microsoft Outlook®.</span><span class="sxs-lookup"><span data-stu-id="95872-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95872-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="95872-108">Compiling the Code</span></span>  
 <span data-ttu-id="95872-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="95872-109">This example requires:</span></span>  
  
-   <span data-ttu-id="95872-110">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="95872-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="95872-111">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="95872-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="95872-112">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="95872-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="95872-113">Viz také [názorný postup: Vytvoření ovládacího prvku ToolStrip s profesionálním](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="95872-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95872-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95872-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="95872-115">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="95872-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="95872-116">Postupy: Zajištění standardních položek nabídky pro formulář</span><span class="sxs-lookup"><span data-stu-id="95872-116">How to: Provide Standard Menu Items to a Form</span></span>](how-to-provide-standard-menu-items-to-a-form.md)
