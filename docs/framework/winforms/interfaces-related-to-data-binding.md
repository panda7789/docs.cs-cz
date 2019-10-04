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
ms.openlocfilehash: 4e40f7ec1922cdf43e6a0b8f5734acaaeefbc514
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834594"
---
# <a name="interfaces-related-to-data-binding"></a>Rozhraní související s datovou vazbou

Pomocí ADO.NET můžete vytvořit mnoho různých datových struktur, které budou vyhovovat potřebám vazby vaší aplikace a datům, se kterými pracujete. Můžete chtít vytvořit vlastní třídy, které poskytují nebo využívají data v model Windows Forms. Tyto objekty mohou nabízet různé úrovně funkcí a složitosti, od základních datových vazeb až po návrhovou podporu, kontrolu chyb, oznámení o změně nebo dokonce podporu pro strukturované vrácení změn provedených v samotných datech.

## <a name="consumers-of-data-binding-interfaces"></a>Spotřebitelé rozhraní datových vazeb

V následujících částech jsou popsány dvě skupiny objektů rozhraní. První skupina uvádí rozhraní, která jsou implementována na zdrojích dat autory zdrojů dat. Tato rozhraní jsou navržena tak, aby byla využívána spotřebiteli zdroje dat, který je ve většině případů model Windows Forms ovládacích prvků nebo komponent. Druhá skupina vypisuje rozhraní navržená pro použití tvůrci součástí. Autoři součástí používají tato rozhraní při vytváření komponenty, která podporuje datovou vazbu, která má být využívána model Windows Forms modul vázání dat. Můžete implementovat tato rozhraní v rámci tříd přidružených k formuláři pro povolení datové vazby; každý případ prezentuje třídu, která implementuje rozhraní, které umožňuje interakci s daty. Nástroje pro návrh dat pro vývoj aplikací pro Visual Studio Rapid (RAD) už tuto funkci využívají.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Rozhraní pro implementaci autory zdrojů dat

Následující rozhraní jsou navržena tak, aby byla využívána model Windows Formsmi ovládacími prvky:

- rozhraní <xref:System.Collections.IList>

  Třída, která implementuje rozhraní <xref:System.Collections.IList>, by mohla být <xref:System.Array>, <xref:System.Collections.ArrayList> nebo <xref:System.Collections.CollectionBase>. Jedná se o indexované seznamy položek typu <xref:System.Object>. Tyto seznamy musí obsahovat homogenní typy, protože první položka indexu Určuje typ. <xref:System.Collections.IList> bude k dispozici pro vazbu pouze v době běhu.

  > [!NOTE]
  > Pokud chcete vytvořit seznam obchodních objektů pro vazbu s model Windows Forms, měli byste zvážit použití <xref:System.ComponentModel.BindingList%601>. @No__t-0 je rozšiřitelná třída, která implementuje primární rozhraní požadovaná pro obousměrnou model Windows Forms datovou vazbu.

- rozhraní <xref:System.ComponentModel.IBindingList>

  Třída, která implementuje rozhraní <xref:System.ComponentModel.IBindingList>, poskytuje mnohem vyšší úroveň funkcí datové vazby. Tato implementace nabízí základní možnosti řazení a oznámení o změně, pro kdy se změní položky seznamu (například třetí položka v seznamu zákazníků má změnu v poli adresa) a také při změně samotného seznamu (například počet položek v seznamu se zvětšuje nebo zmenšuje). Oznámení o změně je důležité, pokud máte v plánu mít více ovládacích prvků vázaných na stejná data a chcete, aby se změny dat provedené v jednom z ovládacích prvků rozšířily do dalších vázaných ovládacích prvků.

  > [!NOTE]
  > Oznámení o změně je povoleno pro rozhraní @no__t 0 prostřednictvím vlastnosti <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A>, která při `true` vyvolává událost <xref:System.ComponentModel.IBindingList.ListChanged>, což značí, že se seznam změnil nebo se změnila položka v seznamu.

  Typ změny je popsán vlastností <xref:System.ComponentModel.ListChangedType> parametru <xref:System.ComponentModel.ListChangedEventArgs>. Všechny závislé pohledy, jako jsou například jiné ovládací prvky vázané na stejný zdroj dat, budou proto aktualizovány také v případě, že dojde k aktualizaci datového modelu. Objekty, které jsou obsaženy v seznamu, ale budou muset upozorňovat seznam, když se změní, takže seznam může vyvolat událost <xref:System.ComponentModel.IBindingList.ListChanged>.

  > [!NOTE]
  > @No__t-0 poskytuje obecnou implementaci rozhraní <xref:System.ComponentModel.IBindingList>.

- rozhraní <xref:System.ComponentModel.IBindingListView>

  Třída, která implementuje rozhraní <xref:System.ComponentModel.IBindingListView>, poskytuje všechny funkce implementace <xref:System.ComponentModel.IBindingList> a také filtrování a pokročilé funkce řazení. Tato implementace nabízí filtrování založené na řetězcích a více sloupců s páry popisovačů vlastností.

