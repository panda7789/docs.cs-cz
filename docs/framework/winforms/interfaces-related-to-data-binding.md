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
ms.openlocfilehash: 9f102b584d2ed0b5a9d2bbb0e7ce3f7871ec40b2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046362"
---
# <a name="interfaces-related-to-data-binding"></a>Rozhraní související s datovou vazbou

Pomocí ADO.NET můžete vytvořit mnoho různých datových struktur, které budou vyhovovat potřebám vazby vaší aplikace a datům, se kterými pracujete. Můžete chtít vytvořit vlastní třídy, které poskytují nebo využívají data v model Windows Forms. Tyto objekty mohou nabízet různé úrovně funkcí a složitosti, od základních datových vazeb až po návrhovou podporu, kontrolu chyb, oznámení o změně nebo dokonce podporu pro strukturované vrácení změn provedených v samotných datech.

## <a name="consumers-of-data-binding-interfaces"></a>Spotřebitelé rozhraní datových vazeb

Následující části popisují dvě skupiny objektů rozhraní. První skupina uvádí rozhraní, která jsou implementována na zdrojích dat autory zdrojů dat. Tato rozhraní jsou navržena tak, aby byla využívána spotřebiteli zdroje dat, který je ve většině případů model Windows Forms ovládacích prvků nebo komponent. Druhá skupina vypisuje rozhraní navržená pro použití tvůrci součástí. Autoři součástí používají tato rozhraní při vytváření komponenty, která podporuje datovou vazbu, která má být využívána model Windows Forms modul vázání dat. Můžete implementovat tato rozhraní v rámci tříd přidružených k formuláři pro povolení datové vazby; každý případ prezentuje třídu, která implementuje rozhraní, které umožňuje interakci s daty. Nástroje pro návrh dat pro vývoj aplikací pro Visual Studio Rapid (RAD) už tuto funkci využívají.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Rozhraní pro implementaci autory zdrojů dat

Následující rozhraní jsou navržena tak, aby byla využívána model Windows Formsmi ovládacími prvky:

- <xref:System.Collections.IList>prostředí

  Třída, která <xref:System.Collections.IList> implementuje rozhraní <xref:System.Array>, může být, <xref:System.Collections.ArrayList>nebo <xref:System.Collections.CollectionBase>. Jedná se o indexované seznamy položek typu <xref:System.Object>. Tyto seznamy musí obsahovat homogenní typy, protože první položka indexu Určuje typ. <xref:System.Collections.IList>bude k dispozici pro vazbu pouze v době běhu.

  > [!NOTE]
  > Chcete-li vytvořit seznam obchodních objektů pro vazbu s model Windows Forms, měli byste zvážit použití <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> Je rozšiřitelná třída, která implementuje primární rozhraní požadovaná pro obousměrnou model Windows Forms datovou vazbu.

- <xref:System.ComponentModel.IBindingList>prostředí

  Třída, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní, poskytuje mnohem vyšší úroveň funkcí datové vazby. Tato implementace nabízí základní možnosti řazení a oznámení o změně, pro kdy se změní položky seznamu (například třetí položka v seznamu zákazníků má změnu v poli adresa) a také při změně samotného seznamu (například počet položek v seznamu se zvětšuje nebo zmenšuje). Oznámení o změně je důležité, pokud máte v plánu mít více ovládacích prvků vázaných na stejná data a chcete, aby se změny dat provedené v jednom z ovládacích prvků rozšířily do dalších vázaných ovládacích prvků.

  > [!NOTE]
  > Oznámení o změně je povoleno pro <xref:System.ComponentModel.IBindingList> rozhraní <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> prostřednictvím vlastnosti <xref:System.ComponentModel.IBindingList.ListChanged> , která při `true`události vyvolá událost, která indikuje, že se seznam změnil nebo se změnila položka v seznamu.

  Typ změny je popsán <xref:System.ComponentModel.ListChangedType> vlastností <xref:System.ComponentModel.ListChangedEventArgs> parametru. Všechny závislé pohledy, jako jsou například jiné ovládací prvky vázané na stejný zdroj dat, budou proto aktualizovány také v případě, že dojde k aktualizaci datového modelu. Objekty, které jsou obsaženy v seznamu, ale budou muset při změně seznamu upozornění zobrazit, aby seznam mohl vyvolat <xref:System.ComponentModel.IBindingList.ListChanged> událost.

  > [!NOTE]
  > Poskytuje obecnou implementaci <xref:System.ComponentModel.IBindingList>rozhraní. <xref:System.ComponentModel.BindingList%601>

- <xref:System.ComponentModel.IBindingListView>prostředí

  Třída, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní <xref:System.ComponentModel.IBindingList>, poskytuje všechny funkce implementace a také filtrování a pokročilé funkce řazení. Tato implementace nabízí filtrování založené na řetězcích a více sloupců s páry popisovačů vlastností.

