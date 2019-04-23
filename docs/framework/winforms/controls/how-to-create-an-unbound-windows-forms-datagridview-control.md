---
title: 'Postupy: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: 9bfffac3d6970aceea3842df95f4bcae970b42e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167905"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="3c2ee-102">Postupy: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3c2ee-102">How to: Create an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3c2ee-103">Následující příklad kódu ukazuje, jak naplnit <xref:System.Windows.Forms.DataGridView> řízení prostřednictvím kódu programu bez vazby ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-103">The following code example demonstrates how to populate a <xref:System.Windows.Forms.DataGridView> control programmatically without binding it to a data source.</span></span> <span data-ttu-id="3c2ee-104">To je užitečné, pokud máte malé množství dat, které chcete zobrazit ve formátu tabulky.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-104">This is useful when you have a small amount of data that you want to display in a table format.</span></span>  
  
 <span data-ttu-id="3c2ee-105">Úplné vysvětlení tento příklad kódu naleznete v tématu [názorný postup: Vytvoření nevázaného Windows Forms DataGridView – ovládací prvek](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="3c2ee-105">For a complete explanation of this code example, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c2ee-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c2ee-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3c2ee-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3c2ee-107">Compiling the Code</span></span>  
 <span data-ttu-id="3c2ee-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="3c2ee-108">This example requires:</span></span>  
  
-   <span data-ttu-id="3c2ee-109">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-109">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3c2ee-110">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3c2ee-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3c2ee-111">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3c2ee-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c2ee-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="3c2ee-113">Návod: Vytvoření nevázaného Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="3c2ee-113">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3c2ee-114">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3c2ee-114">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3c2ee-115">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3c2ee-115">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
