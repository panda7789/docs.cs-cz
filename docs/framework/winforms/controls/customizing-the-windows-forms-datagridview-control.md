---
title: Přizpůsobení ovládacího prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744022"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Přizpůsobení ovládacího prvku Windows Forms DataGridView
Ovládací prvek `DataGridView` poskytuje několik vlastností, které lze použít k úpravě vzhledu a základního chování (vzhled a chování) jeho buněk, řádků a sloupců. Pokud máte zvláštní potřeby, které překračují možnosti <xref:System.Windows.Forms.DataGridViewCellStyle> třídy, můžete také implementovat vykreslování vlastníka pro ovládací prvek nebo roztáhnout jeho funkce vytvořením vlastních buněk, sloupců a řádků.  
  
 Chcete-li malovat buňky a řádky sami, můžete zpracovat různé události Malování `DataGridView`. Chcete-li upravit stávající funkce nebo poskytnout nové funkce, můžete vytvořit vlastní typy odvozené z existujících `DataGridViewCell`, `DataGridViewColumn`a typů `DataGridViewRow`. Můžete také poskytnout nové možnosti úprav vytvořením odvozených typů, které zobrazí ovládací prvek výběru, pokud je buňka v režimu úprav.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md)  
 Popisuje, jak zpracovat událost <xref:System.Windows.Forms.DataGridView.CellPainting>, aby bylo možné buňky vykreslit ručně.  
  
 [Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-rows-in-the-datagrid.md)  
 Popisuje, jak zpracovávat události <xref:System.Windows.Forms.DataGridView.RowPrePaint> a <xref:System.Windows.Forms.DataGridView.RowPostPaint>, aby bylo možné malovat řádky s vlastním pozadím a obsahem přechodu, které jsou rozloženy do více sloupců.  
  
 [Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jejich chování a vzhledu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Popisuje, jak vytvořit vlastní typy odvozené z `DataGridViewCell` a `DataGridViewColumn`, aby bylo možné zvýraznit buňky, když se na ně ukazatel myši nachází.  
  
 [Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Popisuje, jak vytvořit vlastní typy odvozené z <xref:System.Windows.Forms.DataGridViewButtonCell> a <xref:System.Windows.Forms.DataGridViewButtonColumn>, aby se zobrazila zakázaná tlačítka ve sloupci tlačítka.  
  
 [Postupy: Hostování ovládacích prvků v buňkách Windows Forms DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Popisuje, jak implementovat rozhraní `IDataGridViewEditingControl` a vytvořit vlastní typy odvozené z `DataGridViewCell` a `DataGridViewColumn`, aby bylo možné zobrazit ovládací prvek <xref:System.Windows.Forms.DateTimePicker>, pokud je buňka v režimu úprav.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewCell>.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewRow>.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Poskytuje referenční dokumentaci pro rozhraní <xref:System.Windows.Forms.IDataGridViewEditingControl>.  
  
## <a name="related-sections"></a>Související oddíly  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat buněk.  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
