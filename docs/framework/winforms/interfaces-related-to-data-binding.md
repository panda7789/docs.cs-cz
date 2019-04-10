---
title: Rozhraní související s datovou vazbou
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], data-binding interfaces
- INotifyPropertyChanged interface
- IBindingListView interface
- IList interface [Windows Forms], Windows Forms data binding
- IBindingList interface [Windows Forms], Windows Forms data binding
- interfaces [Windows Forms], Windows Forms data binding
- IEditableObject interface [Windows Forms], Windows Forms data binding
- data binding [Windows Forms], interfaces
- IDataErrorInfo interface [Windows Forms], Windows Forms data binding
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
ms.openlocfilehash: ffda85b2704212ea5323117447e0cfe17ffb33db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226954"
---
# <a name="interfaces-related-to-data-binding"></a>Rozhraní související s datovou vazbou
S [!INCLUDE[vstecado](../../../includes/vstecado-md.md)], můžete vytvořit mnoha různými datovými strukturami vazby potřebám vaší aplikace a data, že pracujete s. Můžete chtít vytvořit vlastní třídy, které poskytují nebo využívají data v modelu Windows Forms. Tyto objekty lze nabízejí různé úrovně funkčnosti a složitosti, na základní datové vazby k poskytování podpory během návrhu, kontroly chyb, oznámení o změně nebo dokonce i podporu pro strukturované vrátit zpět změny provedené na vlastní data.  
  
## <a name="consumers-of-data-binding-interfaces"></a>Příjemci rozhraní datové vazby  
 Následující části popisují dvě skupiny objektů, rozhraní. První skupina seznam rozhraní, které jsou implementované u zdrojů dat autory zdroje dat. Tato rozhraní jsou navržené tak být využívány službou spotřebitelé zdroje dat, které jsou ve většině případů, které ovládací prvky Windows Forms nebo komponenty. Druhé skupině obsahuje seznam rozhraní, které jsou určeny k použití autoři komponenty. Autoři komponenty použití těchto rozhraní při vytváření komponenty, která podporuje datovou vazbu pro modul datové vazby Windows Forms. Můžete implementovat tyto rozhraní v rámci třídy související s formuláři a povolují datové vazby; každý případ představuje třídu, která implementuje rozhraní, které umožňuje interakci s daty. Visual Studio rychlé (RAD) data návrhové prostředí nástroje pro vývoj aplikací už využít výhod této funkce.  
  
### <a name="interfaces-for-implementation-by-data-source-authors"></a>Rozhraní pro implementaci autory zdroje dat  
 Následující rozhraní jsou navrženy pro ovládací prvky Windows Forms využívat:  
  
-   <xref:System.Collections.IList> rozhraní  
  
     Třídu, která implementuje <xref:System.Collections.IList> rozhraní může být <xref:System.Array>, <xref:System.Collections.ArrayList>, nebo <xref:System.Collections.CollectionBase>. Toto jsou indexované seznamy položek typu <xref:System.Object>. Tyto seznamy musí obsahovat homogenní typů, protože typ Určuje první položku indexu. <xref:System.Collections.IList> bude k dispozici pro vazbu jenom v době běhu.  
  
    > [!NOTE]
    >  Pokud chcete vytvořit seznam obchodních objektů pro vazbu s Windows Forms, měli byste zvážit použití <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> Je rozšiřitelný třída, která implementuje rozhraní primární vyžadované pro obousměrný Windows Forms – datová vazba.  
  
-   <xref:System.ComponentModel.IBindingList> rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní umožňuje mnohem vyšší úroveň funkcí datové vazby. Tato implementace nabízí základní možnosti řazení a oznámení o změně, jak když v seznamu položek změnu (třetí položka v seznamu zákazníků má například změna do pole adresy), i když samotný seznam změní (například počet položek v seznamu, které zvětší nebo zmenší). Upozornění na změnu je důležité, pokud chcete mít více ovládacích prvků vázaných ke stejným datům, a chcete změny dat v jednom z ovládacích prvků na jiné vázané ovládací prvky.  
  
    > [!NOTE]
    >  Oznámení o změně je povolený pro <xref:System.ComponentModel.IBindingList> rozhraní prostřednictvím <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> vlastnost které, když `true`, vyvolá <xref:System.ComponentModel.IBindingList.ListChanged> určující seznam změnit nebo položku v seznamu událostí, změnit.  
  
     Typ změny je popsán <xref:System.ComponentModel.ListChangedType> vlastnost <xref:System.ComponentModel.ListChangedEventArgs> parametru. Proto při každé aktualizaci datového modelu, všechny závislé zobrazení, jako je například jiných ovládacích prvků vázaných ke stejnému zdroji dat, bude také aktualizovat. Ale bude nutné upozornit seznamu při změnách tak, aby může vyvolat seznam objekty obsažené v seznamu <xref:System.ComponentModel.IBindingList.ListChanged> událostí.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BindingList%601> Poskytuje obecnou implementaci <xref:System.ComponentModel.IBindingList> rozhraní.  
  
