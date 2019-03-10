---
title: Přizpůsobení ovládacího prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 1f9c68ae85d7bad2b8cdcdaa63c1e7b46f9568ed
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703332"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Přizpůsobení ovládacího prvku Windows Forms DataGridView
`DataGridView` Ovládací prvek obsahuje několik vlastností, které vám umožní upravit vzhled a chování základní (vzhled a chování) jeho buněk, řádků a sloupců. Pokud máte zvláštní požadavky, které jde nad rámec možností <xref:System.Windows.Forms.DataGridViewCellStyle> třídy, ale můžete také implementovat kreslení pro ovládací prvek vlastníka nebo rozšířit její schopnosti tak, že vytvoříte vlastní buňky, sloupce a řádky.  
  
 Má Vymalovat buňky a řádky sami, můžete zpracovávat různé `DataGridView` Malování události. K úpravě stávajících funkcí nebo přinášejí nové funkce, můžete vytvořit vlastní typy odvozené z existující `DataGridViewCell`, `DataGridViewColumn`, a `DataGridViewRow` typy. Nové funkce pro úpravy můžete zadat taky tak, že vytvoříte odvozené typy, které zobrazení ovládacího prvku, které si vyberete, pokud je buňka v režimu úprav.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md)  
 Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.CellPainting> událost k vykreslení buňky ručně.  
  
 [Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-rows-in-the-datagrid.md)  
 Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.RowPrePaint> a <xref:System.Windows.Forms.DataGridView.RowPostPaint> události k vykreslení řádky s vlastní, barevného přechodu pozadí a obsah, který zahrnuje několik sloupců.  
  
 [Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jejich chování a vzhledu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Popisuje, jak vytvořit vlastní typy odvozené z `DataGridViewCell` a `DataGridViewColumn` informují buňky při umístění ukazatele myši na ně.  
  
 [Postupy: Zakázat tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Popisuje, jak vytvořit vlastní typy odvozené z <xref:System.Windows.Forms.DataGridViewButtonCell> a <xref:System.Windows.Forms.DataGridViewButtonColumn> mohla zobrazit zakázané tlačítek ve sloupci tlačítek.  
  
 [Postupy: Hostitelské ovládací prvky v buňkách Windows Forms DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Popisuje, jak implementovat `IDataGridViewEditingControl` rozhraní a vytvořit vlastní typy odvozené z `DataGridViewCell` a `DataGridViewColumn` mohla zobrazit <xref:System.Windows.Forms.DateTimePicker> řídit, kdy je buňka v režimu úprav.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewCell> třídy.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewRow> třídy.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewColumn> třídy.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní.  
  
## <a name="related-sections"></a>Související oddíly  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, které popisují, jak změnit základní vzhled ovládacího prvku a formátování zobrazení dat v buňce.  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
