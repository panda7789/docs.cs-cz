---
title: Základní formátování a stylování v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d295718b7bd4f3bc4c5f63b6e6cb911f733525fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731994"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a>Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView
Ovládací prvek `DataGridView` umožňuje snadno definovat základní vzhled buněk a formátování zobrazení hodnot buněk. Můžete definovat styly vzhledu a formátování pro jednotlivé buňky, pro buňky v určitých sloupcích a řádcích nebo pro všechny buňky v ovládacím prvku nastavením vlastností objektů `DataGridViewCellStyle`, ke kterým přistupovaly prostřednictvím různých vlastností ovládacího prvku `DataGridView`. Kromě toho můžete tyto styly dynamicky upravovat na základě faktorů, jako je hodnota buňky, pomocí zpracování události `CellFormatting`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 Popisuje, jak nastavit vlastnosti `DataGridView` definující vzhled ohraničení ovládacího prvku a hraniční čáry mezi buňkami.  
  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)  
 Popisuje třídu `DataGridViewCellStyle` a způsob interakce vlastností daného typu s cílem definovat způsob zobrazení buněk v ovládacím prvku.  
  
 [Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 Popisuje, jak pomocí vlastností `DataGridViewCellStyle` definovat výchozí vzhled buněk v konkrétních řádcích a sloupcích a v celém ovládacím prvku.  
  
 [Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 Popisuje, jak formátovat hodnoty zobrazení buňky pomocí vlastností `DataGridViewCellStyle`.  
  
 [Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 Popisuje, jak použít vlastnost `DefaultCellStyle` k nastavení základních vlastností zobrazení pro všechny buňky v ovládacím prvku.  
  
 [Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 Popisuje, jak vytvořit efekt v hlavní knize v ovládacím prvku pomocí střídavých řádků, které jsou zobrazeny jinak.  
  
 [Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 Popisuje, jak použít vlastnost `RowTemplate` k nastavení vlastností řádku, které budou použity pro všechny řádky ovládacího prvku.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 Poskytuje referenční dokumentaci pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting>.  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, která popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buňky a řádky a vytváření odvozených typů buněk, sloupců a řádků.  
  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 Poskytuje témata, která popisují běžně používané vlastnosti buňky, řádku a sloupce.  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
