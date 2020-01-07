---
title: Datová vazba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: c7048d292bdf5c1372d5f8f174f7f0e84efa7593
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634713"
---
# <a name="data-binding"></a>Datová vazba

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje vazbu na běžné ovládací prvky, jako jsou například ovládací prvky mřížky. Konkrétně [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definuje základní vzory pro svázání s datovou mřížkou a zpracování vazby s hlavními údaji, s ohledem na zobrazení a aktualizaci.

## <a name="underlying-principle"></a>Základní princip

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá dotazy LINQ na SQL ke spuštění v databázi. Výsledky jsou `IEnumerable`silného typu. Vzhledem k tomu, že tyto objekty jsou běžné objekty modulu CLR (Common Language Runtime), lze použít k zobrazení výsledků standardní datovou vazbu objektu. Na druhé straně operace změny (vložení, aktualizace a odstranění) vyžadují další kroky.

## <a name="operation"></a>Operace

Implicitní vazba na ovládací prvky model Windows Forms je zajištěna implementací <xref:System.ComponentModel.IListSource>. Zdroje dat Obecné <xref:System.Data.Linq.Table%601> (`Table<T>` v C# Visual Basic nebo `Table(Of T)` v) a obecné `DataQuery` byly aktualizovány pro implementaci <xref:System.ComponentModel.IListSource>. Moduly uživatelského rozhraní (UI) datové vazby v modulech (model Windows Forms a Windows Presentation Foundation) testují, zda jejich zdroj dat implementuje <xref:System.ComponentModel.IListSource>. Proto zápis přímého vlivu dotazu na zdroj dat ovládacího prvku implicitně volá [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generaci kolekce, jako v následujícím příkladu:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Totéž dojde u Windows Presentation Foundation:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Generace kolekcí jsou implementovány obecnými <xref:System.Data.Linq.Table%601> a obecnými `DataQuery` v <xref:System.ComponentModel.IListSource.GetList%2A>.

## <a name="ilistsource-implementation"></a>Implementace IListSource

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje <xref:System.ComponentModel.IListSource> ve dvou umístěních:

- Zdroj dat je <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prochází tabulku, aby vyplnila `DataBindingList` kolekci, která uchovává odkaz na tabulku.

- Zdroj dat je <xref:System.Linq.IQueryable%601>. Existují dva scénáře:

  - Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] najde základní <xref:System.Data.Linq.Table%601> z <xref:System.Linq.IQueryable%601>, zdroj umožňuje vydání edice a tato situace je stejná jako v prvním bodu odrážky.

  - Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nenalezne základní <xref:System.Data.Linq.Table%601>, zdroj nepovoluje edici (například `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prochází dotaz, aby vyplnil obecný `SortableBindingList`, což je jednoduchý <xref:System.ComponentModel.BindingList%601>, který implementuje funkci řazení pro entity T pro danou vlastnost.

## <a name="specialized-collections"></a>Specializované kolekce

Pro mnoho funkcí popsaných výše v tomto dokumentu je <xref:System.ComponentModel.BindingList%601> specializované na některé jiné třídy. Tyto třídy jsou obecné `SortableBindingList` a obecné `DataBindingList`. Obě jsou deklarovány jako interní.

### <a name="generic-sortablebindinglist"></a>Obecné SortableBindingList

Tato třída dědí z <xref:System.ComponentModel.BindingList%601>a jedná se o nastejnou verzi <xref:System.ComponentModel.BindingList%601>. Řazení je řešení v paměti, které nikdy nekontaktuje samotnou databázi. <xref:System.ComponentModel.BindingList%601> implementuje <xref:System.ComponentModel.IBindingList>, ale ve výchozím nastavení nepodporuje řazení. <xref:System.ComponentModel.BindingList%601> ale implementuje <xref:System.ComponentModel.IBindingList> s virtuálními *základními* metodami. Tyto metody můžete snadno přepsat. Obecný `SortableBindingList` Přepisuje <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>a <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore` je volána <xref:System.ComponentModel.IBindingList.ApplySort%2A> a seřadí seznam T položek pro danou vlastnost.

Výjimka je vyvolána, pokud vlastnost nepatří T.

Aby bylo možné dosáhnout řazení, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří obecnou `SortableBindingList.PropertyComparer` třídu, která dědí z obecného <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> a implementuje výchozí porovnávací metodu pro daný typ T, `PropertyDescriptor`a směr. Tato třída dynamicky vytvoří `Comparer` T, kde T je `PropertyType` `PropertyDescriptor`. Pak je výchozí porovnávací hodnota načtena ze statického obecného `Comparer`. Výchozí instance je získána pomocí reflexe.

Obecné `SortableBindingList` jsou také základní třídou pro `DataBindingList`. Obecný `SortableBindingList` nabízí dvě virtuální metody pro pozastavení nebo obnovení položek přidat/odebrat sledování. Tyto dvě metody lze použít pro základní funkce, jako je například řazení, ale budou skutečně implementovány pomocí horních tříd, jako je obecná `DataBindingList`.

### <a name="generic-databindinglist"></a>Obecné DataBindingList

Tato třída dědí z obecných `SortableBindingLIst`. Obecný `DataBindingList` udržuje odkaz na základní obecné `Table` obecného `IQueryable` použitou pro počáteční vyplňování kolekce. Obecný `DatabindingList` přidá sledování pro položku Přidat/odebrat do kolekce přepsáním `InsertItem`() a `RemoveItem`(). K zajištění podmíněného sledování implementuje taky abstraktní funkci Pozastavení/obnovení. Tato funkce umožňuje obecným `DataBindingList` využít všech polymorfních funkcí funkce sledování nadřazených tříd.

## <a name="binding-to-entitysets"></a>Vazba na objekty EntitySets

Vazba na `EntitySet` je zvláštní případ, protože `EntitySet` již kolekce implementující <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přidává podporu řazení a rušení (<xref:System.ComponentModel.ICancelAddNew>). Třída `EntitySet` používá interní seznam pro ukládání entit. Tento seznam je kolekce nižší úrovně založená na obecném poli, obecné `ItemList` třídy.

### <a name="adding-a-sorting-feature"></a>Přidání funkce řazení

Pole nabízejí metodu řazení (`Array.Sort()`), kterou lze použít s `Comparer` T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá obecnou `SortableBindingList.PropertyComparer` třídu popsanou dříve v tomto tématu, aby získala tuto `Comparer` pro vlastnost a směr, který má být seřazen. K volání této funkce je přidána metoda `ApplySort` do obecného `ItemList`.

Na straně `EntitySet` nyní musíte deklarovat podporu řazení:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> vrátí `true`.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A> volá `entities.ApplySort()` a pak `OnListChanged()`.

- vlastnosti <xref:System.ComponentModel.IBindingList.SortDirection%2A> a <xref:System.ComponentModel.IBindingList.SortProperty%2A> zpřístupňují aktuální definici řazení, která je uložena v místních členech.

Použijete-li System. Windows. Forms. BindingSource a navážete objekt EntitySet\<TEntity > na System. Windows. Forms. BindingSource. DataSource, je nutné volat EntitySet\<TEntity >. GetNewBindingList k aktualizaci objektu BindingSource. list.

Použijete-li System. Windows. Forms. BindingSource a nastavte vlastnost BindingSource. DataMember a nastavte vlastnost BindingSource. DataSource na třídu, která má vlastnost s názvem v objektu BindingSource. DataMember, která zveřejňuje\<TEntity >, nemusíte volat EntitySet\<TEntity >. GetNewBindingList k aktualizaci objektu BindingSource. list, ale ztratíte možnosti řazení.

## <a name="caching"></a>Ukládání do mezipaměti

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy implementují <xref:System.ComponentModel.IListSource.GetList%2A>. Pokud třída model Windows Forms BindingSource splňuje toto rozhraní, volá GetList () tři časy pro jedno připojení. Pro obejít tuto situaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje mezipaměť na instanci, která se uloží, a vždycky vrátí stejnou vygenerovanou kolekci.

## <a name="cancellation"></a>Zrušení

<xref:System.ComponentModel.IBindingList> definuje metodu <xref:System.ComponentModel.IBindingList.AddNew%2A>, která je používána ovládacími prvky pro vytvoření nové položky z vázané kolekce. Ovládací prvek `DataGridView` zobrazí tuto funkci velmi dobře, když poslední viditelný řádek obsahuje hvězdičku ve své hlavičce. Hvězdička vám ukáže, že můžete přidat novou položku.

Kromě této funkce může kolekce také implementovat <xref:System.ComponentModel.ICancelAddNew>. Tato funkce umožňuje ovládacím prvkům zrušit nebo ověřit, zda byla nová upravená položka ověřena nebo nikoli.

<xref:System.ComponentModel.ICancelAddNew> je implementován ve všech [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ch kolekcích vázaných na datové vazby (Obecné `SortableBindingList` a obecné `EntitySet`). V obou implementacích provede kód následující:

- Umožňuje vkládání položek a jejich odebrání z kolekce.

- Nesleduje změny, dokud uživatelské rozhraní nepotvrdí edici.

- Nesleduje změny, dokud je edice zrušená (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).

- Umožňuje sledování, je-li edice potvrzena (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Umožňuje, aby se kolekce normálně chovala v případě, že nová položka nepochází z <xref:System.ComponentModel.IBindingList.AddNew%2A>.

## <a name="troubleshooting"></a>Odstraňování problémů

V této části se volá několik položek, které vám můžou pomoct při řešení potíží s [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mi aplikacemi datových vazeb.

- Je nutné použít vlastnosti; použití pouze polí není dostačující. Model Windows Forms vyžadují toto použití.

- Ve výchozím nastavení jsou typy databází `image`, `varbinary`a `timestamp` mapovány na pole bajtů. Vzhledem k tomu, že `ToString()` není v tomto scénáři podporován, nelze tyto objekty zobrazit.

- Člen třídy mapovaný k primárnímu klíči má metodu Setter, ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje změnu identity objektu. Proto primární/jedinečný klíč, který se používá v mapování, nelze v databázi aktualizovat. Změna v mřížce způsobí výjimku při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

- Pokud je entita svázaná ve dvou samostatných Gridech (například jeden hlavní a další podrobnosti), `Delete` v hlavní mřížce se nerozšíří do tabulky podrobností.

## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
