---
title: Přístup k atributům v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b456dc407f634e7f40f69bbac9b6d932f1f4420
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350712"
---
# <a name="accessing-attributes-in-the-dom"></a>Přístup k atributům v modelu DOM

Atributy jsou vlastnosti prvku, nikoli podřízené položky elementu. Toto rozlišení je důležité z důvodu metod, které slouží k navigaci na stejné úrovni, nadřazených a podřízených uzlech model DOM (Document Object Model) XML (DOM). Například metody **PreviousSibling** a **NextSibling** se nepoužívají k přechodu z prvku na atribut nebo mezi atributy. Místo toho je atribut vlastností elementu a je vlastněn prvkem, má vlastnost **OwnerElement** , nikoli vlastnost **ParentNode** a má odlišné metody navigace.

Pokud je aktuální uzel prvkem, použijte metodu **HasAttribute** , abyste viděli, zda jsou k elementu přidruženy žádné atributy. Jakmile je známo, že element má atributy, existuje více metod pro přístup k atributům. Chcete-li načíst jediný atribut z prvku, můžete použít metody **GetAttribute** a **GetAttributeNode** třídy **XmlElement** nebo můžete získat všechny atributy do kolekce. Získání kolekce je užitečné, pokud potřebujete iterovat v kolekci. Pokud chcete všechny atributy z prvku, použijte vlastnost **atributů** elementu pro načtení všech atributů do kolekce.

## <a name="retrieving-all-attributes-into-a-collection"></a>Načítání všech atributů do kolekce

Chcete-li, aby všechny atributy uzlu elementu byly vloženy do kolekce, zavolejte vlastnost **XmlElement. Attributes** . Tím se získá objekt **XmlAttributeCollection** , který obsahuje všechny atributy elementu. Třída **XmlAttributeCollection** dědí z mapy **XmlNamedNode** . Proto metody a vlastnosti, které jsou k dispozici v kolekci, obsahují kromě metod a vlastností specifických pro třídu **XmlAttributeCollection** , jako je například vlastnost **ItemOf** nebo metoda **Append** , k dispozici na mapě pojmenovaného uzlu. Každá položka v kolekci atributů představuje uzel **XmlAttribute** . Chcete-li najít počet atributů prvku, získat kolekci **XmlAttribute**a použít vlastnost **Count** k zobrazení, kolik uzlů **XmlAttribute** je v kolekci.

Následující příklad kódu ukazuje, jak načíst kolekci atributů a pomocí metody **Count** pro index smyčky, iterovat přes něj. Kód pak ukazuje, jak načíst jediný atribut z kolekce a zobrazit jeho hodnotu.

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim myElement As XmlElement = doc.DocumentElement

        ' Create an attribute collection from the element.
        Dim attrColl As XmlAttributeCollection = myElement.Attributes

        ' Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...")
        Dim i As Integer
        For i = 0 To attrColl.Count - 1
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)
            Console.Write("{0}", attrColl.ItemOf(i).Value)
            Console.WriteLine()
        Next

        ' Retrieve a single attribute from the collection; specifically, the
        ' attribute with the name "misc".
        Dim attr As XmlAttribute = attrColl("misc")

        ' Retrieve the value from that attribute.
        Dim miscValue As String = attr.InnerXml

        Console.WriteLine("Display the attribute information.")
        Console.WriteLine(miscValue)

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
        XmlDocument doc = new XmlDocument();
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +
                      "<title>The Handmaid's Tale</title>" +
                      "<price>14.95</price>" +
                      "</book>");

        // Move to an element.
        XmlElement myElement = doc.DocumentElement;

        // Create an attribute collection from the element.
        XmlAttributeCollection attrColl = myElement.Attributes;

        // Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...");
        for (int i = 0; i < attrColl.Count; i++)
        {
            Console.Write("{0} = ", attrColl[i].Name);
            Console.Write("{0}", attrColl[i].Value);
            Console.WriteLine();
        }

        // Retrieve a single attribute from the collection; specifically, the
        // attribute with the name "misc".
        XmlAttribute attr = attrColl["misc"];

        // Retrieve the value from that attribute.
        String miscValue = attr.InnerXml;

        Console.WriteLine("Display the attribute information.");
        Console.WriteLine(miscValue);

    }
}
```

V tomto příkladu se zobrazí následující výstup:

**Output**

Zobrazí všechny atributy v kolekci.

```console
genre = novel
ISBN = 1-861001-57-5
misc = sale item
Display the attribute information.
sale item
```

Informace v kolekci atributů lze načíst podle názvu nebo čísla indexu. Výše uvedený příklad ukazuje, jak načíst data podle názvu. Další příklad ukazuje, jak načíst data podle čísla indexu.

Vzhledem k tomu, že objekt **XmlAttributeCollection** je kolekce a lze provést iteraci pomocí názvu nebo indexu, tento příklad ukazuje výběr prvního atributu z kolekce pomocí indexu založeného na nule a použití následujícího souboru **baseUri. XML**jako vstupu.

### <a name="input"></a>Vstup

```xml
<!-- XML fragment -->
<book genre="novel">
  <title>Pride And Prejudice</title>
