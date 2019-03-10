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
ms.openlocfilehash: 4a7e74afa985d36281994078bd0ea464f084cfa9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714902"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView
Následující příklad kódu ukazuje, jak implementovat obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost, která se mění způsob zobrazení buněk v závislosti na jejich sloupců a hodnot.  
  
 Buňky v `Balance` sloupec, který obsahují záporná čísla jsou uvedeny červené na pozadí. Můžete také formátovat tyto buňky jako měnu zobrazíte závorky kolem záporné hodnoty. Další informace najdete v tématu [jak: Formátování dat v Windows Forms DataGridView – ovládací prvek](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
 Buňky v `Priority` buňky sloupce zobrazení obrázků místo odpovídající textové hodnoty. <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> Vlastnost <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> slouží k získání hodnoty textovou buňky a nastavit odpovídající zobrazovanou hodnotu image.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
-   <xref:System.Drawing.Bitmap> Image s názvem `highPri.bmp`, `mediumPri.bmp`, a `lowPri.bmp` umístěný ve stejném adresáři jako spustitelný soubor.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Formát dat v Windows Forms DataGridView](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formátování dat v ovládacím prvku Windows Forms DataGridView](data-formatting-in-the-windows-forms-datagridview-control.md)
