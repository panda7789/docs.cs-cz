---
title: Nastavení střídajících se stylů řádků pro ovládací prvek DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 74f65d03a359136de943f8a2937ed5e5f1e62519
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743044"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="0c095-102">Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="0c095-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="0c095-103">Tabulková data jsou často prezentována ve formátu, ve kterém mají střídavé řádky odlišné barvy pozadí.</span><span class="sxs-lookup"><span data-stu-id="0c095-103">Tabular data is often presented in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="0c095-104">Tento formát usnadňuje uživatelům informace o tom, které buňky jsou v jednotlivých řádcích, zejména u rozsáhlých tabulek, které mají mnoho sloupců.</span><span class="sxs-lookup"><span data-stu-id="0c095-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>

<span data-ttu-id="0c095-105">Pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete zadat úplné informace o stylu pro střídavé řádky.</span><span class="sxs-lookup"><span data-stu-id="0c095-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="0c095-106">K odlišení střídajících se řádků můžete použít vlastnosti stylu, jako je barva popředí a písmo, kromě barvy pozadí.</span><span class="sxs-lookup"><span data-stu-id="0c095-106">You can use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span> <span data-ttu-id="0c095-107">Další informace naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="0c095-107">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="0c095-108">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0c095-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0c095-109">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0c095-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="define-styles-for-alternating-rows"></a><span data-ttu-id="0c095-110">Definovat styly pro střídavé řádky</span><span class="sxs-lookup"><span data-stu-id="0c095-110">Define styles for alternating rows</span></span>

1. <span data-ttu-id="0c095-111">V návrháři vyberte ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0c095-111">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>

2. <span data-ttu-id="0c095-112">V okně **vlastnosti** klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c095-112">In the **Properties** window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> property.</span></span>

3. <span data-ttu-id="0c095-113">V dialogovém okně **Tvůrce CellStyle** definujte styl nastavením vlastností a pomocí podokna **náhledu** potvrďte své volby.</span><span class="sxs-lookup"><span data-stu-id="0c095-113">In the **CellStyle Builder** dialog box, define the style by setting the properties, and use the **Preview** pane to confirm your choices.</span></span> <span data-ttu-id="0c095-114">Styly, které zadáte, se použijí pro každý další řádek zobrazený v ovládacím prvku počínaje druhým.</span><span class="sxs-lookup"><span data-stu-id="0c095-114">The styles you specify are used for every other row displayed in the control, starting with the second one.</span></span>

4. <span data-ttu-id="0c095-115">Chcete-li definovat styly pro zbývající řádky, opakujte kroky 2 a 3 pomocí vlastnosti <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c095-115">To define styles for the remaining rows, repeat steps 2 and 3 using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0c095-116">Buňky se zobrazují pomocí stylů děděných z více vlastností.</span><span class="sxs-lookup"><span data-stu-id="0c095-116">Cells are displayed using styles inherited from multiple properties.</span></span> <span data-ttu-id="0c095-117">Další informace o dědičnosti stylu naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="0c095-117">For more information about style inheritance, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c095-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c095-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="0c095-119">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0c095-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="0c095-120">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0c095-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="0c095-121">Používání Návrháře s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0c095-121">Using the Designer with the Windows Forms DataGridView Control</span></span>](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="0c095-122">Postupy: vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="0c095-122">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="0c095-123">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0c095-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
