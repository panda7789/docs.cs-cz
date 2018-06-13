---
title: Souhrn technologie ovládacího prvku DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: cafd832e7105540ae684dd1feb4b33ab74f72836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528870"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Souhrn technologie ovládacího prvku DataGridView (Windows Forms)
Toto téma shrnuje informace o `DataGridView` řízení a třídy, které podporují jeho použití.  
  
 Zobrazení dat ve formátu tabulky je úkol, který budete chtít nejspíš provádět často. `DataGridView` Ovládací prvek je navržený jako kompletního řešení pro zobrazení dat uložených v mřížce.  
  
## <a name="keywords"></a>Klíčová slova  
 DataGridView –, BindingSource, tabulce, buňky, vazby dat, virtuální režim  
  
## <a name="namespaces"></a>Jmenné prostory  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Související technologie  
 `BindingSource`  
  
## <a name="background"></a>Pozadí  
 Návrháři uživatelského rozhraní (UI) často někdy nutné má uživatelům zobrazit tabulková data. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje několik způsobů, jak zobrazit data v tabulce nebo v mřížce. `DataGridView` Řízení představuje nejnovější vývoj této technologie pro aplikace Windows Forms.  
  
 `DataGridView` Ovládací prvek může zobrazit řádky dat z úložiště dat. Mnoho typů úložišť dat jsou podporovány. Úložiště dat mohou být uloženy jednoduchý, bez typu dat, například jednorozměrné pole, nebo může uchovávat zadaných dat, jako například <xref:System.Data.DataSet>. Další informace najdete v tématu [postupy: vytvoření vazby dat ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 `DataGridView` Řízení poskytuje výkonný a flexibilní způsob, jak zobrazit data ve formátu tabulky. Ovládací prvek můžete použít k zobrazení jen pro čtení nebo jej nelze změnit zobrazení malé, aby velmi rozsáhlých datových sad.  
  
 Můžete rozšířit `DataGridView` ovládacího prvku několik způsobů, jak vytvořit vlastní chování do svých aplikací. Například můžete programově zadat vlastní řazení algoritmy a můžete vytvořit vlastní typy buněk. Můžete snadno přizpůsobit vzhled `DataGridView` řízení můžete volit mezi několik vlastností. Mnoho typů úložišť dat lze použít jako zdroj dat nebo `DataGridView` řízení může fungovat i bez zdroji dat, která je vázána k němu.  
  
## <a name="implementing-datagridview-classes"></a>Implementace třídy DataGridView  
 Existuje několik způsobů, abyste mohli využívat výhod `DataGridView` funkce rozšíření ovládacího prvku. Můžete přizpůsobit mnoho aspektů ovládacího prvku prostřednictvím vlastnosti a události, ale některé úpravy vyžadují, abyste vytvořit nové třídy odvozené z existujícího `DataGridView` třídy.  
  
 Jsou obvykle používané základní třídy `DataGridViewCell` a `DataGridViewColumn`. Odvozujete vlastní třídy buňky z `DataGridViewCell` ani v žádné z jejích podřízených tříd. Přestože do žádný sloupec můžete přidat libovolný typ buňky, bude obvykle také odvodíte třídu doprovodné sloupce z `DataGridViewColumn` který je hostitelem buněk vašeho typu vlastní buňky ve výchozím nastavení.  
  
 Můžete implementovat `IDataGridViewEditingCell` rozhraní v vaší buňky odvozené třídy za účelem vytvoření buňky typ, který má úpravy funkce ale není hostitelem ovládacího prvku v režimu úprav. Vytvoření ovládacího prvku, který je možné hostovat v buňce v režimu úprav, můžete implementovat `IDataGridViewEditingControl` rozhraní do třídy odvozené od <xref:System.Windows.Forms.Control>.  
  
 Další informace najdete v tématu [postupy: přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView pomocí rozšíření jejich chování a vzhledu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) a [postup: hostitelské ovládací prvky v systému Windows Forms DataGridView buněk](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>DataGridView – třídy na první pohled  
 <xref:System.Windows.Forms>  
  
|Oblast technologie|Třídy nebo rozhraní nebo konfigurační prvky|  
|---------------------|-------------------------------------------------|  
|Datová vazba|<xref:System.Windows.Forms.BindingSource>|  
|Prezentace dat|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> a odvozených tříd<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> a odvozených tříd<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> a odvozených tříd<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> Rozšiřitelnost|<xref:System.Windows.Forms.DataGridViewCell> a odvozených tříd<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> a odvozených tříd<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Co je nového  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek je navržený jako kompletního řešení pro zobrazení tabulková data s Windows Forms. Měli byste zvážit použití <xref:System.Windows.Forms.DataGridView> řízení před jiných řešení, jako například <xref:System.Windows.Forms.DataGrid>, při vytváření nové aplikace. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView> Řízení může fungovat zavřít společně s <xref:System.Windows.Forms.BindingSource> součásti. Tato součást je navržený jako primární zdroj dat formuláře. Umožňuje spravovat interakce mezi <xref:System.Windows.Forms.DataGridView> typ zdroje pro ovládací prvek a jeho zdroje dat, bez ohledu na data.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [Architektura ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)
