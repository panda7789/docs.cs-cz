---
title: Souhrn technologie ovládacího prvku DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: efa567e6f8a91b40d2710b4cef0d1a56d38650c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737829"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Souhrn technologie ovládacího prvku DataGridView (Windows Forms)
Toto téma shrnuje informace o `DataGridView` ovládacího prvku a tříd, které podporují jeho použití.  
  
 Zobrazení dat ve formátu tabulky je úkol, který budete chtít nejspíš provádět často. `DataGridView` Ovládací prvek je navržena jako kompletní řešení pro zobrazení dat v mřížce.  
  
## <a name="keywords"></a>Klíčová slova  
 Ovládací prvek DataGridView, objekt BindingSource, tabulky, buňky, datové vazby, virtuální režim  
  
## <a name="namespaces"></a>Jmenné prostory  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Související technologie  
 `BindingSource`  
  
## <a name="background"></a>Pozadí  
 Návrháře uživatelské rozhraní (UI) často někdy nutné uživatelům zobrazit data tabulky. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje několik způsobů, jak zobrazit data v tabulce nebo v mřížce. `DataGridView` Řízení představuje nejnovější vývoj tuto technologii pro aplikace Windows Forms.  
  
 `DataGridView` Ovládací prvek mohl zobrazit řádky dat z úložiště dat. Mnoho typů úložišť dat podporovaných. Úložiště dat může obsahovat jednoduché, netypové datové, jako je jednorozměrné pole, nebo může obsahovat typy dat, jako například <xref:System.Data.DataSet>. Další informace najdete v tématu [jak: Vytvoření vazby dat k Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 `DataGridView` Ovládacího prvku poskytuje výkonný a flexibilní způsob, jak zobrazit data ve formátu tabulky. K zobrazení jen pro čtení nebo upravovat malé a velmi velké sady dat můžete použít ovládací prvek.  
  
 Můžete rozšířit `DataGridView` ovládacího prvku v několik způsobů, jak vytvářet vlastní chování do svých aplikací. Například můžete programově zadat vlastní algoritmy řazení a můžete vytvořit vlastní typy buňky. Můžete snadno přizpůsobit vzhled `DataGridView` ovládací prvek výběru mezi několik vlastností. Mnoho typů úložišť dat může sloužit jako zdroj dat nebo `DataGridView` ovládací prvek může pracovat bez zdroje dat vázány.  
  
## <a name="implementing-datagridview-classes"></a>Implementace třídy ovládacího prvku DataGridView  
 Existuje několik způsobů, jak můžete využít `DataGridView` rozšiřující funkce ovládacího prvku. Můžete upravit mnoho aspektů řízení prostřednictvím vlastnosti a události, ale některá vlastní nastavení vyžadují, abyste k vytvoření nové třídy odvozené z existujících `DataGridView` třídy.  
  
 Nejčastěji používané základní třídy jsou `DataGridViewCell` a `DataGridViewColumn`. Lze odvodit vlastní třídu buňky od `DataGridViewCell` ani žádný z jejích podřízených tříd. I když můžete přidat libovolný typ buňky do každého sloupce, je obvykle také odvodí doprovodné třídy sloupce z `DataGridViewColumn` buňky ovládacího prvku vlastní buňka typ, který je hostitelem ve výchozím nastavení.  
  
 Můžete implementovat `IDataGridViewEditingCell` rozhraní ve třídě odvozené buňky a vytvořte typ buňky, která má funkcí pro úpravy, ale není hostitelem ovládací prvek v režimu úprav. Vytvoření ovládacího prvku, který může hostovat v buňce v režimu úprav, můžete implementovat `IDataGridViewEditingControl` rozhraní v třídě odvozené z <xref:System.Windows.Forms.Control>.  
  
 Další informace najdete v tématu [jak: Přizpůsobení buněk a sloupců v Windows Forms DataGridView rozšířením jejich chování a vzhledu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) a [jak: Hostování ovládacích prvků ve Windows Forms DataGridView buňky](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Třídy ovládacího prvku DataGridView na první pohled  
 <xref:System.Windows.Forms>  
  
|Technologickou oblast|Elementy třídy/rozhraní/konfigurace|  
|---------------------|-------------------------------------------------|  
|Datová vazba|<xref:System.Windows.Forms.BindingSource>|  
|Prezentace dat|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> Rozšiřitelnost|<xref:System.Windows.Forms.DataGridViewCell> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Co je nového  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek je navržena jako kompletní řešení pro zobrazení tabulkových dat ovládacím prvkem Windows Forms. Měli byste zvážit použití <xref:System.Windows.Forms.DataGridView> ovládací prvek před další řešení, jako například <xref:System.Windows.Forms.DataGrid>, při vytváření nové aplikace. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek můžou fungovat zavřít společně s <xref:System.Windows.Forms.BindingSource> komponenty. Tato součást byla navržena jako zdroj primární datové formuláře. Interakce mezi dokáže spravovat <xref:System.Windows.Forms.DataGridView> typ zdrojového ovládacího prvku a zdrojem dat, bez ohledu na data.  
  
## <a name="see-also"></a>Viz také:
- [Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
- [Architektura ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
- [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)
