---
title: Formátování dat v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: 5966f16238999655d6072c1127e5bf16aefde5e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969190"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formátování dat v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Ovládací prvek poskytuje automatický převod mezi hodnotami buněk a typy dat, které se zobrazují v nadřazených sloupcích. Sloupce textového pole, například zobrazované řetězcové reprezentace hodnot data, času, čísel a výčtů a převod uživatelem zadaných hodnot řetězce na typy vyžadované úložištěm dat.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formátování pomocí třídy ovládací prvek DataGridViewCellStyle  
 Ovládací prvek poskytuje základní formátování dat hodnot buněk <xref:System.Windows.Forms.DataGridViewCellStyle> přes třídu. <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> Vlastnost lze použít k formátování hodnot data, času, čísel a výčtů pro aktuální výchozí jazykovou verzi pomocí specifikátorů formátu popsaných v tématu [formátování typů](../../../standard/base-types/formatting-types.md). Tyto hodnoty můžete také naformátovat pro konkrétní jazykové verze <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> pomocí vlastnosti. Zadaný formát slouží k zobrazení dat a k analýze dat, která uživatel zadal v zadaném formátu.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Třída poskytuje další vlastnosti formátování pro WordWrap, zarovnání textu a vlastní zobrazení hodnot null databáze. Další informace najdete v tématu [jak: Formátování dat v ovládacím prvku](how-to-format-data-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formátování pomocí události CellFormatting  
 Pokud základní formátování nevyhovuje vašim potřebám, můžete v obslužné rutině pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost zadat vlastní formátování dat. Předaná obslužné rutině <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> má vlastnost, která zpočátku obsahuje hodnotu buňky. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> Obvykle je tato hodnota automaticky převedena na typ zobrazení. Chcete-li hodnotu převést sami, nastavte <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> vlastnost na hodnotu typu zobrazení.  
  
> [!NOTE]
> Pokud je pro buňku platný formátovací řetězec, Přepisuje změnu <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> hodnoty vlastnosti, pokud <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> nenastavíte vlastnost na `true`hodnotu.  
  
 Tato <xref:System.Windows.Forms.DataGridView.CellFormatting> událost je užitečná také v případě, že chcete <xref:System.Windows.Forms.DataGridViewCellStyle> nastavit vlastnosti pro jednotlivé buňky na základě jejich hodnot. Další informace najdete v tématu [jak: Přizpůsobení formátování dat v ovládacím prvku](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.  
  
 Pokud výchozí analýza hodnot zadaných uživatelem nevyhovuje vašim potřebám, můžete zpracovat <xref:System.Windows.Forms.DataGridView.CellParsing> událost <xref:System.Windows.Forms.DataGridView> ovládacího prvku a poskytnout tak vlastní analýzu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Postupy: Formátování dat v ovládacím prvku DataGridView model Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Přizpůsobení formátování dat v ovládacím prvku DataGridView model Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
