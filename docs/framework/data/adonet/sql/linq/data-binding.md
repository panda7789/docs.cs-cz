---
title: Datová vazba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: 440a7eb5af425a3cea46de142e4a7d41f95559c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="data-binding"></a>Datová vazba
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje vytvoření vazby na běžné ovládací prvky, jako je například ovládací prvky mřížky. Konkrétně [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definuje základních sekvencí pro vytvoření vazby na data mřížky a zpracování vazba seznam podrobnosti, jak s ohledem na zobrazení a aktualizace.  
  
## <a name="underlying-principle"></a>Základní princip  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přeloží [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy jazyka SQL pro spuštění v databázi. Výsledky jsou silného typu `IEnumerable`. Protože tyto objekty jsou běžné běžně používané objekty language runtime (CLR), lze zobrazit výsledky obyčejnou objektu datové vazby. Na druhé straně operace změn (vložení, aktualizace a odstranění) vyžadují další kroky.  
  
## <a name="operation"></a>Operace  
 Implicitně vytvoření vazby na ovládací prvky Windows Forms se dosahuje prostřednictvím implementace <xref:System.ComponentModel.IListSource>. Obecné zdroje dat <xref:System.Data.Linq.Table%601> (`Table<T>` v jazyce C# nebo `Table(Of T)` v jazyce Visual Basic) a obecná `DataQuery` byly aktualizovány k implementaci <xref:System.ComponentModel.IListSource>. Uživatelské rozhraní (UI) datové vazby moduly (Windows Forms a Windows Presentation Foundation) i otestovat, zda jejich datového zdroje implementuje <xref:System.ComponentModel.IListSource>. Proto zápis přímého použití dotazu na zdroj dat ovládacího prvku implicitně volání [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generace kolekce, jako v následujícím příkladu:  
  
 [!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
 [!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]  
  
 Stejné dojde k s Windows Presentation Foundation:  
  
 [!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
 [!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]  
  
 Kolekce generace jsou implementované obecného <xref:System.Data.Linq.Table%601> a obecná `DataQuery` v <xref:System.ComponentModel.IListSource.GetList%2A>.  
  
## <a name="ilistsource-implementation"></a>Implementace IListSource  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje <xref:System.ComponentModel.IListSource> ve dvou umístěních:  
  
-   Zdroj dat <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umožňuje tabulky k vyplnění `DataBindingList` kolekce, která udržuje odkaz na tabulku.  
  
-   Zdroj dat je <xref:System.Linq.IQueryable%601>. Existují dva scénáře:  
  
    -   Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vyhledá základní <xref:System.Data.Linq.Table%601> z <xref:System.Linq.IQueryable%601>, zdroj umožňuje edition a situaci je stejné jako na první odrážku.  
  
    -   Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nelze najít základní <xref:System.Data.Linq.Table%601>, zdroj není povolena pro edici (například `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Umožňuje dotazu k vyplnění obecný `SortableBindingList`, což je jednoduchý <xref:System.ComponentModel.BindingList%601> funkci řazení pro T entity pro danou vlastnost, která implementuje.  
  
## <a name="specialized-collections"></a>Specializované kolekce  
 Pro mnoho funkcí popsaných výše v tomto dokumentu <xref:System.ComponentModel.BindingList%601> specializuje na některé jiné třídy. Tyto třídy jsou Obecné `SortableBindingList` a obecná `DataBindingList`. Obě jsou deklarované jako vnitřní.  
  
### <a name="generic-sortablebindinglist"></a>Obecné SortableBindingList  
 Tato třída dědí z <xref:System.ComponentModel.BindingList%601>, a je řazení verze <xref:System.ComponentModel.BindingList%601>. Řazení je řešení v paměti a nikdy kontaktuje samotná databáze. <xref:System.ComponentModel.BindingList%601> implementuje <xref:System.ComponentModel.IBindingList> ale nepodporuje řazení ve výchozím nastavení. Ale <xref:System.ComponentModel.BindingList%601> implementuje <xref:System.ComponentModel.IBindingList> s virtuální *základní* metody. Snadno můžete přepsat tyto metody. Obecné `SortableBindingList` přepsání <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>, a <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore` je volána metodou <xref:System.ComponentModel.IBindingList.ApplySort%2A> a seřadí seznam položek T pro danou vlastnost.  
  
 Je vyvolána výjimka, pokud vlastnost nepatří do T.  
  
 K dosažení, řazení, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří obecný `SortableBindingList.PropertyComparer` třídu, která dědí z obecného <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> a implementuje výchozí porovnávače pro daný typ T, `PropertyDescriptor`a směr. Tato třída se vytvoří dynamicky `Comparer` t, kde T představuje `PropertyType` z `PropertyDescriptor`. Potom výchozí porovnávače se načítají statické obecná `Comparer`. Výchozí instance se získávají pomocí reflexe.  
  
 Obecné `SortableBindingList` je také základní třídu pro `DataBindingList`. Obecné `SortableBindingList` nabízí dvě metody virtuální pro pozastavení nebo obnovení položky Přidat nebo odebrat sledování. Tyto dvě metody lze použít pro základní funkce jako je například řazení, ale bude skutečně implementovat horní třídy jako obecný `DataBindingList`.  
  
### <a name="generic-databindinglist"></a>Obecné DataBindingList  
 Tato třída dědí od obecného `SortableBindingLIst`. Obecné `DataBindingList` udržuje odkaz na základní Obecné `Table` z obecná `IQueryable` použít pro počáteční naplnění kolekce. Obecné `DatabindingList` sledování pro položku Přidat nebo odebrat přidá do kolekce přepsáním `InsertItem`() a `RemoveItem`(). Implementuje také abstraktní pozastavení nebo obnovení činnosti funkce aby sledování podmíněného sledování. Díky této funkci můžete obecný `DataBindingList` využít výhod všech polymorfní používání funkce sledování nadřazené třídy.  
  
## <a name="binding-to-entitysets"></a>Vytvoření vazby na sady EntitySets  
 Vytvoření vazby na `EntitySet` je zvláštní případ, protože `EntitySet` je již kolekce, která implementuje <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přidá řazení a zrušení (<xref:System.ComponentModel.ICancelAddNew>) podporují. `EntitySet` Třída používá interní seznamu k ukládání entit. Tento seznam je nízké úrovně kolekce založené na obecné pole, Obecné `ItemList` třídy.  
  
### <a name="adding-a-sorting-feature"></a>Přidání funkce řazení  
 Pole nabízejí metoda řazení (`Array.Sort()`), můžete použít s `Comparer` z T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá obecná `SortableBindingList.PropertyComparer` třída popsané dříve v tomto tématu získat tuto `Comparer` pro vlastnost a směr, který se má seřadit na. `ApplySort` Metoda se přidá do obecného `ItemList` k volání této funkce.  
  
 Na `EntitySet` straně, teď musíte deklarovat řazení podpory:  
  
-   <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> Vrátí `true`.  
  
-   <xref:System.ComponentModel.IBindingList.ApplySort%2A> volání `entities.ApplySort()` a potom `OnListChanged()`.  
  
-   <xref:System.ComponentModel.IBindingList.SortDirection%2A> a <xref:System.ComponentModel.IBindingList.SortProperty%2A> vlastnosti vystavit aktuální definice řazení, která je uložena v místních členy.  
  
 Pokud použijete System.Windows.Forms.BindingSource a vytvořit vazbu EntitySet\<TEntity > k System.Windows.Forms.BindingSource.DataSource, je třeba volat EntitySet\<Tentity >. GetNewBindingList aktualizace BindingSource.List.  
  
 Pokud pomocí System.Windows.Forms.BindingSource a nastavte vlastnost BindingSource.DataMember a nastavte BindingSource.DataSource na třídu, která má vlastnost s názvem v BindingSource.DataMember, který zveřejňuje EntitySet\<TEntity >, můžete není nutné volat EntitySet\<Tentity >. GetNewBindingList aktualizovat BindingSource.List ale dojít ke ztrátě schopnosti řazení.  
  
## <a name="caching"></a>Ukládání do mezipaměti  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementovat dotazy <xref:System.ComponentModel.IListSource.GetList%2A>. Pokud třída Windows Forms BindingSource splňuje toto rozhraní, zavolá GetList() po třech čas pro jedno připojení. Chcete-li vyřešit tuto situaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje mezipaměti na jednu instanci k ukládání a vždy vrátí stejné generované kolekce.  
  
## <a name="cancellation"></a>Zrušení  
 <xref:System.ComponentModel.IBindingList> definuje <xref:System.ComponentModel.IBindingList.AddNew%2A> metoda, která se používá k vytvoření nové položky z kolekce vázané ovládací prvky. `DataGridView` Ovládací prvek zobrazí tuto funkci velmi dobře, když hvězdu v hlavičce obsahuje poslední řádek viditelné. Hvězdičkou ukazuje, že můžete přidat novou položku.  
  
 Kromě této funkce můžete taky implementovat kolekci <xref:System.ComponentModel.ICancelAddNew>. Tato funkce umožňuje pro ovládací prvky zrušit nebo ověřit, že nové upravit položku byl ověřen nebo ne.  
  
 <xref:System.ComponentModel.ICancelAddNew> je implementována ve všech [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Vycentrovat kolekcí (Obecné `SortableBindingList` a obecná `EntitySet`). V obou implementacích kód provede následujícím způsobem:  
  
-   Umožňuje vložit položky a pak z kolekce odebrán.  
  
-   Nesleduje změny tak dlouho, dokud rozhraní nesměrují edici.  
  
-   Nesleduje změny tak dlouho, dokud se zruší edice (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).  
  
-   Umožňuje sledování při edice je potvrzená (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).  
  
-   Umožňuje chovat normálně, pokud nová položka nepochází z kolekce <xref:System.ComponentModel.IBindingList.AddNew%2A>.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 V této části volá na několik položek, které mohou být užitečné při řešení potíží s vaší [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] datových vazeb aplikací.  
  
-   Je nutné použít vlastnosti; použití pouze pole není dostatečná. Windows Forms vyžadují toto použití.  
  
-   Ve výchozím nastavení `image`, `varbinary`, a `timestamp` mapování typů databáze do bajtového pole. Protože `ToString()` není podporován v tomto scénáři, nelze zobrazit tyto objekty.  
  
-   Člena třídy namapované na primární klíč má nastavení, ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje změnu identity objektu. Primární nebo jedinečný klíč, který se používá v mapování proto nelze aktualizovat v databázi. Ke změně v mřížce dojde k výjimce při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Pokud je propojena entity ve dvou samostatných mřížky (například jeden z nich a další podrobnosti), `Delete` v mřížce hlavní není rozšíří do mřížky podrobností.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
