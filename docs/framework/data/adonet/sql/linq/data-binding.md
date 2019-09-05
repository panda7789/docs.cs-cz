---
title: Datová vazba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: 79a14e787b4fe1aa1b16ad661b11a43b12bdd718
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247383"
---
# <a name="data-binding"></a>Datová vazba

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje vazbu na běžné ovládací prvky, jako jsou například ovládací prvky mřížky. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Konkrétně definuje základní vzory pro svázání s datovou mřížkou a zpracování vazby s hlavními údaji, a to s ohledem na zobrazení a aktualizaci.

## <a name="underlying-principle"></a>Základní princip

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]přeloží [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy na SQL pro spuštění v databázi. Výsledky jsou silného typu `IEnumerable`. Vzhledem k tomu, že tyto objekty jsou běžné objekty modulu CLR (Common Language Runtime), lze použít k zobrazení výsledků standardní datovou vazbu objektu. Na druhé straně operace změny (vložení, aktualizace a odstranění) vyžadují další kroky.

## <a name="operation"></a>Operace

Implicitní vazba na ovládací prvky model Windows Forms je zajištěna implementací <xref:System.ComponentModel.IListSource>. Zdroje dat Obecné <xref:System.Data.Linq.Table%601> (`Table<T>` v C# nebo `Table(Of T)` v Visual Basic) a obecné `DataQuery` byly aktualizovány pro implementaci <xref:System.ComponentModel.IListSource>. Moduly uživatelského rozhraní (UI) datové vazby (model Windows Forms a Windows Presentation Foundation) otestují, zda jejich implementace <xref:System.ComponentModel.IListSource>jejich zdroje dat. Proto zápis přímého vlivu dotazu na zdroj dat ovládacího prvku implicitně volá [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generování kolekce, jako v následujícím příkladu:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Totéž dojde u Windows Presentation Foundation:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Generace kolekcí jsou implementovány obecnými <xref:System.Data.Linq.Table%601> a obecnými `DataQuery` v <xref:System.ComponentModel.IListSource.GetList%2A>.

## <a name="ilistsource-implementation"></a>Implementace IListSource

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]implementuje <xref:System.ComponentModel.IListSource> se ve dvou umístěních:

- Zdroj dat je <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umožňuje přejít `DataBindingList` do tabulky a vyplnit kolekci, která bude uchovávat odkaz na tabulku.

- Zdroj dat je <xref:System.Linq.IQueryable%601>. Existují dva scénáře:

  - Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] najde základní <xref:System.Data.Linq.Table%601> z rozhraní <xref:System.Linq.IQueryable%601>, zdroj umožňuje vydání edice a tato situace je stejná jako v prvním odrážce.

  - Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nelze najít základní <xref:System.Data.Linq.Table%601>, zdroj nepovoluje `groupby`edici (například). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]projde dotazem, aby vyplnil obecný `SortableBindingList`, což je jednoduché <xref:System.ComponentModel.BindingList%601> , které implementuje funkci řazení pro entity T pro danou vlastnost.

## <a name="specialized-collections"></a>Specializované kolekce

Pro mnoho funkcí popsaných výše v tomto <xref:System.ComponentModel.BindingList%601> dokumentu bylo specializované na některé jiné třídy. Tyto třídy jsou obecné `SortableBindingList` a obecné `DataBindingList`. Obě jsou deklarovány jako interní.

### <a name="generic-sortablebindinglist"></a>Obecné SortableBindingList

Tato třída dědí z <xref:System.ComponentModel.BindingList%601>a je seřaditelné <xref:System.ComponentModel.BindingList%601>verze. Řazení je řešení v paměti, které nikdy nekontaktuje samotnou databázi. <xref:System.ComponentModel.BindingList%601>implementuje <xref:System.ComponentModel.IBindingList> , ale nepodporuje řazení ve výchozím nastavení. <xref:System.ComponentModel.BindingList%601> Nicméně implementuje <xref:System.ComponentModel.IBindingList> s virtuálními *základními* metodami. Tyto metody můžete snadno přepsat. Obecná `SortableBindingList` přepsání <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, a<xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>. <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A> `ApplySortCore`je volána <xref:System.ComponentModel.IBindingList.ApplySort%2A> a seřadí seznam T položek pro danou vlastnost.

Výjimka je vyvolána, pokud vlastnost nepatří T.

