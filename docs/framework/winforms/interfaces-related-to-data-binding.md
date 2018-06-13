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
ms.openlocfilehash: 6c4470b33977408fa4429d187dafd76241d0d9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541843"
---
# <a name="interfaces-related-to-data-binding"></a>Rozhraní související s datovou vazbou
S [!INCLUDE[vstecado](../../../includes/vstecado-md.md)], můžete vytvořit vazba potřebám vaší aplikace a data, že pracujete s mnoha různých datových struktur. Můžete vytvořit vaše vlastní třídy, které poskytovat nebo přijímat data ve Windows Forms. Tyto objekty nabízejí různé úrovně funkčnosti a složitost od základní datové vazby k poskytování podpory návrhu, kontrola chyb, upozornění na změnu nebo i podpora pro strukturovaných vrácení zpět změny provedené s vlastními daty.  
  
## <a name="consumers-of-data-binding-interfaces"></a>Příjemci rozhraní datové vazby  
 Následující části popisují dvě skupiny objekty rozhraní. První skupinu uvádí rozhraní, které jsou implementovány na zdroje dat autory zdroje dat. Tato rozhraní jsou navrženy pro uplatníte spotřebitelé zdroje dat, které jsou ve většině případů, které Windows Forms – ovládací prvky nebo součásti. Ve druhé skupině uvádí rozhraní určený k použití autory součásti. Autoři součást používat tato rozhraní při vytváření komponenty, která podporuje datovou vazbu pro modul Windows Forms datové vazby. Můžete implementovat tato rozhraní v rámci třídy, které jsou přidružené k formuláři povolit datové vazby; každý případ představuje třídu, která implementuje rozhraní, které umožňuje interakci s daty. Visual Studio rychlé (RAD) data návrhu prostředí nástroje pro vývoj aplikací již využít tuto funkci.  
  
### <a name="interfaces-for-implementation-by-data-source-authors"></a>Rozhraní pro implementaci autory zdroje dat  
 Následující rozhraní jsou určené pro Windows Forms – ovládací prvky:  
  
-   <xref:System.Collections.IList> Rozhraní  
  
     Třídu, která implementuje <xref:System.Collections.IList> rozhraní může být <xref:System.Array>, <xref:System.Collections.ArrayList>, nebo <xref:System.Collections.CollectionBase>. Toto jsou indexované seznam položek typu <xref:System.Object>. Tyto seznamy musí obsahovat homogenního typů, protože první položka indexu Určuje typ. <xref:System.Collections.IList> bude k dispozici pro vazbu pouze za běhu.  
  
    > [!NOTE]
    >  Pokud chcete vytvořit seznam objektů obchodní pro vazbu s Windows Forms, měli byste zvážit použití <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> Je rozšiřitelný třída, která implementuje rozhraní primární požadované pro dvoucestné Windows Forms – datová vazba.  
  
-   <xref:System.ComponentModel.IBindingList> Rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní poskytuje mnohem vyšší úroveň funkce datové vazby. Tato implementace nabízí základní možnosti řazení a oznámení o změně, pro při seznamu položky změnit (například třetí položku v seznamu zákazníků musí změnu pole adresy), i když samotný seznam změní (například počet položek v seznamu, které zvýší nebo sníží). Upozornění na změnu je důležité, pokud chcete mít více ovládacích prvků vázaných ke stejným datům, a chcete data změny provedené v jednom z ovládacích prvků na vázané ovládací prvky.  
  
    > [!NOTE]
    >  Oznámení o změně je povolený pro <xref:System.ComponentModel.IBindingList> rozhraní prostřednictvím <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> vlastnost která, pokud `true`, vyvolá <xref:System.ComponentModel.IBindingList.ListChanged> událost označující seznamu změnit nebo položku v seznamu změnit.  
  
     Typ změny, je popsán <xref:System.ComponentModel.ListChangedType> vlastnost <xref:System.ComponentModel.ListChangedEventArgs> parametr. Proto při každé aktualizaci datového modelu, všechny závislé zobrazení, například jako další ovládací prvky vázané na stejný zdroj dat, bude také aktualizovat. Nicméně objekty obsažené v seznamu budou mít upozornit seznamu, když se změní, aby můžete zvýšit v seznamu <xref:System.ComponentModel.IBindingList.ListChanged> událostí.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BindingList%601> Poskytuje obecnou implementaci <xref:System.ComponentModel.IBindingList> rozhraní.  
  
-   <xref:System.ComponentModel.IBindingListView> Rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní představuje všechny funkce implementace <xref:System.ComponentModel.IBindingList>, stejně jako filtrování a pokročilé funkce řazení. Tato implementace nabízí založené na řetězcích Filtrování a řazení více sloupců s páry směr popisovače vlastnosti.  
  
