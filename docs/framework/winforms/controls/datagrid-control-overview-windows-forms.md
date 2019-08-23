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
ms.openlocfilehash: 7c67ed499d96ced9bcd9537bd83d6f60037ec27e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969191"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Ovládací prvek <xref:System.Windows.Forms.DataGrid> model Windows Forms zobrazuje data v řadě řádků a sloupců. Nejjednodušší případ je v případě, že je mřížka svázána se zdrojem dat s jedinou tabulkou, která neobsahuje žádné relace. V takovém případě se data zobrazí v jednoduchých řádcích a sloupcích, jako v tabulce. Další informace o vazbě dat na jiné ovládací prvky naleznete v tématu [datové vazby a model Windows Forms](../data-binding-and-windows-forms.md).  
  
 <xref:System.Windows.Forms.DataGrid> Pokud je vazba na data s více souvisejícími tabulkami a v mřížce je povolena navigace, mřížka zobrazí v každém řádku rozevírací seznamy. S rozšířením může uživatel přejít z nadřazené tabulky na podřízenou tabulku. Kliknutím na uzel zobrazíte podřízenou tabulku a kliknutím na tlačítko Zpět zobrazíte původní nadřazenou tabulku. Tímto způsobem Mřížka zobrazuje hierarchické vztahy mezi tabulkami.  
  
 Na následujícím snímku obrazovky vidíte datovou tabulku DataGrid vázaná na data s více tabulkami:  
  
 ![Aplikace WinForms, která zobrazuje objekt DataGrid vázaný na data s více tabulkami.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)  
  
 <xref:System.Windows.Forms.DataGrid> Může poskytovat uživatelské rozhraní pro datovou sadu, navigaci mezi souvisejícími tabulkami a možnosti formátovaného a editačního formátu.  
  
 Zobrazení a manipulace s daty jsou samostatné funkce: Ovládací prvek zpracovává uživatelské rozhraní, zatímco aktualizace dat jsou zpracovávány model Windows Forms architektury datových vazeb a .NET Framework zprostředkovateli dat. Proto bude synchronizace více ovládacích prvků vázaných na stejný zdroj dat stále synchronizovaná.  
  
> [!NOTE]
> Pokud jste obeznámeni s ovládacím prvkem DataGrid v Visual Basic 6,0, v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> se nacházejí nějaké významné rozdíly.  
  
 Když je mřížka svázána <xref:System.Data.DataSet>s, sloupce a řádky se automaticky vytvoří, naformátují a vyplní. Další informace najdete v tématu [datové vazby a model Windows Forms](../data-binding-and-windows-forms.md). Po generování <xref:System.Windows.Forms.DataGrid> ovládacího prvku můžete přidat, odstranit, změnit uspořádání a formátovat sloupce a řádky v závislosti na vašich potřebách.  
  
## <a name="binding-data-to-the-control"></a>Vázání dat k ovládacímu prvku  
 Aby ovládací prvek fungoval, měl by být svázán se zdrojem dat <xref:System.Windows.Forms.DataGrid.DataSource%2A> pomocí vlastností a <xref:System.Windows.Forms.DataGrid.DataMember%2A> v době návrhu nebo <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodou v době běhu. <xref:System.Windows.Forms.DataGrid> Tato vazba odkazuje <xref:System.Windows.Forms.DataGrid> na objekt zdroje dat s vytvořenými instancemi, jako je <xref:System.Data.DataSet> například nebo <xref:System.Data.DataTable>). <xref:System.Windows.Forms.DataGrid> Ovládací prvek zobrazuje výsledky akcí, které jsou prováděny na datech. Většina akcí specifických pro data se neprovede prostřednictvím <xref:System.Windows.Forms.DataGrid> , ale místo přes zdroj dat.  
  
 Pokud jsou data v vázané datové sadě aktualizována prostřednictvím libovolného mechanismu, <xref:System.Windows.Forms.DataGrid> ovládací prvek tyto změny odráží. Pokud má datová mřížka a styly tabulek a sloupců `ReadOnly` vlastnost nastavenou na `false`hodnotu, data v datové sadě <xref:System.Windows.Forms.DataGrid> lze aktualizovat prostřednictvím ovládacího prvku.  
  
 V <xref:System.Windows.Forms.DataGrid> jednom okamžiku může být zobrazena pouze jedna tabulka. Pokud je mezi tabulkami definován vztah nadřazený-podřízený, může uživatel pohybovat mezi souvisejícími tabulkami a vybrat tabulku, která se má zobrazit v <xref:System.Windows.Forms.DataGrid> ovládacím prvku. Informace o vázání <xref:System.Windows.Forms.DataGrid> ovládacího prvku na ADO.NET zdroj dat buď v době návrhu, nebo v době spuštění naleznete v [tématu How to: Navažte model Windows Forms ovládací prvek DataGrid na zdroj](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)dat.  
  
 Platné zdroje dat pro <xref:System.Windows.Forms.DataGrid> zahrnutí:  
  
