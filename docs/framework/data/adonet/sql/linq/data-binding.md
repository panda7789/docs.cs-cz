---
title: Datová vazba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: 66964497159c5c03a9070090ee60b43fa7d31abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032877"
---
# <a name="data-binding"></a>Datová vazba

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje vytvoření vazby na běžné ovládací prvky, jako je například ovládací prvky mřížky. Konkrétně [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definuje základních sekvencí pro vytvoření vazby na mřížky dat a zpracování vazby hlavní podrobnosti, jak jde o zobrazení a aktualizace.

## <a name="underlying-principle"></a>Základní zásady

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přeloží [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazů jazyka SQL spuštěn na databázi. Výsledky jsou silně typované `IEnumerable`. Protože tyto objekty jsou běžné běžně používané objekty jazyka runtime (CLR), obyčejné objekt datové vazby slouží k zobrazení výsledků. Na druhé straně operace změny (vložení, aktualizace a odstranění) vyžadují další kroky.

## <a name="operation"></a>Operace

Implicitně vazby ovládacích prvků Windows Forms je dosaženo implementací <xref:System.ComponentModel.IListSource>. Obecné zdroje dat <xref:System.Data.Linq.Table%601> (`Table<T>` v C# nebo `Table(Of T)` v jazyce Visual Basic) a obecná `DataQuery` byla aktualizována, aby implementace <xref:System.ComponentModel.IListSource>. Uživatelské rozhraní (UI) datové vazby moduly (Windows Forms a Windows Presentation Foundation) i testování, zda svá data zdroje implementuje <xref:System.ComponentModel.IListSource>. Proto zápis přímého použití dotazu ke zdroji dat ovládacího prvku implicitně volání [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kolekce generace, jako v následujícím příkladu:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Stejné dochází u Windows Presentation Foundation:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Kolekce generace jsou implementovány pomocí obecného <xref:System.Data.Linq.Table%601> a obecná `DataQuery` v <xref:System.ComponentModel.IListSource.GetList%2A>.

## <a name="ilistsource-implementation"></a>Implementace rozhraní IListSource

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje <xref:System.ComponentModel.IListSource> ve dvou umístěních:

- Zdroj dat je <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přejde k vyplnění tabulky `DataBindingList` kolekce, která uchovává odkaz na tabulku.

- Zdroj dat je <xref:System.Linq.IQueryable%601>. Existují dva scénáře:

  - Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] najde základní <xref:System.Data.Linq.Table%601> z <xref:System.Linq.IQueryable%601>edition umožňuje zdroji a situace je stejný jako v prvním odrážce.

  - Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nelze najít základní <xref:System.Data.Linq.Table%601>, zdroj neumožňuje edition (například `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Umožňuje dotazu k vyplnění obecný `SortableBindingList`, což je jednoduchý <xref:System.ComponentModel.BindingList%601> , který implementuje funkci řazení pro T entity pro danou vlastnost.

## <a name="specialized-collections"></a>Specializované kolekce

Pro mnoho funkcí, které jsou popsané dříve v tomto dokumentu <xref:System.ComponentModel.BindingList%601> byla zaměřena na některé jiné třídy. Tyto třídy jsou Obecné `SortableBindingList` a obecná `DataBindingList`. Obě jsou deklarovány jako vnitřní.

### <a name="generic-sortablebindinglist"></a>Obecný SortableBindingList

Tato třída dědí z <xref:System.ComponentModel.BindingList%601>, a je seřaditelné verze <xref:System.ComponentModel.BindingList%601>. Řazení je řešení v paměti a nikdy kontaktuje samotná databáze. <xref:System.ComponentModel.BindingList%601> implementuje <xref:System.ComponentModel.IBindingList> ale nepodporuje řazení ve výchozím nastavení. Ale <xref:System.ComponentModel.BindingList%601> implementuje <xref:System.ComponentModel.IBindingList> s virtuální *core* metody. Snadno můžete přepsat tyto metody. Obecný `SortableBindingList` přepíše <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>, a <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore` je volán <xref:System.ComponentModel.IBindingList.ApplySort%2A> a seřadí seznam položek T pro danou vlastnost.

Je vyvolána výjimka, pokud vlastnost nepatří do T.

K dosažení řazení, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří obecný `SortableBindingList.PropertyComparer` třídu odvozenou od obecného <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> a implementuje výchozí porovnávací metody pro daný typ T, `PropertyDescriptor`a směr. Tato třída dynamicky vytvoří `Comparer` t, kde T je `PropertyType` z `PropertyDescriptor`. Pak je výchozí porovnávací metody načten z statické Obecné `Comparer`. Výchozí instance je získat pomocí reflexe.

Obecný `SortableBindingList` je také základní třídu pro `DataBindingList`. Obecný `SortableBindingList` nabízí dvě virtuální metody pro pozastavení nebo obnovení položek přidat nebo odebrat sledování. Tyto dvě metody slouží pro základní funkce, jako je například řazení, ale bude ve skutečnosti provádí velké třídy typu obecného `DataBindingList`.

### <a name="generic-databindinglist"></a>Obecný DataBindingList

Tato třída dědí z obecného `SortableBindingLIst`. Obecný `DataBindingList` uchovává odkaz na základní obecný `Table` z obecného `IQueryable` použít pro počáteční naplnění kolekce. Obecný `DatabindingList` přidá do kolekce sledování pro položku Přidat nebo odebrat tak, že přepíšete `InsertItem`() a `RemoveItem`(). Také implementuje abstraktní operací pozastavit/pokračovat funkce vytvořit sledování podmíněné sledování. Díky této funkci můžete obecný `DataBindingList` využít výhod polymorfní používání funkce sledování nadřazené třídy.

## <a name="binding-to-entitysets"></a>Vytvoření vazby na objekty EntitySet

Vytvoření vazby na `EntitySet` je zvláštní případ, protože `EntitySet` už je kolekce, která implementuje <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přidá řazení a zrušení (<xref:System.ComponentModel.ICancelAddNew>) podporují. `EntitySet` Třída představují vnitřní seznam používá k uložení entity. Tento seznam je nízké úrovně podle obecného pole, obecné kolekce `ItemList` třídy.

### <a name="adding-a-sorting-feature"></a>Přidání funkce řazení

Pole nabízejí sort – metoda (`Array.Sort()`), který lze použít s `Comparer` z T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá Obecné `SortableBindingList.PropertyComparer` třídy je popsáno výše v tomto tématu můžete získat `Comparer` pro vlastnost a směr, který má být seřazená podle. `ApplySort` Metoda je přidána do obecného `ItemList` k volání této funkce.

Na `EntitySet` straně, teď musíte deklarovat řazení podpory:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> Vrátí `true`.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A> volání `entities.ApplySort()` a potom `OnListChanged()`.

- <xref:System.ComponentModel.IBindingList.SortDirection%2A> a <xref:System.ComponentModel.IBindingList.SortProperty%2A> vlastnosti zpřístupnit aktuální definice řazení, který je uložený v místním členy.

Při použití System.Windows.Forms.BindingSource a vytvořit vazbu element EntitySet\<TEntity > k System.Windows.Forms.BindingSource.DataSource, je třeba volat vlastnost EntitySet\<TEntity >. GetNewBindingList aktualizovat BindingSource.List.

Pokud můžete použít System.Windows.Forms.BindingSource a nastavit vlastnost BindingSource.DataMember a nastavit BindingSource.DataSource na třídu, která má vlastnost s názvem v BindingSource.DataMember, který zpřístupňuje vlastnost EntitySet\<TEntity >, které není nutné volat objekt EntitySet\<TEntity >. GetNewBindingList aktualizovat BindingSource.List ale můžete ztratit možnost řazení.

## <a name="caching"></a>Ukládání do mezipaměti

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provádění dotazů <xref:System.ComponentModel.IListSource.GetList%2A>. Pokud třída Windows Forms BindingSource splňuje toto rozhraní, zavolá GetList() po třech čas pro jedno připojení. Chcete-li této situaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje mezipaměti na jednu instanci k ukládání a vždy vrátí stejné generované kolekce.

## <a name="cancellation"></a>Zrušení

<xref:System.ComponentModel.IBindingList> definuje <xref:System.ComponentModel.IBindingList.AddNew%2A> metodu, která používá ovládací prvky k vytvoření nové položky z vázaného kolekce. `DataGridView` Ovládací prvek zobrazí tato funkce velmi dobře při poslední viditelné řádek obsahuje hvězdičku v jeho záhlaví. Barva hvězdičky se dozvíte, které můžete přidat novou položku.

Kromě této funkce můžete také implementovat kolekce <xref:System.ComponentModel.ICancelAddNew>. Tato funkce umožňuje pro ovládací prvky zrušit nebo ověřit, že nový upravovat položky ověřena nebo ne.

<xref:System.ComponentModel.ICancelAddNew> je implementován ve všech [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kolekce datové vazby (obecný `SortableBindingList` a obecná `EntitySet`). V obou implementacích kód provede následujícím způsobem:

- Umožňuje vložit a potom se odeberou z kolekce položek.

- Nesleduje změny, tak dlouho, dokud rozhraní nesměrují edici.

- Nesleduje změny tak dlouho, dokud se zruší edice (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).

- Umožňuje sledování při vydání se zaměřuje (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Umožňuje kolekci chovat normálně Pokud nová položka nepochází z <xref:System.ComponentModel.IBindingList.AddNew%2A>.

## <a name="troubleshooting"></a>Poradce při potížích

Tato část vám sdělí několik položek, které vám mohou pomoci vyřešit vaše [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] datové vazby aplikace.

- Je nutné použít vlastnosti; použití pouze pole není dostatečná. Formuláře Windows vyžadují toto využití.

- Ve výchozím nastavení `image`, `varbinary`, a `timestamp` databáze typy namapovat na pole bajtů. Protože `ToString()` není podporován v tomto scénáři nelze zobrazit tyto objekty.

- Člen třídy, která je namapována na primární klíč má setter, ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje změnu identity objektu. Primární či jedinečný klíč, který se používá v mapování proto nelze aktualizovat v databázi. Změna v mřížce dojde k výjimce při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

- Pokud entita je hranice ve dvou samostatných mřížky (například jeden hlavní server a další podrobnosti), `Delete` hlavní mřížky se nerozšíří do podrobností mřížky.

## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