- rozhraní <xref:System.ComponentModel.IEditableObject>

  Třída, která implementuje rozhraní @no__t 0, umožňuje objektu řídit, kdy jsou změny tohoto objektu provedeny trvalé. Tato implementace vám poskytuje metody <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>, které umožňují vrátit zpět změny provedené v objektu. Následuje stručný popis fungování metod <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> a o tom, jak fungují vzájemně společně, aby bylo možné vrátit změny provedené v datech:

  - Metoda <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> signalizuje začátek úprav objektu. Objekt, který implementuje toto rozhraní, bude muset ukládat jakékoli aktualizace po volání metody <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> takovým způsobem, že aktualizace mohou být zahozeny, pokud je volána metoda <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>. V model Windows Forms vázání dat můžete v rámci jedné úpravy transakce několikrát volat <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> (například <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). Implementace <xref:System.ComponentModel.IEditableObject> by měly sledovat, zda <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> již bylo voláno a ignorovat následná volání <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Vzhledem k tomu, že tuto metodu lze volat víckrát, je důležité, aby následné volání na ni byla nedestruktivní; To znamená, že následné volání <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> nemohou zničit aktualizace, které byly provedeny, nebo změnit data, která byla uložena při prvním volání <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>.

  - Metoda <xref:System.ComponentModel.IEditableObject.EndEdit%2A> vloží všechny změny od volání <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> do podkladového objektu, pokud je objekt aktuálně v režimu úprav.

  - Metoda <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> zahodí všechny změny provedené v objektu.

  Další informace o tom, jak fungují metody <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> a <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>, najdete v tématu [uložení dat zpět do databáze](/visualstudio/data-tools/save-data-back-to-the-database).

  Tento transakční pojem datových funkcí se používá v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.

- rozhraní <xref:System.ComponentModel.ICancelAddNew>

  Třída, která implementuje rozhraní <xref:System.ComponentModel.ICancelAddNew> obvykle implementuje rozhraní <xref:System.ComponentModel.IBindingList> a umožňuje vrátit zpět dodatečnou hodnotu ke zdroji dat pomocí metody <xref:System.ComponentModel.IBindingList.AddNew%2A>. Pokud váš zdroj dat implementuje rozhraní <xref:System.ComponentModel.IBindingList>, měli byste také implementovat rozhraní <xref:System.ComponentModel.ICancelAddNew>.

- rozhraní <xref:System.ComponentModel.IDataErrorInfo>

  Třída, která implementuje rozhraní <xref:System.ComponentModel.IDataErrorInfo> umožňuje objektům nabízet vlastní informace o chybách vázaným ovládacím prvkům:

  - Vlastnost <xref:System.ComponentModel.IDataErrorInfo.Error%2A> vrací obecný text chybové zprávy (například "došlo k chybě").

  - Vlastnost <xref:System.ComponentModel.IDataErrorInfo.Item%2A> vrátí řetězec se specifickou chybovou zprávou ze sloupce (například "hodnota ve sloupci `State` je neplatná").

- rozhraní <xref:System.Collections.IEnumerable>

  Třída, která implementuje rozhraní @no__t 0, je obvykle spotřebovaná pomocí ASP.NET. Podpora model Windows Forms pro toto rozhraní je k dispozici pouze prostřednictvím součásti <xref:System.Windows.Forms.BindingSource>.

  > [!NOTE]
  > Komponenta <xref:System.Windows.Forms.BindingSource> zkopíruje všechny položky <xref:System.Collections.IEnumerable> do samostatného seznamu pro účely vazby.

- rozhraní <xref:System.ComponentModel.ITypedList>

  Třída kolekcí, která implementuje rozhraní @no__t 0, poskytuje možnost řídit pořadí a sadu vlastností, které jsou vystaveny vázanému ovládacímu prvku.

  > [!NOTE]
  > Když implementujete metodu <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> a pole <xref:System.ComponentModel.PropertyDescriptor> nemá hodnotu null, bude poslední položka v poli popisovač vlastnosti, který popisuje vlastnost seznamu, která je dalším seznamem položek.

- rozhraní <xref:System.ComponentModel.ICustomTypeDescriptor>

  Třída, která implementuje rozhraní <xref:System.ComponentModel.ICustomTypeDescriptor>, poskytuje dynamické informace o sobě. Toto rozhraní je podobné jako <xref:System.ComponentModel.ITypedList>, ale používá se pro objekty spíše než seznamy. Toto rozhraní používá <xref:System.Data.DataRowView> k započetí schématu podkladových řádků. Jednoduchá implementace <xref:System.ComponentModel.ICustomTypeDescriptor> je poskytována třídou <xref:System.ComponentModel.CustomTypeDescriptor>.

  > [!NOTE]
  > Aby bylo možné podporovat vytváření vazeb při návrhu na typy, které implementují <xref:System.ComponentModel.ICustomTypeDescriptor>, typ musí také implementovat <xref:System.ComponentModel.IComponent> a ve formuláři existovat jako instance.

