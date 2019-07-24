---
title: Přehled zdrojů připojení
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: 9bb77146a55bae4aed17bdd3ef48eca7890d4807
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401447"
---
# <a name="binding-sources-overview"></a>Přehled zdrojů připojení
V datové vazbě odkazuje zdrojový objekt vazby na objekt, ze kterého získáváte data. Toto téma popisuje typy objektů, které lze použít jako zdroj vazby.  

<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>Vytváření vazeb typů zdrojů  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]datová vazba podporuje následující typy zdrojů vazby:  
  
|Zdroj vazby|Popis|  
|--------------------|-----------------|  
|objekty modulu CLR (Common Language Runtime)|Můžete vytvořit vazby na veřejné vlastnosti, dílčí vlastnosti i indexery libovolného objektu modulu CLR (Common Language Runtime). Modul vazby používá reflexi CLR k získání hodnot vlastností. Alternativně objekty, které <xref:System.ComponentModel.ICustomTypeDescriptor> implementují nebo mají <xref:System.ComponentModel.TypeDescriptionProvider> zaregistrované, pracují i s modulem vazby.<br /><br /> Další informace o tom, jak implementovat třídu, která může sloužit jako zdroj vazby, naleznete v části [implementace třídy pro zdroj vazby](#classes) dále v tomto tématu.|  
|dynamické objekty|Můžete vytvořit <xref:System.Dynamic.IDynamicMetaObjectProvider> propojení s dostupnými vlastnostmi a indexery objektu, který implementuje rozhraní. Pokud máte přístup ke členu v kódu, můžete k němu navazovat vazby. Například pokud dynamický objekt umožňuje přístup ke členu v kódu prostřednictvím `someObjet.AProperty`, můžete k němu vytvořit vazbu nastavením cesty vazby na. `AProperty`|  
|Objekty ADO.NET|Můžete vytvořit propojení s objekty ADO.NET, například <xref:System.Data.DataTable>. <xref:System.Data.DataView> ADO.NET<xref:System.ComponentModel.IBindingList> implementuje rozhraní, které poskytuje oznámení o změně, pro které modul vazby naslouchá.|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]objekty|Můžete vytvořit vazby na a spustit `XPath` dotazy <xref:System.Xml.XmlNode>na, <xref:System.Xml.XmlDocument>nebo <xref:System.Xml.XmlElement>. Pohodlný způsob, jak získat [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] přístup k datům, která jsou zdrojem vazby v kódu, je <xref:System.Windows.Data.XmlDataProvider> použití objektu. Další informace najdete v tématu [vazba na data XML pomocí dotazů XmlDataProvider a XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Můžete také vytvořit vazby na <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>nebo vytvořit vazby k výsledkům dotazů spouštěných na objektech těchto typů pomocí LINQ to XML. Pohodlný způsob, jak použít LINQ to XML k přístupu k datům XML, která jsou zdrojem vazby v kódu, je použití <xref:System.Windows.Data.ObjectDataProvider> objektu. Další informace naleznete v tématu [vazba na XDocument, XElement nebo LINQ pro výsledky dotazu XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|<xref:System.Windows.DependencyObject>objekty|Můžete vytvořit vazby na vlastnosti závislosti libovolného <xref:System.Windows.DependencyObject>. Příklad naleznete v tématu [vazba vlastností dvou ovládacích prvků](how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>Implementace třídy pro zdroj vazby  
 Můžete vytvořit vlastní zdroje vazeb. Tato část popisuje kroky, které potřebujete znát, Pokud implementujete třídu, která bude sloužit jako zdroj vazby.  
  
### <a name="providing-change-notifications"></a>Poskytování oznámení o změnách  
 Pokud používáte buď <xref:System.Windows.Data.BindingMode.OneWay> vazbu nebo <xref:System.Windows.Data.BindingMode.TwoWay> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (protože chcete aktualizovat, když se dynamicky mění vlastnosti zdroje vazby), musíte implementovat vhodný mechanismus pro oznamování změněných vlastností. Doporučeným mechanismem je CLR nebo Dynamická třída k implementaci <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [implementace oznámení změny vlastností](how-to-implement-property-change-notification.md).  
  
 Vytvoříte-li objekt CLR, který není implementován <xref:System.ComponentModel.INotifyPropertyChanged>, je třeba uspořádat do vlastního systému oznámení, aby se zajistilo, že data použitá ve vazbě zůstanou aktuální. Můžete poskytnout oznámení o změnách tím, že `PropertyChanged` budete podporovat vzor každé vlastnosti, pro kterou chcete změnit oznámení. Pro podporu tohoto modelu definujete událost *PropertyName*změněné pro každou vlastnost, kde *PropertyName* je název vlastnosti. Událost vyvoláte pokaždé, když se změní vlastnost.  
  
 Pokud váš zdroj vazby implementuje jeden z těchto mechanismů oznámení, k cílovým aktualizacím dochází automaticky. Pokud z nějakého důvodu váš zdroj vazby neposkytne správnou vlastnost s upozorněním na změnu, máte možnost použít <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> metodu k explicitní aktualizaci cílové vlastnosti.  
  
### <a name="other-characteristics"></a>Další vlastnosti  
 Následující seznam uvádí další důležité body, které je třeba vzít v paměti:  
  
- Chcete-li vytvořit objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nástroji, třída musí mít konstruktor bez parametrů. V některých [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)] jazycích, například C#, může být konstruktor bez parametrů vytvořen za vás.  
  
- Vlastnosti, které slouží jako vazba vlastností zdroje pro vazbu, musí být veřejné vlastnosti vaší třídy. K explicitně definovaným vlastnostem rozhraní nelze přihlašovat pro účely vazby, ani k chráněným, privátním, interním nebo virtuálním vlastnostem, které nemají žádnou základní implementaci.  
  
- Nelze vytvořit propojení s veřejnými poli.  
  
- Typ vlastnosti deklarované ve vaší třídě je typ, který se předává vazbě. Typ, který je nakonec použit vazbou, však závisí na typu vlastnosti target vazby, nikoli na vlastnosti zdroje vazby. Pokud existuje rozdíl v typu, může být vhodné napsat převaděč, který bude zpracovávat, jak je vaše vlastní vlastnost do vazby původně předána. Další informace naleznete v tématu <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>Použití celých objektů jako zdroje vazby  
 Můžete použít celý objekt jako zdroj vazby. Můžete zadat zdroj vazby pomocí <xref:System.Windows.Data.Binding.Source%2A> <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnosti nebo a pak zadat prázdnou deklaraci vazby: `{Binding}`. Scénáře, ve kterých je to užitečné, zahrnují vazbu na objekty, které jsou typu String, vazba na objekty s více vlastnostmi, které vás zajímají, nebo vázání na objekty kolekce. Příklad vazby na celý objekt kolekce najdete v tématu [použití vzoru hlavní-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Všimněte si, že možná budete muset použít vlastní logiku, aby data byla smysluplná na vlastnost cíle vazby. Vlastní logika může být ve formě vlastního převaděče (pokud převod výchozího typu neexistuje) nebo <xref:System.Windows.DataTemplate>. Další informace o převaděčích naleznete v části převod dat v tématu [Přehled datových vazeb](data-binding-overview.md). Další informace o datových šablonách najdete v tématu [Přehled šablonování dat](data-templating-overview.md).  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>Použití objektů kolekce jako zdroje vazby  
 Často objekt, který chcete použít jako zdroj vazby, je kolekce vlastních objektů. Každý objekt slouží jako zdroj pro jednu instanci opakované vazby. Například můžete mít `CustomerOrders` kolekci, která se skládá z `CustomerOrder` objektů, kde vaše aplikace provádí iteraci v kolekci za účelem zjištění, kolik objednávek existuje a data obsažená v každém z nich.  
  
 Můžete vytvořit výčet pro libovolnou kolekci, která implementuje <xref:System.Collections.IEnumerable> rozhraní. Chcete-li však nastavit dynamické vazby tak, aby se vložení nebo odstranění v kolekci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automaticky aktualizovalo, kolekce musí <xref:System.Collections.Specialized.INotifyCollectionChanged> implementovat rozhraní. Toto rozhraní zpřístupňuje událost, která musí být vyvolána při každé změně příslušné kolekce.  
  
 Třída je vestavěnou implementací kolekce dat, která <xref:System.Collections.Specialized.INotifyCollectionChanged> zpřístupňuje rozhraní. <xref:System.Collections.ObjectModel.ObservableCollection%601> Jednotlivé datové objekty v kolekci musí splňovat požadavky popsané v předchozích částech. Příklad najdete v tématu [Vytvoření a vytvoření vazby na kolekci ObservableCollection](how-to-create-and-bind-to-an-observablecollection.md). Před <xref:System.Collections.ObjectModel.ObservableCollection%601> implementací vlastní kolekce zvažte použití nebo jednu z existujících tříd kolekce, <xref:System.Collections.Generic.List%601>například, <xref:System.Collections.ObjectModel.Collection%601>a <xref:System.ComponentModel.BindingList%601>, mezi mnoho dalších.  
  
 WPF se nikdy neváže přímo ke kolekci. Pokud zadáte kolekci jako zdroj vazby, WPF se ve skutečnosti připojí k výchozímu zobrazení kolekce. Informace o výchozích zobrazeních najdete v tématu [Přehled datových vazeb](data-binding-overview.md).  
  
 Pokud máte pokročilý scénář a chcete implementovat vlastní kolekci, zvažte použití <xref:System.Collections.IList> rozhraní. <xref:System.Collections.IList>poskytuje neobecnou kolekci objektů, které mohou být jednotlivě dostupné pomocí indexu, což může zlepšit výkon.  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>Požadavky na oprávnění v datové vazbě  
 Při vytváření datových vazeb je nutné vzít v úvahu úroveň důvěryhodnosti aplikace. Následující tabulka shrnuje, k jakým typům vlastností lze navázat v aplikaci, která je spouštěna buď s úplným vztahem důvěryhodnosti, nebo s částečným vztahem důvěryhodnosti:  
  
|Typ vlastnosti<br /><br /> (všechny modifikátory přístupu)|Vlastnost dynamického objektu|Vlastnost dynamického objektu|Vlastnost CLR|Vlastnost CLR|Vlastnost závislosti|Vlastnost závislosti|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**Úroveň důvěryhodnosti**|**Úplný vztah důvěryhodnosti**|**Částečná důvěryhodnost**|**Úplný vztah důvěryhodnosti**|**Částečná důvěryhodnost**|**Úplný vztah důvěryhodnosti**|**Částečná důvěryhodnost**|  
|Veřejná třída|Ano|Ano|Ano|Ano|Ano|Ano|  
|Neveřejná třída|Ano|Ne|Ano|Ne|Ano|Ano|  
  
 Tato tabulka popisuje následující důležité body týkající se požadavků oprávnění v datové vazbě:  
  
- U vlastností CLR funguje vazba dat za předpokladu, že modul vazby je schopný získat přístup k vlastnosti zdroje vazby pomocí reflexe. V opačném případě modul vazby vydá upozornění, že vlastnost nelze nalézt a používá záložní hodnotu nebo výchozí hodnotu, pokud je k dispozici.  
  
- Můžete vytvořit vazby na vlastnosti dynamických objektů, které jsou definovány v době kompilace nebo v době spuštění.  
  
- Vždy je možné vytvořit vazby na vlastnosti závislosti.  
  
 Požadavek na oprávnění pro [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] vazbu je podobný. V izolovaném prostoru (sandboxu <xref:System.Windows.Data.XmlDataProvider> ) s částečnou důvěryhodností dojde k chybě, pokud nemá oprávnění pro přístup k zadaným datům.  
  
 Objekty s anonymním typem jsou interní. Můžete vytvořit propojení s vlastnostmi anonymních typů pouze v případě, že běží v úplném vztahu důvěryhodnosti. Další informace o anonymních typech naleznete v tématu [anonymní typyC# (Průvodce programování)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md) nebo [anonymní typy (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).  
  
 Další informace o zabezpečení s částečným vztahem důvěryhodnosti najdete v tématu věnovaném [zabezpečení částečné důvěryhodnosti WPF](../wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [Určení zdroje vazby](how-to-specify-the-binding-source.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
- [Přehled datové vazby WPF s LINQ to XML](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [Datová vazba](../advanced/optimizing-performance-data-binding.md)
