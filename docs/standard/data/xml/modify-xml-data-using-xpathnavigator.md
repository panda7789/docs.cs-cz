---
title: Změna dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: ea42cbfe7427e026f5e3339af5f5a2ceec17dad3
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202205"
---
# <a name="modify-xml-data-using-xpathnavigator"></a>Změna dat XML pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Třída poskytuje sadu metod, které slouží k úpravě uzlů a hodnot v dokumentu XML. Aby bylo možné tyto metody použít, <xref:System.Xml.XPath.XPathNavigator> musí být objekt upravitelný, to znamená, že jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastnost musí být `true` .  
  
 <xref:System.Xml.XPath.XPathNavigator>objekty, které mohou upravovat dokument XML, jsou vytvořeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodou <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator>objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod úprav <xref:System.Xml.XPath.XPathNavigator> objektu vytvořeného objektem mají za <xref:System.Xml.XPath.XPathDocument> následek <xref:System.NotSupportedException> .  
  
 Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů najdete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Úprava uzlů  
 Jednoduchá technika pro změnu hodnoty uzlu je použití <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metod a <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
 V následující tabulce jsou uvedeny účinky těchto metod na různé typy uzlů.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Data změněna|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Není podporováno.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Obsah elementu.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Hodnota atributu|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Textový obsah.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Obsah s výjimkou cíle.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Obsah komentáře|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Nepodporuje se.|  
  
> [!NOTE]
> Úprava <xref:System.Xml.XPath.XPathNodeType.Namespace> uzlů nebo <xref:System.Xml.XPath.XPathNodeType.Root> uzlu není podporována.  
  
 <xref:System.Xml.XPath.XPathNavigator>Třída také poskytuje sadu metod, které se používají pro vkládání a odebírání uzlů. Další informace o vkládání a odebírání uzlů z dokumentu XML naleznete v tématu [vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) a [Odebrání XML data pomocí témat XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) .  
  
