---
title: Výběr uzlů pomocí navigace XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e02dd304893e4d9354144c5b412dfd145161c6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026975"
---
# <a name="select-nodes-using-xpath-navigation"></a>Výběr uzlů pomocí navigace XPath
XML Document Object Model (DOM) obsahuje metody, které vám umožní použít navigační jazyk XML Path (XPath) dotaz na informace v modelu DOM. Výraz XPath můžete použít k vyhledání jednoho, konkrétní uzel nebo najít všechny uzly, které odpovídají kritérií.  
  
## <a name="xpath-select-methods"></a>Výběr XPath metody  
 Třídy modelu DOM poskytují dvě metody pro výběr XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metoda a <xref:System.Xml.XmlNode.SelectNodes%2A> metoda. <xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda vrátí první uzel, který by odpovídal kritériím výběru. <xref:System.Xml.XmlNode.SelectNodes%2A> Vrátí metoda <xref:System.Xml.XmlNodeList> , která obsahuje odpovídající uzly.  
  
 V následujícím příkladu <xref:System.Xml.XmlNode.SelectSingleNode%2A> metoda vyberte první `book` uzel, ve kterém autora příjmení splňují zadaná kritéria. Soubor bookstore.xml (který je k dispozici na konci tohoto tématu) se používá jako vstupní soubor.  
  
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
  
 Následující příklad používá <xref:System.Xml.XmlNode.SelectNodes%2A> metoda vybere všechny uzly adresáře, ve kterých je větší než zadaná velikost cena. Cena za jednotlivé knihy ve vybraném seznamu je potom programově snižuje deset procent. Nakonec je aktualizovaný soubor zapsán do konzoly. Soubor bookstore.xml (který je k dispozici na konci tohoto tématu) se používá jako vstupní soubor.  
  
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
  
 Výše uvedených příkladech spustit dotaz XPath na element dokumentu. Nastavení výchozí bod pro cestu XPath dotaz nastaví kontextu uzlu, který je výchozím bodem pro dotaz XPath. Pokud nechcete, aby začínal element dokumentu, ale chcete začít od první podřízený element dokumentu, vám umožní kódování příkaz select následujícím způsobem:  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Všechny <xref:System.Xml.XmlNodeList> objekty jsou synchronizovány s zdrojový dokument. Proto pokud iteraci v rámci seznamu uzlů a změňte hodnotu uzlu, uzlu jsou aktualizované taky v dokumentu, ze které pochází. Všimněte si, že v předchozím příkladu, která při změně uzlu ve vybraném období <xref:System.Xml.XmlNodeList> etag zdrojový dokument.  
  
> [!NOTE]
>  Při změně podkladového dokumentu, je vhodné spustit znovu vybrat. Je-li upravit uzlu je ten, který může způsobit, že uzel, který má přidat do seznamu uzlu, pokud nebyla dříve, nebo ho odebrat ze seznamu uzlů nyní způsobí, není zaručeno, že seznam uzlů je nyní přesné.  
  
## <a name="namespaces-in-xpath-expressions"></a>Obory názvů ve výrazech XPath  
 Výrazy XPath může zahrnovat obory názvů. Namespace rozlišení není podporováno použití <xref:System.Xml.XmlNamespaceManager>. Pokud výraz XPath obsahuje předponu, identifikátor URI dvojice předpony a oboru názvů musí být přidané do <xref:System.Xml.XmlNamespaceManager>a <xref:System.Xml.XmlNamespaceManager> je předán <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> nebo <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metoda. Všimněte si, že pomocí výše uvedených příkladech kódu <xref:System.Xml.XmlNamespaceManager> určit obor názvů bookstore.xml dokumentu.  
  
> [!NOTE]
>  Pokud výraz XPath neobsahuje předponu, předpokládá se, že je obor názvů identifikátoru URI (Uniform Resource) prázdný obor názvů. Pokud soubor XML obsahuje výchozí obor názvů, přesto musí přidat předpony a oboru názvů identifikátoru URI k <xref:System.Xml.XmlNamespaceManager>; v opačném případě bude vybráno žádné uzly.  
  
#### <a name="input-file"></a>Vstupní soubor  
 Toto je bookstore.xml soubor, který slouží jako vstupní soubor v příkladech v tomto tématu:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
