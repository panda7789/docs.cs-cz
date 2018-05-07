---
title: Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d38620c321fb12b9f489fd086e222b7780337ab3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a>Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView
`DataGridView` Ovládací prvek usnadňuje definovat základní vzhledu buněk a formátování zobrazení hodnoty buněk. Můžete definovat vzhled a formátování styly jednotlivých buněk, buněk v určité sloupce a řádky nebo všechny buňky v ovládacím prvku nastavením vlastnosti `DataGridViewCellStyle` objekty přistupovat prostřednictvím různých `DataGridView` vlastností ovládacího prvku. Kromě toho můžete upravit tyto styly dynamicky založeny na faktorech, jako je například hodnotu buňky pomocí zpracování `CellFormatting` událostí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)  
 Popisuje, jak nastavit `DataGridView` vlastnosti, které definují vzhled ohraničení ovládacího prvku a řádky hranice mezi buněk.  
  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 Popisuje `DataGridViewCellStyle` třídy a interakci vlastnosti daného typu k definování zobrazení buňky v ovládacím prvku.  
  
 [Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 Popisuje způsob použití `DataGridViewCellStyle` vlastnosti, které chcete definovat výchozí vzhledu buněk v určitých řádků a sloupců a celý ovládací prvek.  
  
 [Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 Popisuje způsob zobrazení hodnot v buňkách pomocí formátování `DataGridViewCellStyle` vlastnosti.  
  
 [Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 Popisuje postup použití `DefaultCellStyle` vlastnost nastavující základní zobrazit vlastnosti pro všechny buňky v ovládacím prvku.  
  
 [Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 Popisuje, jak vytvořit efekt účetní knihy v ovládacím prvku pomocí střídavých řádků, které se zobrazují jinak.  
  
 [Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 Popisuje postup použití `RowTemplate` vlastnost pro nastavení vlastností řádků, které se použijí pro všechny řádky v ovládacím prvku.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewCellStyle> třídy.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí.  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnost.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buněk a řádků a vytváření odvozené buňky, sloupce a typy řádků.  
  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 Obsahuje témata, která popisují běžně používá vlastnosti buněk, řádků a sloupců.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
