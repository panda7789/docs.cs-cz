---
title: 'Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 948e9bf485b42b445491a4da9f8de7ae7974075c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592825"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b065d-102">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b065d-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b065d-103">Následující příklad kódu ukazuje, jak implementovat obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost, která se mění způsob zobrazení buněk v závislosti na jejich sloupců a hodnot.</span><span class="sxs-lookup"><span data-stu-id="b065d-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="b065d-104">Buňky v `Balance` sloupec, který obsahují záporná čísla jsou uvedeny červené na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b065d-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="b065d-105">Můžete také formátovat tyto buňky jako měnu zobrazíte závorky kolem záporné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b065d-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="b065d-106">Další informace najdete v tématu [jak: Formátování dat v Windows Forms DataGridView – ovládací prvek](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b065d-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="b065d-107">Buňky v `Priority` buňky sloupce zobrazení obrázků místo odpovídající textové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b065d-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="b065d-108"><xref:System.Windows.Forms.ConvertEventArgs.Value%2A> Vlastnost <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> slouží k získání hodnoty textovou buňky a nastavit odpovídající zobrazovanou hodnotu image.</span><span class="sxs-lookup"><span data-stu-id="b065d-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b065d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b065d-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b065d-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b065d-110">Compiling the Code</span></span>  
 <span data-ttu-id="b065d-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b065d-111">This example requires:</span></span>  
  
- <span data-ttu-id="b065d-112">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b065d-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="b065d-113"><xref:System.Drawing.Bitmap> Image s názvem `highPri.bmp`, `mediumPri.bmp`, a `lowPri.bmp` umístěný ve stejném adresáři jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="b065d-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b065d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b065d-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="b065d-115">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b065d-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b065d-116">Postupy: Formát dat v Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b065d-116">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b065d-117">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b065d-117">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b065d-118">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b065d-118">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
