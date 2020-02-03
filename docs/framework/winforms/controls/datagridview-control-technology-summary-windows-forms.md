---
title: Souhrn technologie ovládacího prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: 18eebd067df9768e14cc81258184551d00dd1402
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742474"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Souhrn technologie ovládacího prvku DataGridView (Windows Forms)
Toto téma shrnuje informace o ovládacím prvku `DataGridView` a třídách, které podporují jeho použití.  
  
 Zobrazení dat v tabulkovém formátu je úkol, který se pravděpodobně často provádí. `DataGridView` ovládací prvek je navržen jako kompletní řešení pro prezentaci dat v mřížce.  
  
## <a name="keywords"></a>Klíčová slova  
 DataGridView, BindingSource, tabulka, buňka, datová vazba, virtuální režim  
  
## <a name="namespaces"></a>Obory názvů  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Související technologie  
 `BindingSource`  
  
## <a name="background"></a>Pozadí  
 Návrháři uživatelského rozhraní (UI) často hledají, že je potřeba zobrazit tabulková data pro uživatele. .NET Framework poskytuje několik způsobů, jak zobrazit data v tabulce nebo mřížce. Ovládací prvek `DataGridView` představuje nejnovější vývoj této technologie pro model Windows Forms aplikace.  
  
 Ovládací prvek `DataGridView` může zobrazit řádky dat z úložiště dat. Je podporováno mnoho typů úložišť dat. Úložiště dat může obsahovat jednoduché, netypové údaje, jako je jednorozměrné pole, nebo může uchovávat zadaná data, například <xref:System.Data.DataSet>. Další informace najdete v tématu [Postup: vytvoření vazby dat k ovládacímu prvku DataGridView model Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Ovládací prvek `DataGridView` poskytuje výkonný a flexibilní způsob zobrazení dat v tabulkovém formátu. Ovládací prvek můžete použít k zobrazení zobrazení jen pro čtení nebo upravitelných zobrazení malých až velkých datových sad.  
  
 Ovládací prvek `DataGridView` můžete roztáhnout několika způsoby, abyste mohli vytvářet vlastní chování aplikací. Můžete například programově zadat vlastní algoritmy řazení a můžete vytvořit vlastní typy buněk. Vzhled ovládacího prvku `DataGridView` lze snadno přizpůsobit výběrem z několika vlastností. Jako zdroj dat lze použít mnoho typů úložišť dat, nebo ovládací prvek `DataGridView` může fungovat bez vazby na zdroj dat.  
  
## <a name="implementing-datagridview-classes"></a>Implementace tříd DataGridView  
 K dispozici je několik způsobů, jak využít funkce rozšiřitelnosti ovládacího prvku `DataGridView`. Můžete přizpůsobit mnoho aspektů ovládacího prvku prostřednictvím událostí a vlastností, ale některé vlastní nastavení vyžaduje, abyste vytvořili nové třídy odvozené z existujících tříd `DataGridView`.  
  
 Nejčastěji používané základní třídy jsou `DataGridViewCell` a `DataGridViewColumn`. Můžete odvodit svou vlastní třídu buněk z `DataGridViewCell` nebo z jejích podřízených tříd. I když můžete přidat libovolný typ buňky do libovolného sloupce, obvykle se odvozuje také třída doprovodného sloupce z `DataGridViewColumn`, která hostuje buňky vlastního typu buňky ve výchozím nastavení.  
  
 Můžete implementovat rozhraní `IDataGridViewEditingCell` v odvozené třídě buňky pro vytvoření typu buňky, který má funkce úprav, ale nehostuje ovládací prvek v režimu úprav. Chcete-li vytvořit ovládací prvek, který lze hostovat v buňce v režimu úprav, můžete implementovat rozhraní `IDataGridViewEditingControl` ve třídě odvozené z <xref:System.Windows.Forms.Control>.  
  
 Další informace najdete v tématu [Postup: přizpůsobení buněk a sloupců v ovládacím prvku DataGridView model Windows Forms rozšířením jejich chování a vzhledu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) a [postupem: hostování ovládacích prvků v buňkách DataGridView v model Windows Forms DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Třídy DataGridView na první pohled  
 <xref:System.Windows.Forms>  
  
|Technologické oblasti|Třídy/rozhraní/konfigurační prvky|  
|---------------------|-------------------------------------------------|  
|Datová vazba|<xref:System.Windows.Forms.BindingSource>|  
|Prezentace dat|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|Rozšiřitelnost <xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Forms.DataGridViewCell> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> a odvozené třídy<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Co je nového?  
 <xref:System.Windows.Forms.DataGridView> ovládací prvek je navržen jako kompletní řešení pro zobrazování tabulkových dat pomocí model Windows Forms. Při vytváření nové aplikace byste měli zvážit použití ovládacího prvku <xref:System.Windows.Forms.DataGridView> před dalšími řešeními, jako je například <xref:System.Windows.Forms.DataGrid>. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> může pracovat v těsné spolupráci s komponentou <xref:System.Windows.Forms.BindingSource>. Tato součást je navržena jako primární zdroj dat formuláře. Může spravovat interakci mezi ovládacím prvkem <xref:System.Windows.Forms.DataGridView> a jeho zdrojem dat bez ohledu na typ zdroje dat.  
  
## <a name="see-also"></a>Viz také

- [Přehled ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
