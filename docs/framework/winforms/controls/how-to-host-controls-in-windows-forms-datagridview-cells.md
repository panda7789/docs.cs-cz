---
title: 'Postupy: Umisťování ovládacích prvků do buněk Windows Forms DataGridView'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 96f1c384d42506f498fa2c64feacb6dd96e88b70
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="7d7c4-102">Postupy: Umisťování ovládacích prvků do buněk Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d7c4-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="7d7c4-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje několik typů sloupce, povolíte uživatelům zadat a upravit hodnoty v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="7d7c4-104">Pokud tyto typy sloupců nevyhovuje vašim potřebám zadávání dat, ale můžete vytvořit vlastní typy sloupců s buněk, které jsou hostiteli ovládací prvky dle vlastního výběru.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="7d7c4-105">Chcete-li to provést, je nutné definovat třídy, které jsou odvozeny od <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="7d7c4-106">Je třeba definovat třídu odvozenou z <xref:System.Windows.Forms.Control> a implementuje <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="7d7c4-107">Následující příklad kódu ukazuje, jak vytvořit kalendář sloupec.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="7d7c4-108">V buňkách v tomto sloupci zobrazení dat v buňkách obyčejného textového pole, ale když uživatel upravuje buňku, <xref:System.Windows.Forms.DateTimePicker> ovládací prvek se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="7d7c4-109">Aby se zabránilo museli znovu, implementovat funkce zobrazení textového pole `CalendarCell` třída odvozená z <xref:System.Windows.Forms.DataGridViewTextBoxCell> třída spíše než dědění <xref:System.Windows.Forms.DataGridViewCell> přímo třídu.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d7c4-110">Pokud odvozujete od <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy, je nutné přepsat `Clone` metoda kopírování nové vlastnosti během operací klonování.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="7d7c4-111">Měli byste také zavolat základní třídy `Clone` metoda tak, aby vlastnosti základní třídy jsou zkopírovány do nového buňky nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d7c4-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d7c4-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d7c4-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7d7c4-113">Compiling the Code</span></span>  
 <span data-ttu-id="7d7c4-114">Následující příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7d7c4-114">The following example requires:</span></span>  
  
-   <span data-ttu-id="7d7c4-115">Odkazy na systém a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="7d7c4-116">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7d7c4-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7d7c4-117">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="7d7c4-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="7d7c4-118">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7d7c4-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d7c4-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d7c4-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.DateTimePicker>  
 [<span data-ttu-id="7d7c4-120">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d7c4-120">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="7d7c4-121">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d7c4-121">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [<span data-ttu-id="7d7c4-122">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d7c4-122">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