</book>
```

```vb
Option Explicit On
Option Strict On

Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()
        ' Create the XmlDocument.
        Dim doc As New XmlDocument()
        doc.Load("http://localhost/baseuri.xml")

        ' Display information on the attribute node. The value
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)
        Console.WriteLine("The value of the attribute:  {0}", attr.InnerText)
    End Sub 'Main
End Class 'Sample
```

```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
  public static void Main()
  {
    // Create the XmlDocument.
    XmlDocument doc = new XmlDocument();

    doc.Load("http://localhost/baseuri.xml");

    // Display information on the attribute node. The value
    // returned for BaseURI is 'http://localhost/baseuri.xml'.
    XmlAttribute attr = doc.DocumentElement.Attributes[0];
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);
    Console.WriteLine("The value of the attribute:  {0}", attr.InnerText);
  }
}
```

## <a name="retrieving-an-individual-attribute-node"></a>Načtení jednotlivého uzlu atributu

Chcete-li načíst jeden uzel atributu z prvku, je použita metoda <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType>. Vrátí objekt typu **XmlAttribute**. Po získání **atributu XmlAttribute**jsou všechny metody a vlastnosti, které jsou k dispozici ve třídě <xref:System.Xml.XmlAttribute?displayProperty=nameWithType>, k dispozici pro tento objekt, jako je například hledání **OwnerElement**.

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim root As XmlElement
        root = doc.DocumentElement

        ' Get an attribute.
        Dim attr As XmlAttribute
        attr = root.GetAttributeNode("ISBN")

        ' Display the value of the attribute.
        Dim attrValue As String
        attrValue = attr.InnerXml
        Console.WriteLine(attrValue)

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
    XmlDocument doc = new XmlDocument();
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +
                   "<title>The Handmaid's Tale</title>" +
                   "<price>14.95</price>" +
                   "</book>");

    // Move to an element.
     XmlElement root = doc.DocumentElement;

    // Get an attribute.
     XmlAttribute attr = root.GetAttributeNode("ISBN");

    // Display the value of the attribute.
     String attrValue = attr.InnerXml;
     Console.WriteLine(attrValue);

    }
}
```

Můžete také provést jak je znázorněno v předchozím příkladu, kde je jeden uzel atributu načten z kolekce atributů. Následující příklad kódu ukazuje, jak lze zapsat jeden řádek kódu pro načtení jednoho atributu pomocí čísla indexu z kořene stromu dokumentu XML, označovaného také jako vlastnost **DocumentElement** .

```csharp
XmlAttribute attr = doc.DocumentElement.Attributes[0];
```

## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
