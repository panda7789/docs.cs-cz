---
title: 'Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
ms.openlocfilehash: e076d26f733716967996f7f809abf0b9f946ef5a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590489"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1f56a-102">Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f56a-102">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1f56a-103">Můžete použít <xref:System.Windows.Forms.DataGridView> řídit metody pro změnu velikosti řádky, sloupce a záhlaví tak, aby se zobrazit jejich celý hodnoty bez zkrácení.</span><span class="sxs-lookup"><span data-stu-id="1f56a-103">You can use the <xref:System.Windows.Forms.DataGridView> control methods to resize rows, columns, and headers so that they display their entire values without truncation.</span></span> <span data-ttu-id="1f56a-104">Tyto metody můžete použít ke změně velikosti <xref:System.Windows.Forms.DataGridView> prvky v době podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="1f56a-104">You can use these methods to resize <xref:System.Windows.Forms.DataGridView> elements at times of your choosing.</span></span> <span data-ttu-id="1f56a-105">Alternativně můžete nakonfigurovat ovládací prvek pro velikost tyto prvky automaticky pokaždé, když se změní obsah.</span><span class="sxs-lookup"><span data-stu-id="1f56a-105">Alternately, you can configure the control to resize these elements automatically whenever content changes.</span></span> <span data-ttu-id="1f56a-106">Může to být neefektivní, ale při práci s velkými datovými sadami nebo když se data často mění.</span><span class="sxs-lookup"><span data-stu-id="1f56a-106">This can be inefficient, however, when you are working with large data sets or when your data changes frequently.</span></span> <span data-ttu-id="1f56a-107">Další informace najdete v tématu [možnosti nastavení velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f56a-107">For more information, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="1f56a-108">Obvykle můžete programově upraví <xref:System.Windows.Forms.DataGridView> elementy podle jejich obsahu pouze v případě, že načtení nových dat ze zdroje dat nebo uživatel nemá upravovat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1f56a-108">Typically, you will programmatically adjust <xref:System.Windows.Forms.DataGridView> elements to fit their content only when you load new data from a data source or when the user has edited a value.</span></span> <span data-ttu-id="1f56a-109">To je užitečné pro optimalizaci výkonu, ale je také užitečné, pokud chcete povolit uživatelům ručně změnit velikost řádků a sloupců pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="1f56a-109">This is useful to optimize performance, but it is also useful when you want to enable your users to manually resize rows and columns with the mouse.</span></span>  
  
 <span data-ttu-id="1f56a-110">Následující příklad kódu ukazuje možnosti dostupné pro Programová změna velikosti.</span><span class="sxs-lookup"><span data-stu-id="1f56a-110">The following code example demonstrates the options available to you for programmatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f56a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f56a-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f56a-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1f56a-112">Compiling the Code</span></span>  
 <span data-ttu-id="1f56a-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1f56a-113">This example requires:</span></span>  
  
- <span data-ttu-id="1f56a-114">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1f56a-114">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f56a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f56a-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [<span data-ttu-id="1f56a-116">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f56a-116">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1f56a-117">Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f56a-117">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1f56a-118">Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f56a-118">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)
