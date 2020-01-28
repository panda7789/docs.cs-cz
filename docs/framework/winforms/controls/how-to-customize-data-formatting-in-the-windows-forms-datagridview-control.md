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
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView
Následující příklad kódu ukazuje, jak implementovat obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>, která mění způsob zobrazení buněk v závislosti na jejich sloupcích a hodnotách.  
  
 Buňky ve sloupci `Balance`, které obsahují záporná čísla, mají červené pozadí. Tyto buňky můžete také naformátovat jako měnu, aby se zobrazovaly kulaté závorky kolem záporných hodnot. Další informace naleznete v tématu [How to: Format data in model Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
 Buňky ve sloupci `Priority` zobrazují obrázky místo odpovídajících hodnot textových buněk. Vlastnost <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> slouží k získání hodnoty textové buňky a k nastavení odpovídající hodnoty zobrazení obrázku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
- <xref:System.Drawing.Bitmap> image s názvem `highPri.bmp`, `mediumPri.bmp`a `lowPri.bmp` nacházející se ve stejném adresáři jako spustitelný soubor.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formátování dat v ovládacím prvku Windows Forms DataGridView](data-formatting-in-the-windows-forms-datagridview-control.md)
