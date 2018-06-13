---
title: Vyberte uzel pomocí jazyka XPath navigace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c5a7b9113dd5a4de929f5b88569be89bc1f2c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572707"
---
# <a name="select-nodes-using-xpath-navigation"></a>Vyberte uzel pomocí jazyka XPath navigace
XML modelu DOM (Document Object) obsahuje metody, které vám umožní používat navigační XML Path Language (XPath) dotazů na informace v modelu DOM. Pomocí jazyka XPath se najít uzel jeden, konkrétní nebo k vyhledání všech uzlech, jež některé kritériím.  
  
## <a name="xpath-select-methods"></a>Vyberte XPath metody  
 Třídy DOM nabízí dvě metody pro výběr XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metoda a <xref:System.Xml.XmlNode.SelectNodes%2A> metoda. <xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda vrátí první uzlu, který odpovídá kritériím výběru. <xref:System.Xml.XmlNode.SelectNodes%2A> Metoda vrátí <xref:System.Xml.XmlNodeList> obsahující odpovídající uzly.  
  
 Následující příklad používá <xref:System.Xml.XmlNode.SelectSingleNode%2A> metoda vyberte první `book` uzlu, ve kterém jméno autora poslední splňují zadaná kritéria. Soubor bookstore.xml (které je zadáno na konci tohoto tématu) se používá jako vstupní soubor.  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's   
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's   
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 Další příklad používá <xref:System.Xml.XmlNode.SelectNodes%2A> metoda vyberte všechny uzly adresáře, ve kterých je větší než po zadanou dobu cenu. Ceny pro každou knihu v seznamu vybraný je pak prostřednictvím kódu programu snížit deset procent. Nakonec je aktualizovaný soubor zapsána do konzoly. Soubor bookstore.xml (které je zadáno na konci tohoto tématu) se používá jako vstupní soubor.  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 Výše uvedených příkladech spustí dotaz XPath na element dokumentu. Nastavení výchozí bod pro cestu XPath dotazu nastaví kontext uzlu, který je výchozím bodem pro dotaz XPath. Pokud nechcete, aby pro spuštění na element dokumentu, ale chcete začít od prvního podřízeného prvku dokumentu, můžete příkaz select kódu následujícím způsobem:  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Všechny <xref:System.Xml.XmlNodeList> objekty jsou synchronizovány s zdrojový dokument. Proto pokud iteraci v rámci seznamu uzlu a změňte hodnotu uzlu, tento uzel je aktualizované taky v dokumentu, ze které pochází. Všimněte si v předchozím příkladu, změny uzlu ve vybraných <xref:System.Xml.XmlNodeList> také změněna zdrojový dokument.  
  
> [!NOTE]
>  Pokud zdrojový dokument je změněn, se doporučuje znovu select. Pokud je uzel upravit jeden, který by mohl způsobit uzlu, který má být přidán do seznamu uzlu, pokud nebyla dříve, nebo její odebrání ze seznamu uzlu teď způsobit, není zaručeno, seznam uzlů je nyní přesná.  
  
## <a name="namespaces-in-xpath-expressions"></a>Obory názvů ve výrazech XPath  
 Výrazech XPath může zahrnovat obory názvů. Namespace řešení je podporována při použití <xref:System.Xml.XmlNamespaceManager>. Obsahuje-li výraz XPath předpony, identifikátor URI pár předpony a oboru názvů musí být přidaný do <xref:System.Xml.XmlNamespaceManager>a <xref:System.Xml.XmlNamespaceManager> je předán <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> nebo <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metoda. Všimněte si, že pomocí výše uvedené příklady kódu <xref:System.Xml.XmlNamespaceManager> vyřešit obor názvů bookstore.xml dokumentu.  
  
> [!NOTE]
>  Pokud výraz XPath neobsahuje předpony, předpokládá se, že je obor názvů identifikátor URI (Uniform Resource) prázdného oboru názvů. Pokud soubor XML obsahuje výchozí obor názvů, musí stále přidejte identifikátor URI oboru názvů a předpony k <xref:System.Xml.XmlNamespaceManager>, jinak budou vybrány žádné uzly.  
  
#### <a name="input-file"></a>Vstupní soubor  
 Toto je soubor bookstore.xml, který se používá jako vstupní soubor v příkladech v tomto tématu:  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
