---
title: Přehled zdrojů připojení
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: fe5cb97b4802c2b638a4b218a27da05468dc50fb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505559"
---
# <a name="binding-sources-overview"></a>Přehled zdrojů připojení
V datové vazbě objekt zdroj vazby odkazuje na objekt, který je získat data z. Toto téma popisuje typy objektů, které můžete použít jako zdroj vazby.  

<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>Typ zdroje vazby  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Datová vazba podporuje následující typy zdroj vazby:  
  
|Vytvoření vazby zdroje|Popis|  
|--------------------|-----------------|  
|[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] Objekty|Můžete vázat na veřejné vlastnosti, dílčí vlastnosti, jakož i indexery žádné [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objektu. Modul vazby používá [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] reflexi k získání hodnot vlastností. Můžete také objekty, které implementují <xref:System.ComponentModel.ICustomTypeDescriptor> nebo jste registrovaný <xref:System.ComponentModel.TypeDescriptionProvider> fungovat i pro vazby.<br /><br /> Další informace o tom, jak implementovat třídu, který může sloužit jako zdroj vazby najdete v tématu [implementaci třídy pro zdroj vazby](#classes) dále v tomto tématu.|  
|dynamické objekty|Můžete vázat na dostupné vlastnostmi a indexery objekt, který implementuje <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. Pokud přistupujete můžete členské v kódu, můžete svázat do něj. Například, pokud dynamický objekt umožňuje přístup ke členu v kódu prostřednictvím `someObjet.AProperty`, můžete svázat do ní nastavením cesta vazby `AProperty`.|  
|[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] Objekty|Lze svázat objekty technologie ADO.NET, například <xref:System.Data.DataTable>. ADO.NET <xref:System.Data.DataView> implementuje <xref:System.ComponentModel.IBindingList> rozhraní, které poskytuje oznámení o změnách, které naslouchá vazby.|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] Objekty|Můžete svázat a spustit `XPath` dotazuje na <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument>, nebo <xref:System.Xml.XmlElement>. Pohodlný způsob, jak přistupovat k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data, která je zdrojem vazby v kódu, je použít <xref:System.Windows.Data.XmlDataProvider> objektu. Další informace najdete v tématu [svázání dat XML pomocí XMLDataProvider a dotazů XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Také lze svázat <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>, nebo připojení k výsledkům dotazů, spusťte na tyto typy objektů pomocí LINQ to XML. Pohodlný způsob, jak používat technologie LINQ to XML pro přístup k datům XML, který je zdrojem vazby v kódu je použít <xref:System.Windows.Data.ObjectDataProvider> objektu. Další informace najdete v tématu [připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|<xref:System.Windows.DependencyObject> Objekty|Mohl vytvořit vazbu k vlastnosti závislosti žádné <xref:System.Windows.DependencyObject>. Příklad najdete v tématu [vazby vlastností dvou ovládacích](how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>Implementace třídy pro zdroje připojení  
 Můžete vytvořit vlastní zdroje připojení. Tato část popisuje, co potřebujete vědět, Pokud implementujete třídu, která bude sloužit jako zdroj vazby.  
  
### <a name="providing-change-notifications"></a>Poskytování oznámení o změnách  
 Pokud používáte buď <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> vazby (protože chcete, aby vaše [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aktualizovat při změně vlastnosti zdroje vazby dynamicky), musíte implementovat mechanismus oznámení vhodný změněné vlastnosti. Doporučené mechanismus je určený pro [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nebo dynamické třídu pro implementaci <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [implementace oznámení změn vlastností](how-to-implement-property-change-notification.md).  
  
 Pokud jste vytvořili [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt, který neimplementuje <xref:System.ComponentModel.INotifyPropertyChanged>, pak je nutné uspořádat pro vlastní oznámení systému, abyste měli jistotu, že data používaná ve vazbě zůstane aktuální. Díky podpoře můžete zadat oznámení o změnách `PropertyChanged` vzor pro každou vlastnost, která chcete, aby oznámení o změně. Tento vzor podporovat, můžete definovat *PropertyName*změněné události pro každou vlastnost, kde *PropertyName* je název vlastnosti. Můžete vyvolat událost pokaždé, když se změní vlastnost.  
  
 Pokud váš zdroj vazby implementuje jednu z těchto mechanismů oznámení, zacílením aktualizací probíhají automaticky. Pokud z nějakého důvodu zdroj vazby neposkytuje správná vlastnost změnili oznámení, máte možnost k použití <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> metoda explicitně aktualizovat vlastnost target.  
  
### <a name="other-characteristics"></a>Další vlastnosti  
 Následující seznam uvádí další důležité si uvědomit:  
  
- Pokud chcete vytvořit objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], třídě musí mít výchozí konstruktor. V některých [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)] jazyků, jako například C#, výchozí konstruktor může vytvořit za vás.  
  
- Vlastnosti, je použít jako vazbu vlastnosti zdroje pro vazby musí být veřejné vlastnosti třídy. Vlastnosti explicitně definované rozhraní není přístupná pro účely vazby ani můžete chráněné, soukromé, interní nebo virtuální vlastnosti, které nemají základní implementaci.  
  
- Nelze vytvořit vazbu na veřejné pole.  
  
- Typ proměnné deklarované ve své třídě je typ, který je předán do vazby. Typ, takže v konečném důsledku použitý vazba však závisí na typu vazby vlastnosti cílové, nikoli vlastnosti zdroje vazby. Pokud není rozdíl v typu, můžete chtít napsat převaděč pro zpracování, jak vaši vlastní vlastnost původně předána do vazby. Další informace naleznete v tématu <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>Použití celé objekty jako zdroje vazby  
 Celý objekt slouží jako zdroj vazby. Zdrojem vazby, který můžete určit pomocí <xref:System.Windows.Data.Binding.Source%2A> nebo <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost a pak zadejte prázdnou vazby deklarace: `{Binding}`. Scénáře, ve kterých to je užitečné zahrnout vazby na objekty, které jsou typu String, vytvoření vazby na objekty s více vlastnostmi, které vás zajímají, nebo vytvoření vazby na objekty kolekce. Příklad vytvoření vazby na celou kolekci objektu, najdete v části [použití vzoru seznam-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Všimněte si, že budete muset použít vlastní logiku, aby data má smysl pro vaše vlastností cíle. Vlastní logiky může být v podobě vlastního převaděče (pokud ještě neexistuje výchozí typ převodu) nebo <xref:System.Windows.DataTemplate>. Další informace o převaděčů najdete v části převod dat z [přehled datových vazeb](data-binding-overview.md). Další informace o šablonách dat, naleznete v tématu [přehled datových šablon](data-templating-overview.md).  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>Použití objektů kolekce jako zdroje vazby  
 Objekt, který chcete použít jako zdroj vazby často, je kolekce vlastních objektů. Každý objekt slouží jako zdroj pro jednu instanci opakované vazby. Například můžete mít `CustomerOrders` kolekce, která se skládá z `CustomerOrder` objektů, kde aplikace Iteruje přes kolekci určit, kolik objednávky existují a data obsažená v každém.  
  
 Můžete zobrazit výčet přes jakoukoli kolekci, která implementuje <xref:System.Collections.IEnumerable> rozhraní. Však nastavení dynamické vazby, vložení nebo odstranění v kolekci aktualizovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automaticky, kolekce musí implementovat <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Toto rozhraní poskytuje událost, která musí být vyvolána při každé změně zdrojové kolekce.  
  
 <xref:System.Collections.ObjectModel.ObservableCollection%601> Třídy je předdefinované implementace shromažďování dat, který zpřístupňuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Jednotlivé datové objekty v kolekci musí splňovat požadavky popsané v předchozích částech. Příklad najdete v tématu [vytvoření a připojení ke kolekci ObservableCollection](how-to-create-and-bind-to-an-observablecollection.md). Před implementací vlastní kolekce, zvažte použití <xref:System.Collections.ObjectModel.ObservableCollection%601> nebo jeden z existující kolekce tříd, například <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, a <xref:System.ComponentModel.BindingList%601>, mezi mnoha dalších.  
  
 WPF nikdy vytvořena vazba přímo s kolekce. Pokud chcete zadat kolekci jako zdroj vazby, WPF skutečně vytvoří vazbu kolekce výchozí zobrazení. Informace o výchozích zobrazení najdete v tématu [přehled datových vazeb](data-binding-overview.md).  
  
 Pokud jste pokročilý scénář a chcete implementovat vlastní kolekci, zvažte použití <xref:System.Collections.IList> rozhraní. <xref:System.Collections.IList> poskytuje obecné kolekci objektů, které lze jednotlivě přistupovat pomocí indexu, což může zlepšit výkon.  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>Požadavky na oprávnění v datové vazbě  
 Při vytváření datových vazeb, musíte zvážit úroveň důvěryhodnosti aplikace. Následující tabulka shrnuje vlastnost, jaké typy mohou být vázány na aplikaci, která se spouští v úplném vztahu důvěryhodnosti nebo částečným vztahem důvěryhodnosti:  
  
|Typ vlastnosti<br /><br /> (všechny modifikátory přístupu)|Vlastnost dynamických objektů|Vlastnost dynamických objektů|Vlastnost CLR|Vlastnost CLR|Vlastnost závislosti|Vlastnost závislosti|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**Úroveň důvěryhodnosti**|**Úplný vztah důvěryhodnosti**|**Částečné důvěryhodnosti**|**Úplný vztah důvěryhodnosti**|**Částečné důvěryhodnosti**|**Úplný vztah důvěryhodnosti**|**Částečné důvěryhodnosti**|  
|Veřejná třída|Ano|Ano|Ano|Ano|Ano|Ano|  
|Neveřejné třídě|Ano|Ne|Ano|Ne|Ano|Ano|  
  
 Tato tabulka popisuje následující důležité skutečnosti týkající se požadavků na oprávnění v datové vazbě:  
  
- Pro [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti, datové vazby funguje jako modul vazby je moci přistupovat k vlastnosti zdroje vazby pomocí operace reflection. V opačném případě vazby vydá upozornění, která nebyla nalezena vlastnost a používá záložní hodnotu nebo výchozí hodnotu, pokud je k dispozici.  
  
- Můžete navázat na vlastnosti u dynamických objektů, které jsou definované při kompilaci čas nebo běhu.  
  
- Vždy můžete vázat na vlastnosti závislosti.  
  
 Požadavek na oprávnění [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] vazba je podobné. V izolovaném prostoru částečným vztahem důvěryhodnosti <xref:System.Windows.Data.XmlDataProvider> selže, pokud nemá oprávnění pro přístup k zadaná data.  
  
 Jsou vnitřní objekty anonymního typu. Vlastnosti anonymních typů lze svázat pouze při spuštění v režimu plné důvěryhodnosti. Další informace o anonymních typech najdete v tématu [anonymní typy (C# Programming Guide)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md) nebo [anonymní typy (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).  
  
 Další informace o částečným vztahem důvěryhodnosti zabezpečení najdete v tématu [částečné zabezpečení důvěryhodnosti WPF](../wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [Určení zdroje vazby](how-to-specify-the-binding-source.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
- [Přehled datové vazby WPF s LINQ to XML](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [Datová vazba](../advanced/optimizing-performance-data-binding.md)
