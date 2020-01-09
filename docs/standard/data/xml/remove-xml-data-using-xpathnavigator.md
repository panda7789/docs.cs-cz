---
title: Odebrání dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: 062a98a9cc10e6be00f165cf617de2d92d65acbf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710359"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>Odebrání dat XML pomocí XPathNavigator
Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje sadu metod, které slouží k odebrání uzlů a hodnot z dokumentu XML. Aby bylo možné použít tyto metody, objekt <xref:System.Xml.XPath.XPathNavigator> musí být upravitelný, to znamená, že jeho vlastnost <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> objektů, které mohou upravovat dokument XML, jsou vytvořeny metodou <xref:System.Xml.XmlDocument.CreateNavigator%2A> třídy <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod úprav objektu <xref:System.Xml.XPath.XPathNavigator> vytvořeného objektem <xref:System.Xml.XPath.XPathDocument> mají za následek <xref:System.NotSupportedException>.  
  
 Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů naleznete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Odebírání uzlů  
 Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda pro odebrání uzlů z dokumentu XML.  
  
### <a name="removing-a-node"></a>Odebrání uzlu  
 Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> způsob, jak odstranit aktuální uzel, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný v dokumentu XML.  
  
 Poté, co byl uzel odstraněn pomocí metody <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>, již není dosažitelný z kořenu objektu <xref:System.Xml.XmlDocument>. Po odstranění uzlu je <xref:System.Xml.XPath.XPathNavigator> umístěn v nadřazeném uzlu odstraněného uzlu.  
  
 Operace odstranění nemá vliv na pozici objektu <xref:System.Xml.XPath.XPathNavigator> umístěného na odstraněném uzlu. Tyto objekty <xref:System.Xml.XPath.XPathNavigator> jsou platné v tom smyslu, že je lze přesunout v odstraněném podstromu, ale nelze je přesunout do hlavního stromu uzlů pomocí regulárních metod pro <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
> [!NOTE]
> Metodu <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> třídy <xref:System.Xml.XPath.XPathNavigator> lze použít k přesunutí těchto <xref:System.Xml.XPath.XPathNavigator> objektů zpět do hlavního stromu uzlu nebo z stromu hlavního uzlu do odstraněného podstromu.  
  
 V následujícím příkladu je prvek `price` prvního `book` prvku `contosoBooks.xml` souboru odstraněn pomocí metody <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>. Pozice objektu <xref:System.Xml.XPath.XPathNavigator> po odstranění `price` elementu je na nadřazeném `book` elementu.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Odebrání uzlu atributu  
 Uzly atributů jsou odebrány z dokumentu XML pomocí metody <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>.  
  
 Po odstranění uzlu atributu již není dosažitelný z kořenového uzlu <xref:System.Xml.XmlDocument>ho objektu a objekt <xref:System.Xml.XPath.XPathNavigator> umístěný v nadřazeném elementu.  
  
#### <a name="default-attributes"></a>Výchozí atributy  
 Bez ohledu na metodu použitou k odebrání atributů existují zvláštní omezení na odebrání atributů, které jsou definovány jako výchozí atributy ve schématu DTD nebo XML pro dokument XML. Výchozí atributy nelze odebrat, pokud je odebrán také element, ke kterému patří. Výchozí atributy jsou vždy přítomny pro prvky, které mají deklarované výchozí atributy, a v důsledku toho odstranění výchozího atributu má za následek vložení nahrazujícího atributu do elementu a inicializovaného na výchozí hodnotu, která byla deklarována.  
  
## <a name="removing-values"></a>Odebírají se hodnoty.  
 Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> k odebrání netypových a typových hodnot z dokumentu XML.  
  
### <a name="removing-untyped-values"></a>Odebrání netypových hodnot  
 Metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> jednoduše vloží Netypový `string` hodnotu předanou jako parametr jako hodnotu uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný. Předáním prázdného řetězce do metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> dojde k odebrání hodnoty aktuálního uzlu.  
  
 Následující příklad odstraní hodnotu prvku `price` prvního prvku `book` v souboru `contosoBooks.xml` pomocí metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
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
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Odebírají se typové hodnoty.  
 Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená metodou <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty. Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` u elementu, jehož typ je `xs:positiveInteger`), výsledkem bude výjimka. Metodu <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> také nelze předat `null` jako parametr. Výsledkem odebrání hodnoty typového uzlu musí odpovídat typu schématu uzlu.  
  
 Následující příklad odstraní hodnotu prvku `price` prvního prvku `book` v souboru `contosoBooks.xml` pomocí metody <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> nastavením hodnoty na `0`. Hodnota uzlu není odebrána, ale cena knihy byla odebrána podle jeho datového typu `xs:decimal`.  
  
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
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
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
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a>Uzly oboru názvů  
 Uzly oboru názvů nelze odstranit z objektu <xref:System.Xml.XmlDocument>. Pokusí se odstranit uzly oboru názvů pomocí metody <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> mají za následek výjimku.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Vlastnosti InnerXml a OuterXml  
 Vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> třídy <xref:System.Xml.XPath.XPathNavigator> mění kód XML uzlů, na kterých je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěn.  
  
 Vlastnost <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> změní kód XML podřízených uzlů, na kterých je aktuálně umístěn <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje analyzovaný obsah daného XML `string`. Podobně vlastnost <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> mění kód XML podřízených uzlů, na kterých je aktuálně umístěn <xref:System.Xml.XPath.XPathNavigator> objekt a také na samotném aktuálním uzlu.  
  
 Kromě metod popsaných v tomto tématu, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastností lze použít k odebrání uzlů a hodnot z dokumentu XML. Další informace o použití <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastností pro úpravu uzlů naleznete v tématu [Úprava dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="saving-an-xml-document"></a>Uložení dokumentu XML  
 Uložení změn provedených v objektu <xref:System.Xml.XmlDocument> jako výsledek metod popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy. Další informace o uložení změn provedených v objektu <xref:System.Xml.XmlDocument> naleznete v tématu [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [Změna dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
