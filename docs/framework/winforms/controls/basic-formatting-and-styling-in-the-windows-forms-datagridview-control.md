---
title: Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: 3d185b93f1e040ae320afbfd3e2b010bbf9ca624
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707076"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a>Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView
`DataGridView` Ovládací prvek umožňuje snadno definovat základního vzhledu buněk a formátování zobrazení hodnot v buňkách. Můžete definovat vzhled a formátování styly pro jednotlivé buňky, buněk v určité sloupce a řádky nebo všechny buňky v ovládacím prvku nastavením vlastnosti `DataGridViewCellStyle` objekty přístupné na základě různých `DataGridView` vlastnosti ovládacího prvku. Kromě toho můžete upravit tyto styly dynamicky na základě faktorů, jako je například hodnota buňky pomocí manipulace `CellFormatting` událostí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Změna ohraničení a mřížky styly v ovládacím prvku Windows Forms DataGridView](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 Popisuje, jak nastavit `DataGridView` vlastnosti, které definují vzhled ohraničení ovládacího prvku a hranice čar mezi buňkami.  
  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)  
 Popisuje `DataGridViewCellStyle` třídy a interakci vlastnosti tohoto typu pro definování zobrazení buňky v ovládacím prvku.  
  
 [Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 Popisuje způsob použití `DataGridViewCellStyle` vlastnosti, které chcete definovat výchozí vzhledu buněk v konkrétní řádky a sloupce a celý ovládací prvek.  
  
 [Postupy: Formát dat v Windows Forms DataGridView](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 Popisuje, jak formátovat zobrazované hodnoty buňky pomocí `DataGridViewCellStyle` vlastnosti.  
  
 [Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 Popisuje způsob použití `DefaultCellStyle` vlastnosti chcete nastavit základní zobrazit vlastnosti pro všechny buňky v ovládacím prvku.  
  
 [Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 Popisuje postup vytvoření účetní knihy efektu v ovládacím prvku pomocí střídavé řádky, které se zobrazují jiným způsobem.  
  
 [Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 Popisuje způsob použití `RowTemplate` vlastnosti chcete nastavit vlastnosti řádku, které se použijí pro všechny řádky v ovládacím prvku.  
  
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
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, které popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buňky a řádky a vytváření odvozené buňky, sloupce a typy řádků.  
  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 Obsahuje témata, která popisují běžně používané vlastnosti buněk, řádků a sloupců.  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