- <xref:System.Data.DataTable>Deník  
  
- <xref:System.Data.DataView>Deník  
  
- <xref:System.Data.DataSet>Deník  
  
- <xref:System.Data.DataViewManager>Deník  
  
 Pokud je zdrojem datová sada, může se jednat o objekt ve formuláři nebo o objekt předaný formuláři pomocí webové služby XML. Můžete vytvořit vazby na buď typové, nebo netypové datové sady.  
  
 <xref:System.Windows.Forms.DataGrid> Ovládací prvek lze také navazovat na další struktury, pokud objekty ve struktuře, například prvky v poli, zveřejňujete veřejné vlastnosti. V mřížce se zobrazí všechny veřejné vlastnosti prvků ve struktuře. Pokud například svážete <xref:System.Windows.Forms.DataGrid> ovládací prvek s polem zákaznických objektů, mřížka zobrazí všechny veřejné vlastnosti těchto zákaznických objektů. V některých případech to znamená, že i když můžete vytvořit vazbu na strukturu, výsledná vázaná struktura nemusí mít konkrétní aplikaci. Můžete například vytvořit propojení s polem celých čísel, ale vzhledem k tomu `Integer` , že datový typ nepodporuje veřejnou vlastnost, mřížka nemůže zobrazit žádná data.  
  
 Můžete vytvořit vazby na následující struktury, pokud jejich prvky zveřejňují veřejné vlastnosti:  
  
- Všechny komponenty, které implementují <xref:System.Collections.IList> rozhraní. To zahrnuje pole s jednou dimenzí.  
  
- Všechny komponenty, které implementují <xref:System.ComponentModel.IListSource> rozhraní.  
  
