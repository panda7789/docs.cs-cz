---
title: DataGridView – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: a327b225dca3dfcab8444567d37a6a5ebe7490ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710531"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 S <xref:System.Windows.Forms.DataGridView> ovládacího prvku, můžete zobrazit a upravit tabulková data z mnoha různých druhů zdrojů dat.  
  
 Vazba dat <xref:System.Windows.Forms.DataGridView> ovládacího prvku je jednoduchý a intuitivní a v mnoha případech je stejně jednoduché jako nastavení <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost. Když se navážete na zdroj dat, který obsahuje více seznamů a tabulek, nastavte <xref:System.Windows.Forms.DataGridView.DataMember%2A> nastavte na řetězec, který určuje seznam nebo tabulku k vytvoření vazby.  
  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek podporuje standardní Windows Forms datový model vazby, proto vytvoří vazbu instance tříd, které je popsáno v následujícím seznamu:  
  
-   Všechny třídy, která implementuje <xref:System.Collections.IList> rozhraní, včetně jednorozměrná pole.  
  
-   Všechny třídy, která implementuje <xref:System.ComponentModel.IListSource> rozhraní, jako <xref:System.Data.DataTable> a <xref:System.Data.DataSet> třídy.  
  
-   Všechny třídy, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní, jako <xref:System.ComponentModel.BindingList%601> třídy.  
  
-   Všechny třídy, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní, jako <xref:System.Windows.Forms.BindingSource> třídy.  
  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek podporuje datové vazby k veřejné vlastnosti objektů vrácených podle těchto rozhraní a vlastnosti kolekci vrácené poskytovatelem <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní, je-li implementovat na vrácených objektů.  
  
 Obvykle vytvoří vazbu k <xref:System.Windows.Forms.BindingSource> komponenty a vazby <xref:System.Windows.Forms.BindingSource> komponentu do jiného zdroje dat, nebo přidejte do ní pro obchodní objekty. <xref:System.Windows.Forms.BindingSource> Komponenta je upřednostňovaný zdroj, protože můžete vázat na širokou škálu zdrojů dat a můžete vyřešit řadu problémů vazby dat automaticky. Další informace najdete v tématu [komponenty BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek lze také v *nevázaného* režimu s žádná základní data store. Příklad kódu, který používá nevázaný <xref:System.Windows.Forms.DataGridView> řídí, najdete v článku [názorný postup: Vytvoření nevázaného Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek je vysoce konfigurovatelné a rozšiřitelné, a poskytuje mnoho vlastnosti, metody a události přizpůsobit její vzhled a chování. Pokud chcete aplikaci Windows Forms k zobrazení tabulky dat, zvažte použití <xref:System.Windows.Forms.DataGridView> ovládací prvek před ostatními (například <xref:System.Windows.Forms.DataGrid>). Pokud zobrazujete Jemná mřížka jen pro čtení hodnot, nebo pokud chcete povolit uživatelům upravit tabulku s milióny záznamů, <xref:System.Windows.Forms.DataGridView> ovládací prvek vám poskytne řešení snadno programovatelná, efektivně využívajícího paměť.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Souhrn technologie ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 Shrnuje <xref:System.Windows.Forms.DataGridView> řídit koncepty a používání související třídy.  
  
 [Architektura ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 Popisuje architekturu <xref:System.Windows.Forms.DataGridView> ovládacího prvku, s vysvětlením, její typ struktura hierarchie a dědičnost.  
  
 [Scénáře ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 Popisuje nejběžnější scénáře, ve kterém <xref:System.Windows.Forms.DataGridView> ovládací prvky se používají.  
  
 [Adresář kódu ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 Obsahuje odkazy na příklady kódu v dokumentaci pro různé <xref:System.Windows.Forms.DataGridView> úlohy. Tyto příklady jsou rozděleny podle typu úlohy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Tento článek popisuje typy sloupců v modelu Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek použitý k zobrazení informací a umožní uživatelům změnit nebo přidat informace.  
  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, které popisují, jak ručně, nebo z externího zdroje dat naplnění ovládacího prvku s daty.  
  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, které popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buňky a řádky a vytváření odvozené buňky, sloupce a typy řádků.  
  
 [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, které popisují, jak pomocí efektivně se vyhnout problémům s výkonem při práci s velkými objemy dat ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Ovládací prvek DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [Výchozí funkce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)
- [Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
