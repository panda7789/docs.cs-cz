---
title: DataGrid – přehled ovládacího prvku
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
ms.openlocfilehash: df559926dbc9141276f0a03deb99e340fd7212da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742575"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid – přehled ovládacího prvku (Windows Forms)

> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGrid> zobrazuje data v řadě řádků a sloupců. Nejjednodušší případ je v případě, že je mřížka svázána se zdrojem dat s jedinou tabulkou, která neobsahuje žádné relace. V takovém případě se data zobrazí v jednoduchých řádcích a sloupcích, jako v tabulce. Další informace o vazbě dat na jiné ovládací prvky naleznete v tématu [datové vazby a model Windows Forms](../data-binding-and-windows-forms.md).

Pokud je <xref:System.Windows.Forms.DataGrid> svázán s daty s více souvisejícími tabulkami a pokud je v mřížce povolena navigace, mřížka zobrazí v každém řádku rozevírací seznamy. S rozšířením může uživatel přejít z nadřazené tabulky na podřízenou tabulku. Kliknutím na uzel zobrazíte podřízenou tabulku a kliknutím na tlačítko Zpět zobrazíte původní nadřazenou tabulku. Tímto způsobem Mřížka zobrazuje hierarchické vztahy mezi tabulkami.

Na následujícím snímku obrazovky vidíte datovou tabulku DataGrid vázaná na data s více tabulkami:

![Aplikace WinForms, která zobrazuje objekt DataGrid vázaný na data s více tabulkami.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)

<xref:System.Windows.Forms.DataGrid> může poskytnout uživatelské rozhraní pro datovou sadu, navigaci mezi souvisejícími tabulkami a možnosti formátování a úprav ve formátu.

Zobrazení a manipulace s daty jsou samostatné funkce: ovládací prvek zpracovává uživatelské rozhraní, zatímco aktualizace dat jsou zpracovávány model Windows Forms architektury datových vazeb a .NET Framework zprostředkovateli dat. Proto bude synchronizace více ovládacích prvků vázaných na stejný zdroj dat stále synchronizovaná.

> [!NOTE]
> Pokud jste obeznámeni s ovládacím prvkem DataGrid v Visual Basic 6,0, najdete v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> nějaké významné rozdíly.

Když je mřížka svázaná s <xref:System.Data.DataSet>, sloupce a řádky se automaticky vytvoří, naformátují a vyplní. Další informace najdete v tématu [datové vazby a model Windows Forms](../data-binding-and-windows-forms.md). Po generování ovládacího prvku <xref:System.Windows.Forms.DataGrid> můžete přidávat, odstraňovat, měnit uspořádání a formátovat sloupce a řádky v závislosti na vašich potřebách.

## <a name="binding-data-to-the-control"></a>Vázání dat k ovládacímu prvku

Aby byl ovládací prvek <xref:System.Windows.Forms.DataGrid> fungovat, měl by být svázán se zdrojem dat pomocí <xref:System.Windows.Forms.DataGrid.DataSource%2A> a vlastností <xref:System.Windows.Forms.DataGrid.DataMember%2A> v době návrhu nebo metodou <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> v době běhu. Tato vazba ukazuje <xref:System.Windows.Forms.DataGrid> na instanci objektu zdroje dat, jako je například <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>). Ovládací prvek <xref:System.Windows.Forms.DataGrid> zobrazuje výsledky akcí, které jsou prováděny na datech. Většina akcí specifických pro data se neprovede prostřednictvím <xref:System.Windows.Forms.DataGrid>, ale místo přes zdroj dat.

Pokud jsou data v vázané datové sadě aktualizována prostřednictvím libovolného mechanismu, ovládací prvek <xref:System.Windows.Forms.DataGrid> odráží změny. Pokud má datová mřížka a styly tabulek a sloupců vlastnost `ReadOnly` nastavena na hodnotu `false`, data v datové sadě lze aktualizovat prostřednictvím ovládacího prvku <xref:System.Windows.Forms.DataGrid>.

V <xref:System.Windows.Forms.DataGrid> může v jednom okamžiku zobrazit pouze jednu tabulku. Pokud je mezi tabulkami definován vztah nadřazený-podřízený, může uživatel pohybovat mezi souvisejícími tabulkami a vybrat tabulku, která se má zobrazit v ovládacím prvku <xref:System.Windows.Forms.DataGrid>. Informace o vazbách <xref:System.Windows.Forms.DataGrid> ovládacího prvku na zdroj dat ADO.NET buď v době návrhu nebo v době spuštění, naleznete v tématu [How to: bind the model Windows Forms DataGrid Control to a Source (zdroj dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)).