- Všechny komponenty, které implementují <xref:System.ComponentModel.IBindingList> rozhraní.  
  
 Další informace o možných zdrojích dat najdete v tématu [zdroje dat podporované nástrojem model Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
## <a name="grid-display"></a>Zobrazení mřížky  
 Běžné použití <xref:System.Windows.Forms.DataGrid> ovládacího prvku je zobrazení jedné tabulky dat z datové sady. Ovládací prvek lze však také použít k zobrazení více tabulek, včetně souvisejících tabulek. Zobrazení mřížky se automaticky upraví podle zdroje dat. Následující tabulka ukazuje, co se zobrazí v různých konfiguracích.  
  
|Obsah sady dat|Co se zobrazí|  
|--------------------------|-----------------------|  
|Jedna tabulka|Tabulka se zobrazí v mřížce.|  
|Více tabulek.|Mřížka může zobrazit stromové zobrazení, které mohou uživatelé přejít k umístění tabulky, kterou chtějí zobrazit.|  
|Více souvisejících tabulek.|Mřížka může zobrazit stromové zobrazení pro výběr tabulek pomocí, nebo můžete určit, že mřížka zobrazuje nadřazenou tabulku. Záznamy v nadřazené tabulce umožňují uživatelům přejít na související podřízené řádky.|  
  
> [!NOTE]
> Tabulky v datové sadě souvisejí s použitím <xref:System.Data.DataRelation>. Viz také téma [Vytvoření vztahů mezi datovými sadami](/visualstudio/data-tools/relationships-in-datasets).
  
 Když ovládací prvek zobrazuje tabulku <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> a vlastnost je nastavena na `true`hodnotu, mohou být data vytvořena kliknutím na záhlaví sloupců. <xref:System.Windows.Forms.DataGrid> Uživatel může také přidávat řádky a upravovat buňky.  
  
 Vztahy mezi sadou tabulek se uživatelům zobrazí pomocí nadřazené/podřízené struktury navigace. Nadřazené tabulky představují nejvyšší úroveň dat a podřízené tabulky jsou tabulky dat, které jsou odvozeny z jednotlivých výpisů v nadřazených tabulkách. Rozšířené objekty se zobrazí v každém nadřazeném řádku, který obsahuje podřízenou tabulku. Kliknutím na rozšíření se vygeneruje seznam odkazů na webové odkazy na podřízené tabulky. Když uživatel vybere odkaz, zobrazí se podřízená tabulka. Kliknutím na ikonu Zobrazit/skrýt nadřazené řádky (![Ikona zobrazení nebo skrytí nadřazených řádků](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) skryje informace o nadřazené tabulce nebo způsobí, že se bude znovu zobrazovat, pokud ho uživatel dříve skryl. Uživatel může kliknout na tlačítko zpět a přejít zpět k dříve zobrazené tabulce.  
  
## <a name="columns-and-rows"></a>Sloupce a řádky  
 Obsahuje kolekci objektů, které jsou<xref:System.Windows.Forms.DataGrid.TableStyles%2A> obsaženy v vlastnosti ovládacíhoprvku.<xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridTableStyle> <xref:System.Windows.Forms.DataGrid> Styl tabulky může obsahovat kolekci <xref:System.Windows.Forms.DataGridColumnStyle> objektů, které jsou obsaženy <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> ve vlastnosti objektu <xref:System.Windows.Forms.DataGridTableStyle>.. Můžete upravit <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnosti a <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> pomocí editorů kolekce, které jsou k dispozici prostřednictvím okna **vlastnosti** .  
  
 Všechny <xref:System.Windows.Forms.DataGridTableStyle> <xref:System.Windows.Forms.GridTableStylesCollection>přidružené <xref:System.Windows.Forms.DataGrid> k ovládacímu prvku jsou k dispozici prostřednictvím. Lze upravit v Návrháři <xref:System.Windows.Forms.DataGridTableStyle> pomocí editoru kolekce nebo <xref:System.Windows.Forms.DataGrid.TableStyles%2A> programově prostřednictvím <xref:System.Windows.Forms.DataGrid> vlastnosti ovládacího prvku. <xref:System.Windows.Forms.GridTableStylesCollection>  

 Následující ilustrace znázorňuje objekty zahrnuté v ovládacím prvku DataGrid:

 ![Diagram, který zobrazuje objekty obsažené v ovládacím prvku DataGrid](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)  
  
 Styly tabulky a styly sloupců jsou synchronizovány <xref:System.Data.DataTable> s objekty <xref:System.Data.DataColumn> a objekty nastavením jejich `MappingName` vlastností na příslušné <xref:System.Data.DataTable.TableName%2A> vlastnosti a <xref:System.Data.DataColumn.ColumnName%2A> . <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> <xref:System.Data.DataTable.TableName%2A> Když se do ovládacího prvku vázaného na platný zdroj dat přidají žádné styly sloupců a vlastnost tohoto stylu tabulky je nastavená <xref:System.Windows.Forms.DataGridColumnStyle> na platnou vlastnost, vytvoří se pro ni kolekce objektů. <xref:System.Windows.Forms.DataGridTableStyle> styl tabulky Pro každou <xref:System.Data.DataColumn> nalezenou <xref:System.Data.DataTable.Columns%2A> kolekci <xref:System.Data.DataTable>v je do přidat <xref:System.Windows.Forms.GridColumnStylesCollection>odpovídající <xref:System.Windows.Forms.DataGridColumnStyle> . <xref:System.Windows.Forms.GridColumnStylesCollection>je k dispozici <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> prostřednictvím vlastnosti. <xref:System.Windows.Forms.DataGridTableStyle> Sloupce lze přidat nebo odstranit z mřížky pomocí <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> metody nebo <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> v <xref:System.Windows.Forms.GridColumnStylesCollection>. Další informace najdete v tématu [jak: Přidejte tabulky a sloupce do model Windows Forms ovládacího prvku](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) DataGrid a [postup: Odstraní nebo skryje sloupce v ovládacím prvku](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)DataGrid model Windows Forms.  
  
 Kolekce typů sloupců rozšiřuje <xref:System.Windows.Forms.DataGridColumnStyle> třídu o možnosti formátování a úprav formátovaného textu. Všechny typy sloupců dědí ze <xref:System.Windows.Forms.DataGridColumnStyle> základní třídy. Vytvořená třída závisí na <xref:System.Data.DataColumn.DataType%2A> vlastnosti <xref:System.Data.DataColumn> třídy, ze které <xref:System.Web.UI.WebControls.DataGridColumn> je založena. Například <xref:System.Data.DataColumn> , který <xref:System.Data.DataColumn.DataType%2A> má vlastnost nastavenou na <xref:System.Boolean> , bude přidružen <xref:System.Windows.Forms.DataGridBoolColumn>k. Následující tabulka popisuje každý z těchto typů sloupců.  
  
|Typ sloupce|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Přijímá a zobrazuje data jako formátované nebo neformátované řetězce. Možnosti úprav jsou stejné jako při jednoduché <xref:System.Windows.Forms.TextBox>úpravě dat. Dědí z <xref:System.Windows.Forms.DataGridColumnStyle>.|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|Přijímá a zobrazuje `true` `false`hodnoty null. Dědí z <xref:System.Windows.Forms.DataGridColumnStyle>.|  
  
 Dvojím kliknutím na pravý okraj sloupce se změní velikost sloupce a zobrazí se jeho úplný popisek a nejširší položka.  
  
## <a name="table-styles-and-column-styles"></a>Styly tabulky a styly sloupců  
 Jakmile zadáte výchozí formát <xref:System.Windows.Forms.DataGrid> ovládacího prvku, můžete přizpůsobit barvy, které budou použity při zobrazení určitých tabulek v datové mřížce.  
  
 Toho je dosaženo vytvořením instancí <xref:System.Windows.Forms.DataGridTableStyle> třídy. Styly tabulky určují formátování konkrétních tabulek, které se liší od výchozího formátování <xref:System.Windows.Forms.DataGrid> samotného ovládacího prvku. Každá tabulka může mít pro tento čas definován pouze jeden styl tabulky.  
  
 V některých případech budete chtít, aby určitý sloupec vypadal jinak než ostatní sloupce konkrétní tabulky dat. Můžete vytvořit přizpůsobenou sadu stylů sloupců pomocí <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnosti.  
  
 Styly sloupců se vztahují ke sloupcům v datové sadě stejně jako styly tabulek souvisejí s tabulkami dat. Stejně jako každá tabulka může mít definován pouze jeden styl tabulky v daném čase, takže pro každý sloupec je také pro každý sloupec definován pouze jeden styl sloupce, v konkrétním stylu tabulky. Tento vztah je definován ve <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> vlastnosti sloupce.  
  
 Pokud jste vytvořili styl tabulky bez přidaných stylů sloupců, Visual Studio přidá výchozí styly sloupců při vytvoření formuláře a mřížky v době běhu. Pokud jste však vytvořili styl tabulky a přidali do něj všechny styly sloupců, Visual Studio nevytvoří žádné styly sloupců. Také budete muset definovat styly sloupců a přiřadit jim název mapování, aby se v mřížce zobrazily požadované sloupce.  
  
 Vzhledem k tomu, že určíte, které sloupce jsou zahrnuty v datové mřížce tím, že jim přiřadíte styl sloupce a ke sloupcům není přiřazen žádný styl sloupce, můžete do datové sady zahrnout sloupce dat, které nejsou v mřížce zobrazeny. Protože datový sloupec je ale součástí datové sady, můžete programově upravovat data, která nejsou zobrazená.  
  
> [!NOTE]
> Obecně lze vytvořit styly sloupců a přidat je do kolekce stylů sloupců před přidáním stylů tabulky do kolekce stylů tabulek. Když do kolekce přidáte prázdný styl tabulky, automaticky se vygenerují styly sloupců. V důsledku toho bude vyvolána výjimka, pokud se pokusíte přidat nové styly sloupců s duplicitními <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> hodnotami do kolekce stylů sloupců.  
>   
>  V některých případech budete chtít pouze selepšit jeden sloupec mezi mnoho sloupců. například datová sada obsahuje sloupce 50 a vy chcete pouze 49 z nich. V takovém případě je snazší importovat všechny sloupce 50 a programově je odebrat, nikoli programově přidávat každý ze 49 jednotlivých sloupců, které chcete.  
  
## <a name="formatting"></a>Formátování  
 Formátování, které lze použít pro <xref:System.Windows.Forms.DataGrid> ovládací prvek, zahrnuje styly ohraničení, styly čar mřížky, písma, vlastnosti titulků, zarovnání dat a střídavé barvy pozadí mezi řádky. Další informace najdete v tématu [jak: Naformátujte model Windows Forms ovládací](how-to-format-the-windows-forms-datagrid-control.md)prvek DataGrid.  
  
## <a name="events"></a>Události  
 Kromě <xref:System.Windows.Forms.Control.MouseDown>běžných událostí ovládacích prvků, jako jsou <xref:System.Windows.Forms.Control.Enter>, a <xref:System.Windows.Forms.DataGrid.Scroll>, <xref:System.Windows.Forms.DataGrid> ovládací prvek podporuje události spojené s úpravami a navigací v mřížce. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> Vlastnost určuje, která buňka je vybrána. <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> Událost se vyvolá, když uživatel přejde na novou buňku. Když uživatel přejde na novou tabulku prostřednictvím vztahů nadřazených a podřízených, <xref:System.Windows.Forms.DataGrid.Navigate> vyvolá se událost. Událost se vyvolá, když uživatel klikne na tlačítko zpět, když uživatel zobrazuje podřízenou tabulku <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> a událost se vyvolá při kliknutí na ikonu Zobrazit/skrýt nadřazené řádky. <xref:System.Windows.Forms.DataGrid.BackButtonClick>  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Postupy: Navázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Postupy: Přidání tabulek a sloupců do model Windows Forms ovládacího prvku DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Postupy: Odstranění nebo skrytí sloupců v model Windows Forms ovládacím prvku DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Postupy: Formátování model Windows Forms ovládacího prvku DataGrid](how-to-format-the-windows-forms-datagrid-control.md)
