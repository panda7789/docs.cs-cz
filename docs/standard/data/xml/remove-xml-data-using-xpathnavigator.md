---
title: Odebrání dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27c19c82270b9d67b6cd308386aa93c6112d59ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909685"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>Odebrání dat XML pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k odebrání uzlů a hodnot z dokumentu XML. Aby bylo možné tyto metody použít, <xref:System.Xml.XPath.XPathNavigator> musí být objekt upravitelný, to znamená, že jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastnost musí `true`být.  
  
 <xref:System.Xml.XPath.XPathNavigator>objekty, které mohou upravovat dokument XML, jsou vytvořeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodou <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator>objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod <xref:System.Xml.XPath.XPathNavigator> úprav objektu vytvořeného <xref:System.Xml.XPath.XPathDocument> objektem mají za <xref:System.NotSupportedException>následek.  
  
 Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů najdete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Odebírání uzlů  
 <xref:System.Xml.XPath.XPathNavigator> Třída<xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> poskytuje metodu pro odebrání uzlů z dokumentu XML.  
  
### <a name="removing-a-node"></a>Odebrání uzlu  
 Třída poskytuje metodu pro<xref:System.Xml.XPath.XPathNavigator> odstranění aktuálního uzlu, na kterém je objekt aktuálně umístěný z dokumentu XML. <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> <xref:System.Xml.XPath.XPathNavigator>  
  
 Poté, co byl uzel odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody, již není dosažitelný z kořenu <xref:System.Xml.XmlDocument> objektu. Po odstranění <xref:System.Xml.XPath.XPathNavigator> uzlu je umístěn v nadřazeném uzlu odstraněného uzlu.  
  
 Operace odstranění nemá vliv na pozici žádného <xref:System.Xml.XPath.XPathNavigator> objektu umístěného na odstraněném uzlu. Tyto <xref:System.Xml.XPath.XPathNavigator> objekty jsou platné v tom smyslu, že mohou být přesunuty v odstraněném podstromu, ale nelze je přesunout do hlavního stromu uzlu pomocí regulárních metod <xref:System.Xml.XPath.XPathNavigator> navigace pro třídu.  
  
> [!NOTE]
> Metodu třídy lze použít k přesunutí těchto <xref:System.Xml.XPath.XPathNavigator> objektů zpět do hlavního stromu uzlu nebo z hlavního stromu uzlu do odstraněného podstromu. <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
 V následujícím příkladu `price` je prvek prvního `book` prvku `contosoBooks.xml` souboru odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody. Pozice <xref:System.Xml.XPath.XPathNavigator> objektu `book` po odstranění elementu je v nadřazeném elementu. `price`  
  
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
  
 Po odstranění uzlu atributu již není dosažitelný z kořenového uzlu <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XPath.XPathNavigator> a objekt je umístěn v nadřazeném elementu.  
  
#### <a name="default-attributes"></a>Výchozí atributy  
 Bez ohledu na metodu použitou k odebrání atributů existují zvláštní omezení na odebrání atributů, které jsou definovány jako výchozí atributy ve schématu DTD nebo XML pro dokument XML. Výchozí atributy nelze odebrat, pokud je odebrán také element, ke kterému patří. Výchozí atributy jsou vždy přítomny pro prvky, které mají deklarované výchozí atributy, a v důsledku toho odstranění výchozího atributu má za následek vložení nahrazujícího atributu do elementu a inicializovaného na výchozí hodnotu, která byla deklarována.  
  
## <a name="removing-values"></a>Odebírají se hodnoty.  
 Třída poskytuje metody<xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> a k odebrání netypových a typových hodnot z dokumentu XML. <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator>  
  
### <a name="removing-untyped-values"></a>Odebrání netypových hodnot  
 Metoda jednoduše vloží `string` netypové hodnoty předané jako parametr jako hodnotu uzlu, na kterém <xref:System.Xml.XPath.XPathNavigator> je objekt aktuálně umístěn. <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Předáním prázdného řetězce <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metodě dojde k odebrání hodnoty aktuálního uzlu.  
  
 Následující `price` příklad odebere hodnotu prvku prvního `book` prvku <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> v `contosoBooks.xml` souboru pomocí metody.  
  
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
 Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodou zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty. Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` na elementu, jehož typ je `xs:positiveInteger`), výsledkem je výjimka. Metodu nelze předat `null` také jako parametr. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Výsledkem odebrání hodnoty typového uzlu musí odpovídat typu schématu uzlu.  
  
 `price` Následující příklad odebere hodnotu prvku prvního `book` prvku <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> v `contosoBooks.xml` souboru pomocí metody nastavením hodnoty na `0`. Hodnota uzlu není odebrána, ale cena knihy byla odebrána podle jeho datového typu `xs:decimal`.  
  
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
 Uzly oboru názvů nelze odstranit z <xref:System.Xml.XmlDocument> objektu. Při pokusu o odstranění uzlů oboru <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> názvů pomocí metody dojde k výjimce.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Vlastnosti InnerXml a OuterXml  
 Vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A>třídya třídy<xref:System.Xml.XPath.XPathNavigator> mění kód XML uzlů, na kterých je objekt aktuálně umístěn. <xref:System.Xml.XPath.XPathNavigator>  
  
 Vlastnost změní kód XML podřízených <xref:System.Xml.XPath.XPathNavigator> uzlů, na kterých je objekt aktuálně umístěn, s analyzovaným obsahem daného XML `string`. <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Podobně vlastnost mění kód XML podřízených <xref:System.Xml.XPath.XPathNavigator> uzlů, na kterých je objekt aktuálně umístěn, i v samotném aktuálním uzlu. <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A>  
  
 Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> lze vlastnosti a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> použít k odebrání uzlů a hodnot z dokumentu XML. Další informace o použití <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> vlastností a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> pro úpravu uzlů naleznete v tématu [Úprava dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="saving-an-xml-document"></a>Uložení dokumentu XML  
 Uložení změn provedených <xref:System.Xml.XmlDocument> v objektu jako výsledek metod popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy. Další informace o ukládání změn provedených <xref:System.Xml.XmlDocument> v objektu naleznete v tématu [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [Změna dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
