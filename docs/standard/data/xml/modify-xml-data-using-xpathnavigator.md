---
title: Změna dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 219327d246416cfb3d76919680aa74a58bae5fb3
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085869"
---
# <a name="modify-xml-data-using-xpathnavigator"></a>Změna dat XML pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k úpravě uzly a hodnoty v dokumentu XML. Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, to znamená, jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML jsou vytvářeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a žádný pokus o použití metod pro posunutí úprav <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený pomocí <xref:System.Xml.XPath.XPathDocument> výsledek v objektu <xref:System.NotSupportedException>.  
  
 Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Úprava uzlů  
 Jednoduchý postup pro změnu hodnoty uzlu je použít <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
 V následující tabulce jsou uvedeny účinky z těchto metod na různé typy uzlů.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Změny dat|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Není podporováno.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Obsah elementu.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Hodnota atributu.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Textový obsah.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Obsah, s výjimkou cíl.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Obsah komentář.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Nepodporuje se.|  
  
> [!NOTE]
>  Úpravy <xref:System.Xml.XPath.XPathNodeType.Namespace> uzly nebo <xref:System.Xml.XPath.XPathNodeType.Root> uzel není podporován.  
  
 <xref:System.Xml.XPath.XPathNavigator> Třída rovněž poskytuje sadu metod používaných pro vložení a odebrání uzlů. Další informace o vkládání a odstranění uzlů z dokumentu XML, najdete v článku [vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) a [odebrání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) témata.  
  
### <a name="modifying-untyped-values"></a>Úprava Netypové hodnoty  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` předanou jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na. Hodnota je vložen bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná pro typ uzlu, pokud je k dispozici informace o schématu.  
  
 V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda se používá k aktualizaci všech `price` prvků v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Úprava zadaných hodnot  
 Pokud je typ uzlu W3C XML schématu jednoduché zadejte, nová hodnota vkládat stisknutím <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda je porovnávána s omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavena. Pokud je nová hodnota není platná pro typ uzlu (například nastavíte hodnotu `-1` na element, jehož typ je `xs:positiveInteger`), je výsledkem výjimky.  
  
 V následujícím příkladu se pokusí změnit hodnotu `price` prvek první `book` prvek `contosoBooks.xml` do souboru <xref:System.DateTime> hodnotu. Protože typ schématu XML `price` element je definován jako `xs:decimal` v `contosoBooks.xsd` souborů, v důsledku výjimky.  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad využívá taky `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Účinky úpravy dat XML silného typu  
 <xref:System.Xml.XPath.XPathNavigator> Třída používá W3C XML schématu jako základ pro popisující XML silného typu. Elementy a atributy, mohou být opatřeny poznámkami s informací o typu podle ověřování podle W3C XML schématu dokumentu. Prvky, které může obsahovat další elementy nebo atributy se nazývají komplexní typy, zatímco ty, které může obsahovat jenom textový obsah se nazývají jednoduché typy.  
  
> [!NOTE]
>  Jednoduché typy může mít pouze atributy.  
  
 Elementu nebo atributu může být považovány za schématu platný, pokud splňuje všechna pravidla, které jsou specifické pro své definice typu. Element, který má jednoduchý typ `xs:int` musí obsahovat číselná hodnota mezi -2147483648 a 2147483647 schématu platný. U komplexních typů schématu platnosti elementu je závislá na schéma platnost jeho podřízené prvky a atributy. Proto pokud element je platný pro jeho definice komplexní typ, všechny jeho podřízené prvky a atributy jsou platné pro jejich definice typu. Podobně, pokud ještě jeden z podřízených elementů nebo atributů elementu není platná před jeho definice typu, nebo má neznámý platnosti, element je také buď neplatná nebo neznámá platnosti.  
  
 Vzhledem k tomu, že platnost elementu je závislá na platnost jeho podřízené prvky a atributy, způsobit změny buď změna platnosti elementu, pokud byla dříve platný. Konkrétně podřízené elementy nebo atributy elementu se přidají, aktualizována nebo odstraněna, pak platnosti prvek stane neznámý. To je reprezentována <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastnost elementu, který <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost nastavena na <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>. Kromě toho tento efekt uspořádá sebe nahoru rekurzivně v dokumentu XML, protože platnost nadřazeného elementu (a jeho nadřazeného elementu a tak dále) se také stane neznámý.  
  
 Další informace o ověřování schématu a <xref:System.Xml.XPath.XPathNavigator> najdete v tématu [ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Úprava atributů  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody slouží k úpravě typové a netypové atribut uzlů, jakož i jiné typy uzlů uvedených v části "Úpravy uzly".  
  
 Následující příklad změní hodnotu `genre` atribut první `book` prvek `books.xml` souboru.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, naleznete v částech "Úpravy Netypové hodnoty" a "Úprava zadané hodnoty".  
  
## <a name="innerxml-and-outerxml-properties"></a>InnerXml a OuterXml vlastnosti  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na s analyzovaný obsah XML daného `string`. Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na i samotný uzel aktuální.  
  
 V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost na hodnotu změnit `price` elementu a vložit nový `discount` atribut na první `book` prvek v `contosoBooks.xml` souboru.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Úprava uzlů Namespace  
 V Document Object Model (DOM), deklarace oboru názvů jsou považovány, jako by šlo regulární atributy, které lze vložit, aktualizovat a odstranit. <xref:System.Xml.XPath.XPathNavigator> Třídy nepovoluje tyto operace na uzly oboru názvů, protože změna hodnota uzlu oboru názvů můžete změnit identitu této elementů a atributů v rámci oboru uzel oboru názvů, jak je znázorněno v následujícím příkladu.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 Pokud se výše uvedený příklad XML změní následujícím způsobem, to každý prvek v dokumentu efektivně přejmenuje, vzhledem k tomu, že se změní hodnota identifikátoru URI oboru názvů každý prvek.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 Vkládání uzly oboru názvů, které nejsou v konfliktu s deklarací oboru názvů v oboru, který se vloží do povoluje <xref:System.Xml.XPath.XPathNavigator> třídy. Deklarace oboru názvů v tomto případě nejsou deklarovány na nižší obory v dokumentu XML a nemá za následek přejmenování, jak je znázorněno v následujícím příkladu.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Pokud výše uvedený příklad XML se změní následujícím způsobem, deklarace oboru názvů se rozšíří správně v následujícím oboru dalších deklarace oboru názvů dokumentu XML.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 V příkladu XML výše, atribut `a:parent-id` disku do mechaniky na `parent` prvek `http://www.contoso.com/parent-id` oboru názvů. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metody slouží k vložení Přestože umístěn na atribut `parent` elementu. `http://www.contoso.com` Deklarace oboru názvů se automaticky vložit <xref:System.Xml.XPath.XPathNavigator> třídy pro zachování konzistence zbývající části dokumentu XML.  
  
