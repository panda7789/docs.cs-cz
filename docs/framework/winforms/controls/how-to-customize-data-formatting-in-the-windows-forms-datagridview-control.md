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
ms.openlocfilehash: 81fe4cb836d358a0625e79344650951dce3ba4a6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402276"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1c746-102">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1c746-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1c746-103">Následující příklad kódu ukazuje, jak implementovat obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost, která se mění způsob zobrazení buněk v závislosti na jejich sloupců a hodnot.</span><span class="sxs-lookup"><span data-stu-id="1c746-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="1c746-104">Buňky v `Balance` sloupec, který obsahují záporná čísla jsou uvedeny červené na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1c746-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="1c746-105">Můžete také formátovat tyto buňky jako měnu zobrazíte závorky kolem záporné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1c746-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="1c746-106">Další informace najdete v tématu [postupy: formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1c746-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="1c746-107">Buňky v `Priority` buňky sloupce zobrazení obrázků místo odpovídající textové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1c746-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="1c746-108"><xref:System.Windows.Forms.ConvertEventArgs.Value%2A> Vlastnost <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> slouží k získání hodnoty textovou buňky a nastavit odpovídající zobrazovanou hodnotu image.</span><span class="sxs-lookup"><span data-stu-id="1c746-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c746-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c746-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c746-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1c746-110">Compiling the Code</span></span>  
 <span data-ttu-id="1c746-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1c746-111">This example requires:</span></span>  
  
-   <span data-ttu-id="1c746-112">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1c746-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="1c746-113"><xref:System.Drawing.Bitmap> Image s názvem `highPri.bmp`, `mediumPri.bmp`, a `lowPri.bmp` umístěný ve stejném adresáři jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="1c746-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="1c746-114">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1c746-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1c746-115">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="1c746-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1c746-116">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1c746-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c746-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c746-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Drawing.Bitmap>  
 [<span data-ttu-id="1c746-118">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1c746-118">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1c746-119">Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1c746-119">How to: Format Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1c746-120">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1c746-120">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1c746-121">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1c746-121">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
