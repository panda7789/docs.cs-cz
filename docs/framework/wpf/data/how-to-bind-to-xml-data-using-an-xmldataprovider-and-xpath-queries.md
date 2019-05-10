---
title: 'Postupy: Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 49f32ae4f358885268044cbfd785239f537940ae
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609424"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Postupy: Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath
Tento příklad ukazuje, jak vytvořit vazbu na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data s využitím <xref:System.Windows.Data.XmlDataProvider>.  
  
 Pomocí <xref:System.Windows.Data.XmlDataProvider>, podkladová data, která je přístupná prostřednictvím datové vazby v aplikaci může být jakékoli stromu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] uzly. Jinými slovy <xref:System.Windows.Data.XmlDataProvider> poskytuje pohodlný způsob, jak používat jakékoli stromu [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] uzlů jako zdroj vazby.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, vložení dat přímo jako [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *datový ostrůvek* v rámci <xref:System.Windows.FrameworkElement.Resources%2A> oddílu. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Datový ostrůvek musí být zabalené v `<x:XData>` značek a mít jeden kořenový uzel, který je vždy *inventáře* v tomto příkladu.  
  
> [!NOTE]
>  Kořenový uzel [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data mají **xmlns** atribut, který nastaví [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] oboru názvů na prázdný řetězec. Jde o požadavek pro použití dotazy XPath, který je vložený v rámci dat ostrov [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky. V tomto případě vložené [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a proto dědí ostrov data <xref:System.Windows> oboru názvů. Z toho důvodu je potřeba nastavit obor názvů prázdné, pokud chcete zabránit dotazy jazyka XPath je kvalifikován <xref:System.Windows> obor názvů, který by přesměruje dotazy.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak je znázorněno v tomto příkladu, k vytvoření jedné vazby deklaraci v syntaxi atributu musíte před speciální znaky správně. Další informace najdete v tématu [znakové entity XML a XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 <xref:System.Windows.Controls.ListBox> Při spuštění v tomto příkladu se zobrazí následující položky. Jedná se o *název*s všech prvků v rámci *knihy* buď *akcie* hodnotu "*si*" nebo *číslo* hodnotu 3 nebo větší než nebo se rovná 8. Všimněte si, že žádné *CD* položky jsou vráceny, protože <xref:System.Windows.Data.XmlDataProvider.XPath%2A> na hodnotu set <xref:System.Windows.Data.XmlDataProvider> označuje pouze *knihy* prvky by měly být vystaveny (v podstatě nastavení filtru).  
  
 ![Snímek obrazovky příklad XPath zobrazen titulek čtyři knihy.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 V tomto příkladu se zobrazí názvů knih, protože <xref:System.Windows.Data.Binding.XPath%2A> z <xref:System.Windows.Controls.TextBlock> vazby v <xref:System.Windows.DataTemplate> je nastavena na "*Title*". Pokud chcete zobrazit hodnotu atributu, jako *ISBN*, nastavíte, který <xref:System.Windows.Data.Binding.XPath%2A> hodnota, která se "`@ISBN`".  
  
 **XPath** vlastnosti v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XmlNode.SelectNodes metoda zpracovává. Můžete upravit **XPath** dotazů získat jiné výsledky. Tady je několik příkladů, pro <xref:System.Windows.Data.Binding.XPath%2A> dotazem na je mez <xref:System.Windows.Controls.ListBox> z předchozího příkladu:  
  
- `XPath="Book[1]"` Vrátí první prvek book ("XML v akci"). Všimněte si, že **XPath** indexy jsou založeny na 1, není 0.  
  
- `XPath="Book[@*]"` Vrátí všechny knihy elementy s atributy.  
  
- `XPath="Book[last()-1]"` Vrátí druhou na poslední prvek book ("představení rozhraní Microsoft .NET").  
  
- `XPath="*[position()>3]"` Vrátí všechny knihy elementy s výjimkou první 3.  
  
 Při spuštění **XPath** dotazování, vrátí se <xref:System.Xml.XmlNode> nebo seznam XmlNodes. <xref:System.Xml.XmlNode> je [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekt, což znamená, že můžete použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost k vytvoření vazby [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnosti. Podívejte se na předchozí příklad znovu. Pokud zbytek v příkladu zůstane stejný a změníte <xref:System.Windows.Controls.TextBlock> vazby pro následující, se zobrazí názvy vrácené uzly XmlNodes v <xref:System.Windows.Controls.ListBox>. V takovém případě je název vrácená uzlů "*knihy*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 V některých aplikacích mohou vkládání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jako datový ostrůvek ve zdroji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka může být nevhodné, protože musí být znám přesný obsah data v době kompilace. Proto se získávání dat z externího [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] souboru je také podporována jako v následujícím příkladu:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Pokud [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data se nachází na vzdáleném [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] souboru byste definovali přístup k datům tak, že přiřadíte odpovídající [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] k <xref:System.Windows.Data.XmlDataProvider.Source%2A> atribut následujícím způsobem:  
  
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
