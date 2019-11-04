---
title: 'Postupy: Připojení k datům XML použitím objektu XMLDataProvider a dotazů XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 0f39c9d42abfaba1327f2c189ac6ce3d40db6e89
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459207"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Postupy: Připojení k datům XML použitím objektu XMLDataProvider a dotazů XPath
Tento příklad ukazuje, jak vytvořit vazby na data [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] pomocí <xref:System.Windows.Data.XmlDataProvider>.  
  
 U <xref:System.Windows.Data.XmlDataProvider>jsou podkladová data, ke kterým je možné přistupovat prostřednictvím datové vazby ve vaší aplikaci, libovolný strom [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] uzlů. Jinými slovy <xref:System.Windows.Data.XmlDataProvider> poskytuje pohodlný způsob, jak použít libovolný strom [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] uzlů jako zdroj vazby.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou data vložena přímo jako [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *datový ostrůvek* v rámci <xref:System.Windows.FrameworkElement.Resources%2A> části. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] datový ostrůvek musí být zabalen do značek `<x:XData>` a vždy mít jeden kořenový uzel, který je v tomto příkladu *inventářem* .  
  
> [!NOTE]
> Kořenový uzel dat [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] má atribut **xmlns** , který nastaví [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] oboru názvů na prázdný řetězec. Toto je požadavek na použití dotazů XPath na datový ostrůvek, který je vložený na stránce [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. V tomto vloženém případě dědí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a tudíž datový ostrůvek, dědí obor názvů <xref:System.Windows>. Z tohoto důvodu je třeba nastavit obor názvů jako prázdný, aby byly dotazy XPath kvalifikovány pomocí oboru názvů <xref:System.Windows>, které by mohly dotaz nesměrovat.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Jak ukazuje tento příklad, chcete-li vytvořit stejnou deklaraci vazby v syntaxi atributu, je nutné speciální znaky správně Escape. Další informace naleznete v tématu [znakové entity XML a XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 Při spuštění tohoto příkladu se v <xref:System.Windows.Controls.ListBox> zobrazí následující položky. Jedná se o *název*všech prvků v *knihách* , které *mají hodnotu "* *out*" nebo *číslo* hodnoty 3 nebo větší nebo rovno 8. Všimněte si, že nejsou vráceny žádné položky *CD* , protože <xref:System.Windows.Data.XmlDataProvider.XPath%2A> hodnota nastavená v <xref:System.Windows.Data.XmlDataProvider> označuje, že by měly být vystaveny pouze prvky *Books* (v zásadě nastavení filtru).  
  
 ![Snímek obrazovky s příkladem XPath znázorňující název čtyř knih](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 V tomto příkladu se zobrazí názvy knih, protože <xref:System.Windows.Data.Binding.XPath%2A> <xref:System.Windows.Controls.TextBlock> vazby v <xref:System.Windows.DataTemplate> je nastavená na "*title*". Pokud chcete zobrazit hodnotu atributu, jako je například *ISBN*, nastavíte <xref:System.Windows.Data.Binding.XPath%2A> hodnotu na "`@ISBN`".  
  
 Vlastnosti **XPath** v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou zpracovávány metodou XMLNode. SelectNodes. Můžete upravit dotazy **XPath** a získat tak různé výsledky. Tady jsou některé příklady pro <xref:System.Windows.Data.Binding.XPath%2A> dotaz na vázané <xref:System.Windows.Controls.ListBox> z předchozího příkladu:  
  
- `XPath="Book[1]"` vrátí první prvek Book ("XML v akci"). Všimněte si, že indexy **XPath** jsou založené na 1, nikoli 0.  
  
- `XPath="Book[@*]"` vrátí všechny prvky knihy s libovolnými atributy.  
  
- `XPath="Book[last()-1]"` vrátí druhý k poslednímu prvku Book ("Představujeme Microsoft .NET").  
  
- `XPath="*[position()>3]"` vrátí všechny prvky knihy s výjimkou prvního 3.  
  
 Když spustíte dotaz **XPath** , vrátí <xref:System.Xml.XmlNode> nebo seznam XMLNode. <xref:System.Xml.XmlNode> je objekt modulu CLR (Common Language Runtime), což znamená, že můžete použít vlastnost <xref:System.Windows.Data.Binding.Path%2A> pro vytvoření vazby k vlastnostem CLR (Common Language Runtime). Předchozí příklad zvažte znovu. Pokud zbytek příkladu zůstává stejný a měníte <xref:System.Windows.Controls.TextBlock> vazba na následující, zobrazí se názvy vrácených XmlNode v <xref:System.Windows.Controls.ListBox>. V tomto případě je název všech vrácených uzlů "*Book*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 V některých aplikacích může být vkládání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jako datové ostrůvky v rámci zdrojového [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky nepohodlné, protože přesný obsah dat musí být známý v době kompilace. Proto je také podporováno získávání dat z externího souboru [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], jak je uvedeno v následujícím příkladu:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Pokud se [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data nachází ve vzdáleném [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] souboru, měli byste definovat přístup k datům přiřazením příslušné adresy URL k atributu <xref:System.Windows.Data.XmlDataProvider.Source%2A> následujícím způsobem:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.ObjectDataProvider>
- [Vytvoření vazby k XDocument, XElement nebo LINQ pro výsledky XQuery](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [Použití vzoru seznam-podrobnosti s hierarchickými daty XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Přehled zdrojů vazby](binding-sources-overview.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
