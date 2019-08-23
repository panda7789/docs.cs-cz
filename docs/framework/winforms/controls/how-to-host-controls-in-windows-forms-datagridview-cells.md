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
ms.openlocfilehash: a97af9bf0ef4016e54f877d934ed401b8dde7d4e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966597"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="99824-102">Postupy: Hostitelské ovládací prvky v buňkách Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="99824-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="99824-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek poskytuje několik typů sloupců, které uživatelům umožňují zadávat a upravovat hodnoty mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="99824-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="99824-104">Pokud tyto typy sloupců nesplňují požadavky na datovou položku, můžete vytvořit vlastní typy sloupců s buňkami, které řídí ovládací prvky pro výběr.</span><span class="sxs-lookup"><span data-stu-id="99824-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="99824-105">Chcete-li to provést, je nutné definovat třídy, <xref:System.Windows.Forms.DataGridViewColumn> které <xref:System.Windows.Forms.DataGridViewCell>jsou odvozeny z a.</span><span class="sxs-lookup"><span data-stu-id="99824-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="99824-106">Musíte také definovat třídu, která je odvozena z <xref:System.Windows.Forms.Control> a <xref:System.Windows.Forms.IDataGridViewEditingControl> implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99824-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="99824-107">Následující příklad kódu ukazuje, jak vytvořit sloupec kalendáře.</span><span class="sxs-lookup"><span data-stu-id="99824-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="99824-108">Buňky v tomto sloupci zobrazují data v běžných buňkách textového pole, ale když uživatel upraví buňku, <xref:System.Windows.Forms.DateTimePicker> zobrazí se ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="99824-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="99824-109">Chcete-li se vyhnout nutnosti implementovat funkce textového pole znovu, `CalendarCell` třída je odvozena <xref:System.Windows.Forms.DataGridViewTextBoxCell> od třídy <xref:System.Windows.Forms.DataGridViewCell> místo přímého dědění třídy.</span><span class="sxs-lookup"><span data-stu-id="99824-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99824-110">Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností na odvozenou třídu nezapomeňte přepsat `Clone` metodu pro kopírování nových vlastností během operací klonování.</span><span class="sxs-lookup"><span data-stu-id="99824-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="99824-111">Měli byste také zavolat `Clone` metodu základní třídy tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="99824-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99824-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="99824-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99824-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="99824-113">Compiling the Code</span></span>  
 <span data-ttu-id="99824-114">Následující příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="99824-114">The following example requires:</span></span>  
  
- <span data-ttu-id="99824-115">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="99824-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99824-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99824-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="99824-117">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="99824-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="99824-118">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="99824-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="99824-119">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="99824-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