- <xref:System.ComponentModel.IEditableObject>prostředí

  Třída, která implementuje <xref:System.ComponentModel.IEditableObject> rozhraní, umožňuje objektu řídit, kdy jsou změny tohoto objektu provedeny trvalé. Tato implementace poskytuje <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>metody, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> , které umožňují vrátit zpět změny provedené v objektu. Toto je stručné vysvětlení fungování <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metod, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, a, jak fungují společně s sebou, aby bylo možné vrátit změny provedené v datech:

  - <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> Metoda signalizuje začátek úpravy objektu. Objekt, který implementuje toto rozhraní, bude muset ukládat jakékoli aktualizace po <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> volání metody takovým způsobem, že aktualizace mohou být zahozeny, <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Pokud je metoda volána. V model Windows Forms vazby <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> dat můžete volat vícekrát v rámci oboru jedné úpravy transakce ( <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>například <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.EndEdit%2A>,,). Implementace by měly sledovat, zda <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> již bylo voláno a ignorovat následná volání na <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. <xref:System.ComponentModel.IEditableObject> Vzhledem k tomu, že tuto metodu lze volat víckrát, je důležité, aby následné volání na ni byla nedestruktivní; To znamená, že <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> následná volání nemohou zničit aktualizace, které byly provedeny, nebo změnit data, která byla uložena při <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> prvním volání.

  - Metoda vloží všechny změny, protože <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> byly volány do podkladového objektu, pokud je objekt aktuálně v režimu úprav. <xref:System.ComponentModel.IEditableObject.EndEdit%2A>

  - <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Metoda zahodí všechny změny provedené v objektu.

  Další informace o <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>fungování metod, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> naleznete v tématu [uložení dat zpět do databáze](/visualstudio/data-tools/save-data-back-to-the-database).

  Tento transakční pojem datových funkcí je používán <xref:System.Windows.Forms.DataGridView> ovládacím prvkem.

- <xref:System.ComponentModel.ICancelAddNew>prostředí

  Třída, která implementuje <xref:System.ComponentModel.ICancelAddNew> rozhraní, obvykle <xref:System.ComponentModel.IBindingList> implementuje rozhraní a umožňuje vrátit zpět sčítání provedené ve zdroji <xref:System.ComponentModel.IBindingList.AddNew%2A> dat metodou. Pokud váš zdroj dat implementuje <xref:System.ComponentModel.IBindingList> rozhraní, měli byste také <xref:System.ComponentModel.ICancelAddNew> implementovat rozhraní.

- <xref:System.ComponentModel.IDataErrorInfo>prostředí

  Třída, která implementuje <xref:System.ComponentModel.IDataErrorInfo> rozhraní, umožňuje objektům nabízet vlastní informace o chybách vázaným ovládacím prvkům:

  - <xref:System.ComponentModel.IDataErrorInfo.Error%2A> Vlastnost vrátí obecný text chybové zprávy (například "došlo k chybě").

  - Vlastnost vrátí řetězec se specifickou chybovou zprávou ze sloupce (například "hodnota `State` ve sloupci je neplatná"). <xref:System.ComponentModel.IDataErrorInfo.Item%2A>

- <xref:System.Collections.IEnumerable>prostředí

  Třída, která implementuje <xref:System.Collections.IEnumerable> rozhraní, je obvykle spotřebovaná pomocí ASP.NET. Podpora model Windows Forms pro toto rozhraní je k dispozici pouze <xref:System.Windows.Forms.BindingSource> prostřednictvím součásti.

  > [!NOTE]
  > Komponenta zkopíruje všechny <xref:System.Collections.IEnumerable> položky do samostatného seznamu pro účely vazby. <xref:System.Windows.Forms.BindingSource>

- <xref:System.ComponentModel.ITypedList>prostředí

  Třída kolekce, která implementuje <xref:System.ComponentModel.ITypedList> rozhraní, poskytuje možnost řídit pořadí a sadu vlastností vystavených pro vázaný ovládací prvek.

  > [!NOTE]
  > Při implementaci <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> metody <xref:System.ComponentModel.PropertyDescriptor> a pole není null, poslední položka v poli bude popisovač vlastnosti, který popisuje vlastnost seznamu, která je další seznam položek.

- <xref:System.ComponentModel.ICustomTypeDescriptor>prostředí

  Třída, která implementuje <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní, poskytuje dynamické informace o sobě. Toto rozhraní je podobné, <xref:System.ComponentModel.ITypedList> ale používá se spíše pro objekty, nikoli pro seznamy. Toto rozhraní se používá k <xref:System.Data.DataRowView> vytvoření projektového schématu podkladových řádků. Jednoduchá implementace <xref:System.ComponentModel.ICustomTypeDescriptor> <xref:System.ComponentModel.CustomTypeDescriptor> třídy je poskytována třídou.

  > [!NOTE]
  > Pro podporu vazby při návrhu na typy, které implementují <xref:System.ComponentModel.ICustomTypeDescriptor>, musí být typ také implementován <xref:System.ComponentModel.IComponent> a existovat jako instance ve formuláři.

- <xref:System.ComponentModel.IListSource>prostředí

  Třída, která implementuje <xref:System.ComponentModel.IListSource> rozhraní, povoluje vazbu založenou na seznamu pro objekty, které nejsou typu list. Metoda je použita k vrácení seznamu s možností vazby z objektu, který nedědí z <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource.GetList%2A> <xref:System.ComponentModel.IListSource> <xref:System.ComponentModel.IListSource>je používán <xref:System.Data.DataSet> třídou.

