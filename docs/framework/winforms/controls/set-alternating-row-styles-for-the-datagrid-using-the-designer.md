---
title: "Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0473e0bdb0cdc57836baffaee38b47c89d2723ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="27a0a-102">Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="27a0a-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="27a0a-103">Tabulková data se zobrazí často ve formátu účetní knihy, kde mají střídavých řádků různých barev pozadí.</span><span class="sxs-lookup"><span data-stu-id="27a0a-103">Tabular data is often presented in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="27a0a-104">Tento formát usnadňuje uživatelům říct buněk, které jsou v jednotlivých řádcích, zejména s wide tabulky, které mají mnoho sloupců.</span><span class="sxs-lookup"><span data-stu-id="27a0a-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="27a0a-105">Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete zadat informace o dokončení stylu střídavých řádků.</span><span class="sxs-lookup"><span data-stu-id="27a0a-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="27a0a-106">Styl charakteristiky, jako jsou například barvu popředí a písma, kromě barvu pozadí slouží k odlišení střídavých řádků.</span><span class="sxs-lookup"><span data-stu-id="27a0a-106">You can use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span> <span data-ttu-id="27a0a-107">Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="27a0a-107">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="27a0a-108">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="27a0a-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="27a0a-109">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="27a0a-109">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27a0a-110">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="27a0a-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="27a0a-111">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="27a0a-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="27a0a-112">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="27a0a-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="define-styles-for-alternating-rows"></a><span data-ttu-id="27a0a-113">Definování stylů střídavých řádků</span><span class="sxs-lookup"><span data-stu-id="27a0a-113">Define styles for alternating rows</span></span>  
  
1.  <span data-ttu-id="27a0a-114">Vyberte <xref:System.Windows.Forms.DataGridView> ovládacího prvku v návrháři.</span><span class="sxs-lookup"><span data-stu-id="27a0a-114">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>  
  
2.  <span data-ttu-id="27a0a-115">V **vlastnosti** okně klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="27a0a-115">In the **Properties** window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> property.</span></span>  
  
3.  <span data-ttu-id="27a0a-116">V **objektu CellStyle** dialogové okno, zadejte styl nastavením vlastností a použít **Preview** podokně k potvrzení voleb.</span><span class="sxs-lookup"><span data-stu-id="27a0a-116">In the **CellStyle Builder** dialog box, define the style by setting the properties, and use the **Preview** pane to confirm your choices.</span></span> <span data-ttu-id="27a0a-117">Styly, které zadáte, se používají pro každý druhý řádek, který se zobrazí v ovládacím prvku, počínaje na druhou.</span><span class="sxs-lookup"><span data-stu-id="27a0a-117">The styles you specify are used for every other row displayed in the control, starting with the second one.</span></span>  
  
4.  <span data-ttu-id="27a0a-118">Chcete-li definovat styly pro zbývající řádky, opakujte kroky 2 a 3 pomocí <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="27a0a-118">To define styles for the remaining rows, repeat steps 2 and 3 using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27a0a-119">Zobrazení buněk pomocí styly zděděno z více vlastností.</span><span class="sxs-lookup"><span data-stu-id="27a0a-119">Cells are displayed using styles inherited from multiple properties.</span></span> <span data-ttu-id="27a0a-120">Další informace o dědičnosti styl najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="27a0a-120">For more information about style inheritance, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a0a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="27a0a-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="27a0a-122">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27a0a-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="27a0a-123">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27a0a-123">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="27a0a-124">Používání Návrháře s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27a0a-124">Using the Designer with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="27a0a-125">Postupy: vytvoření projektu aplikace Windows</span><span class="sxs-lookup"><span data-stu-id="27a0a-125">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="27a0a-126">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27a0a-126">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