-   <xref:System.ComponentModel.IEditableObject> Rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IEditableObject> rozhraní, které umožňuje objekt k řízení, když jsou vytvářeny trvalé změny tohoto objektu. Tato implementace umožňuje <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody, které vám umožní vrátit zpět změny provedené v objektu. Následuje stručné vysvětlení fungování <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody a jak pracují ve spojení s navzájem povolit možné vrátit zpět změny provedené v datech:  
  
    -   <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> Metoda signály začátek upravíte objektu. Objekt, který toto rozhraní implementuje potřeba ukládat žádné aktualizace po <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> volání metody tak, že může být vymazány aktualizace Pokud <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metoda je volána. V datové vazbě Windows Forms, můžete volat <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> více než jednou. v rámci oboru jedné upravit transakce (například <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). Implementace <xref:System.ComponentModel.IEditableObject> měli sledovat jestli <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> již byla volána a ignorovat následující volání <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Tuto metodu lze volat vícekrát, proto je důležité, jsou následující volání nedestruktivní; To znamená následných <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> volání nelze destroy aktualizace, které byly provedeny nebo změnit data, která byla uložena v prvním <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> volání.  
  
    -   <xref:System.ComponentModel.IEditableObject.EndEdit%2A> Metoda nabízených oznámení změny od <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> byla volána do základní objekt, pokud objekt se aktuálně v režimu úprav.  
  
    -   <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Metoda zahodí všechny změny do objektu.  
  
     Další informace o tom, jak <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody naleznete v tématech [uložit data zpět do databáze](/visualstudio/data-tools/save-data-back-to-the-database).  
  
     Tento transakční představu o data funkce používá <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
-   <xref:System.ComponentModel.ICancelAddNew> Rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.ICancelAddNew> obvykle implementuje rozhraní <xref:System.ComponentModel.IBindingList> rozhraní a umožňuje vrátit zpět ke zdroji dat s doplňkem <xref:System.ComponentModel.IBindingList.AddNew%2A> metoda. Pokud vaše data zdroje implementuje <xref:System.ComponentModel.IBindingList> rozhraní, měli byste také mít ho implementovat <xref:System.ComponentModel.ICancelAddNew> rozhraní.  
  
-   <xref:System.ComponentModel.IDataErrorInfo> Rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IDataErrorInfo> rozhraní, které umožňuje objekty, které se nabízejí informace o vlastní chybě vázané ovládací prvky:  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Error%2A> Vlastnost vrací text obecné chybové zprávy (například "došlo k chybě").  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Item%2A> Vlastnost vrátí řetězec s konkrétní chybová zpráva ze sloupce (například "hodnota v `State` sloupec není platný").  
  
