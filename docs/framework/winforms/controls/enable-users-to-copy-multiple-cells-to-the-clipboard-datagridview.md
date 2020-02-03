---
title: Povolit uživatelům kopírovat více buněk do schránky z ovládacího prvku DataGridView
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
ms.openlocfilehash: 2bb74a1f0c59b28ab496ce9c89c1c1b5f9d8147b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745784"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="040bc-102">Postupy: Povolení kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="040bc-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="040bc-103">Když povolíte kopírování buněk, zpřístupníte data v ovládacím prvku <xref:System.Windows.Forms.DataGridView> k ostatním aplikacím prostřednictvím <xref:System.Windows.Forms.Clipboard>.</span><span class="sxs-lookup"><span data-stu-id="040bc-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="040bc-104">Hodnoty vybraných buněk jsou převedeny na řetězce a přidány do schránky jako textové hodnoty s oddělovači pro vložení do aplikací, jako je například Poznámkový blok a Excel, a jako tabulka ve formátu HTML pro vložení do aplikací, jako je Word.</span><span class="sxs-lookup"><span data-stu-id="040bc-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="040bc-105">Můžete nakonfigurovat kopírování buňky pouze pro kopírování hodnot buňky, pro zahrnutí textu záhlaví řádku a sloupce do dat schránky nebo pro zahrnutí textu záhlaví, pokud uživatelé vyberou celé řádky nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="040bc-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="040bc-106">V závislosti na režimu výběru můžou uživatelé vybrat několik odpojených skupin buněk.</span><span class="sxs-lookup"><span data-stu-id="040bc-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="040bc-107">Když uživatel zkopíruje buňky do schránky, řádky a sloupce, které neobsahují vybrané buňky, se nezkopírují.</span><span class="sxs-lookup"><span data-stu-id="040bc-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="040bc-108">Všechny ostatní řádky nebo sloupce se stanou řádky a sloupci v tabulce dat zkopírovaných do schránky.</span><span class="sxs-lookup"><span data-stu-id="040bc-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="040bc-109">Nevybrané buňky na těchto řádcích nebo sloupcích se zkopírují jako prázdná zástupné symboly do schránky.</span><span class="sxs-lookup"><span data-stu-id="040bc-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="040bc-110">Povolení kopírování buněk</span><span class="sxs-lookup"><span data-stu-id="040bc-110">To enable cell copying</span></span>  
  
- <span data-ttu-id="040bc-111">Nastavte vlastnost <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="040bc-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="040bc-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="040bc-112">Example</span></span>  
 <span data-ttu-id="040bc-113">Následující příklad kompletního kódu ukazuje, jak se buňky zkopírují do schránky.</span><span class="sxs-lookup"><span data-stu-id="040bc-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="040bc-114">Tento příklad obsahuje tlačítko, které zkopíruje vybrané buňky do schránky pomocí metody <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> a zobrazí obsah schránky v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="040bc-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="040bc-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="040bc-115">Compiling the Code</span></span>  
 <span data-ttu-id="040bc-116">Tento kód vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="040bc-116">This code requires:</span></span>  
  
- <span data-ttu-id="040bc-117">Odkazy na sestavení N:System a N:System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="040bc-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="040bc-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="040bc-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [<span data-ttu-id="040bc-119">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="040bc-119">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
