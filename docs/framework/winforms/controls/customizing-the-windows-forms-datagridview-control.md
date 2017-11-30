---
title: "Přizpůsobení ovládacího prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d1246a8052af19057f7aa9d6729e34203177f8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Přizpůsobení ovládacího prvku Windows Forms DataGridView
`DataGridView` Řízení nabízí několik vlastností, které můžete upravit vzhled a chování základní (vzhled a chování) jeho buněk, řádků a sloupců. Pokud máte speciální požadavky nad rámec možností <xref:System.Windows.Forms.DataGridViewCellStyle> třídy, ale můžete také implementovat kreslení pro ovládací prvek vlastníka nebo rozšířit možnosti tak, že vytvoříte vlastní buněk, sloupce a řádky.  
  
 Chcete-li malovat buněk a řádky, sami, může zpracovávat různé `DataGridView` Malování události. Chcete-li upravit stávající funkce nebo přinášejí nové funkce, můžete vytvořit vlastní typy odvozené z existující `DataGridViewCell`, `DataGridViewColumn`, a `DataGridViewRow` typy. Můžete zadat také nové možnosti úprav vytvořením odvozené typy, které zobrazení ovládacího prvku dle vlastního výběru, když je buňku v režimu úprav.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.CellPainting> událostí k vyplnění buněk ručně.  
  
 [Postupy: přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.RowPrePaint> a <xref:System.Windows.Forms.DataGridView.RowPostPaint> události k vykreslení řádky s vlastní, barevného přechodu pozadí nebo obsahu, který zahrnuje několik sloupců.  
  
 [Postupy: přizpůsobení buněk a sloupců v systému Windows Forms DataGridView – ovládací prvek rozšířením jeho chování a vzhledu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Popisuje, jak vytvořit vlastní typy odvozené od `DataGridViewCell` a `DataGridViewColumn` Chcete-li zvýraznění buněk při umístění ukazatele myši na ně.  
  
 [Postupy: zákaz tlačítek ve sloupci tlačítek v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Popisuje, jak vytvořit vlastní typy odvozené od <xref:System.Windows.Forms.DataGridViewButtonCell> a <xref:System.Windows.Forms.DataGridViewButtonColumn> aby bylo možné zobrazit zakázané tlačítek ve sloupci tlačítek.  
  
 [Postupy: umisťování ovládacích prvků ve Windows Forms DataGridView buněk](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Popisuje, jak implementovat `IDataGridViewEditingControl` rozhraní a vytvořit vlastní typy odvozené z `DataGridViewCell` a `DataGridViewColumn` aby bylo možné zobrazit <xref:System.Windows.Forms.DateTimePicker> řídit, kdy buňku je v režimu úprav.  
  
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
 [Základní formátování a styly v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat v buňce.  
  
## <a name="see-also"></a>Viz také  
 [DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