### <a name="modifying-untyped-values"></a>Úprava netypových hodnot  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Metoda jednoduše vloží netypové `string` hodnoty předané jako parametr jako hodnotu uzlu, <xref:System.Xml.XPath.XPathNavigator> na kterém je objekt aktuálně umístěn. Hodnota je vložena bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud jsou k dispozici informace o schématu.  
  
 V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> je metoda použita k aktualizaci všech `price` prvků v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Úprava zadaných hodnot  
 Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodou zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty. Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` na elementu, jehož typ je `xs:positiveInteger` ), výsledkem je výjimka.  
  
 Následující příklad se pokusí změnit hodnotu `price` prvku prvního `book` prvku v `contosoBooks.xml` souboru na <xref:System.DateTime> hodnotu. Vzhledem k tomu, že typ schématu XML `price` elementu je definován jako `xs:decimal` v `contosoBooks.xsd` souborech, výsledkem je výjimka.  
  
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
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Příklad také přebírá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Důsledky úprav dat XML se silnými typy  
 <xref:System.Xml.XPath.XPathNavigator>Třída používá schéma W3C XML jako základ pro popis silného typu XML. Elementy a atributy lze opatřit poznámkami pomocí informací o typu na základě ověřování v dokumentu schématu W3C XML. Prvky, které mohou obsahovat další elementy nebo atributy, se nazývají komplexní typy, zatímco ty, které mohou obsahovat pouze textový obsah, se nazývají jednoduché typy.  
  
> [!NOTE]
> Atributy můžou mít jenom jednoduché typy.  
  
 Element nebo atribut lze považovat za schéma – platný, pokud odpovídá všem pravidlům, která jsou specifická pro jeho definici typu. Element, který má jednoduchý typ, `xs:int` musí obsahovat číselnou hodnotu mezi-2147483648 a 2147483647, aby bylo schématu platné. U komplexních typů je platnost schématu platnosti elementu závislá na schématu platnosti svých podřízených prvků a atributů. Proto pokud je element platný proti definici komplexního typu, všechny jeho podřízené prvky a atributy jsou platné proti definicím jejich typu. Podobně, pokud je i jeden z podřízených elementů nebo atributů elementu neplatný proti své definici typu nebo má neznámou platnost, prvek je také buď neplatný, nebo neznámou platnost.  
  
 Vzhledem k tomu, že platnost elementu je závislá na platnosti svých podřízených prvků a atributů, úpravy v důsledku změny platnosti prvku, pokud byl dříve platný. Konkrétně, pokud jsou podřízené prvky nebo atributy elementu vloženy, aktualizovány nebo smazány, pak platnost elementu bude neznáma. Toto je reprezentované <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastností <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti elementu nastavenou na <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown> . Kromě toho tento efekt kaskádě provede v dokumentu XML rekurzivně nahoru, protože platnost nadřazeného elementu elementu (a jeho nadřazeného elementu atd.) je také neznámá.  
  
 Další informace o ověřování schématu a <xref:System.Xml.XPath.XPathNavigator> třídě naleznete v tématu [ověřování schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Úprava atributů  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Metody a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> lze použít pro úpravu netypových a typových uzlů atributů a také jiných typů uzlů uvedených v části "Změna uzlů".  
  
 Následující příklad změní hodnotu `genre` atributu prvního `book` prvku v `books.xml` souboru.  
  
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
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodách a naleznete v částech "úpravy netypových hodnot" a "úpravy zadaných hodnot".  
  
## <a name="innerxml-and-outerxml-properties"></a>Vlastnosti InnerXml a OuterXml  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy a třídy mění kód XML uzlů, <xref:System.Xml.XPath.XPathNavigator> na kterých je objekt aktuálně umístěn.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Vlastnost změní kód XML podřízených uzlů, <xref:System.Xml.XPath.XPathNavigator> na kterých je objekt aktuálně umístěn, s analyzovaným obsahem daného XML `string` . Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost mění kód XML podřízených uzlů, <xref:System.Xml.XPath.XPathNavigator> na kterých je objekt aktuálně umístěn, i v samotném aktuálním uzlu.  
  
 V následujícím příkladu je použita <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost pro úpravu hodnoty `price` prvku a vložení nového `discount` atributu do prvního `book` prvku v `contosoBooks.xml` souboru.  
  
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
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Úprava uzlů oboru názvů  
 V model DOM (Document Object Model) (DOM) se deklarace oborů názvů považují za, jako by se jednalo o běžné atributy, které se dají vkládat, aktualizovat a odstraňovat. <xref:System.Xml.XPath.XPathNavigator>Třída nepovoluje takové operace na uzlech oboru názvů, protože změna hodnoty uzlu oboru názvů může změnit identitu prvků a atributů v rámci oboru oboru názvů, jak je znázorněno v následujícím příkladu.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 Pokud se výše uvedený příklad XML změní následujícím způsobem, tato možnost efektivně přejmenuje každý prvek v dokumentu, protože se změnila hodnota identifikátoru URI oboru názvů každého elementu.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 Vložení uzlů oboru názvů, které nejsou v konfliktu s deklaracemi oboru názvů v oboru, ve kterém jsou vloženy, je povoleno <xref:System.Xml.XPath.XPathNavigator> třídou. V tomto případě deklarace oboru názvů nejsou deklarovány v nižších oborech v dokumentu XML a nevedou k přejmenování, jak je znázorněno v následujícím příkladu.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Pokud se výše uvedený příklad XML změní následujícím způsobem, deklarace oboru názvů jsou správně šířeny v rámci dokumentu XML pod rozsahem jiné deklarace oboru názvů.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 Ve výše uvedeném příkladu XML `a:parent-id` je atribut vložen na `parent` prvek v `http://www.contoso.com/parent-id` oboru názvů. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>Metoda se používá k vložení atributu při umístění na `parent` element. `http://www.contoso.com`Deklarace oboru názvů je automaticky vložena <xref:System.Xml.XPath.XPathNavigator> třídou, která zachovává konzistenci zbytku dokumentu XML.  
  
## <a name="modifying-entity-reference-nodes"></a>Úprava uzlů odkazů na entity  
 Uzly odkazů na entity v <xref:System.Xml.XmlDocument> objektu jsou jen pro čtení a nelze je upravovat pomocí <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlNode> tříd nebo. Jakýkoli pokus o změnu uzlu odkazu na entitu má za následek <xref:System.InvalidOperationException> .  
  
## <a name="modifying-xsinil-nodes"></a>Úprava uzlů xsi: nil  
 Doporučení schématu W3C XML zavádí koncept prvku, který je nillable. Když je element nillable, je možné, že element nemá žádný obsah a bude nadále platný. Koncept prvku, který je nillable, je podobný konceptu objektu, který je `null` . Hlavním rozdílem je, že k `null` objektu nelze přistup jakýmkoli způsobem, zatímco `xsi:nil` element stále obsahuje vlastnosti, jako jsou například atributy, které lze použít, ale nemá žádný obsah (podřízené prvky nebo text). Existence `xsi:nil` atributu s hodnotou `true` elementu v dokumentu XML slouží k označení toho, že element nemá žádný obsah.  
  
 Pokud <xref:System.Xml.XPath.XPathNavigator> je objekt použit k přidání obsahu do platného prvku s `xsi:nil` atributem s hodnotou `true` , hodnota jeho `xsi:nil` atributu je nastavena na `false` .  
  
> [!NOTE]
> Pokud je obsah elementu s `xsi:nil` atributem nastaveným na hodnotu `false` odstraněn, hodnota atributu není změněna na `true` .  
  
## <a name="saving-an-xml-document"></a>Uložení dokumentu XML  
 Uložení změn provedených <xref:System.Xml.XmlDocument> v objektu jako výsledek metod úprav popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy. Další informace o ukládání změn provedených v <xref:System.Xml.XmlDocument> objektu naleznete v tématu [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [Odebrání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
