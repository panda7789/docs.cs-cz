---
title: 'Postupy: Připojení k datům XML použitím objektu XMLDataProvider a dotazů XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: bb8eb727fb6614440721c4d34a7d1828182d2f14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Postupy: Připojení k datům XML použitím objektu XMLDataProvider a dotazů XPath
Tento příklad ukazuje, jak vytvořit vazbu na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] dat pomocí <xref:System.Windows.Data.XmlDataProvider>.  
  
 S <xref:System.Windows.Data.XmlDataProvider>, základní data, která je přístupná prostřednictvím datové vazby v aplikaci může být jakékoli stromu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] uzlů. Jinými slovy <xref:System.Windows.Data.XmlDataProvider> nabízí pohodlný způsob, jak používat všechny stromu [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] uzly jako zdroj vazby.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je vložených data přímo jako [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *data island* v rámci <xref:System.Windows.FrameworkElement.Resources%2A> části. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Data island musí být uzavřen do `<x:XData>` značky a mít vždy jediném kořenovém uzlu, který je *inventáře* v tomto příkladu.  
  
> [!NOTE]
>  Kořenový uzel [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] má data **xmlns** atribut, který nastaví [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] oboru názvů na prázdný řetězec. Jde o požadavek použití dotazů XPath pro island data, která je ve vloženém [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky. V tomto případě vložené [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a proto dědí island dat, <xref:System.Windows> oboru názvů. Z toho důvodu je nutné nastavit obor názvů prázdné zabránit dotazů XPath se kvalifikovaný <xref:System.Windows> názvů, který by přesměruje dotazy.  
  
 [!code-xaml[XMLDataSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak je znázorněno v tomto příkladu, vytvořit stejnou deklaraci vazby v syntaxi atribut musíte použít řídící zvláštní znaky správně. Další informace najdete v tématu [znakové entity XML a jazyk XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md).  
  
 <xref:System.Windows.Controls.ListBox> Následující položky se zobrazí, když se spustí v tomto příkladu. Jedná se o *název*s všech elementů v rámci *knihy* s buď *Stock* hodnotu "*se*" nebo *číslo* hodnotu 3 nebo větší než nebo rovno na 8. Všimněte si, že žádné *CD* položky se vrátí, protože <xref:System.Windows.Data.XmlDataProvider.XPath%2A> hodnotu sadu na <xref:System.Windows.Data.XmlDataProvider> označuje pouze *knihy* elementy by měly být vystaveny (v podstatě nastavení filtru).  
  
 ![Příklad XPath](../../../../docs/framework/wpf/data/media/xpathexample.PNG "XPathExample")  
  
 V tomto příkladu se zobrazí názvů knih, protože <xref:System.Windows.Data.Binding.XPath%2A> z <xref:System.Windows.Controls.TextBlock> vazby ve <xref:System.Windows.DataTemplate> je nastaven na "*název*". Pokud chcete zobrazit hodnotu atributu, jako *ISBN*, byste měli nastavit, <xref:System.Windows.Data.Binding.XPath%2A> hodnotu "`@ISBN`".  
  
 **XPath** vlastnosti v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XmlNode.SelectNodes metoda zpracovává. Můžete upravit **XPath** dotazy získat odlišné výsledky. Zde jsou některé příklady pro <xref:System.Windows.Data.Binding.XPath%2A> dotaz na vázaného <xref:System.Windows.Controls.ListBox> z předchozího příkladu:  
  
-   `XPath="Book[1]"` Vrátí první prvek adresáře ("XML v akci"). Všimněte si, že **XPath** indexy jsou založené na 1, není 0.  
  
-   `XPath="Book[@*]"` Vrátí všechny elementy kniha s žádné atributy.  
  
-   `XPath="Book[last()-1]"` Vrátí druhou na posledním elementem adresáře ("představení Microsoft .NET").  
  
-   `XPath="*[position()>3]"` Vrátí všechny prvky kniha s výjimkou první 3.  
  
 Při spuštění **XPath** dotaz vrátí <xref:System.Xml.XmlNode> nebo seznam XmlNodes –. <xref:System.Xml.XmlNode> je [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekt, což znamená, můžete použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost pro vazbu [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnosti. Podívejte se na předchozí příklad znovu. Pokud zbytek příklad zůstává stejný a můžete změnit <xref:System.Windows.Controls.TextBlock> vytvoření vazby na následující, se zobrazí názvy vrácený XmlNodes – v <xref:System.Windows.Controls.ListBox>. V takovém případě je název všech vrácený uzlů "*kniha*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 V některých aplikacích vložení [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jako island data v rámci zdroj [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka může být nepohodlná, protože přesný obsah dat musí být známo v době kompilace. Proto se dá získat data z externího [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] také podporovány jsou soubory, jako v následujícím příkladu:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Pokud [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data se nachází ve vzdálené [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] souboru, můžete nadefinovat přístup k datům přiřazením odpovídající [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] k <xref:System.Windows.Data.XmlDataProvider.Source%2A> atribut následujícím způsobem:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.ObjectDataProvider>  
 [Vytvoření vazby k XDocument, XElement nebo LINQ pro výsledky XQuery](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)  
 [Použití vzoru seznam-podrobnosti s hierarchickými daty XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
