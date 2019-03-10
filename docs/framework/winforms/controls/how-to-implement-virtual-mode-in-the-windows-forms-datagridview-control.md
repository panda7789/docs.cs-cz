---
title: 'Postupy: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode
- DataGridView control [Windows Forms], large data sets
ms.assetid: 98236267-f08e-4918-bcf9-77acf050a3ca
ms.openlocfilehash: da62d7f58b6a5f8231df17ecf3301f004219e35e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717762"
---
# <a name="how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7d6a2-102">Postupy: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d6a2-102">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7d6a2-103">Následující příklad kódu ukazuje, jak spravovat velké sady dat pomocí <xref:System.Windows.Forms.DataGridView> ovládacím prvkem jeho <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> nastavenou na `true`.</span><span class="sxs-lookup"><span data-stu-id="7d6a2-103">The following code example demonstrates how to manage large sets of data using a <xref:System.Windows.Forms.DataGridView> control with its <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property set to `true`.</span></span>  
  
 <span data-ttu-id="7d6a2-104">Úplné vysvětlení tento příklad kódu naleznete v tématu [názorný postup: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7d6a2-104">For a complete explanation of this code example, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d6a2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d6a2-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#000)]
 [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d6a2-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7d6a2-106">Compiling the Code</span></span>  
 <span data-ttu-id="7d6a2-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7d6a2-107">This example requires:</span></span>  
  
-   <span data-ttu-id="7d6a2-108">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7d6a2-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="7d6a2-109">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7d6a2-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7d6a2-110">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="7d6a2-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d6a2-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d6a2-111">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="7d6a2-112">Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d6a2-112">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)
- [<span data-ttu-id="7d6a2-113">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d6a2-113">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7d6a2-114">Virtuální režim v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d6a2-114">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)