Chcete-li dosáhnout [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řazení, vytvoří `SortableBindingList.PropertyComparer` obecnou třídu, která <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> dědí z obecného a implementuje výchozí `PropertyDescriptor`porovnávací metodu pro daný typ T, a a směr. Tato třída dynamicky vytvoří hodnotu `Comparer` t, kde t `PropertyType` je `PropertyDescriptor`. Pak je výchozí porovnávací hodnota načtena ze statického `Comparer`obecného. Výchozí instance je získána pomocí reflexe.

Obecná `SortableBindingList` je také základní třídou pro `DataBindingList`. Obecné `SortableBindingList` nabízí dvě virtuální metody pro pozastavení nebo obnovení položek přidat/odebrat sledování. Tyto dvě metody lze použít pro základní funkce, jako je například řazení, ale budou skutečně implementovány pomocí horních tříd `DataBindingList`, jako je obecná.

### <a name="generic-databindinglist"></a>Obecné DataBindingList

Tato třída dědí z obecného `SortableBindingLIst`. Obecný `DataBindingList` udržuje odkaz na základní obecný `Table` `IQueryable` základ, který se používá pro počáteční vyplňování kolekce. Generic `DatabindingList` přidá sledování pro položku Přidat/odebrat do kolekce přepsáním `InsertItem`() a `RemoveItem`(). K zajištění podmíněného sledování implementuje taky abstraktní funkci Pozastavení/obnovení. Tato funkce umožňuje obecné `DataBindingList` využití všech polymorfních funkcí sledování nadřazených tříd.

## <a name="binding-to-entitysets"></a>Vazba na objekty EntitySets

Vazba na `EntitySet` je zvláštní případ, protože `EntitySet` je již kolekce implementovaná <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Přidá podporu řazení a zrušení (<xref:System.ComponentModel.ICancelAddNew>). `EntitySet` Třída používá interní seznam pro ukládání entit. Tento seznam je kolekce nižší úrovně založená na obecném poli obecné `ItemList` třídy.

### <a name="adding-a-sorting-feature"></a>Přidání funkce řazení

Pole`Array.Sort()`nabízejí metodu řazení (), kterou lze použít `Comparer` s metodou T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá obecnou `SortableBindingList.PropertyComparer` třídu popsanou dříve v tomto tématu k získání této `Comparer` vlastnosti a směru řazení. Metoda je přidána do obecného `ItemList` pro volání této funkce. `ApplySort`

`EntitySet` Na straně sebe teď musíte deklarovat podporu řazení:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A>Vrátí `true`.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A>volání `entities.ApplySort()` a potom `OnListChanged()`.

- <xref:System.ComponentModel.IBindingList.SortDirection%2A>a <xref:System.ComponentModel.IBindingList.SortProperty%2A> vlastnosti zpřístupňují aktuální definici řazení, která je uložena v místních členech.

Použijete-li System. Windows. Forms. BindingSource a navážete\<objekt EntitySet TEntity > na System. Windows. Forms. BindingSource. DataSource, je nutné volat\<EntitySet TEntity >. GetNewBindingList k aktualizaci objektu BindingSource. list.

Použijete-li System. Windows. Forms. BindingSource a nastavte vlastnost BindingSource. DataMember a nastavte vlastnost BindingSource. DataSource na třídu, která má vlastnost s názvem v objektu BindingSource. DataMember, která zpřístupňuje\<> EntitySet TEntity, je nemusíte volat EntitySet\<TEntity >. GetNewBindingList k aktualizaci objektu BindingSource. list, ale ztratíte možnosti řazení.

## <a name="caching"></a>Ukládání do mezipaměti

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dotazy implementují <xref:System.ComponentModel.IListSource.GetList%2A>. Pokud třída model Windows Forms BindingSource splňuje toto rozhraní, volá GetList () tři časy pro jedno připojení. Tuto situaci můžete obejít tak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , že implementuje mezipaměť na instanci, která se uloží, a vždycky vrátí stejnou vygenerovanou kolekci.

## <a name="cancellation"></a>Zrušení

<xref:System.ComponentModel.IBindingList><xref:System.ComponentModel.IBindingList.AddNew%2A> definuje metodu, která je používána ovládacími prvky pro vytvoření nové položky z vázané kolekce. `DataGridView` Ovládací prvek zobrazí tuto funkci velmi dobře, když poslední viditelný řádek obsahuje hvězdičku ve své hlavičce. Hvězdička vám ukáže, že můžete přidat novou položku.

Kromě této funkce může kolekce také implementovat <xref:System.ComponentModel.ICancelAddNew>. Tato funkce umožňuje ovládacím prvkům zrušit nebo ověřit, zda byla nová upravená položka ověřena nebo nikoli.

<xref:System.ComponentModel.ICancelAddNew>je implementováno ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] všech kolekcích vázaných `SortableBindingList` na datové `EntitySet`vazby (Obecné a obecné). V obou implementacích provede kód následující:

- Umožňuje vkládání položek a jejich odebrání z kolekce.

- Nesleduje změny, dokud uživatelské rozhraní nepotvrdí edici.

- Nesleduje změny, dokud je edice zrušená (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).

- Umožňuje sledování, je-li edice potvrzena (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Umožňuje, aby se kolekce normálně chovala v případě, že nová položka <xref:System.ComponentModel.IBindingList.AddNew%2A>nepochází z.

## <a name="troubleshooting"></a>Poradce při potížích

V této části se volá několik položek, které mohou pomoct [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] při odstraňování problémů s vašimi aplikacemi datových vazeb.

- Je nutné použít vlastnosti; použití pouze polí není dostačující. Model Windows Forms vyžadují toto použití.

- Ve výchozím nastavení `image`jsou `varbinary`typy databází mapovány na pole bajtů. `timestamp` Vzhledem `ToString()` k tomu, že není v tomto scénáři podporován, nelze tyto objekty zobrazit.

- Člen třídy mapovaný k primárnímu klíči má metodu Setter, ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje změnu identity objektu. Proto primární/jedinečný klíč, který se používá v mapování, nelze v databázi aktualizovat. Změna v mřížce způsobí při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>výjimku.

- Pokud je entita svázaná ve dvou samostatných Gridech (například jeden hlavní a další podrobnosti), `Delete` v hlavní mřížce se nerozšíří do mřížky podrobností.

## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
