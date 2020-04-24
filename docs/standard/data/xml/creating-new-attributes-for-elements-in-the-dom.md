---
title: Vytváření nových atributů pro elementy v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
ms.openlocfilehash: 79a3390933256ed862d35c90db0aab2177cdfc41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711009"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>Vytváření nových atributů pro elementy v modelu DOM

Vytváření nových atributů se liší od vytvoření jiných typů uzlů, protože atributy nejsou uzly, ale jsou vlastnosti uzlu elementu a jsou obsaženy v objektu **XmlAttributeCollection** přidruženého k elementu. Existuje několik způsobů, jak vytvořit atribut a připojit jej k elementu:

- Získejte uzel element a použijte atribut **SetAttributes** pro přidání atributu do kolekce atributů daného elementu.

- Vytvořte uzel **XmlAttribute** pomocí metody **CreateAttribute** , Získejte uzel element a pak použijte **SetAttributeNode** pro přidání uzlu do kolekce atributů daného elementu.

Následující příklad ukazuje, jak přidat atribut k elementu pomocí metody **SetAttributes** :

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As New XmlDocument()
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _
                    "<title>Pride And Prejudice</title>" & _
                    "</book>")
        Dim root As XmlElement = doc.DocumentElement

        ' Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel")

        Console.WriteLine("Display the modified XML...")
        Console.WriteLine(doc.InnerXml)
    End Sub
End Class
```  
  
```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
    public static void Main()
    {
        var doc = new XmlDocument();
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +
                    "<title>Pride And Prejudice</title>" +
                    "</book>");
        XmlElement root = doc.DocumentElement;

        // Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel");

        Console.WriteLine("Display the modified XML...");
        Console.WriteLine(doc.InnerXml);
    }
}
```

Následující příklad ukazuje nový atribut, který je vytvářen pomocí metody **CreateAttribute** . Pak zobrazuje atribut přidaný do kolekce atributů prvku **Book** pomocí metody **SetAttributeNode** .

S ohledem na následující kód XML:
  
```xml
<book genre='novel' ISBN='1-861001-57-5'>
<title>Pride And Prejudice</title>
</book>
```

Vytvořte nový atribut a poskytněte mu hodnotu:

```vb
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")
attr.Value = "WorldWide Publishing"
```

```csharp
XmlAttribute attr = doc.CreateAttribute("publisher");
attr.Value = "WorldWide Publishing";
```

a připojte jej k elementu:

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

Úplný vzorek kódu najdete na adrese <xref:System.Xml.XmlDocument.CreateAttribute%2A>.

Můžete také vytvořit uzel **XmlAttribute** a použít metody **InsertBefore** nebo **InsertAfter** k umístění do příslušné pozice v kolekci. Pokud je v kolekci atributů již přítomen atribut se stejným názvem, existující uzel **XmlAttribute** je odebrán z kolekce a je vložen nový uzel **XmlAttribute** . To funguje stejným způsobem jako metoda **SetAttributes** . Tyto metody přebírají jako parametr existující uzel jako referenční bod pro provádění **InsertBefore** a **InsertAfter**. Pokud neposkytnete referenční uzel určující, kam vložit nový uzel, je výchozím nastavením pro metodu **InsertAfter** vložení nového uzlu na začátek kolekce. Výchozí pozice pro **InsertBefore**, pokud není k dispozici žádný uzel odkazu, je na konci kolekce.

Pokud jste vytvořili **XmlNamedNodeMap** atributů, můžete přidat atribut podle názvu pomocí <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> metody. Další informace najdete v tématu [kolekce uzlů v NamedNodeMaps a NodeLists](node-collections-in-namednodemaps-and-nodelists.md).

## <a name="default-attributes"></a>Výchozí atributy

Vytvoříte-li prvek, který je deklarován jako výchozí atribut, je vytvořen nový výchozí atribut s výchozí hodnotou v souboru XML model DOM (Document Object Model) (DOM) a připojen k elementu. V tuto chvíli se vytvoří i podřízených uzlů výchozích atributů.

## <a name="attribute-child-nodes"></a>Podřízené uzly atributu

Hodnota uzlu atributu se bude jednat o své podřízené uzly. Existují pouze dva typy platných podřízených uzlů: uzly **XmlText** a uzly **XmlEntityReference** . Jedná se o podřízené uzly v tom smyslu, že metody jako **hodnotu FirstChild** a **LastChild** je zpracovávají jako podřízené uzly. Toto rozlišení atributu s podřízenými uzly je důležité při pokusu o odebrání atributů nebo podřízených uzlů atributů. Další informace naleznete v tématu [Odebrání atributů z uzlu elementu v modelu DOM](removing-attributes-from-an-element-node-in-the-dom.md).

## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
