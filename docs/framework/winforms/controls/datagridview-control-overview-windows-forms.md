---
title: "DataGridView – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d9cc6568813af866acaf20696b870bedc3099be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete zobrazit a upravit tabulková data z mnoha různých datových zdrojů.  
  
 Vazba dat k <xref:System.Windows.Forms.DataGridView> ovládací prvek je jednoduché a intuitivní a v mnoha případech je jednoduché, nastavení <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost. Při vytvoření vazby ke zdroji dat, která obsahuje více seznamů nebo tabulek, nastavte <xref:System.Windows.Forms.DataGridView.DataMember%2A> vlastnost na řetězec, který určuje seznamu nebo tabulky pro vazbu.  
  
 <xref:System.Windows.Forms.DataGridView> Řízení podporuje standardní Windows Forms datový model vazby, tak ho vytvoří vazbu k instance tříd, které jsou popsané v následujícím seznamu:  
  
-   Všechny třídy, která implementuje <xref:System.Collections.IList> rozhraní, včetně jednorozměrná pole.  
  
-   Všechny třídy, která implementuje <xref:System.ComponentModel.IListSource> rozhraní, jako <xref:System.Data.DataTable> a <xref:System.Data.DataSet> třídy.  
  
-   Všechny třídy, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní, například <xref:System.ComponentModel.BindingList%601> třídy.  
  
-   Všechny třídy, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní, například <xref:System.Windows.Forms.BindingSource> třídy.  
  
 <xref:System.Windows.Forms.DataGridView> Řízení podporuje datovou vazbu veřejné vlastnosti objektů vrácených z těchto rozhraní a vlastnosti kolekce vrácené <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní, pokud se implementuje na vrácených objektů.  
  
 Obvykle vytvoří vazbu k <xref:System.Windows.Forms.BindingSource> součásti a vazby <xref:System.Windows.Forms.BindingSource> součásti do jiného zdroje dat, nebo jeho naplnění objekty firmy. <xref:System.Windows.Forms.BindingSource> Součást je zdroj dat upřednostňované, protože lze vázat k široké škále zdrojů dat a může vyřešit řadu problémů vazby dat automaticky. Další informace najdete v tématu [BindingSource – komponenta](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView> Řízení lze také v *nevázaný* režimu s žádné příslušné datové úložiště. Pro příklad kódu, který se používá nevázaný <xref:System.Windows.Forms.DataGridView> řízení najdete v tématu [návod: vytváření nevázaný ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView> Řízení je vysoce Konfigurovatelný a rozšiřitelný a poskytuje mnoho vlastností, metod a událostí přizpůsobit její vzhled a chování. Když chcete aplikaci Windows Forms k zobrazení tabulková data, zvažte použití <xref:System.Windows.Forms.DataGridView> řízení před jiné (například <xref:System.Windows.Forms.DataGrid>). Pokud jsou zobrazení malé mřížky hodnot jen pro čtení, nebo pokud chcete povolit uživatelům upravit tabulku s miliony záznamů, <xref:System.Windows.Forms.DataGridView> řízení vám poskytne snadno programovatelná a paměti efektivní řešení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Souhrn technologie ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 Shrnuje <xref:System.Windows.Forms.DataGridView> řízení konceptech a použití související třídy.  
  
 [Architektura ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 Popisuje architekturu <xref:System.Windows.Forms.DataGridView> řízení, vysvětlením struktura hierarchie a dědičnost jeho typu.  
  
 [Scénáře ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 Popisuje nejběžnější scénáře, ve kterém <xref:System.Windows.Forms.DataGridView> ovládací prvky jsou používány.  
  
 [Adresář kódu ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 Obsahuje odkazy na příklady kódu v dokumentaci pro různé <xref:System.Windows.Forms.DataGridView> úlohy. Tyto příklady jsou klasifikovány podle typu úlohy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Popisuje typy sloupců v modelu Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek použitý k zobrazení informací a povolit uživatelům změnit nebo přidat informace.  
  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují, jak buď ručně, nebo z externího zdroje dat naplnit ovládací prvek s daty.  
  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buněk a řádků a vytváření odvozené buňky, sloupce a typy řádků.  
  
 [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkými objemy dat.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Ovládací prvek DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Výchozí funkce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
