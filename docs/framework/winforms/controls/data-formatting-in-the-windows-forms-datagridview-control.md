---
title: Formátování dat v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: a041bcc5e1b65afb3123f1f42e0f1b5a479b5764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743980"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formátování dat v ovládacím prvku Windows Forms DataGridView
Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje automatický převod mezi hodnotami buněk a typy dat, které se zobrazují v nadřazených sloupcích. Sloupce textového pole, například zobrazované řetězcové reprezentace hodnot data, času, čísel a výčtů a převod uživatelem zadaných hodnot řetězce na typy vyžadované úložištěm dat.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formátování pomocí třídy ovládací prvek DataGridViewCellStyle  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje základní formátování dat hodnot buněk prostřednictvím třídy <xref:System.Windows.Forms.DataGridViewCellStyle>. Vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> lze použít k formátování hodnot data, času, čísel a výčtů pro aktuální výchozí jazykovou verzi pomocí specifikátoru formátu popsaných v tématu [formátování typů](../../../standard/base-types/formatting-types.md). Tyto hodnoty můžete také naformátovat pro konkrétní jazykové verze pomocí vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>. Zadaný formát slouží k zobrazení dat a k analýze dat, která uživatel zadal v zadaném formátu.  
  
 Třída <xref:System.Windows.Forms.DataGridViewCellStyle> poskytuje další vlastnosti formátování pro WordWrap, zarovnání textu a vlastní zobrazení hodnot null databáze. Další informace naleznete v tématu [How to: Format data in model Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formátování pomocí události CellFormatting  
 Pokud základní formátování nevyhovuje vašim potřebám, můžete zadat vlastní formátování dat v obslužné rutině pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> předaný obslužné rutině má vlastnost <xref:System.Windows.Forms.ConvertEventArgs.Value%2A>, která zpočátku obsahuje hodnotu buňky. Obvykle je tato hodnota automaticky převedena na typ zobrazení. Chcete-li hodnotu převést sami, nastavte vlastnost <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> na hodnotu typu zobrazení.  
  
> [!NOTE]
> Pokud je pro buňku platný formátovací řetězec, Přepisuje změnu hodnoty vlastnosti <xref:System.Windows.Forms.ConvertEventArgs.Value%2A>, pokud nenastavíte vlastnost <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> na `true`.  
  
 Událost <xref:System.Windows.Forms.DataGridView.CellFormatting> je užitečná také v případě, že chcete nastavit vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> pro jednotlivé buňky na základě jejich hodnot. Další informace najdete v tématu [Postup: Přizpůsobení formátování dat v ovládacím prvku DataGridView model Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Pokud výchozí analýza hodnot zadaných uživatelem nevyhovuje vašim potřebám, můžete zpracovat událost <xref:System.Windows.Forms.DataGridView.CellParsing> ovládacího prvku <xref:System.Windows.Forms.DataGridView> a poskytnout tak vlastní analýzu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
