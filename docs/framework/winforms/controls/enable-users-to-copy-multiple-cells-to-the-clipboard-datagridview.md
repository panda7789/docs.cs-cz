---
title: 'Postupy: Povolit uživatelům kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: b8b466aac35f928be66b46a2fe840945847f4bc6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220254"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="b71e3-102">Postupy: Povolit uživatelům kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b71e3-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b71e3-103">Když povolíte kopírování buňky, provedete data ve vaší <xref:System.Windows.Forms.DataGridView> snadný přístup k ostatním aplikacím prostřednictvím ovládacího prvku <xref:System.Windows.Forms.Clipboard>.</span><span class="sxs-lookup"><span data-stu-id="b71e3-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="b71e3-104">Hodnoty vybrané buňky jsou převedeny na řetězce a přidali do schránky jako text oddělený tabulátory hodnoty pro vkládání do aplikací, jako je Poznámkový blok a Excel a jako tabulka ve formátu HTML pro vkládání do aplikací, jako je Word.</span><span class="sxs-lookup"><span data-stu-id="b71e3-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="b71e3-105">Můžete nakonfigurovat buňky kopírování ke kopírování hodnot v buňkách, zahrnout text záhlaví řádků a sloupců do schránky dat nebo obsahovat text záhlaví jenom v případě, že uživatelé vybrat celé řádky nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="b71e3-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="b71e3-106">V závislosti na režimu výběru mohou uživatelé vybrat více skupin odpojené buněk.</span><span class="sxs-lookup"><span data-stu-id="b71e3-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="b71e3-107">Když uživatel zkopíruje do schránky buněk, řádků a sloupců s žádné vybrané buňky nejsou zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="b71e3-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="b71e3-108">Všechny ostatní řádky nebo sloupce se stanou řádků a sloupců v tabulce dat zkopírována do schránky.</span><span class="sxs-lookup"><span data-stu-id="b71e3-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="b71e3-109">Nevybrané buňky v těchto řádcích nebo sloupcích se zkopírují jako prázdné zástupné symboly do schránky.</span><span class="sxs-lookup"><span data-stu-id="b71e3-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="b71e3-110">Povolit kopírování buňky</span><span class="sxs-lookup"><span data-stu-id="b71e3-110">To enable cell copying</span></span>  
  
-   <span data-ttu-id="b71e3-111">Nastavte <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b71e3-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="b71e3-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b71e3-112">Example</span></span>  
 <span data-ttu-id="b71e3-113">Následující příklad kompletní kód ukazuje, jak se zkopírují buněk do schránky.</span><span class="sxs-lookup"><span data-stu-id="b71e3-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="b71e3-114">Tento příklad obsahuje tlačítko, které se zkopíruje do schránky pomocí vybrané buňky <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> metoda a zobrazí obsah schránky do textového pole.</span><span class="sxs-lookup"><span data-stu-id="b71e3-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b71e3-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b71e3-115">Compiling the Code</span></span>  
 <span data-ttu-id="b71e3-116">Tento kód vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b71e3-116">This code requires:</span></span>  
  
-   <span data-ttu-id="b71e3-117">Odkazy na sestavení n: System a N:System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b71e3-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b71e3-118">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b71e3-118">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b71e3-119">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="b71e3-119">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b71e3-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b71e3-120">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [<span data-ttu-id="b71e3-121">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b71e3-121">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
