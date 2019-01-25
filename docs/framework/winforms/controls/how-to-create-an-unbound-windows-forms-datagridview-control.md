---
title: 'Postupy: Vytvoření ovládacího prvku nevázaného Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: a1752be8aaac71dff62fe0e4fcd75ab8e386bae5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703100"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="87db4-102">Postupy: Vytvoření ovládacího prvku nevázaného Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="87db4-102">How to: Create an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="87db4-103">Následující příklad kódu ukazuje, jak naplnit <xref:System.Windows.Forms.DataGridView> řízení prostřednictvím kódu programu bez vazby ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="87db4-103">The following code example demonstrates how to populate a <xref:System.Windows.Forms.DataGridView> control programmatically without binding it to a data source.</span></span> <span data-ttu-id="87db4-104">To je užitečné, pokud máte malé množství dat, které chcete zobrazit ve formátu tabulky.</span><span class="sxs-lookup"><span data-stu-id="87db4-104">This is useful when you have a small amount of data that you want to display in a table format.</span></span>  
  
 <span data-ttu-id="87db4-105">Úplné vysvětlení tento příklad kódu naleznete v tématu [názorný postup: Vytvoření nevázaného Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="87db4-105">For a complete explanation of this code example, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87db4-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="87db4-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="87db4-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="87db4-107">Compiling the Code</span></span>  
 <span data-ttu-id="87db4-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="87db4-108">This example requires:</span></span>  
  
-   <span data-ttu-id="87db4-109">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="87db4-109">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="87db4-110">Informace o vytváření použijeme příklad z příkazového řádku pro visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="87db4-110">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="87db4-111">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="87db4-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="87db4-112">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="87db4-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87db4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87db4-113">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="87db4-114">Návod: Vytvoření nevázaného Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="87db4-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [<span data-ttu-id="87db4-115">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="87db4-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="87db4-116">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="87db4-116">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
