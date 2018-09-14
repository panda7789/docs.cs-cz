---
title: Vytvoření nových atributů pro elementy v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 870e800220031338557792fa612d4a3101e79f90
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45583434"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>Vytvoření nových atributů pro elementy v modelu DOM
Vytvoření nového atributu se liší od vytvoření jiných typů uzlu, protože atributy nejsou uzly, ale jsou vlastnosti uzlu elementu jsou součástí **XmlAttributeCollection** spojené s tímto prvkem. Existuje několik způsobů, jak vytvořit atribut a připojit ho k elementu:  
  
-   Získejte uzlu elementu a použijte **SetAttribute** přidání atributu do kolekce atributů daného prvku.  
  
-   Vytvoření **XmlAttribute** pomocí uzlu **CreateAttribute** metody get uzlu elementu, a pak pomocí **SetAttributeNode** k přidání uzlu do kolekce atributů, které element.  
  
 Následující příklad ukazuje, jak přidat atribut do elementu pomocí **SetAttribute** metody.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    XmlDocument doc = new XmlDocument();  
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 Následující příklad ukazuje nový atribut vytváří pomocí **CreateAttribute** metody. Pak znázorňuje atribut přidána do kolekce atributů **knihy** prvku pomocí **SetAttributeNode** metoda.  
  
 Daný následující kód XML:  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Vytvořte nový atribut a přiřaďte jí hodnotu:  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 a připojit ho k elementu:  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **Output**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Úplný příklad najdete tady <xref:System.Xml.XmlDocument.CreateAttribute%2A>.  
  
 Můžete taky vytvořit **XmlAttribute** uzlu a použití **InsertBefore** nebo **InsertAfter** metody umístit na odpovídající pozici v kolekci. Pokud atribut se stejným názvem už existuje v kolekci atributů existující **XmlAttribute** uzel je odebrán z kolekce a nové **XmlAttribute** uzlu je vložen. To se provádí stejným způsobem jako **SetAttribute** metody. Tyto metody přijímají jako parametr, existující uzel jako referenční bod provedete **InsertBefore** a **InsertAfter**. Pokud nezadáte uzel odkazu určující, kam chcete vložit nový uzel, na výchozí hodnoty pro **InsertAfter** se vložit nový uzel na začátku kolekce. Výchozí umístění **InsertBefore**, pokud je k dispozici žádný uzel odkazu, je na konec kolekce.  
  
 Pokud jste vytvořili **XmlNamedNodeMap** atributů, můžete přidat atribut s použitím názvu <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>. Další informace najdete v tématu [kolekce uzlů v NamedNodeMaps a NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).  
  
## <a name="default-attributes"></a>Výchozí atributy  
 Pokud vytvoříte element, který je deklarován mít atribut výchozí, nový výchozí atribut s jeho výchozí hodnota je vytvořené pomocí XML Document Object Model (DOM) a připojen k elementu. V tuto chvíli jsou také vytvořit podřízené uzly výchozího atributu.  
  
## <a name="attribute-child-nodes"></a>Atribut podřízené uzly  
 Hodnota uzlu atributu se změní jeho podřízených uzlů. Existují jenom dva typy platný podřízené uzly: **XmlText** uzly, a **XmlEntityReference** uzly. Tyto jsou podřízené uzly v tom smyslu, že tyto metody, jako **FirstChild** a **LastChild** zpracovat jako podřízené uzly. Toto rozlišení atribut s podřízenými uzly je důležité při pokusu o odebrání atributů nebo atribut podřízené uzly. Další informace najdete v tématu [odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
