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
ms.openlocfilehash: 8f33b210a454dddf318c2dd78ce170caa2ff1770
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488050"
---
# <a name="how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3464f-102">Postupy: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3464f-102">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3464f-103">Následující příklad kódu ukazuje, jak spravovat velké sady dat pomocí <xref:System.Windows.Forms.DataGridView> ovládacím prvkem jeho <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> nastavenou na `true`.</span><span class="sxs-lookup"><span data-stu-id="3464f-103">The following code example demonstrates how to manage large sets of data using a <xref:System.Windows.Forms.DataGridView> control with its <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property set to `true`.</span></span>  
  
 <span data-ttu-id="3464f-104">Úplné vysvětlení tento příklad kódu naleznete v tématu [návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="3464f-104">For a complete explanation of this code example, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3464f-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3464f-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#000](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#000)]
 [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3464f-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3464f-106">Compiling the Code</span></span>  
 <span data-ttu-id="3464f-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="3464f-107">This example requires:</span></span>  
  
-   <span data-ttu-id="3464f-108">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3464f-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3464f-109">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3464f-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3464f-110">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="3464f-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="3464f-111">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="3464f-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3464f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3464f-112">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [<span data-ttu-id="3464f-113">Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3464f-113">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [<span data-ttu-id="3464f-114">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3464f-114">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="3464f-115">Virtuální režim v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3464f-115">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)
