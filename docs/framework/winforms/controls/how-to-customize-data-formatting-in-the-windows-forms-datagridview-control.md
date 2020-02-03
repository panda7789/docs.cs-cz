---
title: Přizpůsobení formátování dat v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], changing colors in DataGridView control [Windows Forms]
- colors [Windows Forms], changing in DataGridView control [Windows Forms]
- data [Windows Forms], formatting in DataGridView control
- DataGridView control [Windows Forms], cell customization
- DataGridView control [Windows Forms], changing cell colors
- Windows Forms, changing colors of DataGridView cells
- DataGridView control [Windows Forms], substituting cell values for display
- data grids [Windows Forms], formatting data
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
ms.openlocfilehash: 6bc1a65b876df842df322db165dc08fcc0c931dc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746787"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7e262-102">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7e262-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7e262-103">Následující příklad kódu ukazuje, jak implementovat obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>, která mění způsob zobrazení buněk v závislosti na jejich sloupcích a hodnotách.</span><span class="sxs-lookup"><span data-stu-id="7e262-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="7e262-104">Buňky ve sloupci `Balance`, které obsahují záporná čísla, mají červené pozadí.</span><span class="sxs-lookup"><span data-stu-id="7e262-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="7e262-105">Tyto buňky můžete také naformátovat jako měnu, aby se zobrazovaly kulaté závorky kolem záporných hodnot.</span><span class="sxs-lookup"><span data-stu-id="7e262-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="7e262-106">Další informace naleznete v tématu [How to: Format data in model Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7e262-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="7e262-107">Buňky ve sloupci `Priority` zobrazují obrázky místo odpovídajících hodnot textových buněk.</span><span class="sxs-lookup"><span data-stu-id="7e262-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="7e262-108">Vlastnost <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> slouží k získání hodnoty textové buňky a k nastavení odpovídající hodnoty zobrazení obrázku.</span><span class="sxs-lookup"><span data-stu-id="7e262-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e262-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e262-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e262-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7e262-110">Compiling the Code</span></span>  
 <span data-ttu-id="7e262-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7e262-111">This example requires:</span></span>  
  
- <span data-ttu-id="7e262-112">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="7e262-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="7e262-113"><xref:System.Drawing.Bitmap> image s názvem `highPri.bmp`, `mediumPri.bmp`a `lowPri.bmp` nacházející se ve stejném adresáři jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="7e262-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e262-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e262-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="7e262-115">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7e262-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7e262-116">Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7e262-116">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7e262-117">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7e262-117">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7e262-118">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7e262-118">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
