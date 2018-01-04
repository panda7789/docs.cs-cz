---
title: "DataGrid – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataGrid
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- columns [Windows Forms], DataGrid control
- data sources [Windows Forms], binding to DataGrid control
- tables [Windows Forms], binding to DataGrid control
- DataGrid control [Windows Forms], data binding
- DataGrid control [Windows Forms], about DataGrid control
- parent tables in DataGrid control
- tables [Windows Forms], displaying in DataGrid control
- data grids [Windows Forms], about data grids
- multiple tables in DataGrid control
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- parent table navigation in DataGrid
- child tables [Windows Forms], dataGrid control
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10220efc0bb77ddcc7f0f9fa0e3f2793a032a1bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek zobrazí data v řadě řádků a sloupců. Nejjednodušším případě je při mřížky je vázán na zdroj dat se jedna tabulka, která obsahuje žádné relace. V takovém případě se data zobrazí v jednoduchých řádků a sloupců v tabulce. Další informace o vytvoření vazby dat pro další ovládací prvky najdete v tématu [datová vazba a systém Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
 Pokud <xref:System.Windows.Forms.DataGrid> vázané na data s více související tabulky, a pokud navigační je povolena v mřížce, mřížky zobrazí rozšíření, která jsou v jednotlivých řádcích. S expander může uživatel přesunout z nadřazené do podřízené tabulky. Kliknutím na uzel zobrazí podřízené tabulky, a kliknutím na tlačítko zpět původní nadřazené tabulce. Tímto způsobem zobrazí mřížku hierarchické relace mezi tabulkami.  
  
 Následující snímek obrazovky ukazuje, že DataGrid vázané na data s více tabulek.  
  
 ![DataGrid vázané na data s více tabulek](../../../../docs/framework/winforms/controls/media/vbcontrol1.gif "vbControl1")  
Vázání na data s více tabulek DataGrid  
  
 <xref:System.Windows.Forms.DataGrid> Můžete nabízí uživatelské rozhraní pro datovou sadu, navigace mezi související tabulky a bohaté formátování a možností pro úpravy.  
  
 Zobrazení a manipulace dat jsou samostatné funkce: ovládací prvek zpracovává uživatelské rozhraní, zatímco aktualizace dat jsou zpracovávány v architektuře Windows Forms datové vazby a nástrojem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat. Proto více ovládacích prvků vázaných ke stejnému zdroji dat bude zůstanou synchronizovány.  
  
> [!NOTE]
>  Pokud jste obeznámeni s DataGrid – ovládací prvek v jazyce Visual Basic 6.0, zjistíte, některé významné rozdíly v systému Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
 Když je vázána mřížky <xref:System.Data.DataSet>, sloupců a řádků se vytváří, formátu a automaticky vyplněna. Další informace najdete v tématu [datové vazby a rozhraní Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md). Následující generování <xref:System.Windows.Forms.DataGrid> řízení, můžete přidat, odstranit, změnit uspořádání a naformátovat sloupců a řádků v závislosti na vašich potřebách.  
  
## <a name="binding-data-to-the-control"></a>Vazba dat k ovládacímu prvku  
 Pro <xref:System.Windows.Forms.DataGrid> řízení fungovat, musí být vázána na zdroje dat pomocí <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti v době návrhu nebo <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda za běhu. Body tuto vazbu <xref:System.Windows.Forms.DataGrid> do objektu instancí zdroje dat, jako <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>). <xref:System.Windows.Forms.DataGrid> Řízení zobrazuje výsledky akcí, které se provádí na data. Většina dat konkrétní akce se neprovádí prostřednictvím <xref:System.Windows.Forms.DataGrid> , ale místo toho prostřednictvím zdroj dat.  
  
 Pokud aktualizaci dat v datové sadě vázané prostřednictvím jakéhokoli mechanismu <xref:System.Windows.Forms.DataGrid> ovládací prvek odráží změny. Pokud data mřížky a jeho tabulky styly a styly sloupec `ReadOnly` vlastnost nastavena na hodnotu `false`, data v sadě dat se dá aktualizovat přes <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
 V lze zobrazit pouze jedna tabulka <xref:System.Windows.Forms.DataGrid> najednou. Pokud relaci nadřazený podřízený definovaná mezi tabulkami, může uživatel přesunout mezi související tabulky, vyberte tabulku, který se má zobrazit v <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Informace o vazbě <xref:System.Windows.Forms.DataGrid> řídit k [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zdroje dat v době návrhu nebo běhu, naleznete v [postupy: vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
 Zdroje dat platný pro <xref:System.Windows.Forms.DataGrid> zahrnují:  
  
-   <xref:System.Data.DataTable>– Třída  
  
-   <xref:System.Data.DataView>– Třída  
  
-   <xref:System.Data.DataSet>– Třída  
  
-   <xref:System.Data.DataViewManager>– Třída  
  
 Pokud je zdrojem datovou sadu, datová sada může být objekt ve formátu nebo objekt předaná do formuláře webové služby XML. Můžete vázat na typu nebo netypové datové sady.  
  
 Můžete také navázat <xref:System.Windows.Forms.DataGrid> řízení další struktury, pokud objekty ve struktuře, jako je například prvků v poli, vystavit veřejné vlastnosti. Mřížky se zobrazí všechny veřejné vlastnosti elementů v strukturu. Například, pokud vytvoření vazby <xref:System.Windows.Forms.DataGrid> objekty ovládacího prvku na pole zákazníka, mřížky se zobrazí všechny veřejné vlastnosti těchto objektů zákazníka. V některých případech to znamená, že i když můžete vázat na strukturu, výsledná vázané struktura nemusí mít praktické aplikace. Například můžete vázat na pole celých čísel, ale protože `Integer` datový typ nepodporuje veřejné vlastnosti, tabulka nemůže zobrazit žádná data.  
  
 Můžete vázat na následující struktury, pokud jejich elementů vystavit veřejné vlastnosti:  
  
-   Všechny součásti, která implementuje <xref:System.Collections.IList> rozhraní. To zahrnuje dimenze jednoho pole.  
  
-   Všechny součásti, která implementuje <xref:System.ComponentModel.IListSource> rozhraní.  
  
-   Všechny součásti, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní.  
  
 Další informace o zdrojích dat najdete v tématu [datového zdroje podporované rozhraním Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
## <a name="grid-display"></a>Zobrazení mřížky  
 Běžně se používají <xref:System.Windows.Forms.DataGrid> ovládací prvek, je zobrazit jednu tabulku dat z datové sady. Ale ovládací prvek lze také zobrazit více tabulek, včetně související tabulky. Zobrazení mřížky se podle zdroj dat automaticky upraví. Následující tabulka uvádí, co se zobrazí u různých konfigurací.  
  
|Obsah sady dat|Co se zobrazí|  
|--------------------------|-----------------------|  
|Jednu tabulku.|Tabulka se zobrazí v mřížce.|  
|Více tabulek.|Mřížky můžete zobrazit stromové zobrazení, které uživatelé mohou přejít na najít tabulku, která se má zobrazit.|  
|Více souvisejících tabulek.|Mřížky můžete zobrazit zobrazení stromu pro výběr tabulek s, nebo můžete zadat, že zobrazení mřížky v nadřazené tabulce. Přejděte na řádky souvisejících podřízených uživatelům záznamy v nadřazené tabulce.|  
  
> [!NOTE]
>  Tabulky v datové sadě jsou propojeny pomocí <xref:System.Data.DataRelation>.  Viz také [HYPERLINK "http://msdn.microsoft.com/library/dbwcse3d (v=vs.110)" vztahy v datových sadách](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.110\)) nebo [vztahy v datových sadách](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.120\)).  
  
 Když <xref:System.Windows.Forms.DataGrid> ovládací prvek zobrazuje tabulku a <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> je nastavena na `true`, přeuspořádat dat kliknutím na záhlaví sloupce. Uživatele můžete také přidat řádky a upravit buněk.  
  
 Vztahy mezi sadu tabulek se zobrazí uživatelům s použitím nadřazených a podřízených struktury navigace. Nadřazené tabulky jsou nejvyšší úroveň dat a podřízené tabulky těchto datových tabulek, které jsou odvozeny od jednotlivých výpisy v nadřazené tabulky. Zobrazí se rozšíření, která jsou v jednotlivých řádcích nadřazené, která obsahuje podřízené tabulce. Kliknutím expander vytvoří seznam jako webové odkazy na podřízené tabulky. Když uživatel vybere odkaz, zobrazí se v podřízené tabulce. Kliknutím na ikonu Zobrazit či skrýt nadřazené řádky (![Zobrazit &#47; skrýt nadřazené řádky ikonu](../../../../docs/framework/winforms/controls/media/vbicon.gif "vbIcon")) bude skrýt informace o nadřazenou tabulku nebo způsobit, že pokud uživatel má skryté ho objevit znova. Uživatele můžete kliknout na tlačítko Zpět a vrátit do předchozího prohlíženého tabulky.  
  
## <a name="columns-and-rows"></a>Sloupců a řádků  
 <xref:System.Windows.Forms.DataGrid> Se skládá z kolekce <xref:System.Windows.Forms.DataGridTableStyle> objekty, které jsou součástí <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost. Styl tabulky mohou obsahovat kolekce <xref:System.Windows.Forms.DataGridColumnStyle> objekty, které jsou součástí <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle>... Můžete upravit <xref:System.Windows.Forms.DataGrid.TableStyles%2A> a <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnosti pomocí editory kolekce přistupovat prostřednictvím **vlastnosti** okno.  
  
 Všechny <xref:System.Windows.Forms.DataGridTableStyle> přidružené <xref:System.Windows.Forms.DataGrid> řízení je možné přistupovat prostřednictvím <xref:System.Windows.Forms.GridTableStylesCollection>. <xref:System.Windows.Forms.GridTableStylesCollection> Lze upravit v návrháři se <xref:System.Windows.Forms.DataGridTableStyle> editor kolekce nebo programově pomocí <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost.  
  
 ![Objektů obsažených v ovládacím prvku DataGrid](../../../../docs/framework/winforms/controls/media/vbcolumns1.gif "vbColumns1")  
Následující obrázek znázorňuje objektů obsažených v ovládacím prvku DataGrid.  
  
 Tabulka styly a styly sloupce jsou synchronizovány s <xref:System.Data.DataTable> objekty a <xref:System.Data.DataColumn> objekty podle nastavení jejich `MappingName` vlastnosti na příslušné <xref:System.Data.DataTable.TableName%2A> a <xref:System.Data.DataColumn.ColumnName%2A> vlastnosti. Při <xref:System.Windows.Forms.DataGridTableStyle> , neobsahuje žádné sloupce styly se přidá do <xref:System.Windows.Forms.DataGrid> ovládací prvky vázané na platný datový zdroj a <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost daný styl tabulky je nastavena na platný <xref:System.Data.DataTable.TableName%2A> vlastnost, kolekce <xref:System.Windows.Forms.DataGridColumnStyle> pro který se vytvoří objekty Styl tabulky. Pro každou <xref:System.Data.DataColumn> v nalezen <xref:System.Data.DataTable.Columns%2A> kolekce <xref:System.Data.DataTable>, odpovídající <xref:System.Windows.Forms.DataGridColumnStyle> se přidá do <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection>je přístupné přes <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle>. Sloupce můžete přidat nebo odstranit pomocí mřížky <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> nebo <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> metodu <xref:System.Windows.Forms.GridColumnStylesCollection>. Další informace najdete v tématu [postupy: přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) a [postupy: odstranění nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).  
  
 Rozšiřuje kolekce typy sloupců <xref:System.Windows.Forms.DataGridColumnStyle> s bohatou formátování a možností pro úpravy. Dědí všechny typy sloupců <xref:System.Windows.Forms.DataGridColumnStyle> základní třídy. Třída, která je vytvořila, závisí na <xref:System.Data.DataColumn.DataType%2A> vlastnost <xref:System.Data.DataColumn> ze kterého <xref:System.Web.UI.WebControls.DataGridColumn> je založena. Například <xref:System.Data.DataColumn> s jeho <xref:System.Data.DataColumn.DataType%2A> vlastnost nastavena na hodnotu <xref:System.Boolean> bude přidružen <xref:System.Windows.Forms.DataGridBoolColumn>. Následující tabulka popisuje každý z těchto typů sloupec.  
  
|Typ sloupce|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Přijme a zobrazí data jako formátovaném nebo neformátovaném řetězce. Funkce pro úpravy jsou stejné, jako jsou pro úpravy dat v jednoduchou <xref:System.Windows.Forms.TextBox>. Dědí z <xref:System.Windows.Forms.DataGridColumnStyle>.|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|Přijme a zobrazí `true`, `false`a hodnoty null. Dědí z <xref:System.Windows.Forms.DataGridColumnStyle>.|  
  
 Dvakrát klikněte na pravý okraj sloupce změní sloupce k zobrazení jeho úplnou popisek a nejširší položky.  
  
## <a name="table-styles-and-column-styles"></a>Tabulka styly a styly sloupců  
 Jakmile jste vytvořili výchozí formát <xref:System.Windows.Forms.DataGrid> ovládací prvek, můžete přizpůsobit barvy, které se použijí při určité tabulky jsou zobrazeny v datové mřížce.  
  
 To je dosaženo vytvořením instance <xref:System.Windows.Forms.DataGridTableStyle> třídy. Styly tabulky zadejte formátování konkrétní tabulky, liší od výchozí formátování <xref:System.Windows.Forms.DataGrid> ovládací prvek. Každá tabulka může mít pouze jednu tabulku styl definovaný pro něj najednou.  
  
 V některých případech budete chtít konkrétní sloupec podívejte se liší od zbytku sloupce tabulky konkrétní data. Můžete vytvořit vlastní sadu sloupců stylů pomocí <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost.  
  
 Styly sloupců se vztahují k sloupců v datové sadě, stejně jako styly tabulky se vztahují k datových tabulek. Stejně jako každá tabulka může mít pouze jeden styl tabulky definované pro něj najednou, takže příliš můžete každý sloupec pouze jeden sloupec styl definovali její ve stylu konkrétní tabulky. Tento vztah je definována v sloupce <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> vlastnost.  
  
 Pokud jste vytvořili styl tabulky bez styly sloupec přidán do něj [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] přidá výchozí styly sloupce při vytvoření formuláře a mřížky v době běhu. Ale v případě, že jste vytvořili styl tabulky a přidat všechny sloupce styly, [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] nevytvoří žádné sloupce stylů. Bude také muset definovat sloupce styly a přiřadit jim s názvem mapování má sloupce, které chcete zobrazit v mřížce.  
  
 Vzhledem k tomu, že zadáte sloupce, které jsou zahrnuty v datové mřížce přiřazením styl sloupce a sloupce byl přiřazen žádný sloupec styl, můžete zahrnout sloupce dat v datové sadě, které se nezobrazí v mřížce. Ale protože datový sloupec je obsažena v datové sadě, můžete prostřednictvím kódu programu upravit data, která se nezobrazí.  
  
> [!NOTE]
>  Obecně platí vytvořit sloupec styly a přidat je do kolekce sloupců styly před přidáním styly tabulky do kolekce styly tabulky. Když přidáte prázdná tabulka styl do kolekce, styly sloupec vygenerují automaticky za vás. V důsledku toho se výjimka vyvolána, pokud se pokusíte přidat nové styly sloupec s duplicitní <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> hodnot do kolekce sloupců stylů.  
>   
>  V některých případech můžete upravit pouze jeden sloupec mezi mnoho sloupců; například datová sada obsahuje 50 sloupce a chcete 49 z nich. V takovém případě je jednodušší a importovat všechny sloupce 50 prostřednictvím kódu programu odebrat jedno namísto programové přidání všech 49 jednotlivých sloupcích chcete.  
  
## <a name="formatting"></a>Formátování  
 Formátování, které lze použít <xref:System.Windows.Forms.DataGrid> řízení zahrnuje styly ohraničení, styly mřížky, písma, Vlastnosti titulku, zarovnání dat a střídání barvy pozadí mezi řádky. Další informace najdete v tématu [postupy: formátování ovládacího prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md).  
  
## <a name="events"></a>Události  
 Kromě toho nejběžnější řídit události <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>, a <xref:System.Windows.Forms.DataGrid.Scroll>, <xref:System.Windows.Forms.DataGrid> řízení podporuje události související s úpravy a navigace v mřížce. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> Vlastnost určuje, která buňka je vybrána. <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> Událost se vyvolá, když uživatel přejde na nové buňky. Když uživatel přejde na novou tabulku prostřednictvím vztahů nadřazený podřízený <xref:System.Windows.Forms.DataGrid.Navigate> událost se vyvolá. <xref:System.Windows.Forms.DataGrid.BackButtonClick> Událost se vyvolá, když uživatel klikne na tlačítko Zpět, když uživatel prohlíží podřízené tabulky a <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> událost se vyvolá při kliknutí na ikonu Zobrazit či skrýt nadřazené řádky.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Postupy: Formátování ovládacího prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)