-   <xref:System.ComponentModel.IBindingListView> rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní poskytuje všechny funkce, které jsou součástí implementace <xref:System.ComponentModel.IBindingList>, stejně jako filtrování a pokročilé funkce řazení. Tato implementace nabízí založené na řetězci filtrování a řazení více sloupců s páry směr popisovače vlastnosti.  
  
-   <xref:System.ComponentModel.IEditableObject> rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IEditableObject> rozhraní umožňuje řídit, kdy na tento objekt dojde ke změně trvalého objektu. Tato implementace zajišťuje <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody, které umožňují snadno vrátit zpět změny provedené v objektu. Tady je stručné vysvětlení fungování <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metod a jak fungují společně s možností vzájemné umožňující možné vrátit zpět změny provedené v datech:  
  
    -   <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> Metoda signály start úpravy objektu. Objekt, který implementuje toto rozhraní bude nutné ukládat žádné aktualizace po <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> volání metody tak, že aktualizace můžete zahodit Pokud <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metoda je volána. V datové vazbě Windows Forms, můžete volat <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> více než jednou v rámci oboru jednoho upravit transakci (třeba <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). Implementace <xref:System.ComponentModel.IEditableObject> měli sledovat, jestli se <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> již byla volána a ignorovat následných volání <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Tuto metodu lze volat vícekrát, proto je důležité, že jsou následných volání nedestruktivní; To znamená následné <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> volání nelze zničit aktualizace, které byly provedeny nebo změnit data, která byla uložena v prvním <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> volání.  
  
    -   <xref:System.ComponentModel.IEditableObject.EndEdit%2A> Metoda nabízených oznámení změny od <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> byla volána na základní objekt, pokud objekt je aktuálně v režimu úprav.  
  
    -   <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Metoda zahodí všechny změny provedené objektu.  
  
     Další informace o tom, jak <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody práce, naleznete v tématu [uložit data zpět do databáze](/visualstudio/data-tools/save-data-back-to-the-database).  
  
     Transakční vyskytují funkci dat používá <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
-   <xref:System.ComponentModel.ICancelAddNew> rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.ICancelAddNew> obvykle implementuje rozhraní <xref:System.ComponentModel.IBindingList> rozhraní a umožňuje vrátit zpět přidání provedené ke zdroji dat s <xref:System.ComponentModel.IBindingList.AddNew%2A> metody. Pokud zdroj dat implementuje <xref:System.ComponentModel.IBindingList> rozhraní, měli byste také mít ho implementovat <xref:System.ComponentModel.ICancelAddNew> rozhraní.  
  
-   <xref:System.ComponentModel.IDataErrorInfo> rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IDataErrorInfo> rozhraní umožňuje objekty nabízí informace o vlastní chybě vázané ovládací prvky:  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Error%2A> Vlastnost vrací text obecné chybové zprávy (například "došlo k chybě").  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Item%2A> Vlastnost vrátí řetězec s určité chybové zprávě ve sloupci (například "hodnota v `State` sloupec není platný").  
  
