---
title: DataGrid – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DataGrid
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
ms.openlocfilehash: 8deb151572b8a83396e4204378783304b66216c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648133"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek zobrazuje data ve skupině řádků a sloupců. Nejjednodušší případ je při mřížky je svázán se zdrojem dat u jedné tabulky, který obsahuje žádné relace. V takovém případě se data zobrazí v jednoduché řádků a sloupců, stejně jako v tabulce. Další informace o vazbě dat na další ovládací prvky najdete v tématu [a datové vazby Windows Forms](../data-binding-and-windows-forms.md).  
  
 Pokud <xref:System.Windows.Forms.DataGrid> je vázán na data s několika související tabulky, a pokud je povolena navigace v mřížce, mřížky se zobrazí jde v jednotlivých řádcích. Pomocí rozšíření může uživatel přesunout z nadřazené tabulky podřízené tabulky. Kliknutím na uzel zobrazí v podřízené tabulce, a kliknutím na tlačítko zpět původní nadřazené tabulky. Tímto způsobem v mřížce zobrazené hierarchických vztahů mezi tabulkami.  
  
 Následující snímek obrazovky ukazuje, že ovládacího prvku DataGrid vázán na data s více tabulkami:  
  
 ![Aplikace WinForms v jazyce zobrazení ovládacího prvku DataGrid vázán na data s více tabulkami.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)  
  
 <xref:System.Windows.Forms.DataGrid> Může poskytnout uživatelského rozhraní pro datovou sadu, navigaci mezi souvisejícími tabulkami a bohaté formátování a možností pro úpravy.  
  
 Zobrazení a manipulaci s daty jsou samostatné funkce: Ovládací prvek zpracovává uživatelské rozhraní, zatímco zpracování aktualizací dat podle architektury datové vazby Windows Forms a tím [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data zprostředkovatele. Proto více ovládacích prvků vázaných ke stejnému zdroji dat zůstane synchronizovaná.  
  
> [!NOTE]
>  Pokud jste se seznámili s ovládacího prvku DataGrid v jazyce Visual Basic 6.0, najdete několik významných rozdílů v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
 Mřížka je vázána k <xref:System.Data.DataSet>, sloupců a řádků jsou automaticky vytvořeny ve formátu a vyplněné. Další informace najdete v tématu [datové vazby a Windows Forms](../data-binding-and-windows-forms.md). Následující generování <xref:System.Windows.Forms.DataGrid> ovládacího prvku, můžete přidat, odstranit, změnit uspořádání a formátování sloupců a řádků v závislosti na požadavcích.  
  
## <a name="binding-data-to-the-control"></a>Vazba dat k ovládacímu prvku  
 Pro <xref:System.Windows.Forms.DataGrid> řídit práci, by měl být vázán na zdroj dat pomocí <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti v době návrhu nebo <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda v době běhu. Ukazuje tuto vazbu <xref:System.Windows.Forms.DataGrid> instance zdroje dat objektu, například <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>). <xref:System.Windows.Forms.DataGrid> Ovládací prvek zobrazuje výsledky akcí, které se provádějí s daty. Většinu akcí týkající se dat se neprovádí přes <xref:System.Windows.Forms.DataGrid> , ale místo toho prostřednictvím datového zdroje.  
  
 Pokud prostřednictvím každý použitý mechanizmus, se aktualizuje data v datové sadě vázané <xref:System.Windows.Forms.DataGrid> ovládací prvek se změny projeví. Pokud máte datové mřížky a jeho styly a styly sloupců `ReadOnly` vlastnost nastavena na hodnotu `false`, data v datové sadě je možné aktualizovat prostřednictvím <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
 Je možné zobrazit pouze jednu tabulku v <xref:System.Windows.Forms.DataGrid> najednou. Pokud je definována hierarchických vztahů mezi tabulkami, uživatel může přecházet mezi tabulkami, vyberte tabulku, který se má zobrazit <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Informace o vazbách <xref:System.Windows.Forms.DataGrid> ovládací prvek [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zdroje dat v době návrhu nebo běhu, naleznete v [jak: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
 Platné datové zdroje pro <xref:System.Windows.Forms.DataGrid> patří:  
  
- <xref:System.Data.DataTable> Třída  
  
- <xref:System.Data.DataView> Třída  
  
- <xref:System.Data.DataSet> Třída  
  
- <xref:System.Data.DataViewManager> Třída  
  
 Pokud je zdrojem datovou sadu, může být datovou sadu objektu ve formě nebo objekt předaných do formuláře webové služby XML. Můžete vytvořit vazbu na typové a netypové datové sady.  
  
 Můžete také navázat <xref:System.Windows.Forms.DataGrid> ovládací prvek další struktury, pokud objekty ve struktuře, jako jsou například prvky v poli, zpřístupnit veřejné vlastnosti. Mřížka se zobrazí všechny veřejné vlastnosti prvků ve struktuře. Například, pokud vytvoření vazby <xref:System.Windows.Forms.DataGrid> objekty ovládacího prvku na celou řadu zákazníků, mřížky se zobrazí všechny veřejné vlastnosti těchto objektů zákazníka. V některých případech to znamená, že i když můžete vázat na strukturu, výsledná vázaná struktura možná není praktické aplikace. Například lze svázat pole celých čísel, ale protože `Integer` datový typ není podporován veřejnou vlastnost, mřížky nelze zobrazit žádná data.  
  
 Pokud se jejich prvky zpřístupňují veřejných vlastností můžete vázat na následující struktury:  
  
- Všechny komponenty, která implementuje <xref:System.Collections.IList> rozhraní. To zahrnuje pole jednou dimenzí.  
  
- Všechny komponenty, která implementuje <xref:System.ComponentModel.IListSource> rozhraní.  
  
- Všechny komponenty, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní.  
  
 Další informace o zdrojích dat najdete v části [zdroje dat podporované rozhraním Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
## <a name="grid-display"></a>Zobrazení mřížky  
 Běžně <xref:System.Windows.Forms.DataGrid> je ovládací prvek pro zobrazení dat z datové sady jedné tabulky. Nicméně ovládací prvek lze také k zobrazení více tabulkami včetně tabulek. Zobrazení mřížky se automaticky upraví podle zdroje dat. Následující tabulka uvádí, co se zobrazí pro různé konfigurace.  
  
|Obsah sady dat|Co se zobrazí|  
|--------------------------|-----------------------|  
|Jedné tabulky.|Tabulky se zobrazí v mřížce.|  
|Více tabulek.|Mřížky můžete zobrazit stromové zobrazení, které uživatelé mohou přejít k vyhledání v tabulce, které se mají zobrazit.|  
|Více souvisejícími tabulkami.|Mřížky můžete zobrazit zobrazení stromu pro výběr tabulky s, nebo můžete určit, že mřížky se zobrazí nadřazené tabulky. Přejít na související podřízené řádky uživatelům záznamů v nadřazené tabulce.|  
  
> [!NOTE]
> Tabulky v datové sadě se týkají používání <xref:System.Data.DataRelation>. Viz také [vytváření vztahů mezi tabulkami](/visualstudio/data-tools/relationships-in-datasets).
  
 Když <xref:System.Windows.Forms.DataGrid> ovládací prvek je zobrazení tabulky a <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> je nastavena na `true`, přeuspořádat dat kliknutím na záhlaví sloupců. Uživatele můžete také přidat řádky a upravovat buňky.  
  
 Relace mezi sadou tabulek se zobrazí uživatelům s použitím nadřazené a podřízené struktury navigace. Nadřazené tabulky jsou nejvyšší úroveň dat a podřízené tabulky jsou tabulkami dat, které jsou odvozeny od seznamu jednotlivých do nadřazených tabulek. Rozšíření se zobrazí v každé nadřazené řádek, který obsahuje podřízené tabulky. Kliknutím na rozšíření generuje seznam jako webové odkazy na podřízené tabulky. Když uživatel vybere odkaz, zobrazí se v podřízené tabulce. Kliknutím na ikonu (Zobrazit/skrýt nadřazené řádky![Zobrazit nebo skrýt ikony nadřazené řádky](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) se skrýt informace o nadřazené tabulky nebo způsobit, že ji znovu zobrazit, pokud uživatel má dříve je skrytý. Uživatel můžete kliknout na tlačítko Zpět chcete vrátit do předchozího prohlíženého tabulky.  
  
## <a name="columns-and-rows"></a>Sloupců a řádků  
 <xref:System.Windows.Forms.DataGrid> Se skládá z kolekce <xref:System.Windows.Forms.DataGridTableStyle> objekty, které jsou součástí <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost. Styl tabulky mohou obsahovat kolekce <xref:System.Windows.Forms.DataGridColumnStyle> objekty, které jsou součástí <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle>... Můžete upravit <xref:System.Windows.Forms.DataGrid.TableStyles%2A> a <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnosti pomocí editory kolekce přistupovat prostřednictvím **vlastnosti** okna.  
  
 Žádné <xref:System.Windows.Forms.DataGridTableStyle> přidružené <xref:System.Windows.Forms.DataGrid> ovládací prvek je přístupný prostřednictvím <xref:System.Windows.Forms.GridTableStylesCollection>. <xref:System.Windows.Forms.GridTableStylesCollection> Lze upravit v návrháři se <xref:System.Windows.Forms.DataGridTableStyle> editor kolekce, nebo prostřednictvím kódu programu přes <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnost.  

 Objektů obsažených v ovládacím prvku DataGrid naleznete na následujícím obrázku:

 ![Diagram zobrazující průběh objektů obsažených v ovládacím prvku DataGrid.](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)  
  
 Styly a styly sloupců jsou synchronizovány s <xref:System.Data.DataTable> objekty a <xref:System.Data.DataColumn> objekty tak, že nastavíte jejich `MappingName` vlastnosti na příslušné <xref:System.Data.DataTable.TableName%2A> a <xref:System.Data.DataColumn.ColumnName%2A> vlastnosti. Při <xref:System.Windows.Forms.DataGridTableStyle> , který nemá žádný sloupec styly se přidá do <xref:System.Windows.Forms.DataGrid> ovládací prvek vázán na platný zdroj dat a <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> daného stylu tabulky je nastavena na platnou <xref:System.Data.DataTable.TableName%2A> vlastnost, kolekce <xref:System.Windows.Forms.DataGridColumnStyle> pro, který se vytvoří objekty Styl tabulky. Pro každou <xref:System.Data.DataColumn> součástí <xref:System.Data.DataTable.Columns%2A> kolekce <xref:System.Data.DataTable>, odpovídající <xref:System.Windows.Forms.DataGridColumnStyle> se přidá do <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection> je přístupný prostřednictvím <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle>. Sloupce lze přidat nebo odstranit pomocí mřížky <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> nebo <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> metodu <xref:System.Windows.Forms.GridColumnStylesCollection>. Další informace najdete v tématu [jak: Přidání tabulek a sloupců do Windows Forms DataGrid – ovládací prvek](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) a [jak: Odstranění či skrytí sloupců v Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).  
  
 Kolekce typů sloupce rozšiřuje <xref:System.Windows.Forms.DataGridColumnStyle> třída s atributem bohaté možnosti formátování a možností pro úpravy. Dědí všechny typy sloupců <xref:System.Windows.Forms.DataGridColumnStyle> základní třídy. Třída, která je vytvořena závisí na <xref:System.Data.DataColumn.DataType%2A> vlastnost <xref:System.Data.DataColumn> ze kterého <xref:System.Web.UI.WebControls.DataGridColumn> je založena. Například <xref:System.Data.DataColumn> , který má jeho <xref:System.Data.DataColumn.DataType%2A> vlastnost nastavena na hodnotu <xref:System.Boolean> přidruží <xref:System.Windows.Forms.DataGridBoolColumn>. Následující tabulka popisuje každý z těchto typů sloupců.  
  
|Typ sloupce|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Přijímá a zobrazuje data jako řetězce formátovaném nebo neformátovaném tvaru. Funkce pro úpravy jsou stejné jako pro úpravy dat v jednoduché <xref:System.Windows.Forms.TextBox>. Dědí z <xref:System.Windows.Forms.DataGridColumnStyle>.|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|Přijímá a zobrazuje `true`, `false`a hodnoty null. Dědí z <xref:System.Windows.Forms.DataGridColumnStyle>.|  
  
 Dvojitým kliknutím pravého okraje sloupce se změní velikost sloupce zobrazíte jeho plnou titulek a nejširší položky.  
  
## <a name="table-styles-and-column-styles"></a>Styly a styly sloupců  
 Jakmile ověříte výchozí formát <xref:System.Windows.Forms.DataGrid> ovládacího prvku, můžete také přizpůsobit barvy, které se mají použít při určité tabulky se zobrazí v datové mřížce.  
  
 Toho dosáhnete pomocí vytváření instancí <xref:System.Windows.Forms.DataGridTableStyle> třídy. Styly tabulky zadejte formátování konkrétní tabulky, liší od výchozí formátování <xref:System.Windows.Forms.DataGrid> samotného ovládacího prvku. Každá tabulka může mít pouze jeden styl tabulky pro ni definována současně.  
  
 V některých případech budete chtít podívejte konkrétní sloupce se liší od zbývající sloupce konkrétní datové tabulky. Můžete vytvořit vlastní sadu styly sloupců pomocí <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnost.  
  
 Styly sloupců se vztahují k sloupců v datové sadě, stejně jako styly tabulky se vztahují k datových tabulek. Stejně jako každá tabulka může mít jenom jeden styl tabulky pro ni definována najednou, takže příliš může každý sloupec pouze jeden sloupec styl definovali, ve stylu konkrétní tabulku. Tento vztah je definována v sloupce <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> vlastnost.  
  
 Pokud jste vytvořili styl tabulky bez styly sloupců, které jsou přidány do tohoto fondu, Visual Studio přidá výchozí styly sloupců při formulář opravdu zavřít a mřížky jsou vytvořeny v době běhu. Pokud jste vytvořili styl tabulky a do ní přidat všechny styly sloupců, ale Visual Studio nevytvoří všechny styly sloupců. Musíte také definovat styly sloupců a přiřadit jim s názvem mapování mít sloupce, které se zobrazí v mřížce.  
  
 Protože určit sloupce, které jsou zahrnuty v datové mřížce přiřazením styl sloupce a sloupce, které byl přiřazen žádný sloupec styl, můžete zahrnout sloupce dat v datové sadě, která se zobrazí v mřížce. Ale protože datový sloupec, který je zahrnutý v datové sadě, můžete prostřednictvím kódu programu upravovat data, která se nezobrazí.  
  
> [!NOTE]
>  Obecně platí vytvořte styly sloupců a přidat je do kolekce stylů sloupců před přidáním do kolekce stylů tabulek styly tabulky. Když přidáte do kolekce je prázdná tabulka styl, jsou pro vás automaticky generovány styly sloupců. V důsledku toho bude výjimka vyvolána, pokud se pokusíte přidat nové styly sloupců s duplicitními <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> hodnot do kolekce stylů sloupců.  
>   
>  V některých případech budete chtít upravit jen jeden sloupec mezi mnoho sloupců. například datová sada obsahuje 50 sloupců a chcete jenom 49 z nich. V takovém případě je snazší pro import všech 50 sloupců a programově odebrat jedno místo programové přidání všech 49 jednotlivé sloupce chcete.  
  
## <a name="formatting"></a>Formátování  
 Formátování, který lze použít <xref:System.Windows.Forms.DataGrid> ovládací prvek obsahuje styly ohraničení, styly mřížky, písem, Vlastnosti titulku, zarovnání dat a každou druhou barvy pozadí mezi řádky. Další informace najdete v tématu [jak: Formátování ovládacího prvku Windows Forms DataGrid](how-to-format-the-windows-forms-datagrid-control.md).  
  
## <a name="events"></a>Události  
 Kromě běžné řízení událostí <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>, a <xref:System.Windows.Forms.DataGrid.Scroll>, <xref:System.Windows.Forms.DataGrid> ovládací prvek podporuje události související s úpravou a navigace v rámci mřížky. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> Výběru buňky, která určuje vlastnost. <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> Událost se vyvolá, když uživatel přejde na novou buňku. Když uživatel přejde do nové tabulky prostřednictvím nadřazené a podřízené vztahy <xref:System.Windows.Forms.DataGrid.Navigate> událost se vyvolá. <xref:System.Windows.Forms.DataGrid.BackButtonClick> Událost se vyvolá, když uživatel klikne na tlačítko Zpět, když uživatel prohlíží podřízené tabulky a <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> událost je aktivována při kliknutí na ikonu Zobrazení/skrytí nadřazené řádky.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Postupy: Formátování ovládacího prvku Windows Forms DataGrid](how-to-format-the-windows-forms-datagrid-control.md)
