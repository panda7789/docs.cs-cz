---
title: Výběr uzlů pomocí navigace XPath
description: Naučte se vybírat uzly XML v .NET. Použijte metody model DOM (Document Object Model) (DOM), které vám umožní použít k dotazování na informace DOM navigaci pomocí jazyka XML Path (XPath).
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: aa8b6d93e25d974a0e1b53ae8be9868f6bf64be6
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662508"
---
# <a name="select-nodes-using-xpath-navigation"></a>Výběr uzlů pomocí navigace XPath
XML model DOM (Document Object Model) (DOM) obsahuje metody, které umožňují použít navigaci jazyka XML Path (XPath) k dotazování na informace v modelu DOM. Pomocí XPath můžete najít jeden konkrétní uzel nebo najít všechny uzly, které splňují určitá kritéria.  
  
## <a name="xpath-select-methods"></a>Metody výběru XPath  
 Třídy modelu DOM poskytují dvě metody pro výběr XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metodu a <xref:System.Xml.XmlNode.SelectNodes%2A> metodu. <xref:System.Xml.XmlNode.SelectSingleNode%2A>Metoda vrátí první uzel, který odpovídá kritériím výběru. <xref:System.Xml.XmlNode.SelectNodes%2A>Metoda vrací objekt <xref:System.Xml.XmlNodeList> , který obsahuje odpovídající uzly.  
  
 V následujícím příkladu je použita <xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda k výběru prvního `book` uzlu, ve kterém poslední jméno autora splňuje zadaná kritéria. Soubor bookstore.xml (který je k dispozici na konci tohoto tématu) se používá jako vstupní soubor.  
  
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
  
 Následující příklad používá <xref:System.Xml.XmlNode.SelectNodes%2A> metodu pro výběr všech uzlů knihy, ve kterých je cena větší než zadaná hodnota. Cena za každou knihu ve vybraném seznamu se pak programově sníží o deset procent. Nakonec se aktualizovaný soubor zapíše do konzoly. Soubor bookstore.xml (který je k dispozici na konci tohoto tématu) se používá jako vstupní soubor.  
  
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
  
 Výše uvedené příklady spouštějí dotaz XPath na elementu dokumentu. Nastavením počátečního bodu pro dotaz XPath nastavíte kontextový uzel, což je výchozí bod pro dotaz XPath. Pokud nechcete začít na elementu dokumentu, ale chcete začít od prvního podřízeného prvku dokumentu, můžete příkaz Select vytvořit následujícím způsobem:  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Všechny <xref:System.Xml.XmlNodeList> objekty jsou synchronizovány s podkladovým dokumentem. Proto pokud procházíte seznamem uzlů a upravíte hodnotu uzlu, je tento uzel aktualizován také v dokumentu, ze kterého pochází. Všimněte si, že v předchozím příkladu se změnila i změna uzlu, který je upravený ve vybraném <xref:System.Xml.XmlNodeList> podkladovém dokumentu.  
  
> [!NOTE]
> Při změně podkladového dokumentu je vhodné znovu spustit příkaz SELECT. Pokud je uzel změněn, což by mohlo způsobit, že uzel bude přidán do seznamu uzlů, pokud předtím nebyl, nebo by nyní mohl být odebrán ze seznamu uzlů, není zaručeno, že seznam uzlů je nyní přesný.  
  
## <a name="namespaces-in-xpath-expressions"></a>Obory názvů ve výrazech XPath  
 Výrazy XPath můžou zahrnovat obory názvů. Překlad oboru názvů je podporován pomocí <xref:System.Xml.XmlNamespaceManager> . Pokud výraz XPath obsahuje předponu, předpona a identifikátor URI oboru názvů musí být přidán do <xref:System.Xml.XmlNamespaceManager> , a <xref:System.Xml.XmlNamespaceManager> je předána <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metodě nebo. Všimněte si, že výše uvedené příklady kódu používají <xref:System.Xml.XmlNamespaceManager> k překladu oboru názvů bookstore.xmlho dokumentu.  
  
> [!NOTE]
> Pokud výraz XPath neobsahuje předponu, předpokládá se, že obor názvů URI (Uniform Resource Identifier) je prázdný obor názvů. Pokud váš kód XML obsahuje výchozí obor názvů, je stále nutné přidat předponu a identifikátor URI oboru názvů do <xref:System.Xml.XmlNamespaceManager> ; v opačném případě nebudou vybrány žádné uzly.  
  
#### <a name="input-file"></a>Vstupní soubor  
 Následuje bookstore.xml soubor, který se používá jako vstupní soubor v příkladech v tomto tématu:  
  
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

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