-   <xref:System.Collections.IEnumerable> Rozhraní  
  
     Třídu, která implementuje <xref:System.Collections.IEnumerable> rozhraní obvykle využívá [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. Windows Forms podporu pro toto rozhraní je k dispozici prostřednictvím pouze <xref:System.Windows.Forms.BindingSource> součásti.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource> Součást zkopíruje všechny <xref:System.Collections.IEnumerable> položky na samostatných seznam pro účely vazby.  
  
-   <xref:System.ComponentModel.ITypedList> Rozhraní  
  
     Třídy kolekce, která implementuje <xref:System.ComponentModel.ITypedList> rozhraní umožňuje řídit pořadí a sadu vlastností, které jsou zpřístupněny připojeného ovládacího prvku.  
  
    > [!NOTE]
    >  Při implementaci <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> metody a <xref:System.ComponentModel.PropertyDescriptor> pole nemá hodnotu null, poslední položky v poli, bude popisovač vlastnosti, která popisuje vlastnosti seznamu, která je jiný seznam položek.  
  
-   <xref:System.ComponentModel.ICustomTypeDescriptor> Rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní představuje dynamické informace o sobě. Toto rozhraní je podobná <xref:System.ComponentModel.ITypedList> ale používá se pro objekty, nikoli seznamy. Toto rozhraní je používán <xref:System.Data.DataRowView> do projektu schéma zadané řádky. Jednoduchá implementace <xref:System.ComponentModel.ICustomTypeDescriptor> zajišťuje <xref:System.ComponentModel.CustomTypeDescriptor> třídy.  
  
    > [!NOTE]
    >  Pro podporu návrhu vazbu na typy, které implementují <xref:System.ComponentModel.ICustomTypeDescriptor>, musíte také implementovat typ <xref:System.ComponentModel.IComponent> existuje jako instance na formuláři.  
  
-   <xref:System.ComponentModel.IListSource> Rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IListSource> rozhraní umožňuje na základě seznamu vazbu na jiný list – objekty. <xref:System.ComponentModel.IListSource.GetList%2A> Metodu <xref:System.ComponentModel.IListSource> se používá k vrácení seznam vazbu z objektu, který nedědí z <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> je používán <xref:System.Data.DataSet> třídy.  
  
-   <xref:System.ComponentModel.IRaiseItemChangedEvents> Rozhraní  
  
     Třídu, která implementuje <xref:System.ComponentModel.IRaiseItemChangedEvents> rozhraní je vazbu seznamu, který je navíc implementovaná <xref:System.ComponentModel.IBindingList> rozhraní. Toto rozhraní slouží k označení, pokud typ vašeho vyvolá <xref:System.ComponentModel.IBindingList.ListChanged> události typu <xref:System.ComponentModel.ListChangedType.ItemChanged> prostřednictvím jeho <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> vlastnost.  
  
    > [!NOTE]
    >  Měli byste implementovat <xref:System.ComponentModel.IRaiseItemChangedEvents> Pokud zdroje dat obsahuje vlastnosti seznamu převod událostí popsané a komunikuje s <xref:System.Windows.Forms.BindingSource> součásti. Jinak <xref:System.Windows.Forms.BindingSource> také provede vlastnost pro převod událostí seznamu vést k nižšímu výkonu.  
  
-   <xref:System.ComponentModel.ISupportInitialize> Rozhraní  
  
     Komponenty, která implementuje <xref:System.ComponentModel.ISupportInitialize> rozhraní se využívají batch optimalizace pro nastavení vlastností a společné závislé vlastnosti inicializace. <xref:System.ComponentModel.ISupportInitialize> Obsahuje dvě metody:  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> signalizuje, že se spouští této inicializace objektů.  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> signalizuje, že tento inicializace objektů se nepřipojujte.  
  
-   <xref:System.ComponentModel.ISupportInitializeNotification> Rozhraní  
  
     Komponenty, která implementuje <xref:System.ComponentModel.ISupportInitializeNotification> rozhraní také implementuje <xref:System.ComponentModel.ISupportInitialize> rozhraní. Toto rozhraní umožňuje oznámit dalších <xref:System.ComponentModel.ISupportInitialize> součásti tohoto inicializace je dokončena. <xref:System.ComponentModel.ISupportInitializeNotification> Rozhraní obsahuje dva členy:  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> Vrátí `boolean` hodnotu, která určuje, zda je součást inicializován.  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> nastane při <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> je volána.  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged> Rozhraní  
  
     Třída, která implementuje toto rozhraní je typ, který vyvolá událost, pokud některý z jeho hodnoty vlastností změnit. Toto rozhraní je určena k nahrazení vzoru toho, že událost změny pro každou vlastnost ovládacího prvku. Při použití v <xref:System.ComponentModel.BindingList%601>, musí implementovat objekt obchodní <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a BindingList\`1 převede <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události <xref:System.ComponentModel.BindingList%601.ListChanged> události typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
    > [!NOTE]
    >  Pro změnu oznámení v vazbu mezi vázané klienta a dat k vaší vázaný zdroj dat typ zdroje musí buď implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní (doporučeno) nebo je můžete zadat *propertyName* `Changed` události typu vázané, ale neměli proveďte obojí.  
  
### <a name="interfaces-for-implementation-by-component-authors"></a>Rozhraní pro implementaci autory součásti  
 Následující rozhraní jsou určené pro spotřebu modul Windows Forms vazby dat:  
  
-   <xref:System.Windows.Forms.IBindableComponent> Rozhraní  
  
     Třída, která implementuje toto rozhraní je komponentu – ovládací prvek, který podporuje datovou vazbu. Tato třída vrátí datové vazby a kontextu vazby součásti prostřednictvím <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> a <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> vlastnosti tohoto rozhraní.  
  
    > [!NOTE]
    >  Pokud příslušné součásti dědí z <xref:System.Windows.Forms.Control>, není potřeba implementovat <xref:System.Windows.Forms.IBindableComponent> rozhraní.  
  
-   <xref:System.Windows.Forms.ICurrencyManagerProvider> Rozhraní  
  
     Třídu, která implementuje <xref:System.Windows.Forms.ICurrencyManagerProvider> rozhraní je komponenta, která poskytuje vlastní <xref:System.Windows.Forms.CurrencyManager> ke správě vazby přidružený k této konkrétní součásti. Přístup k vlastní <xref:System.Windows.Forms.CurrencyManager> zajišťuje <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> vlastnost.  
  
    > [!NOTE]
    >  Třída, která dědí z <xref:System.Windows.Forms.Control> spravuje vazby automaticky pomocí jeho <xref:System.Windows.Forms.Control.BindingContext%2A> vlastnost, tak případy, ve kterých potřebujete implementovat <xref:System.Windows.Forms.ICurrencyManagerProvider> jsou poměrně výjimečných.  
  
## <a name="see-also"></a>Viz také  
 [Datové vazby a Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)
