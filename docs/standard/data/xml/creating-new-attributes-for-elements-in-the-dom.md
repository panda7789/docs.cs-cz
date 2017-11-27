---
title: "Vytvoření nové atributy pro elementy v modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6970ffc38e900c9b47c58c8ae4b81b9551f5589b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>Vytvoření nové atributy pro elementy v modelu DOM
Vytvoření nového atributu se liší od vytvoření jiných typů uzlů, protože atributy nejsou uzly, ale jsou vlastnosti uzlu elementu a jsou součástí **XmlAttributeCollection** přidružené k elementu. Vytvořte atribut a jeho připojení pro element několika způsoby:  
  
-   Získat uzlu elementu a použít **SetAttribute** přidání atributu do atribut kolekce daný element.  
  
-   Vytvoření **XmlAttribute** uzlu pomocí **CreateAttribute** metoda, získat uzel elementu, potom použijte **SetAttributeNode** přidání uzlu do atribut kolekce, element.  
  
 Následující příklad ukazuje, jak přidat atribut k elementu pomocí **SetAttribute** metoda.  
  
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
  
 Následující příklad ukazuje nový atribut vytváří pomocí **CreateAttribute** metoda. Se potom zobrazí atribut přidán do atribut kolekce **kniha** element pomocí **SetAttributeNode** metoda.  
  
 Zadané následující kód XML:  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Vytvořte nový atribut a přiřaďte mu hodnotu:  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 a připojte ji k prvku:  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **Výstup**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Úplný příklad najdete na <xref:System.Xml.XmlDocument.CreateAttribute%2A>.  
  
 Můžete taky vytvořit **XmlAttribute** uzel a použití **InsertBefore** nebo **InsertAfter** metody pro jeho umístění v příslušné pozici v kolekci. Pokud atribut se stejným názvem již existuje v kolekci atributů existující **XmlAttribute** uzel je odebrán z kolekce a nové **XmlAttribute** je vložen uzlu. Provede stejným způsobem jako **SetAttribute** metoda. Tyto metody přijímají jako parametr, stávající uzel jako referenční bod uděláte **InsertBefore** a **InsertAfter**. Pokud nezadáte uzlu odkazu, která určuje, kam chcete vložit nový uzel, je výchozí hodnotou **InsertAfter** metodou, je na začátek kolekce vložte nový uzel. Výchozí umístění **InsertBefore**, pokud je k dispozici žádný uzel odkazu, je na konec kolekce.  
  
 Pokud jste vytvořili **XmlNamedNodeMap** atributů, můžete přidat atribut pomocí názvu <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>. Další informace najdete v tématu [uzlu kolekce v NamedNodeMaps a NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).  
  
## <a name="default-attributes"></a>Výchozí atributy  
 Pokud vytvoříte element, který je deklarován tak, aby měl výchozí atribut, nový výchozí atribut s jeho výchozí hodnota je vytvořen pomocí XML modelu DOM (Document Object) a připojen k elementu. V tuto chvíli se také vytvořit podřízené uzly výchozí atribut.  
  
## <a name="attribute-child-nodes"></a>Atribut podřízené uzly  
 Hodnota uzlu atributu se změní jeho podřízené uzly. Existují jenom dva typy platný podřízené uzly: **XmlText** uzly, a **XmlEntityReference** uzlů. Tyto jsou podřízené uzly v tom smyslu, že tyto metody, jako **hodnotu FirstChild** a **LastChild** zpracovat jako podřízené uzly. Tento rozdíl atributu s podřízenými uzly je důležité při pokusu o odebrání atributů nebo atribut podřízené uzly. Další informace najdete v tématu [odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
