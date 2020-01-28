---
title: Programové změny velikosti buněk podle obsahu v ovládacím prvku DataGridView
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
ms.openlocfilehash: df3b378a8ba358fa0bfe549a7901b3d59d53f556
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742449"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3d6f7-102">Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3d6f7-102">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3d6f7-103">Pomocí metod ovládacího prvku <xref:System.Windows.Forms.DataGridView> lze změnit velikost řádků, sloupců a záhlaví tak, aby zobrazovaly celé hodnoty bez zkrácení.</span><span class="sxs-lookup"><span data-stu-id="3d6f7-103">You can use the <xref:System.Windows.Forms.DataGridView> control methods to resize rows, columns, and headers so that they display their entire values without truncation.</span></span> <span data-ttu-id="3d6f7-104">Tyto metody můžete použít ke změně velikosti <xref:System.Windows.Forms.DataGridView> prvků v době, kdy zvolíte.</span><span class="sxs-lookup"><span data-stu-id="3d6f7-104">You can use these methods to resize <xref:System.Windows.Forms.DataGridView> elements at times of your choosing.</span></span> <span data-ttu-id="3d6f7-105">Alternativně můžete nakonfigurovat ovládací prvek tak, aby automaticky měnil velikost těchto prvků vždy, když dojde ke změně obsahu.</span><span class="sxs-lookup"><span data-stu-id="3d6f7-105">Alternately, you can configure the control to resize these elements automatically whenever content changes.</span></span> <span data-ttu-id="3d6f7-106">Tato možnost může být neefektivní, ale když pracujete s velkými sadami dat nebo když se data často mění.</span><span class="sxs-lookup"><span data-stu-id="3d6f7-106">This can be inefficient, however, when you are working with large data sets or when your data changes frequently.</span></span> <span data-ttu-id="3d6f7-107">Další informace najdete v tématu [Možnosti změny velikosti v ovládacím prvku DataGridView model Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="3d6f7-107">For more information, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="3d6f7-108">Obvykle budete programově upravovat <xref:System.Windows.Forms.DataGridView> prvky tak, aby odpovídaly jejich obsahu pouze při načtení nových dat ze zdroje dat nebo při úpravě hodnoty uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3d6f7-108">Typically, you will programmatically adjust <xref:System.Windows.Forms.DataGridView> elements to fit their content only when you load new data from a data source or when the user has edited a value.</span></span> <span data-ttu-id="3d6f7-109">To je užitečné pro optimalizaci výkonu, ale je užitečné také v případě, že chcete uživatelům umožnit ruční změnu velikosti řádků a sloupců pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="3d6f7-109">This is useful to optimize performance, but it is also useful when you want to enable your users to manually resize rows and columns with the mouse.</span></span>  
  
 <span data-ttu-id="3d6f7-110">Následující příklad kódu ukazuje možnosti, které jsou k dispozici pro programovou změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="3d6f7-110">The following code example demonstrates the options available to you for programmatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d6f7-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d6f7-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3d6f7-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3d6f7-112">Compiling the Code</span></span>  
 <span data-ttu-id="3d6f7-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="3d6f7-113">This example requires:</span></span>  
  
- <span data-ttu-id="3d6f7-114">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="3d6f7-114">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6f7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d6f7-115">See also</span></span>

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
- [<span data-ttu-id="3d6f7-116">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3d6f7-116">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3d6f7-117">Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3d6f7-117">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3d6f7-118">Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="3d6f7-118">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)
