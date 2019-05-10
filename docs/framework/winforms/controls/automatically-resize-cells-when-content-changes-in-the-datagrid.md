---
title: 'Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 436f5d4a77a3119fe5b16afa1a4e71c55b3751dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587638"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f5095-102">Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f5095-102">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f5095-103">Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> řízení ke změně velikosti jeho řádky, sloupce a záhlaví automaticky pokaždé, když obsah změny, tak, aby buňky jsou vždy dostatečně velký pro zobrazení jejich hodnoty bez oříznutí.</span><span class="sxs-lookup"><span data-stu-id="f5095-103">You can configure the <xref:System.Windows.Forms.DataGridView> control to resize its rows, columns, and headers automatically whenever content changes, so that cells are always large enough to display their values without clipping.</span></span>  
  
 <span data-ttu-id="f5095-104">Máte řadu možností pro omezení buněk, které se používají k určení nové velikosti.</span><span class="sxs-lookup"><span data-stu-id="f5095-104">You have many options to restrict which cells are used to determine the new sizes.</span></span> <span data-ttu-id="f5095-105">Můžete například nakonfigurovat ovládací prvek automaticky změní velikost šířku sloupce pouze na základě hodnot v řádcích, které jsou aktuálně zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="f5095-105">For example, you can configure the control to automatically resize the width of its columns based only on the values in rows that are currently displayed.</span></span> <span data-ttu-id="f5095-106">Díky tomu se můžete vyhnout neefektivnost při práci s velkým počtem řádků, i když se v takovém případě můžete chtít použít nastavení velikosti metody, jako <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> upravit velikost v době podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="f5095-106">With this, you can avoid inefficiency when working with large numbers of rows, although in this case, you might want to use sizing methods such as <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> to adjust sizes at times of your choosing.</span></span>  
  
 <span data-ttu-id="f5095-107">Další informace o automatickou změnu velikosti najdete v tématu [možnosti nastavení velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f5095-107">For more information about automatic resizing, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="f5095-108">Následující příklad kódu ukazuje možnosti dostupné pro automatickou změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="f5095-108">The following code example demonstrates the options available for automatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5095-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5095-109">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f5095-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f5095-110">Compiling the Code</span></span>  
 <span data-ttu-id="f5095-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f5095-111">This example requires:</span></span>  
  
- <span data-ttu-id="f5095-112">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f5095-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="f5095-113">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f5095-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f5095-114">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f5095-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f5095-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5095-115">See also</span></span>

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
- [<span data-ttu-id="f5095-116">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f5095-116">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f5095-117">Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f5095-117">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f5095-118">Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f5095-118">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
