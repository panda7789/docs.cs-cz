---
title: "Upravit pomocí objektem XPathNavigator nastaveným na Data XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cc46aeda6efe9f21bc094a4bc9d211fc282e9b65
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="modify-xml-data-using-xpathnavigator"></a>Upravit pomocí objektem XPathNavigator nastaveným na Data XML
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které používají k úpravě uzly a hodnoty v dokumentu XML. Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, který je jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator>objekty, které můžete upravit dokument XML, které jsou vytvořené pomocí <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator>objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a žádný pokus o použití úpravy metody <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený <xref:System.Xml.XPath.XPathDocument> objektu vést <xref:System.NotSupportedException>.  
  
 Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete v části [čtení dat XML pomocí XPathDocument třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Úprava uzly  
 Jednoduché technik pro změnu hodnoty uzlu je použít <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
 Následující tabulka uvádí důsledky z těchto metod pro různé typy uzlů.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Změnit data|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Není podporováno.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Obsah elementu.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Hodnota atributu.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Obsah textu.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Obsah, s výjimkou cíl.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Obsah komentář.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Není podporováno.|  
  
> [!NOTE]
>  Úpravy <xref:System.Xml.XPath.XPathNodeType.Namespace> uzly nebo <xref:System.Xml.XPath.XPathNodeType.Root> uzel není podporován.  
  
 <xref:System.Xml.XPath.XPathNavigator> Třída rovněž poskytuje sadu metod používaných k vložení a odebrání uzlů. Další informace o vložení a odebrání uzlů z dokumentu XML, najdete v článku [vložit Data XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) a [odebrat Data XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) témata.  
  
### <a name="modifying-untyped-values"></a>Úprava Netypové hodnoty  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` hodnota předaná jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na. Hodnota je vložen bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud je k dispozici informace o schématu.  
  
 V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda se používá k aktualizaci všech `price` elementů v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Úprava zadávaných hodnot  
 Pokud je typ uzlu schématu XML W3C jednoduchý typ, nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda bude zkontrolován omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavená. Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnotu `-1` u elementu, jehož typ je `xs:positiveInteger`), výsledkem výjimka.  
  
 V následujícím příkladu se pokusí změnit hodnotu `price` element první `book` element v `contosoBooks.xml` do souboru <xref:System.DateTime> hodnotu. Vzhledem k tomu, že typ schématu XML `price` element je definován jako `xs:decimal` v `contosoBooks.xsd` soubory, to vede k výjimce.  
  
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
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad také trvá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Účinky úpravy dat silného typu XML  
 <xref:System.Xml.XPath.XPathNavigator> Třída používá schéma XML W3C jako základ pro popisující silného typu XML. Elementů a atributů může být označený poznámkou, s informací o typu založené na ověření na základě dokument schématu XML W3C. Prvky, které může obsahovat další elementy nebo atributy se označují jako komplexní typy, zatímco ty, které může obsahovat pouze textové obsah se nazývají jednoduché typy.  
  
