---
title: 'Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 9f3ce61b3692f0b83298bdf9a19cb98fb5d5ab7f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723800"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="b0d28-102">Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b0d28-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="b0d28-103">Následující příklad kódu ukazuje, jak vytvořit vazbu na kolekci objektů do <xref:System.Windows.Forms.DataGridView> tak, aby každý objekt zobrazí jako samostatný řádek.</span><span class="sxs-lookup"><span data-stu-id="b0d28-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="b0d28-104">Tento příklad také znázorňuje způsob zobrazení vlastností s typem výčtu v <xref:System.Windows.Forms.DataGridViewComboBoxColumn> tak, aby rozevíracího seznamu pole se seznamem obsahuje hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="b0d28-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0d28-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0d28-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b0d28-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b0d28-106">Compiling the Code</span></span>  
 <span data-ttu-id="b0d28-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b0d28-107">This example requires:</span></span>  
  
-   <span data-ttu-id="b0d28-108">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b0d28-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b0d28-109">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b0d28-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b0d28-110">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="b0d28-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d28-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0d28-111">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b0d28-112">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b0d28-112">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b0d28-113">Postupy: Přístup k objektům Svázaným Windows Forms DataGridView řádků</span><span class="sxs-lookup"><span data-stu-id="b0d28-113">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
