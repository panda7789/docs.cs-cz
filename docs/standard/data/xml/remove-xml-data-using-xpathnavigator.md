---
title: Odebrat pomocí objektem XPathNavigator nastaveným na Data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87dc7d83692f081f2c48a34cef8a33564f0e3089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577030"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>Odebrat pomocí objektem XPathNavigator nastaveným na Data XML
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k odebírání uzlů a hodnoty dokument XML. Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, který je jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML, které jsou vytvořené pomocí <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a jakýkoli pokus o úpravu metody použijte <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený <xref:System.Xml.XPath.XPathDocument> objekt výsledkem <xref:System.NotSupportedException>.  
  
 Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete v části [čtení dat XML pomocí XPathDocument třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Odebrání uzlů  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda odebrat uzly ze dokument XML.  
  
### <a name="removing-a-node"></a>Odebrání uzlu  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda odstranit aktuální uzel <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na z dokumentu XML.  
  
 Poté, co uzel byl odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda, již není dostupný z kořenové složky <xref:System.Xml.XmlDocument> objektu. Po odstranění uzlu, <xref:System.Xml.XPath.XPathNavigator> je umístěn na nadřazený uzel odstraněné uzlu.  
  
 Operace odstranění nemá vliv na polohu všech <xref:System.Xml.XPath.XPathNavigator> umístěný na uzlu odstraněného objektu. Tyto <xref:System.Xml.XPath.XPathNavigator> objekty jsou platné v tom smyslu, že můžete přesunout v rámci odstraněné podstrom, ale nelze přesunout do hlavní uzel stromu pomocí uzlu regulární nastavit metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Metodu <xref:System.Xml.XPath.XPathNavigator> třídu lze použít k přesunutí těchto <xref:System.Xml.XPath.XPathNavigator> objekty zpět do hlavní uzel stromu, nebo je z hlavní uzel stromu do odstraněného podstrom.  
  
 V následujícím příkladu `price` element první `book` element `contosoBooks.xml` soubor se odstraní pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda. Pozice <xref:System.Xml.XPath.XPathNavigator> objektu po `price` odstraněn prvek je v nadřazené `book` elementu.  
  
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
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Odebrání uzlu atributu.  
 Atribut uzly jsou odebrat z dokumentu XML pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda.  
  
 Po odstranění do atribut uzlu, již není dostupný z kořenový uzel <xref:System.Xml.XmlDocument> objektu a <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn na nadřazený element.  
  
#### <a name="default-attributes"></a>Výchozí atributy  
 Bez ohledu na to, v případě metody slouží k odebírání atributy jsou speciální omezení odebrání atributů, které jsou definovány jako výchozí atributy v souboru DTD protokolu nebo schématu XML pro dokument XML. Výchozí atributy nelze odebrat, pokud mají být odebrán také na element, který náleží do. Výchozí atributy jsou vždy k dispozici pro prvky, které mají výchozí atributy deklarovat a v důsledku toho odstranění výsledků výchozí atribut ve nahrazení atributu vkládání do elementu a inicializovat na výchozí hodnotu, která byla definována.  
  
## <a name="removing-values"></a>Odebírání hodnot  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody odebrat netypová a zadali hodnoty z dokumentu XML.  
  
### <a name="removing-untyped-values"></a>Odebrání Netypové hodnoty  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` hodnota předaná jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na. Předávání prázdného řetězce <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda odebere hodnotu, aktuální uzel.  
  
 Následující příklad odebere hodnotu `price` element první `book` element v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda.  
  
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
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Odebrání zadávaných hodnot  
 Pokud je typ uzlu schématu XML W3C jednoduchý typ, nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda bude zkontrolován omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavená. Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnotu `-1` u elementu, jehož typ je `xs:positiveInteger`), výsledkem výjimka. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Metoda také nelze předat `null` jako parametr. V důsledku odebrání hodnoty typu uzlu musí odpovídat typ schématu uzlu.  
  
 Následující příklad odebere hodnotu `price` element první `book` element v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda podle nastavení na hodnotu `0`. Hodnota uzlu není odebrána, ale byla odebrána cenu knihy podle jeho datového typu z `xs:decimal`.  
  
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
  
## <a name="namespace-nodes"></a>Namespace uzly  
 Namespace uzly nelze odstranit ze <xref:System.Xml.XmlDocument> objektu. Pokusí se odstranit uzly oboru názvů pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody za následek výjimku.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml a OuterXml vlastnosti  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třída změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na s Analyzovaná obsah daného XML `string`. Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na i aktuální uzel.  
  
 Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti lze použít k odebrání uzlů a hodnoty ze dokument XML. Další informace o používání <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> najdete v části vlastnosti, jimiž upravíte uzly, [upravit Data XML pomocí objektem XPathNavigator nastaveným](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.  
  
## <a name="saving-an-xml-document"></a>Uložení dokumentu XML  
 Ukládají se změny provedené v <xref:System.Xml.XmlDocument> objektu jako výsledek metody popsané v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy. Další informace o ukládání změny <xref:System.Xml.XmlDocument> objektu, najdete v části [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [Změna dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
