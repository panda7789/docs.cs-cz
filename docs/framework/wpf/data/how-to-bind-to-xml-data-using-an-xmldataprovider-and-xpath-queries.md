---
title: 'Postupy: Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 4833e024fcd352094a2163f11df8572aa4c241f8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944651"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Postupy: Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath
Tento příklad ukazuje, jak vytvořit propojení [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] s daty <xref:System.Windows.Data.XmlDataProvider>pomocí.  
  
 Pomocí nástroje mohou být podkladová data, ke kterým lze přistupovat prostřednictvím datové vazby ve vaší aplikaci [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ,libovolnéstromovéstrukturyuzlů.<xref:System.Windows.Data.XmlDataProvider> Jinými slovy, <xref:System.Windows.Data.XmlDataProvider> nabízí pohodlný způsob použití jakéhokoli [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] stromu uzlů jako zdroje vazby.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou data vložena přímo jako [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *datový* <xref:System.Windows.FrameworkElement.Resources%2A> ostrůvek v rámci oddílu. Datový ostrůvek musí být zabalen do `<x:XData>` značek a vždy mít jeden kořenový uzel, který je v tomto příkladu *inventářem* . [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]  
  
> [!NOTE]
> Kořenový uzel [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat má [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] atribut **xmlns** , který nastaví obor názvů na prázdný řetězec. Toto je požadavek na použití dotazů XPath na datový ostrůvek, který je vložen do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky. V tomto vloženém případě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows> dědí obor názvů a tudíž datový ostrov. Z tohoto důvodu je třeba nastavit obor názvů jako prázdný, aby byly dotazy XPath v <xref:System.Windows> oboru názvů kvalifikovány, což by mělo být dotazům příliš nasměrované.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak ukazuje tento příklad, chcete-li vytvořit stejnou deklaraci vazby v syntaxi atributu, je nutné speciální znaky správně Escape. Další informace naleznete v tématu [znakové entity XML a XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 V <xref:System.Windows.Controls.ListBox> případě spuštění tohoto příkladu se zobrazí následující položky. Jedná se o *název*všech prvků v *knihách* , které mají hodnotu "*out*" nebo *číslo* hodnoty 3 nebo větší nebo rovno 8. Všimněte si, že nejsou vráceny žádné položky CD <xref:System.Windows.Data.XmlDataProvider.XPath%2A> , protože hodnota nastavená v poli <xref:System.Windows.Data.XmlDataProvider> označuje, že by měly být vystaveny pouze prvky *Books* (v zásadě nastavení filtru).  
  
 ![Snímek obrazovky s příkladem XPath znázorňující název čtyř knih](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 V tomto příkladu se zobrazí názvy knih <xref:System.Windows.Data.Binding.XPath%2A> , protože <xref:System.Windows.Controls.TextBlock> vazba v <xref:System.Windows.DataTemplate> je nastavená na "*title*". Pokud chcete zobrazit hodnotu atributu, jako je například *ISBN*, nastavte tuto <xref:System.Windows.Data.Binding.XPath%2A> hodnotu na "`@ISBN`".  
  
 Vlastnosti **XPath** v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou zpracovávány metodou XMLNode. SelectNodes. Můžete upravit dotazy **XPath** a získat tak různé výsledky. Tady je několik příkladů <xref:System.Windows.Data.Binding.XPath%2A> dotazu na vazbu <xref:System.Windows.Controls.ListBox> z předchozího příkladu:  
  
- `XPath="Book[1]"`Vrátí první prvek Book ("XML v akci"). Všimněte si, že indexy **XPath** jsou založené na 1, nikoli 0.  
  
- `XPath="Book[@*]"`Vrátí všechny prvky knihy s libovolnými atributy.  
  
- `XPath="Book[last()-1]"`Vrátí druhý k poslednímu prvku Book ("Představujeme Microsoft .NET").  
  
- `XPath="*[position()>3]"`Vrátí všechny prvky knihy s výjimkou prvního 3.  
  
 Když spustíte dotaz **XPath** , vrátí <xref:System.Xml.XmlNode> nebo seznam XMLNodes. <xref:System.Xml.XmlNode>je objekt modulu CLR (Common Language Runtime), což znamená, že můžete použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost pro vytvoření vazby k vlastnostem CLR (Common Language Runtime). Předchozí příklad zvažte znovu. Pokud zbytek příkladu zůstává stejný a měníte <xref:System.Windows.Controls.TextBlock> vazbu na následující, zobrazí se názvy vrácených XmlNode <xref:System.Windows.Controls.ListBox>v. V tomto případě je název všech vrácených uzlů "*Book*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 V některých aplikacích může být vkládání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jako datový ostrůvek v rámci zdroje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky nepohodlné, protože přesný obsah dat musí být známý v době kompilace. Proto je také podporováno získávání dat z externího [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] souboru, jako v následujícím příkladu:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Pokud se [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data nachází ve vzdáleném [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] souboru, měli byste definovat přístup k datům <xref:System.Windows.Data.XmlDataProvider.Source%2A> přiřazením vhodného [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] k atributu následujícím způsobem:  
  
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
