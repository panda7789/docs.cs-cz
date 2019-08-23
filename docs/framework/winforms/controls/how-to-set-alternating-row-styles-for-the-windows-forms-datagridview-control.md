---
title: 'Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: d113c45469f6a78c94b9489bd82f9e55b5b96bba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962274"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="26d28-102">Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="26d28-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="26d28-103">Tabulková data se často prezentují uživatelům ve formátu, ve kterém mají střídavé řádky různé barvy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="26d28-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="26d28-104">Tento formát usnadňuje uživatelům informace o tom, které buňky jsou v jednotlivých řádcích, zejména u rozsáhlých tabulek, které mají mnoho sloupců.</span><span class="sxs-lookup"><span data-stu-id="26d28-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="26d28-105"><xref:System.Windows.Forms.DataGridView> Pomocí ovládacího prvku můžete zadat úplné informace o stylu pro střídavé řádky.</span><span class="sxs-lookup"><span data-stu-id="26d28-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="26d28-106">To umožňuje použít charakteristiky stylu jako barvu popředí a písmo, kromě barvy pozadí pro odlišení střídajících se řádků.</span><span class="sxs-lookup"><span data-stu-id="26d28-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="26d28-107">Pro tuto úlohu se v aplikaci Visual Studio podporuje.</span><span class="sxs-lookup"><span data-stu-id="26d28-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="26d28-108">Podívejte [se také na postupy: Pomocí návrháře](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)nastavte střídavé styly řádků pro ovládací prvek DataGridView model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="26d28-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="26d28-109">Nastavení střídavých stylů řádků prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="26d28-109">To set alternating row styles programmatically</span></span>  
  
- <span data-ttu-id="26d28-110">Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> objektů vrácených <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnostmi<xref:System.Windows.Forms.DataGridView>a.</span><span class="sxs-lookup"><span data-stu-id="26d28-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > <span data-ttu-id="26d28-111">Styly určené pomocí <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> vlastností a <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> přepíšou styly zadané na sloupci a <xref:System.Windows.Forms.DataGridView> úrovni, ale jsou přepsány styly nastavenými na úrovni jednotlivých řádků a buněk.</span><span class="sxs-lookup"><span data-stu-id="26d28-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="26d28-112">Další informace naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="26d28-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26d28-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="26d28-113">Compiling the Code</span></span>  
 <span data-ttu-id="26d28-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="26d28-114">This example requires:</span></span>  
  
- <span data-ttu-id="26d28-115">Ovládací prvek s `dataGridView1`názvem. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="26d28-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="26d28-116">Odkazy na <xref:System?displayProperty=nameWithType>sestavení, <xref:System.Drawing?displayProperty=nameWithType>a. <xref:System.Windows.Forms?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="26d28-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="26d28-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="26d28-117">Robust Programming</span></span>  
 <span data-ttu-id="26d28-118">Pro zajištění maximální škálovatelnosti byste měli sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objekty napříč více řádky, sloupci nebo buňkami, které používají stejné styly, nikoli nastavovat vlastnosti stylu pro každý prvek samostatně.</span><span class="sxs-lookup"><span data-stu-id="26d28-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="26d28-119">Další informace najdete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="26d28-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d28-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26d28-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="26d28-121">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="26d28-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="26d28-122">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="26d28-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="26d28-123">Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="26d28-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="26d28-124">Postupy: Nastavení stylů písma a barev v ovládacím prvku DataGridView model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26d28-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