-   <xref:System.Collections.IEnumerable> rozhraní  
  
     Třídu, která implementuje <xref:System.Collections.IEnumerable> rozhraní obvykle využívá [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. Podpora Windows Forms pro toto rozhraní je dostupná jenom <xref:System.Windows.Forms.BindingSource> komponenty.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource> Komponenty zkopíruje všechny <xref:System.Collections.IEnumerable> položek do samostatného seznamu pro účely vazby.  
  
-   <xref:System.ComponentModel.ITypedList> rozhraní  
  
     Třídy kolekcí, která implementuje <xref:System.ComponentModel.ITypedList> rozhraní umožňuje řídit pořadí a sadu vlastností, které jsou vystaveny vázaného ovládacího prvku.  
  
    > [!NOTE]
    >  Při implementaci <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> metody a <xref:System.ComponentModel.PropertyDescriptor> pole nemá hodnotu null, že poslední položka v poli bude popisovač vlastnosti, která popisuje vlastnosti seznamu, který je jiný seznam položek.  
  
-   <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní poskytuje dynamických informací o sobě. Toto rozhraní je podobný <xref:System.ComponentModel.ITypedList> ale používá se pro objekty, spíše než seznamy. Toto rozhraní je používán <xref:System.Data.DataRowView> do projektu schématu podkladových řádků. Jednoduchá implementace <xref:System.ComponentModel.ICustomTypeDescriptor> je poskytován <xref:System.ComponentModel.CustomTypeDescriptor> třídy.  
  
    > [!NOTE]
    >  Pro podporu návrhu vazbu na typy, které implementují <xref:System.ComponentModel.ICustomTypeDescriptor>, musíte také implementovat typ <xref:System.ComponentModel.IComponent> existovat jako instance na formulář.  
  
-   <xref:System.ComponentModel.IListSource> rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IListSource> rozhraní umožňuje vytvořit vazbu na základě seznamu na jiné seznam objektů. <xref:System.ComponentModel.IListSource.GetList%2A> Metoda <xref:System.ComponentModel.IListSource> se používá k vrácení umožňujících vazbu seznamu z objektu, který nedědí od <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> používá <xref:System.Data.DataSet> třídy.  
  
-   <xref:System.ComponentModel.IRaiseItemChangedEvents> rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IRaiseItemChangedEvents> rozhraní je s možností vazby seznam, který také implementuje <xref:System.ComponentModel.IBindingList> rozhraní. Toto rozhraní se používá k označení, pokud váš typ vyvolá <xref:System.ComponentModel.IBindingList.ListChanged> události typu <xref:System.ComponentModel.ListChangedType.ItemChanged> prostřednictvím jeho <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> vlastnost.  
  
    > [!NOTE]
    >  Měli byste implementovat <xref:System.ComponentModel.IRaiseItemChangedEvents> Pokud zdroj dat obsahuje vlastnost, která má seznam událostí převodu je popsáno výše a interakci s <xref:System.Windows.Forms.BindingSource> komponenty. V opačném případě <xref:System.Windows.Forms.BindingSource> také provede vlastnost do seznamu událostí převod výsledkem je pomalejší výkon.  
  
-   <xref:System.ComponentModel.ISupportInitialize> rozhraní  
  
     Komponenty, která implementuje <xref:System.ComponentModel.ISupportInitialize> rozhraní využívá výhod optimalizací služby batch pro nastavení vlastností a inicializace závislé na společné vlastnosti. <xref:System.ComponentModel.ISupportInitialize> Obsahuje dvě metody:  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> signalizuje, že se, že inicializace objektu se spouští.  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> signalizuje, že se, že inicializace objektu se nepřipojujte.  
  
-   <xref:System.ComponentModel.ISupportInitializeNotification> rozhraní  
  
     Komponenty, která implementuje <xref:System.ComponentModel.ISupportInitializeNotification> rozhraní také implementuje <xref:System.ComponentModel.ISupportInitialize> rozhraní. Toto rozhraní umožňuje informovat ostatní <xref:System.ComponentModel.ISupportInitialize> komponenty, že inicializace je dokončena. <xref:System.ComponentModel.ISupportInitializeNotification> Rozhraní obsahuje dva členy:  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> Vrátí `boolean` hodnotu, která udává, zda je komponenta inicializována.  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> Nastane, když <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> je volána.  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní  
  
     Třída, která implementuje toto rozhraní je typ, který vyvolá událost, když se změní některý z jeho hodnot vlastností. Toto rozhraní je určena k nahrazení vzor s událost změny pro každou vlastnost ovládacího prvku. Při použití v <xref:System.ComponentModel.BindingList%601>, by měly implementovat obchodní objekt <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a BindingList\`1 budou převedeny <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události <xref:System.ComponentModel.BindingList%601.ListChanged> události typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
    > [!NOTE]
    >  Změna oznámení probíhá vytvoření vazby mezi vazby klienta a data vašeho vázaný zdroj dat typu zdroje by měly buď implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní (upřednostňováno) nebo vám může poskytnout *propertyName* `Changed` události pro typ vazby, ale by neměly provést obojí.  
  
### <a name="interfaces-for-implementation-by-component-authors"></a>Rozhraní pro implementaci autoři komponenty  
 Následující rozhraní jsou navrženy pro použití modulem datové vazby Windows Forms:  
  
-   <xref:System.Windows.Forms.IBindableComponent> rozhraní  
  
     Třída, která implementuje toto rozhraní je komponenty – ovládací prvek, který podporuje datovou vazbu. Tato třída vrátí datové vazby a kontextu vazby součásti prostřednictvím <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> a <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> vlastnosti tohoto rozhraní.  
  
    > [!NOTE]
    >  Pokud vaše komponenta dědí z <xref:System.Windows.Forms.Control>, není potřeba implementovat <xref:System.Windows.Forms.IBindableComponent> rozhraní.  
  
-   <xref:System.Windows.Forms.ICurrencyManagerProvider> rozhraní  
  
     Třídu, která implementuje <xref:System.Windows.Forms.ICurrencyManagerProvider> rozhraní je komponenta, která poskytuje vlastní <xref:System.Windows.Forms.CurrencyManager> ke správě vazeb spojených s Tato konkrétní komponenta. Přístup k vlastní <xref:System.Windows.Forms.CurrencyManager> je poskytován <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> vlastnost.  
  
    > [!NOTE]
    >  Třída, která dědí z <xref:System.Windows.Forms.Control> spravuje vazby automaticky prostřednictvím jeho <xref:System.Windows.Forms.Control.BindingContext%2A> vlastnosti, takže případy, ve kterých je nutné implementovat <xref:System.Windows.Forms.ICurrencyManagerProvider> jsou velmi malý.  
  
## <a name="see-also"></a>Viz také:

- [Datové vazby a rozhraní Windows Forms](data-binding-and-windows-forms.md)
- [Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
