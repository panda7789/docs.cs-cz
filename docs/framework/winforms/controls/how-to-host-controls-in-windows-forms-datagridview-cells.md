---
title: 'Postupy: Hostitelské ovládací prvky v buňkách Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 86a1577174c12e55b23dd8bce2cf00ac0e780abb
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261255"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="bc819-102">Postupy: Hostitelské ovládací prvky v buňkách Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="bc819-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="bc819-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje několik typů sloupce, povolení uživatelům zadávat a upravovat hodnoty v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="bc819-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="bc819-104">Pokud tyto typy sloupců nevyhovují vašim potřebám zadávání dat, ale můžete vytvořit vlastní typy sloupců s buňky, které jsou hostiteli ovládací prvky, které si vyberete.</span><span class="sxs-lookup"><span data-stu-id="bc819-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="bc819-105">Chcete-li to provést, je nutné definovat třídy, které jsou odvozeny z <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="bc819-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="bc819-106">Musíte také definovat třídu, která je odvozena z <xref:System.Windows.Forms.Control> a implementuje <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc819-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="bc819-107">Následující příklad kódu ukazuje, jak vytvořit sloupec kalendáře.</span><span class="sxs-lookup"><span data-stu-id="bc819-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="bc819-108">Buňkách tohoto sloupce zobrazení dat v buňkách běžný text, ale když uživatel upravuje buňky, <xref:System.Windows.Forms.DateTimePicker> ovládací prvek se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="bc819-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="bc819-109">Aby bylo možné vyhnout se nutnosti znovu implementovat funkčnost zobrazení textového pole `CalendarCell` třída odvozena z <xref:System.Windows.Forms.DataGridViewTextBoxCell> třídy namísto dědění <xref:System.Windows.Forms.DataGridViewCell> třídy přímo.</span><span class="sxs-lookup"><span data-stu-id="bc819-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc819-110">Pokud odvozujete od <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy, je nutné přepsat `Clone` metoda kopírování nové vlastnosti během operace klonování.</span><span class="sxs-lookup"><span data-stu-id="bc819-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="bc819-111">Měli byste také zavolat základní třídu `Clone` metodu tak, aby vlastností základní třídy jsou zkopírovány do nové buňky nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="bc819-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc819-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc819-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc819-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bc819-113">Compiling the Code</span></span>  
 <span data-ttu-id="bc819-114">V následujícím příkladu vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="bc819-114">The following example requires:</span></span>  
  
-   <span data-ttu-id="bc819-115">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="bc819-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bc819-116">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bc819-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bc819-117">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="bc819-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc819-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc819-118">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="bc819-119">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="bc819-119">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bc819-120">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="bc819-120">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="bc819-121">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="bc819-121">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