## <a name="modifying-entity-reference-nodes"></a>Úprava uzlů odkaz na entitu  
 Uzly odkaz na entitu v <xref:System.Xml.XmlDocument> objektu jsou jen pro čtení a nejde upravovat pomocí buď <xref:System.Xml.XPath.XPathNavigator> nebo <xref:System.Xml.XmlNode> třídy. Výsledkem jakýkoliv pokus upravit uzlu odkazu entity <xref:System.InvalidOperationException>.  
  
## <a name="modifying-xsinil-nodes"></a>Úprava xsi: nil uzly  
 Doporučení W3C XML schématu zavádí koncepci element je nepovinné. Pokud element je nepovinné, je možné pro element nemají žádný obsah a stále platit. Je podobný koncept objektu se koncept element je nepovinné `null`. Hlavní rozdíl je, že `null` objekt nelze získat přístup k žádným způsobem, zatímco `xsi:nil` element stále má vlastnosti, jako jsou atributy, které lze získat přístup, ale nemá žádný obsah (podřízené elementy nebo text). Existence `xsi:nil` atributu s hodnotou `true` v elementu ve formátu XML dokumentu se používá k označení, že element nemá žádný obsah.  
  
 Pokud <xref:System.Xml.XPath.XPathNavigator> objektu se používá k přidání obsahu na platný element s `xsi:nil` atributu s hodnotou `true`, hodnota jeho `xsi:nil` atribut je nastaven na `false`.  
  
> [!NOTE]
>  Pokud obsah elementu se `xsi:nil` atribut nastaven na `false` je odstraněn, hodnota atributu se nezmění na `true`.  
  
## <a name="saving-an-xml-document"></a>Uložení dokumentu XML  
 Ukládají se změny provedené <xref:System.Xml.XmlDocument> jak výsledky úprav metod popsaných v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy. Další informace o uložení změny <xref:System.Xml.XmlDocument> objektu, najdete v článku [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [Odebrání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