Platné zdroje dat pro <xref:System.Windows.Forms.DataGrid> zahrnují:

- <xref:System.Data.DataTable> – třída

- <xref:System.Data.DataView> – třída

- <xref:System.Data.DataSet> – třída

- <xref:System.Data.DataViewManager> – třída

Pokud je zdrojem datová sada, může se jednat o objekt ve formuláři nebo o objekt předaný formuláři pomocí webové služby XML. Můžete vytvořit vazby na buď typové, nebo netypové datové sady.

<xref:System.Windows.Forms.DataGrid> ovládací prvek lze také navazovat na další struktury, pokud objekty ve struktuře, například prvky v poli, zveřejňují veřejné vlastnosti. V mřížce se zobrazí všechny veřejné vlastnosti prvků ve struktuře. Například Pokud svážete <xref:System.Windows.Forms.DataGrid> ovládací prvek s polem zákaznických objektů, mřížka zobrazí všechny veřejné vlastnosti těchto zákaznických objektů. V některých případech to znamená, že i když můžete vytvořit vazbu na strukturu, výsledná vázaná struktura nemusí mít konkrétní aplikaci. Můžete například vytvořit propojení s polem celých čísel, ale vzhledem k tomu, že datový typ `Integer` nepodporuje veřejnou vlastnost, mřížka nemůže zobrazit žádná data.

Můžete vytvořit vazby na následující struktury, pokud jejich prvky zveřejňují veřejné vlastnosti:

- Všechny komponenty, které implementují rozhraní <xref:System.Collections.IList>. To zahrnuje pole s jednou dimenzí.

- Všechny komponenty, které implementují rozhraní <xref:System.ComponentModel.IListSource>.

- Všechny komponenty, které implementují rozhraní <xref:System.ComponentModel.IBindingList>.

 Další informace o možných zdrojích dat najdete v tématu [zdroje dat podporované nástrojem model Windows Forms](../data-sources-supported-by-windows-forms.md).

## <a name="grid-display"></a>Zobrazení mřížky

Běžné použití ovládacího prvku <xref:System.Windows.Forms.DataGrid> je zobrazení jedné tabulky dat z datové sady. Ovládací prvek lze však také použít k zobrazení více tabulek, včetně souvisejících tabulek. Zobrazení mřížky se automaticky upraví podle zdroje dat. Následující tabulka ukazuje, co se zobrazí v různých konfiguracích.

|Obsah sady dat|Co se zobrazí|
|--------------------------|-----------------------|
|Jedna tabulka|Tabulka se zobrazí v mřížce.|
|Více tabulek.|Mřížka může zobrazit stromové zobrazení, které mohou uživatelé přejít k umístění tabulky, kterou chtějí zobrazit.|
|Více souvisejících tabulek.|Mřížka může zobrazit stromové zobrazení pro výběr tabulek pomocí, nebo můžete určit, že mřížka zobrazuje nadřazenou tabulku. Záznamy v nadřazené tabulce umožňují uživatelům přejít na související podřízené řádky.|

> [!NOTE]
> Tabulky v datové sadě souvisejí s použitím <xref:System.Data.DataRelation>. Viz také téma [Vytvoření vztahů mezi datovými sadami](/visualstudio/data-tools/relationships-in-datasets).

Když <xref:System.Windows.Forms.DataGrid> ovládací prvek zobrazuje tabulku a vlastnost <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> je nastavená na `true`, mohou být data na základě kliknutí na záhlaví sloupců. Uživatel může také přidávat řádky a upravovat buňky.