- <xref:System.ComponentModel.IRaiseItemChangedEvents>prostředí

  Třída, která implementuje <xref:System.ComponentModel.IRaiseItemChangedEvents> rozhraní, je seznam s možností vazby, který <xref:System.ComponentModel.IBindingList> implementuje i rozhraní. Toto rozhraní slouží k označení, zda váš typ vyvolá <xref:System.ComponentModel.IBindingList.ListChanged> události typu <xref:System.ComponentModel.ListChangedType.ItemChanged> prostřednictvím jeho <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> vlastnosti.

  > [!NOTE]
  > Měli byste implementovat, <xref:System.ComponentModel.IRaiseItemChangedEvents> Pokud váš zdroj dat poskytuje vlastnost k vypsání výše popsaného převodu události a interakci <xref:System.Windows.Forms.BindingSource> s komponentou. V opačném případě bude také provedeno vlastnost k vypsání převodu události, což vede k nižšímu výkonu. <xref:System.Windows.Forms.BindingSource>

- <xref:System.ComponentModel.ISupportInitialize>prostředí

  Komponenta, která implementuje <xref:System.ComponentModel.ISupportInitialize> rozhraní, využívá výhody optimalizace dávek pro nastavení vlastností a inicializaci souběžně závislých vlastností. <xref:System.ComponentModel.ISupportInitialize> Obsahuje dvě metody:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>signalizuje, že se spouští inicializace objektu.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>signalizuje, že se dokončuje inicializace objektu.

- <xref:System.ComponentModel.ISupportInitializeNotification>prostředí

  Komponenta, která implementuje <xref:System.ComponentModel.ISupportInitializeNotification> rozhraní, <xref:System.ComponentModel.ISupportInitialize> implementuje také rozhraní. Toto rozhraní vám umožní informovat ostatní <xref:System.ComponentModel.ISupportInitialize> komponenty, které se inicializace dokončila. <xref:System.ComponentModel.ISupportInitializeNotification> Rozhraní obsahuje dva členy:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A>`boolean` vrátí hodnotu, která označuje, zda je komponenta inicializována.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized>nastane, <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> když se zavolá.

- <xref:System.ComponentModel.INotifyPropertyChanged>prostředí

  Třída, která implementuje toto rozhraní, je typ, který vyvolá událost, když se změní kterákoli jeho hodnota vlastnosti. Toto rozhraní je navrženo tak, aby nahradilo vzor, který má událost změny pro každou vlastnost ovládacího prvku. Při <xref:System.ComponentModel.BindingList%601>použití v nástroji by obchodní objekt měl <xref:System.ComponentModel.INotifyPropertyChanged> implementovat rozhraní a BindingList\`1 převede <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události na <xref:System.ComponentModel.BindingList%601.ListChanged> události typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.

  > [!NOTE]
  > Aby mohlo dojít ke změně v vazbě mezi vázaným klientem a zdrojem dat, váš typ zdroje vázaných dat by měl buď implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní (upřednostňovaná), nebo můžete zadat události *PropertyName* `Changed` pro vázaný typ. ale neměli byste dělat obojí.

### <a name="interfaces-for-implementation-by-component-authors"></a>Rozhraní pro implementaci pomocí autorů součástí

Následující rozhraní jsou navržena pro využití model Windows Forms modul vázání dat:

- <xref:System.Windows.Forms.IBindableComponent>prostředí

  Třída, která implementuje toto rozhraní, je neovládací komponenta, která podporuje datovou vazbu. Tato třída vrací datové vazby a kontext vazby součásti prostřednictvím <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> vlastností a <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> tohoto rozhraní.

  > [!NOTE]
  > Pokud vaše komponenta dědí z <xref:System.Windows.Forms.Control>, není nutné <xref:System.Windows.Forms.IBindableComponent> implementovat rozhraní.

- <xref:System.Windows.Forms.ICurrencyManagerProvider>prostředí

  Třída, která implementuje <xref:System.Windows.Forms.ICurrencyManagerProvider> rozhraní, je komponenta, která poskytuje vlastní <xref:System.Windows.Forms.CurrencyManager> správu vazeb přidružených k této konkrétní komponentě. Přístup k vlastnímu <xref:System.Windows.Forms.CurrencyManager> je poskytován <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> vlastností.

  > [!NOTE]
  > Třída, která dědí z <xref:System.Windows.Forms.Control> spravuje vazby automaticky prostřednictvím své <xref:System.Windows.Forms.Control.BindingContext%2A> vlastnosti, takže případy, kdy je nutné implementovat rozhraní <xref:System.Windows.Forms.ICurrencyManagerProvider> , jsou poměrně zřídka.

## <a name="see-also"></a>Viz také:

- [Datové vazby a Windows Forms](data-binding-and-windows-forms.md)
- [Postupy: Vytvoření jednoduchého ovládacího prvku vázaného na formuláři Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
