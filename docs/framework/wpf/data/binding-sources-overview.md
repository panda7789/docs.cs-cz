---
title: "Přehled zdrojů připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88f1a22fc15e85e687c7b7eeb0a6e01445277d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="binding-sources-overview"></a>Přehled zdrojů připojení
V datové vazbě zdrojového objektu vazby odkazuje na objekt, který je získat data z. Toto téma popisuje typy objektů, které můžete použít jako zdroj vazby.  
  
  
  
<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>Typy zdrojů vazby  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Datová vazba podporuje následující typy zdrojů vazby:  
  
|Vytvoření vazby zdroje|Popis|  
|--------------------|-----------------|  
|[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]objekty|Můžete vázat na veřejné vlastnosti, dílčí vlastnosti, jakož i indexery všech [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objektu. Modul vazba používá [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] reflexe k získání hodnoty vlastnosti. Případně, které implementují objekty <xref:System.ComponentModel.ICustomTypeDescriptor> nebo registrovaný <xref:System.ComponentModel.TypeDescriptionProvider> také práci s modulem vazby.<br /><br /> Další informace o tom, jak implementovat třídu, která může sloužit jako zdroj vazby najdete v tématu [implementaci třídy zdroje vazba](#classes) dál v tomto tématu.|  
|dynamické objekty|Můžete vázat na k dispozici vlastnostmi a indexery objekt, který implementuje <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. Pokud máte přístup člen v kódu, můžete vázat na ni. Například, pokud dynamický objekt umožňuje přístup ke členu v kódu pomocí `someObjet.AProperty`, lze navázat na nastavením cestu vazby na `AProperty`.|  
|[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)]objekty|Můžete vázat na [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] objekty, jako například <xref:System.Data.DataTable>. [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] <xref:System.Data.DataView> Implementuje <xref:System.ComponentModel.IBindingList> rozhraní, která obsahuje oznámení o změnách, které modul vazby naslouchá.|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]objekty|Můžete vytvořit vazbu k a spustit `XPath` dotazuje na <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument>, nebo <xref:System.Xml.XmlElement>. Pohodlný způsob pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data, která je zdrojem vazby v kódu se má používat <xref:System.Windows.Data.XmlDataProvider> objektu. Další informace najdete v tématu [vazby na Data XML pomocí služby XMLDataProvider a dotazy jazyka XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Také můžete vázat na <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>, nebo vytvořit vazbu na výsledky dotazů, spusťte na objekty z těchto typů pomocí technologie LINQ to XML. Pohodlný způsob, jak používat technologie LINQ to XML pro přístup k datům XML, který je zdrojem vazby v kódu se má používat <xref:System.Windows.Data.ObjectDataProvider> objektu. Další informace najdete v tématu [vytvořit vazbu na XDocument, XElement nebo LINQ na výsledky dotazu XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|<xref:System.Windows.DependencyObject>objekty|Můžete vázat na závislost propertiesof žádné <xref:System.Windows.DependencyObject>. Příklad, naleznete v části [vazby vlastnosti dva prvky](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>Implementace třídy zdroje vazby  
 Můžete vytvořit vlastní vazby zdroje. Tato část popisuje, co potřebujete vědět, pokud jsou implementaci třídy sloužit jako zdroj vazby.  
  
### <a name="providing-change-notifications"></a>Poskytuje oznámení změn  
 Pokud používáte buď <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> vazba (protože chcete, aby vaše [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aktualizovat při změně vlastnosti zdroje vazba dynamicky), musí implementovat změněné vlastnosti vhodný mechanismus oznámení. Je doporučené mechanismus pro [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nebo dynamické třídu pro implementaci <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [oznámení o změně vlastnost implementace](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 Pokud vytvoříte [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt, který neimplementuje <xref:System.ComponentModel.INotifyPropertyChanged>, pak musí zajistit, aby vlastní oznámení systému a ujistěte se, že data použitá ve vazbě zůstává aktuální. Díky podpoře můžete poskytnout oznámení o změnách `PropertyChanged` vzor pro každou vlastnost, která chcete oznámení o změně. Tento vzor podporovat, můžete definovat *PropertyName*změněno událost pro každou vlastnost, kde *PropertyName* je název vlastnosti. Můžete vyvolat událost pokaždé, když se změní vlastnost.  
  
 Pokud vaše zdrojová vazba implementuje jednoho z těchto mechanismů oznámení, zacílením aktualizací dojít automaticky. Pokud z nějakého důvodu vaše zdrojová vazba neposkytuje vlastnost správné změnili oznámení, máte možnost k použití <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> metoda explicitně aktualizovat vlastnost target.  
  
### <a name="other-characteristics"></a>Dalších vlastností  
 Následující seznam uvádí další důležité si uvědomit:  
  
-   Pokud chcete vytvořit objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], třídu musí mít výchozí konstruktor. V některých [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)] jazyky, jako například [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], výchozí konstruktor může vytvořit za vás.  
  
-   Vlastnosti, je použít jako vazby vlastnosti zdroje pro vazbu musí být veřejné vlastnosti vaší třídy. Vlastnosti explicitně definovaných rozhraní nejsou přístupné pro účely vazby, ani můžete chráněný, privátní, interní nebo virtuální vlastností, které nemají základní implementaci.  
  
-   Nelze vytvořit vazbu na veřejná pole.  
  
-   Typ vlastnosti deklarovaná ve třídě je typ, který je předán vazby. Typ výsledku používané vazby však závisí na typu vlastnosti cílového vazby, ne zdrojová vlastnost vazby. Pokud je rozdíl v typu, můžete chtít zápisu převaděč pro zpracování, jak vaše vlastní vlastnost původně předaný vazby. Další informace naleznete v tématu <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>Pomocí celé objekty jako zdroj vazby  
 Celý objekt můžete použít jako zdroj vazby. Zdroj vazby můžete zadat pomocí <xref:System.Windows.Data.Binding.Source%2A> nebo <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost a pak zadejte deklaraci prázdné vazby: `{Binding}`. Scénáře, ve kterých to je užitečné zahrnout vazby na objekty, které jsou typu řetězec, vytvoření vazby na objekty s více vlastností, které vás zajímají nebo vytvoření vazby na objekty kolekce. Příklad vazby na objekt celou kolekci, naleznete v části [použití vzoru seznam-podrobnosti s hierarchické Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Všimněte si, že budete muset použít vlastní logiku, aby byla data smysl vázané cílovou vlastnost. Vlastní logika může být ve tvaru vlastního převaděče (Pokud je výchozí typ převodu neexistuje) nebo <xref:System.Windows.DataTemplate>. Další informace o převaděče, najdete v části převod dat [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md). Další informace o šablonách dat najdete v tématu [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>Používání kolekce objektů jako zdroj vazby  
 Objekt, který chcete použít jako zdroj vazby často je kolekce vlastních objektů. Každý objekt slouží jako zdroj pro jednu instanci opakovaných vazby. Například můžete mít `CustomerOrders` kolekce, která se skládá z `CustomerOrder` objekty, které vaše aplikace iteruje nad kolekce k určení, kolik objednávky existují a data obsažená v každém.  
  
 Můžete vytvořit výčet přes jakoukoli kolekci, která implementuje <xref:System.Collections.IEnumerable> rozhraní. Ale nastavit dynamické vazby tak, aby vložení nebo odstranění v kolekci aktualizovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automaticky, kolekce musí implementovat <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Toto rozhraní zpřístupní událost, která musí být vyvolány při každé změně zdrojové kolekce.  
  
 <xref:System.Collections.ObjectModel.ObservableCollection%601> Třída je implementace předdefinované shromažďování dat, která zveřejňuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Jednotlivé datové objekty v kolekci musí splňovat požadavky popsané v předchozí části. Příklad, naleznete v části [vytvořit a vytvořit vazbu ObservableCollection](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md). Před implementací vlastní kolekce, zvažte použití <xref:System.Collections.ObjectModel.ObservableCollection%601> nebo jeden z existující kolekci třídy, jako například <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, a <xref:System.ComponentModel.BindingList%601>, mezi mnohé další.  
  
 WPF nikdy váže přímo do kolekce. Pokud zadáte kolekci jako zdroj vazby, WPF ve skutečnosti sváže kolekce výchozí zobrazení. Informace o výchozích zobrazeních najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Pokud máte složitější scénář a chcete implementovat vlastní kolekci, zvažte použití <xref:System.Collections.IList> rozhraní. <xref:System.Collections.IList>poskytuje neobecnou kolekci objektů, které může být index individuálně získávat přístup, což může zlepšit výkon.  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>Požadavky na oprávnění v datová vazba  
 Po vytvoření vazby dat, musíte zvážit úroveň důvěryhodnosti aplikace. Následující tabulka shrnuje vlastnost, jaké typy mohou být vázány na v aplikaci, která spouští v režimu plné důvěryhodnosti nebo částečné důvěryhodnosti:  
  
|Typ vlastnosti<br /><br /> (všechny modifikátory přístupu)|Vlastnost dynamických objektů|Vlastnost dynamických objektů|Vlastnost CLR|Vlastnost CLR|Vlastnost závislosti|Vlastnost závislosti|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**Úroveň důvěryhodnosti**|**Úplný vztah důvěryhodnosti**|**Částečná důvěryhodnost**|**Úplný vztah důvěryhodnosti**|**Částečná důvěryhodnost**|**Úplný vztah důvěryhodnosti**|**Částečná důvěryhodnost**|  
|Veřejná třída|Ano|Ano|Ano|Ano|Ano|Ano|  
|Není veřejné – třída|Ano|Ne|Ano|Ne|Ano|Ano|  
  
 Tato tabulka popisuje následující důležité skutečnosti o požadavky na oprávnění v datové vazby:  
  
-   Pro [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti datové vazby funguje tak dlouho, dokud modul vazba je mít přístup k vlastnosti Zdroj vazbu pomocí reflexe. Modul vazbu, jinak hodnota vydá upozornění, která vlastnost nebyla nalezena a používá záložní hodnotu nebo výchozí hodnotu, pokud je k dispozici.  
  
-   Můžete vázat na vlastnosti u dynamických objektů, které jsou definovány v kompilaci čas nebo dobu spuštění.  
  
-   Vždy můžete vázat na vlastnosti závislosti.  
  
 Požadavek na oprávnění pro [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] vazba je podobné. V izolovaném prostoru částečným vztahem důvěryhodnosti <xref:System.Windows.Data.XmlDataProvider> selže, pokud nemá oprávnění pro přístup k zadaná data.  
  
 Objekty anonymního typu jsou interní. Můžete vázat na vlastnosti anonymní typy jenom v případě, že je spuštěna v režimu plné důvěryhodnosti. Další informace o anonymních typech najdete v tématu [anonymní typy (C# Průvodce programováním)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md) nebo [anonymní typy (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).  
  
 Další informace o částečným vztahem důvěryhodnosti zabezpečení najdete v tématu [WPF částečné důvěryhodnosti zabezpečení](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.ObjectDataProvider>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [Určení zdroje vazby](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Přehled datové vazby WPF s LINQ to XML](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