- rozhraní <xref:System.ComponentModel.IListSource>

  Třída, která implementuje rozhraní <xref:System.ComponentModel.IListSource>, umožňuje vázání na základě seznamu pro objekty, které nejsou typu list. Metoda <xref:System.ComponentModel.IListSource.GetList%2A> <xref:System.ComponentModel.IListSource> slouží k vrácení seznamu s možností vazby z objektu, který nedědí z <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> používá třída <xref:System.Data.DataSet>.

- rozhraní <xref:System.ComponentModel.IRaiseItemChangedEvents>

  Třída, která implementuje rozhraní <xref:System.ComponentModel.IRaiseItemChangedEvents> je seznam s možností vazby, který také implementuje rozhraní <xref:System.ComponentModel.IBindingList>. Toto rozhraní slouží k označení, zda váš typ vyvolá události <xref:System.ComponentModel.IBindingList.ListChanged> typu <xref:System.ComponentModel.ListChangedType.ItemChanged> prostřednictvím vlastnosti <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>.

  > [!NOTE]
  > Je nutné implementovat <xref:System.ComponentModel.IRaiseItemChangedEvents>, pokud zdroj dat poskytuje vlastnost k vypsání výše popsaného převodu události a pracuje s komponentou <xref:System.Windows.Forms.BindingSource>. V opačném případě <xref:System.Windows.Forms.BindingSource> také provede vlastnost k vypsání převodu události, což vede k nižšímu výkonu.

- rozhraní <xref:System.ComponentModel.ISupportInitialize>

  Komponenta, která implementuje rozhraní <xref:System.ComponentModel.ISupportInitialize>, využívá výhody optimalizace dávek pro nastavení vlastností a inicializaci souběžně závislých vlastností. @No__t-0 obsahuje dvě metody:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> signalizuje, že se spouští inicializace objektu.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> signalizuje, že se inicializace objektu dokončuje.

- rozhraní <xref:System.ComponentModel.ISupportInitializeNotification>

  Komponenta, která implementuje rozhraní <xref:System.ComponentModel.ISupportInitializeNotification>, implementuje také rozhraní <xref:System.ComponentModel.ISupportInitialize>. Toto rozhraní vám umožní informovat ostatní komponenty <xref:System.ComponentModel.ISupportInitialize>, které se inicializace dokončila. Rozhraní <xref:System.ComponentModel.ISupportInitializeNotification> obsahuje dva členy:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> vrátí hodnotu `boolean`, která označuje, zda je komponenta inicializována.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> nastane při volání <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>.

- rozhraní <xref:System.ComponentModel.INotifyPropertyChanged>

  Třída, která implementuje toto rozhraní, je typ, který vyvolá událost, když se změní kterákoli jeho hodnota vlastnosti. Toto rozhraní je navrženo tak, aby nahradilo vzor, který má událost změny pro každou vlastnost ovládacího prvku. Při použití v <xref:System.ComponentModel.BindingList%601> by obchodní objekt měl implementovat rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> a BindingList @ no__t-21 převede události <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> na události <xref:System.ComponentModel.BindingList%601.ListChanged> typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.

  > [!NOTE]
  > Aby mohlo dojít ke změně vazby mezi vázaným klientem a zdrojem dat, měl by váš typ zdroje vázaných dat buď implementovat rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> (upřednostňovaná), nebo můžete zadat události *propertyName*`Changed` pro vázaný typ, ale nemělo by to dělat obojí.

### <a name="interfaces-for-implementation-by-component-authors"></a>Rozhraní pro implementaci pomocí autorů součástí

Následující rozhraní jsou navržena pro využití model Windows Forms modul vázání dat:

- rozhraní <xref:System.Windows.Forms.IBindableComponent>

  Třída, která implementuje toto rozhraní, je neovládací komponenta, která podporuje datovou vazbu. Tato třída vrátí datové vazby a kontext vazby součásti prostřednictvím vlastností <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> a <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> tohoto rozhraní.

  > [!NOTE]
  > Pokud vaše komponenta dědí z <xref:System.Windows.Forms.Control>, není nutné implementovat rozhraní <xref:System.Windows.Forms.IBindableComponent>.

- rozhraní <xref:System.Windows.Forms.ICurrencyManagerProvider>

  Třída, která implementuje rozhraní <xref:System.Windows.Forms.ICurrencyManagerProvider>, je komponenta, která poskytuje vlastní <xref:System.Windows.Forms.CurrencyManager> ke správě vazeb přidružených k této konkrétní komponentě. Přístup k vlastnímu <xref:System.Windows.Forms.CurrencyManager> poskytuje vlastnost <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>.

  > [!NOTE]
  > Třída, která dědí z <xref:System.Windows.Forms.Control> spravuje vazby automaticky prostřednictvím vlastnosti <xref:System.Windows.Forms.Control.BindingContext%2A>, takže případy, kdy je nutné implementovat <xref:System.Windows.Forms.ICurrencyManagerProvider>, jsou poměrně zřídka.

## <a name="see-also"></a>Viz také:

- [Datové vazby a Windows Forms](data-binding-and-windows-forms.md)
- [Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
