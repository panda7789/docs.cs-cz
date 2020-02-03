---
title: Hostitelské ovládací prvky v buňkách DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a64521a15a272ca8140302f39d15e7f17e0c423b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736536"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="ef8b3-102">Postupy: Umisťování ovládacích prvků do buněk Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef8b3-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="ef8b3-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje několik typů sloupců a umožňuje uživatelům zadávat a upravovat hodnoty různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="ef8b3-104">Pokud tyto typy sloupců nesplňují požadavky na datovou položku, můžete vytvořit vlastní typy sloupců s buňkami, které řídí ovládací prvky pro výběr.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="ef8b3-105">Chcete-li to provést, je nutné definovat třídy, které jsou odvozeny z <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="ef8b3-106">Musíte také definovat třídu, která je odvozena z <xref:System.Windows.Forms.Control> a implementuje rozhraní <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="ef8b3-107">Následující příklad kódu ukazuje, jak vytvořit sloupec kalendáře.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="ef8b3-108">Buňky v tomto sloupci zobrazují data v běžných buňkách textového pole, ale když uživatel upraví buňku, zobrazí se ovládací prvek <xref:System.Windows.Forms.DateTimePicker>.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="ef8b3-109">Chcete-li se vyhnout nutnosti implementovat funkce textového pole, je `CalendarCell` Třída odvozena od <xref:System.Windows.Forms.DataGridViewTextBoxCell> třídy místo přímého dědění třídy <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef8b3-110">Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy nezapomeňte přepsat metodu `Clone` pro kopírování nových vlastností během operací klonování.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="ef8b3-111">Měli byste také zavolat metodu `Clone` základní třídy tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef8b3-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef8b3-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef8b3-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ef8b3-113">Compiling the Code</span></span>  
 <span data-ttu-id="ef8b3-114">Následující příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ef8b3-114">The following example requires:</span></span>  
  
- <span data-ttu-id="ef8b3-115">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="ef8b3-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8b3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef8b3-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="ef8b3-117">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef8b3-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ef8b3-118">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef8b3-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="ef8b3-119">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef8b3-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