Vztahy mezi sadou tabulek se uživatelům zobrazí pomocí nadřazené/podřízené struktury navigace. Nadřazené tabulky představují nejvyšší úroveň dat a podřízené tabulky jsou tabulky dat, které jsou odvozeny z jednotlivých výpisů v nadřazených tabulkách. Rozšířené objekty se zobrazí v každém nadřazeném řádku, který obsahuje podřízenou tabulku. Kliknutím na rozšíření se vygeneruje seznam odkazů na webové odkazy na podřízené tabulky. Když uživatel vybere odkaz, zobrazí se podřízená tabulka. Kliknutím na ikonu Zobrazit/skrýt nadřazené řádky (![Ikona zobrazení nebo skrytí nadřazených řádků](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) skryje informace o nadřazené tabulce nebo způsobí, že se bude znovu zobrazovat, pokud ho uživatel dříve skryl. Uživatel může kliknout na tlačítko zpět a přejít zpět k dříve zobrazené tabulce.

## <a name="columns-and-rows"></a>Sloupce a řádky

<xref:System.Windows.Forms.DataGrid> se skládá z kolekce objektů <xref:System.Windows.Forms.DataGridTableStyle>, které jsou obsaženy ve vlastnosti <xref:System.Windows.Forms.DataGrid.TableStyles%2A> ovládacího prvku <xref:System.Windows.Forms.DataGrid>. Styl tabulky může obsahovat kolekci <xref:System.Windows.Forms.DataGridColumnStyle> objektů, které jsou obsaženy ve vlastnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> <xref:System.Windows.Forms.DataGridTableStyle>.. Vlastnosti <xref:System.Windows.Forms.DataGrid.TableStyles%2A> a <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> můžete upravit pomocí editorů kolekcí, ke kterým jste přistupovali prostřednictvím okna **vlastnosti** .

K jakémukoli <xref:System.Windows.Forms.DataGridTableStyle> přidruženému k ovládacímu prvku <xref:System.Windows.Forms.DataGrid> je možné přistupovat prostřednictvím <xref:System.Windows.Forms.GridTableStylesCollection>. <xref:System.Windows.Forms.GridTableStylesCollection> lze upravit v Návrháři pomocí editoru kolekce <xref:System.Windows.Forms.DataGridTableStyle> nebo programově prostřednictvím vlastnosti <xref:System.Windows.Forms.DataGrid.TableStyles%2A> ovládacího prvku <xref:System.Windows.Forms.DataGrid>.

Následující ilustrace znázorňuje objekty zahrnuté v ovládacím prvku DataGrid:

![Diagram, který zobrazuje objekty obsažené v ovládacím prvku DataGrid](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)

Styly tabulky a styly sloupců jsou synchronizovány s <xref:System.Data.DataTable> objekty a objekty <xref:System.Data.DataColumn> nastavením jejich vlastností `MappingName` na příslušné <xref:System.Data.DataTable.TableName%2A> a <xref:System.Data.DataColumn.ColumnName%2A> vlastnosti. Pokud se do ovládacího prvku <xref:System.Windows.Forms.DataGrid> vázaného na platný zdroj dat nepřidá <xref:System.Windows.Forms.DataGridTableStyle>, který nemá žádné styly sloupců, a vlastnost <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> tohoto stylu tabulky je nastavená na platnou vlastnost <xref:System.Data.DataTable.TableName%2A>, vytvoří se pro tento styl tabulky kolekce <xref:System.Windows.Forms.DataGridColumnStyle> objektů. Pro každý <xref:System.Data.DataColumn> nalezené v kolekci <xref:System.Data.DataTable.Columns%2A> <xref:System.Data.DataTable>se do <xref:System.Windows.Forms.GridColumnStylesCollection>přidá odpovídající <xref:System.Windows.Forms.DataGridColumnStyle>. k <xref:System.Windows.Forms.GridColumnStylesCollection> je k dispozici prostřednictvím vlastnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> <xref:System.Windows.Forms.DataGridTableStyle>. Sloupce lze přidat nebo odstranit z mřížky pomocí metody <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> nebo <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> na <xref:System.Windows.Forms.GridColumnStylesCollection>. Další informace najdete v tématu [Postup: Přidání tabulek a sloupců do ovládacího prvku model Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) a [Postup: odstranění nebo skrytí sloupců v ovládacím prvku model Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).

Kolekce typů sloupců rozšiřuje třídu <xref:System.Windows.Forms.DataGridColumnStyle> o možnosti formátování a úprav formátovaného textu. Všechny typy sloupců dědí z <xref:System.Windows.Forms.DataGridColumnStyle> základní třídy. Vytvořená třída závisí na vlastnosti <xref:System.Data.DataColumn.DataType%2A> <xref:System.Data.DataColumn>, ze které je <xref:System.Web.UI.WebControls.DataGridColumn> založena. Například <xref:System.Data.DataColumn>, která má vlastnost <xref:System.Data.DataColumn.DataType%2A> nastavenou na <xref:System.Boolean>, bude přidružena k <xref:System.Windows.Forms.DataGridBoolColumn>. Následující tabulka popisuje každý z těchto typů sloupců.

|Typ sloupce|Popis|
|-----------------|-----------------|
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Přijímá a zobrazuje data jako formátované nebo neformátované řetězce. Možnosti úprav jsou stejné jako pro úpravu dat v jednoduchém <xref:System.Windows.Forms.TextBox>. Dědí z <xref:System.Windows.Forms.DataGridColumnStyle>.|
|<xref:System.Windows.Forms.DataGridBoolColumn>|Přijímá a zobrazuje `true`, `false`a hodnoty null. Dědí z <xref:System.Windows.Forms.DataGridColumnStyle>.|

Dvojím kliknutím na pravý okraj sloupce se změní velikost sloupce a zobrazí se jeho úplný popisek a nejširší položka.

## <a name="table-styles-and-column-styles"></a>Styly tabulky a styly sloupců

Jakmile zadáte výchozí formát <xref:System.Windows.Forms.DataGrid> ovládacího prvku, můžete přizpůsobit barvy, které budou použity při zobrazení určitých tabulek v datové mřížce.

Toho je dosaženo vytvořením instancí třídy <xref:System.Windows.Forms.DataGridTableStyle>. Styly tabulky určují formátování konkrétních tabulek, které se liší od výchozího formátování samotného ovládacího prvku <xref:System.Windows.Forms.DataGrid>. Každá tabulka může mít pro tento čas definován pouze jeden styl tabulky.

V některých případech budete chtít, aby určitý sloupec vypadal jinak než ostatní sloupce konkrétní tabulky dat. Můžete vytvořit přizpůsobenou sadu stylů sloupců pomocí vlastnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>.

Styly sloupců se vztahují ke sloupcům v datové sadě stejně jako styly tabulek souvisejí s tabulkami dat. Stejně jako každá tabulka může mít definován pouze jeden styl tabulky v daném čase, takže pro každý sloupec je také pro každý sloupec definován pouze jeden styl sloupce, v konkrétním stylu tabulky. Tento vztah je definován ve vlastnosti <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> sloupce.

Pokud jste vytvořili styl tabulky bez přidaných stylů sloupců, Visual Studio přidá výchozí styly sloupců při vytvoření formuláře a mřížky v době běhu. Pokud jste však vytvořili styl tabulky a přidali do něj všechny styly sloupců, Visual Studio nevytvoří žádné styly sloupců. Také budete muset definovat styly sloupců a přiřadit jim název mapování, aby se v mřížce zobrazily požadované sloupce.

Vzhledem k tomu, že určíte, které sloupce jsou zahrnuty v datové mřížce tím, že jim přiřadíte styl sloupce a ke sloupcům není přiřazen žádný styl sloupce, můžete do datové sady zahrnout sloupce dat, které nejsou v mřížce zobrazeny. Protože datový sloupec je ale součástí datové sady, můžete programově upravovat data, která nejsou zobrazená.

> [!NOTE]
> Obecně lze vytvořit styly sloupců a přidat je do kolekce stylů sloupců před přidáním stylů tabulky do kolekce stylů tabulek. Když do kolekce přidáte prázdný styl tabulky, automaticky se vygenerují styly sloupců. V důsledku toho bude vyvolána výjimka, pokud se pokusíte přidat nové styly sloupců s duplicitními <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> hodnotami do kolekce stylů sloupců.
>
> V některých případech budete chtít pouze selepšit jeden sloupec mezi mnoho sloupců. například datová sada obsahuje sloupce 50 a vy chcete pouze 49 z nich. V takovém případě je snazší importovat všechny sloupce 50 a programově je odebrat, nikoli programově přidávat každý ze 49 jednotlivých sloupců, které chcete.

## <a name="formatting"></a>Formátování

Formátování, které lze použít pro ovládací prvek <xref:System.Windows.Forms.DataGrid>, zahrnuje styly ohraničení, styly čar mřížky, písma, vlastnosti titulků, zarovnání dat a střídající se barvy pozadí mezi řádky. Další informace najdete v tématu [Postup: formátování model Windows Forms ovládacího prvku DataGrid](how-to-format-the-windows-forms-datagrid-control.md).

## <a name="events"></a>Události

Kromě běžných událostí ovládacích prvků, jako jsou <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>a <xref:System.Windows.Forms.DataGrid.Scroll>, ovládací prvek <xref:System.Windows.Forms.DataGrid> podporuje události spojené s úpravami a navigací v mřížce. Vlastnost <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> určuje, která buňka je vybrána. Událost <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> se vyvolá, když uživatel přejde na novou buňku. Když uživatel přejde na novou tabulku prostřednictvím vztahů nadřazených a podřízených, vyvolá se událost <xref:System.Windows.Forms.DataGrid.Navigate>. Událost <xref:System.Windows.Forms.DataGrid.BackButtonClick> je vyvolána, když uživatel klikne na tlačítko zpět, když uživatel zobrazuje podřízenou tabulku a událost <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> je vyvolána při kliknutí na ikonu Zobrazit/skrýt nadřazené řádky.

## <a name="see-also"></a>Viz také:

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Postupy: Formátování ovládacího prvku Windows Forms DataGrid](how-to-format-the-windows-forms-datagrid-control.md)