> [!NOTE]
>  Atributy mohou mít pouze jednoduché typy.  
  
 Elementu nebo atributu může být považuje za schématu platný, pokud je ve shodě se všechna pravidla, které jsou specifické pro jeho definice typu. Element, který má jednoduchý typ `xs:int` obsahovat numerická hodnota mezi -2147483648 a 2147483647 schématu platný. Pro komplexní typy je závislá na schéma platnosti jeho podřízených elementů a atributů schématu platnost elementu. Proto pokud element je platné před jeho definice komplexního typu, všechny její podřízené elementy a atributy jsou platné pro jejich definice typu. Podobně pokud ani jeden z podřízené elementy nebo atributy elementu je neplatný pro jeho definice typu nebo má neznámý platnosti, element je také buď neplatný, nebo neznámé platnosti.  
  
 Vzhledem k tomu, že platnost elementu je závislá na platnost jeho podřízených elementů a atributů, změny buď za následek změny platnosti elementu, pokud byl dříve platný. Konkrétně Pokud podřízené elementy nebo atributy elementu se přidají, aktualizovat nebo odstranit, pak platnosti elementu stává neznámé. To je reprezentována <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastnost elementu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost je nastavená na <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>. Kromě toho tato vliv uspořádá sebe směrem nahoru rekurzivně napříč v dokumentu XML protože platnost nadřazeného elementu (a jeho nadřazený element a tak dále) se také stane neznámé.  
  
 Další informace o ověřování schématu a <xref:System.Xml.XPath.XPathNavigator> třídy najdete v tématu [ověřování schématu pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Úprava atributů  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody slouží k úpravě bez typu a zadaných atributů uzly, jakož i jiné typy uzlů uvedené v části "Úprava uzlů".  
  
 Následující příklad změní hodnotu `genre` atribut první `book` element v `books.xml` souboru.  
  
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
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, najdete v částech "Úprava Netypové hodnoty" a "Úprava zadali hodnoty".  
  
## <a name="innerxml-and-outerxml-properties"></a>InnerXml a OuterXml vlastnosti  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třída změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na s Analyzovaná obsah daného XML `string`. Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na i aktuální uzel.  
  
 Následující příklad používá <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost změnit hodnotu `price` elementu a vložit nový `discount` atribut v prvním `book` element v `contosoBooks.xml` souboru.  
  
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
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Úprava Namespace uzly  
 V modelu DOM (Document Object), deklarace oboru názvů, které jsou zpracovány jako v případě, že jsou regulární atributy, které můžete vložit, aktualizovat a odstranit. <xref:System.Xml.XPath.XPathNavigator> – Třída neumožňuje tyto operace na uzlech obor názvů, protože změna hodnotu uzlu oboru názvů můžete změnit identitu elementů a atributů v rámci oboru názvů uzlu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 V předchozím příkladu XML dojde ke změně následujícím způsobem, to každý element v dokumentu efektivně přejmenuje, protože se změní hodnota každý prvek identifikátor URI oboru názvů.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 Vkládání uzly oboru názvů, které nejsou v konfliktu s deklarace oboru názvů v oboru, který se vloží do povolilo <xref:System.Xml.XPath.XPathNavigator> třídy. V takovém případě deklarace oboru názvů nejsou deklarovat na nižší obory v dokumentu XML a nevede přejmenování, jak je znázorněno v následujícím příkladu.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Pokud se v předchozím příkladu XML změnil následujícím způsobem, deklarace oboru názvů správně rozšířeny napříč v dokumentu XML níže oboru další deklarace oboru názvů.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 V XML příkladu výše, atribut `a:parent-id` na zadává `parent` element v `http://www.contoso.com/parent-id` oboru názvů. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda slouží k vložení atribut při umístěný na `parent` elementu. `http://www.contoso.com` Deklaraci oboru názvů je automaticky vkládat <xref:System.Xml.XPath.XPathNavigator> třídu k zachování konzistence zbývající části dokumentu XML.  
  
## <a name="modifying-entity-reference-nodes"></a>Úprava uzly odkaz Entity  
 Uzly odkaz na entitu v <xref:System.Xml.XmlDocument> objekt jsou jen pro čtení a nelze je upravit pomocí <xref:System.Xml.XPath.XPathNavigator> nebo <xref:System.Xml.XmlNode> třídy. Výsledkem žádné pokusu o změnu uzlu odkazu entity <xref:System.InvalidOperationException>.  
  
## <a name="modifying-xsinil-nodes"></a>Úprava xsi: nil uzly  
 Doporučení schématu XML W3C zavádí koncepci elementu se povolenou hodnotu Null. Když je element povolenou hodnotu Null, je možné pro element nemají žádný obsah a být stále platné. Koncept elementu se povolenou je podobný koncept k objektu se `null`. Hlavní rozdíl je, že `null` objekt nemůže mít přístup k žádným způsobem, při `xsi:nil` element stále existují vlastnosti, například atributy, které jsou přístupné, ale nemá žádný obsah (podřízené elementy nebo text). Existenci `xsi:nil` atributu s hodnotou `true` v elementu v kódu XML dokumentu slouží k označení, že element nemá žádný obsah.  
  
 Pokud <xref:System.Xml.XPath.XPathNavigator> objekt se používá k přidání obsahu do platný element s `xsi:nil` atributu s hodnotou `true`, hodnota jeho `xsi:nil` je nastavena na hodnotu `false`.  
  
> [!NOTE]
>  Pokud obsah elementu se `xsi:nil` atribut nastaven na `false` je odstranit, hodnota atributu není změněna na `true`.  
  
## <a name="saving-an-xml-document"></a>Uložení dokumentu XML  
 Ukládají se změny provedené v <xref:System.Xml.XmlDocument> objektu jako výsledek úprav metod popsaných v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy. Další informace o ukládání změny <xref:System.Xml.XmlDocument> objektu, najdete v části [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [Odebrání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
