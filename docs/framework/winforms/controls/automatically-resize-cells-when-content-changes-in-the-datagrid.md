---
title: Automaticky měnit velikost buněk při změně obsahu v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
ms.openlocfilehash: 86e3bce993aa06546e301c6d7a7e03a31013c337
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732070"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9903f-102">Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9903f-102">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9903f-103">Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> ovládacímu prvku, aby při každé změně obsahu automaticky změnil velikost jeho řádků, sloupců a hlaviček, takže jsou buňky vždycky dostatečně velké, aby se zobrazily jejich hodnoty bez omezení.</span><span class="sxs-lookup"><span data-stu-id="9903f-103">You can configure the <xref:System.Windows.Forms.DataGridView> control to resize its rows, columns, and headers automatically whenever content changes, so that cells are always large enough to display their values without clipping.</span></span>  
  
 <span data-ttu-id="9903f-104">Máte spoustu možností, jak omezit, které buňky se používají k určení nových velikostí.</span><span class="sxs-lookup"><span data-stu-id="9903f-104">You have many options to restrict which cells are used to determine the new sizes.</span></span> <span data-ttu-id="9903f-105">Můžete například nakonfigurovat ovládací prvek tak, aby automaticky změnil šířku sloupce na základě hodnot v aktuálně zobrazených řádcích.</span><span class="sxs-lookup"><span data-stu-id="9903f-105">For example, you can configure the control to automatically resize the width of its columns based only on the values in rows that are currently displayed.</span></span> <span data-ttu-id="9903f-106">Díky tomu se můžete vyhnout neefektivitě při práci s velkým počtem řádků, i když v takovém případě můžete chtít použít metody změny velikosti, například <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>, a upravit velikosti v době, kdy zvolíte.</span><span class="sxs-lookup"><span data-stu-id="9903f-106">With this, you can avoid inefficiency when working with large numbers of rows, although in this case, you might want to use sizing methods such as <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> to adjust sizes at times of your choosing.</span></span>  
  
 <span data-ttu-id="9903f-107">Další informace o automatické změně velikosti najdete v tématu [Možnosti změny velikosti v ovládacím prvku DataGridView model Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9903f-107">For more information about automatic resizing, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="9903f-108">Následující příklad kódu ukazuje možnosti, které jsou k dispozici pro automatickou změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="9903f-108">The following code example demonstrates the options available for automatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9903f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9903f-109">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9903f-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9903f-110">Compiling the Code</span></span>  
 <span data-ttu-id="9903f-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9903f-111">This example requires:</span></span>  
  
- <span data-ttu-id="9903f-112">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="9903f-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9903f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9903f-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [<span data-ttu-id="9903f-114">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9903f-114">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9903f-115">Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9903f-115">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9903f-116">Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9903f-116">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
