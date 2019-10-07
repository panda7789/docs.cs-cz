---
title: 'Postupy: Připojení k datům XML použitím objektu XMLDataProvider a dotazů XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: d92b01c453a9e07a5d4a6d1900d54e8c86210041
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005691"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Postupy: Připojení k datům XML použitím objektu XMLDataProvider a dotazů XPath
Tento příklad ukazuje, jak vytvořit vazby na data [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] pomocí <xref:System.Windows.Data.XmlDataProvider>.  
  
 Pomocí <xref:System.Windows.Data.XmlDataProvider> mohou být podkladová data, ke kterým lze přicházet prostřednictvím datové vazby ve vaší aplikaci, libovolného stromu uzlů [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Jinými slovy <xref:System.Windows.Data.XmlDataProvider> poskytuje pohodlný způsob použití jakéhokoli stromu uzlů [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] jako zdroje vazby.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou data vložena přímo jako *datový ostrůvek* [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] v části <xref:System.Windows.FrameworkElement.Resources%2A>. Datový ostrůvek [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] musí být zabalen do značek `<x:XData>` a vždy mít jeden kořenový uzel, který je v tomto příkladu *inventářem* .  
  
> [!NOTE]
> Kořenový uzel dat [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] má atribut **xmlns** , který nastaví obor názvů [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] na prázdný řetězec. Toto je požadavek na použití dotazů XPath na datový ostrůvek, který je vložený na stránce [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. V tomto vloženém případě dědí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obor názvů <xref:System.Windows>. Z tohoto důvodu je třeba nastavit obor názvů jako prázdný, aby byly dotazy XPath kvalifikovány pomocí oboru názvů <xref:System.Windows>, které by mohly dotaz nesměrovat.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak ukazuje tento příklad, chcete-li vytvořit stejnou deklaraci vazby v syntaxi atributu, je nutné speciální znaky správně Escape. Další informace naleznete v tématu [znakové entity XML a XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 @No__t-0 zobrazí při spuštění tohoto příkladu následující položky. Jedná se o *název*všech prvků v *knihách* , které *mají hodnotu "* *out*" nebo *číslo* hodnoty 3 nebo větší nebo rovno 8. Všimněte si, že nejsou vráceny žádné položky *CD* , protože hodnota <xref:System.Windows.Data.XmlDataProvider.XPath%2A> nastavená na <xref:System.Windows.Data.XmlDataProvider> znamená, že by měly být vystaveny pouze prvky *Books* (v zásadě nastavení filtru).  
  
 ![Snímek obrazovky s příkladem XPath znázorňující název čtyř knih](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 V tomto příkladu se zobrazí názvy knih, protože @no__t 0 vazby <xref:System.Windows.Controls.TextBlock> v <xref:System.Windows.DataTemplate> je nastavená na "*title*". Pokud chcete zobrazit hodnotu atributu, jako je například *ISBN*, nastaví se hodnota <xref:System.Windows.Data.Binding.XPath%2A> na "`@ISBN`".  
  
 Vlastnosti **XPath** v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou zpracovávány metodou XMLNode. SelectNodes. Můžete upravit dotazy **XPath** a získat tak různé výsledky. Tady jsou některé příklady pro dotaz <xref:System.Windows.Data.Binding.XPath%2A> na vázané <xref:System.Windows.Controls.ListBox> v předchozím příkladu:  
  
- `XPath="Book[1]"` vrátí první prvek Book ("XML v akci"). Všimněte si, že indexy **XPath** jsou založené na 1, nikoli 0.  
  
- `XPath="Book[@*]"` vrátí všechny prvky knihy s libovolnými atributy.  
  
- `XPath="Book[last()-1]"` vrátí druhý k poslednímu prvku Book ("Představujeme Microsoft .NET").  
  
- `XPath="*[position()>3]"` vrátí všechny prvky knihy s výjimkou prvního 3.  
  
 Když spustíte dotaz **XPath** , vrátí <xref:System.Xml.XmlNode> nebo seznam XMLNode. <xref:System.Xml.XmlNode> je objekt modulu CLR (Common Language Runtime), což znamená, že můžete použít vlastnost <xref:System.Windows.Data.Binding.Path%2A> pro vytvoření vazby k vlastnostem CLR (Common Language Runtime). Předchozí příklad zvažte znovu. Pokud zbytek příkladu zůstává stejný a měníte <xref:System.Windows.Controls.TextBlock> vazba na následující, zobrazí se názvy vrácených XmlNode v <xref:System.Windows.Controls.ListBox>. V tomto případě je název všech vrácených uzlů "*Book*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 V některých aplikacích může být vkládání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jako datového ostrova v rámci zdroje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nepohodlné, protože přesný obsah dat musí být známý v době kompilace. Proto je také podporováno získávání dat z externího souboru [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], jak je uvedeno v následujícím příkladu:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Pokud se data [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nachází ve vzdáleném souboru [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], definovali jste přístup k datům tak, že do atributu <xref:System.Windows.Data.XmlDataProvider.Source%2A> přiřadíte příslušnou adresu URL následujícím způsobem:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.ObjectDataProvider>
- [Vytvoření vazby k XDocument, XElement nebo LINQ pro výsledky XQuery](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [Použití vzoru seznam-podrobnosti s hierarchickými daty XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Přehled zdrojů vazby](binding-sources-overview.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
