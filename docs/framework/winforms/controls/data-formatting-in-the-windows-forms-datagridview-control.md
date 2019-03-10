---
title: Formátování dat v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: 60fc567a700bdfc8cfe088f4d31a68fd5de9aa29
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722045"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formátování dat v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení poskytuje automatický převod mezi hodnot v buňkách a datové typy, které zobrazují nadřazené sloupce. Textové pole sloupce, například zobrazit řetězcové reprezentace datum, čas, čísla a hodnoty výčtu a převod na typy potřebné v úložišti dat uživatel zadal řetězcové hodnoty.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formátování pomocí třídy ovládací prvek DataGridViewCellStyle  
 <xref:System.Windows.Forms.DataGridView> Řízení poskytuje základní data formátování hodnot v buňkách prostřednictvím <xref:System.Windows.Forms.DataGridViewCellStyle> třídy. Můžete použít <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> vlastnost k formátování data, času, čísla a výčet hodnot pro výchozí jazykovou verzi pomocí specifikátorů formátu, je popsáno v [Formatting Types](../../../standard/base-types/formatting-types.md). Můžete také formátovat tyto hodnoty pro konkrétní jazykovou verzi pomocí <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> vlastnost. Zadaný formát se používá k zobrazení dat a analyzovat data, která uživatel zadá v zadaném formátu.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Třída poskytuje další vlastnosti formátování pro zalamování řádků, zarovnání textu a vlastní zobrazení hodnot null databáze. Další informace najdete v tématu [jak: Formátování dat v Windows Forms DataGridView – ovládací prvek](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formátování s CellFormatting událostí  
 Pokud základní formátování nevyhovuje vašim potřebám, můžete zadat vlastní formátování dat v obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událostí. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> Předaný obslužné rutině má <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> vlastnost, která obsahuje počáteční hodnotu buňky. Za normálních okolností tuto hodnotu automaticky převést na typ zobrazení. Chcete-li převést hodnotu, nastavte <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> vlastnost na hodnotu typu zobrazení.  
  
> [!NOTE]
>  Pokud formátovací řetězec je v platnosti pro buňku, přepíše vaše změna <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> hodnota vlastnosti, pokud nenastavíte <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> vlastnost `true`.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting> Událostí je užitečné také, když chcete nastavit <xref:System.Windows.Forms.DataGridViewCellStyle> vlastnosti pro jednotlivé buňky na základě jejich hodnot. Další informace najdete v tématu [jak: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Pokud analýza výchozí hodnoty uživatelem zadaného nevyhovuje vašim potřebám, můžete zpracovávat <xref:System.Windows.Forms.DataGridView.CellParsing> událost <xref:System.Windows.Forms.DataGridView> ovládacího prvku poskytnout vlastní analýza kódu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Postupy: Formát dat v Windows Forms DataGridView](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
