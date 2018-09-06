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
ms.openlocfilehash: 1827e40256bc4307006ce081cbb6cbc44a89a0bc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871082"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>Odebrání dat XML pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k odebrání uzlů a hodnot z dokumentu XML. Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, to znamená, jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML jsou vytvářeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a žádný pokus o použití metod pro posunutí úprav <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený pomocí <xref:System.Xml.XPath.XPathDocument> výsledkem objektu <xref:System.NotSupportedException>.  
  
 Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Odebrání uzlů  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda odebrání uzlů z dokumentu XML.  
  
### <a name="removing-a-node"></a>Odebrání uzlu  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda odstranit aktuální uzel <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na z dokumentu XML.  
  
 Poté, co uzel byl odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda, už nejsou dostupné z kořenového adresáře <xref:System.Xml.XmlDocument> objektu. Po odstranění uzlu <xref:System.Xml.XPath.XPathNavigator> je umístěn na nadřazený uzel z odstraněného uzlu.  
  
 Operace odstranění nemá vliv na pozici žádné <xref:System.Xml.XPath.XPathNavigator> objektu umístěn na odstraněného uzlu. Tyto <xref:System.Xml.XPath.XPathNavigator> objekty jsou platné v tom smyslu, že můžete přesouvat v rámci podstrom odstranila, ale nelze přesunout do hlavního uzlu stromové struktury pomocí regulárních uzel nastavení metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Metodu <xref:System.Xml.XPath.XPathNavigator> třídy lze použít k přesunutí těchto <xref:System.Xml.XPath.XPathNavigator> objektů zpět do hlavního uzlu stromu, nebo je z hlavního uzlu stromu odstraněné podstrom.  
  
 V následujícím příkladu `price` prvek první `book` elementu `contosoBooks.xml` soubor se odstraní pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda. Pozice <xref:System.Xml.XPath.XPathNavigator> objektu po `price` odstranit prvek je v nadřazené `book` elementu.  
  
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
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Odebrání uzlu atributu  
 Odeberou se z dokumentu XML pomocí uzlů atributů <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.  
  
 Po odstranění uzlu atributu, již není dosažitelný z kořenového uzlu <xref:System.Xml.XmlDocument> objektu a <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn na nadřazený element.  
  
#### <a name="default-attributes"></a>Výchozí atributy  
 Bez ohledu na použitou k odebrání atributů metodu jsou zvláštní omezení týkající se odebrání atributů, které jsou definovány jako výchozí atributy v souboru DTD nebo schématu XML pro dokument XML. Výchozí atributy nelze odebrat, pokud je odebrána také elementu, do kterých patří. Výchozí atributy jsou vždy k dispozici pro prvky, které mají výchozí atributy deklarovány a proto odstranění výchozí atribut výsledky v nahrazení atributu do elementu a inicializovat na výchozí hodnotu, která byla deklarována.  
  
## <a name="removing-values"></a>Odebrání hodnoty  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody odebrat netypová a zadané hodnoty z dokumentu XML.  
  
### <a name="removing-untyped-values"></a>Odebrání Netypové hodnoty  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` předanou jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na. Prázdný řetězec k předání <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda odebere hodnotu pro aktuální uzel.  
  
 Následující příklad odebere hodnotu `price` prvek první `book` element v `contosoBooks.xml` soubor pomocí <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody.  
  
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
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Odebrání zadaných hodnot  
 Pokud je typ uzlu W3C XML schématu jednoduché zadejte, nová hodnota vkládat stisknutím <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda je porovnávána s omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavena. Pokud je nová hodnota není platná pro typ uzlu (například nastavíte hodnotu `-1` na element, jehož typ je `xs:positiveInteger`), je výsledkem výjimky. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Metody nelze předat také `null` jako parametr. V důsledku odstranění hodnotu typu uzlu musí být v souladu s typem schématu uzlu.  
  
 Následující příklad odebere hodnotu `price` prvek první `book` element v `contosoBooks.xml` soubor pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda nastavením hodnoty `0`. Hodnota uzlu se neodebere, ale podle jeho datového typu byla odebrána cena knihu `xs:decimal`.  
  
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
 Namespace uzly nelze odstranit ze <xref:System.Xml.XmlDocument> objektu. Pokusí se odstranit obor názvů uzlů pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodu vede k výjimce.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml a OuterXml vlastnosti  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na s analyzovaný obsah XML daného `string`. Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na i samotný uzel aktuální.  
  
 Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti můžete použít k odebrání uzlů a hodnot z dokumentu XML. Další informace o používání <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti, které chcete upravit uzly, najdete v článku [upravit dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.  
  
## <a name="saving-an-xml-document"></a>Uložení dokumentu XML  
 Ukládají se změny provedené <xref:System.Xml.XmlDocument> objekt výsledku z metod popsaných v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy. Další informace o uložení změny <xref:System.Xml.XmlDocument> objektu, najdete v článku [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [Změna dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
