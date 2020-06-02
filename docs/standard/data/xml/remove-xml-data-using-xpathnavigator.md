---
title: Odebrání dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: fa331757fac3f30ee86a24bbd0ee12b5f1031a4b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288664"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>Odebrání dat XML pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Třída poskytuje sadu metod, které slouží k odebrání uzlů a hodnot z dokumentu XML. Aby bylo možné tyto metody použít, <xref:System.Xml.XPath.XPathNavigator> musí být objekt upravitelný, to znamená, že jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastnost musí být `true` .  
  
 <xref:System.Xml.XPath.XPathNavigator>objekty, které mohou upravovat dokument XML, jsou vytvořeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodou <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator>objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod úprav <xref:System.Xml.XPath.XPathNavigator> objektu vytvořeného <xref:System.Xml.XPath.XPathDocument> objektem mají za následek <xref:System.NotSupportedException> .  
  
 Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů najdete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Odebírání uzlů  
 <xref:System.Xml.XPath.XPathNavigator>Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodu pro odebrání uzlů z dokumentu XML.  
  
### <a name="removing-a-node"></a>Odebrání uzlu  
 <xref:System.Xml.XPath.XPathNavigator>Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodu pro odstranění aktuálního uzlu, <xref:System.Xml.XPath.XPathNavigator> na kterém je objekt aktuálně umístěný z dokumentu XML.  
  
 Poté, co byl uzel odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody, již není dosažitelný z kořenu <xref:System.Xml.XmlDocument> objektu. Po odstranění uzlu <xref:System.Xml.XPath.XPathNavigator> je umístěn v nadřazeném uzlu odstraněného uzlu.  
  
 Operace odstranění nemá vliv na pozici žádného <xref:System.Xml.XPath.XPathNavigator> objektu umístěného na odstraněném uzlu. Tyto <xref:System.Xml.XPath.XPathNavigator> objekty jsou platné v tom smyslu, že mohou být přesunuty v odstraněném podstromu, ale nelze je přesunout do hlavního stromu uzlu pomocí regulárních metod navigace pro <xref:System.Xml.XPath.XPathNavigator> třídu.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>Metodu <xref:System.Xml.XPath.XPathNavigator> třídy lze použít k přesunutí těchto <xref:System.Xml.XPath.XPathNavigator> objektů zpět do hlavního stromu uzlu nebo z hlavního stromu uzlu do odstraněného podstromu.  
  
 V následujícím příkladu `price` je prvek prvního `book` prvku `contosoBooks.xml` souboru odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody. Pozice <xref:System.Xml.XPath.XPathNavigator> objektu po `price` odstranění elementu je v nadřazeném `book` elementu.  
  
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
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Odebrání uzlu atributu  
 Uzly atributů jsou odebrány z dokumentu XML pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.  
  
 Po odstranění uzlu atributu již není dosažitelný z kořenového uzlu <xref:System.Xml.XmlDocument> objektu a <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn v nadřazeném elementu.  
  
#### <a name="default-attributes"></a>Výchozí atributy  
 Bez ohledu na metodu použitou k odebrání atributů existují zvláštní omezení na odebrání atributů, které jsou definovány jako výchozí atributy ve schématu DTD nebo XML pro dokument XML. Výchozí atributy nelze odebrat, pokud je odebrán také element, ke kterému patří. Výchozí atributy jsou vždy přítomny pro prvky, které mají deklarované výchozí atributy, a v důsledku toho odstranění výchozího atributu má za následek vložení nahrazujícího atributu do elementu a inicializovaného na výchozí hodnotu, která byla deklarována.  
  
## <a name="removing-values"></a>Odebírají se hodnoty.  
 <xref:System.Xml.XPath.XPathNavigator>Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody a k odebrání netypových a typových hodnot z dokumentu XML.  
  
### <a name="removing-untyped-values"></a>Odebrání netypových hodnot  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Metoda jednoduše vloží netypové `string` hodnoty předané jako parametr jako hodnotu uzlu, <xref:System.Xml.XPath.XPathNavigator> na kterém je objekt aktuálně umístěn. Předáním prázdného řetězce <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metodě dojde k odebrání hodnoty aktuálního uzlu.  
  
 Následující příklad odebere hodnotu `price` prvku prvního `book` prvku v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody.  
  
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
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Odebírají se typové hodnoty.  
 Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodou zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty. Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` na elementu, jehož typ je `xs:positiveInteger` ), výsledkem je výjimka. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>Metodu nelze předat také `null` jako parametr. Výsledkem odebrání hodnoty typového uzlu musí odpovídat typu schématu uzlu.  
  
 Následující příklad odebere hodnotu `price` prvku prvního `book` prvku v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody nastavením hodnoty na `0` . Hodnota uzlu není odebrána, ale cena knihy byla odebrána podle jeho datového typu `xs:decimal` .  
  
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
 Uzly oboru názvů nelze odstranit z <xref:System.Xml.XmlDocument> objektu. Při pokusu o odstranění uzlů oboru názvů pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody dojde k výjimce.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Vlastnosti InnerXml a OuterXml  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy a třídy mění kód XML uzlů, <xref:System.Xml.XPath.XPathNavigator> na kterých je objekt aktuálně umístěn.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Vlastnost změní kód XML podřízených uzlů, <xref:System.Xml.XPath.XPathNavigator> na kterých je objekt aktuálně umístěn, s analyzovaným obsahem daného XML `string` . Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost mění kód XML podřízených uzlů, <xref:System.Xml.XPath.XPathNavigator> na kterých je objekt aktuálně umístěn, i v samotném aktuálním uzlu.  
  
 Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> lze vlastnosti a použít k odebrání uzlů a hodnot z dokumentu XML. Další informace o použití <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastností a pro úpravu uzlů naleznete v tématu [Úprava dat XML pomocí XPathNavigator](modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="saving-an-xml-document"></a>Uložení dokumentu XML  
 Uložení změn provedených <xref:System.Xml.XmlDocument> v objektu jako výsledek metod popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy. Další informace o ukládání změn provedených v <xref:System.Xml.XmlDocument> objektu naleznete v tématu [ukládání a zápis dokumentu](saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](process-xml-data-using-the-xpath-data-model.md)
- [Vložení dat XML pomocí XPathNavigator](insert-xml-data-using-xpathnavigator.md)
- [Změna dat XML pomocí XPathNavigator](modify-xml-data-using-xpathnavigator.md)
