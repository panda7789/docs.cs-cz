---
title: 'Postupy: zařazení – Element XML a názvy atributů XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 3c477923387e5a28dcc14b44b0f77bb6acb686e5
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326108"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a>Postupy: zařazení – Element XML a názvy atributů XML

Obory názvů XML, které obsahují touto instancí <xref:System.Xml.Serialization.XmlSerializerNamespaces> třída musí odpovídat specifikaci World Wide Web Consortium (W3C) volá [obory názvů v XML](https://www.w3.org/TR/REC-xml-names/).

Obory názvů XML poskytuje metodu pro kvalifikované názvy elementů XML a atributy ve formátu XML v dokumentech XML. Úplný název se skládá z předpony a názvu místní, oddělených středníkem. Předpona, která funguje pouze jako zástupný symbol; je mapován na identifikátor URI, který určuje obor názvů. Kombinace oboru názvů univerzálně spravované identifikátoru URI a místní název vytváří název, který je musí být jedinečný.

Po vytvoření instance `XmlSerializerNamespaces` a přidání dvojice názvů do objektu, můžete zadat předpony použitý v dokumentu XML.

## <a name="to-create-qualified-names-in-an-xml-document"></a>Chcete-li vytvořit kvalifikované názvy v dokumentu XML

1. Vytvořit instanci `XmlSerializerNamespaces` třídy.

2. Všechny předpony a dvojice názvů chcete přidat `XmlSerializerNamespaces`.

3. Použít odpovídající `System.Xml.Serialization` atribut pro každého člena nebo třída, která <xref:System.Xml.Serialization.XmlSerializer> je k serializaci do dokumentu XML.

  Jsou dostupné atributy: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, a <xref:System.Xml.Serialization.XmlTypeAttribute>.

4. Nastavte `Namespace` vlastnost každý atribut na jednu z oboru názvů hodnot z `XmlSerializerNamespaces`.

5. Předat `XmlSerializerNamespaces` k `Serialize` metodu `XmlSerializer`.

## <a name="example"></a>Příklad

Následující příklad vytvoří `XmlSerializerNamespaces`, a přidá dvě dvojice předpony a oboru názvů do objektu. Kód vytvoří `XmlSerializer` která je použita k serializaci instancí `Books` třídy. Volání kódu `Serialize` metodu se `XmlSerializerNamespaces`, povolení XML tak, aby obsahovala s předponou obory názvů.

```vb
Option Explicit
public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}

Option Strict

Imports System
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Class Run

    Public Shared Sub Main()
        Dim test As New Run()
        test.SerializeObject("XmlNamespaces.xml")
    End Sub 'Main

    Public Sub SerializeObject(filename As String)
        Dim mySerializer As New XmlSerializer(GetType(Books))
        ' Writing a file requires a TextWriter.
        Dim myWriter As New StreamWriter(filename)

        ' Creates an XmlSerializerNamespaces and adds two
        ' prefix-namespace pairs.
        Dim myNamespaces As New XmlSerializerNamespaces()
        myNamespaces.Add("books", "http://www.cpandl.com")
        myNamespaces.Add("money", "http://www.cohowinery.com")

        ' Creates a Book.
        Dim myBook As New Book()
        myBook.TITLE = "A Book Title"
        Dim myPrice As New Price()
        myPrice.price = CDec(9.95)
        myPrice.currency = "US Dollar"
        myBook.PRICE = myPrice
        Dim myBooks As New Books()
        myBooks.Book = myBook
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)
        myWriter.Close()
    End Sub
End Class

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class 'Books

<XmlType([Namespace] := "http://www.cpandl.com")> _
Public Class Book

    <XmlElement([Namespace] := "http://www.cpandl.com")> _
    Public TITLE As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public PRICE As Price
End Class

Public Class Price
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _
    Public currency As String
    Public <XmlElement([Namespace] := "http://www.cohowinery.com")> _
        price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Run
{
    public static void Main()
    {
        Run test = new Run();
        test.SerializeObject("XmlNamespaces.xml");
    }
    public void SerializeObject(string filename)
    {
        XmlSerializer mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        XmlSerializerNamespaces myNamespaces =
        new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        Book myBook = new Book();
        myBook.TITLE = "A Book Title";
        Price myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        Books myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter,myBooks,myNamespaces);
        myWriter.Close();
    }
}

public class Books
{
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public Book Book;
}

[XmlType(Namespace ="http://www.cpandl.com")]
public class Book
{
    [XmlElement(Namespace = "http://www.cpandl.com")]
    public string TITLE;
    [XmlElement(Namespace ="http://www.cohowinery.com")]
    public Price PRICE;
}
```

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Serialization.XmlSerializer>
- [Nástroj pro definici schématu XML a serializace XML](the-xml-schema-definition-tool-and-xml-serialization.md)
- [Představení serializace XML](introducing-xml-serialization.md)
- [Třídy XmlSerializer](xref:System.Xml.Serialization.XmlSerializer)
- [Seznam atributů řídících serializaci XML](attributes-that-control-xml-serialization.md)
- [Postupy: Zadání alternativního názvu elementu pro XML stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Postupy: Serializace objektu](how-to-serialize-an-object.md)
- [Postupy: Deserializace objektu](how-to-deserialize-an-object.md)
