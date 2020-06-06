---
title: Jak kvalifikovat elementy XML a názvy atributů XML
description: V tomto článku se dozvíte, jak kvalifikovat názvy elementů XML a atributů XML v dokumentech XML.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 6c29e03d9ce28e5b0abc68a5d7e8d82f4485ac93
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "83378415"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="58102-103">Jak kvalifikovat elementy XML a názvy atributů XML</span><span class="sxs-lookup"><span data-stu-id="58102-103">How to qualify XML element and XML attribute names</span></span>

<span data-ttu-id="58102-104">Obory názvů XML obsažené v instancích <xref:System.Xml.Serialization.XmlSerializerNamespaces> třídy musí odpovídat specifikaci konsorcium World Wide Web (W3C), která se nazývá [obory názvů v XML](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="58102-104">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="58102-105">Obory názvů XML poskytuje metodu pro kvalifikované názvy elementů XML a atributy ve formátu XML v dokumentech XML.</span><span class="sxs-lookup"><span data-stu-id="58102-105">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="58102-106">Úplný název se skládá z předpony a názvu místní, oddělených středníkem.</span><span class="sxs-lookup"><span data-stu-id="58102-106">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="58102-107">Předpona, která funguje pouze jako zástupný symbol; je mapován na identifikátor URI, který určuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="58102-107">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="58102-108">Kombinace oboru názvů univerzálně spravované identifikátoru URI a místní název vytváří název, který je musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="58102-108">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="58102-109">Po vytvoření instance `XmlSerializerNamespaces` a přidání dvojice názvů do objektu, můžete zadat předpony použitý v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="58102-109">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="58102-110">Chcete-li vytvořit kvalifikované názvy v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="58102-110">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="58102-111">Vytvořit instanci `XmlSerializerNamespaces` třídy.</span><span class="sxs-lookup"><span data-stu-id="58102-111">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="58102-112">Všechny předpony a dvojice názvů chcete přidat `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="58102-112">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="58102-113">Použít odpovídající `System.Xml.Serialization` atribut pro každého člena nebo třída, která <xref:System.Xml.Serialization.XmlSerializer> je k serializaci do dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="58102-113">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

    <span data-ttu-id="58102-114">Jsou dostupné atributy: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, a <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="58102-114">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="58102-115">Nastavte `Namespace` vlastnost každý atribut na jednu z oboru názvů hodnot z `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="58102-115">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="58102-116">Předat `XmlSerializerNamespaces` k `Serialize` metodu `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="58102-116">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="58102-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="58102-117">Example</span></span>

<span data-ttu-id="58102-118">Následující příklad vytvoří `XmlSerializerNamespaces`, a přidá dvě dvojice předpony a oboru názvů do objektu.</span><span class="sxs-lookup"><span data-stu-id="58102-118">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="58102-119">Kód vytvoří `XmlSerializer` která je použita k serializaci instancí `Books` třídy.</span><span class="sxs-lookup"><span data-stu-id="58102-119">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="58102-120">Volání kódu `Serialize` metodu se `XmlSerializerNamespaces`, povolení XML tak, aby obsahovala s předponou obory názvů.</span><span class="sxs-lookup"><span data-stu-id="58102-120">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Module Program

    Public Sub Main()
        SerializeObject("XmlNamespaces.xml")
    End Sub

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
End Module

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class

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
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Program
{
    public static void Main()
    {
        SerializeObject("XmlNamespaces.xml");
    }

    public static void SerializeObject(string filename)
    {
        var mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        var myNamespaces = new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        var myBook = new Book();
        myBook.TITLE = "A Book Title";
        var myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        var myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter, myBooks, myNamespaces);
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

public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}
```

## <a name="see-also"></a><span data-ttu-id="58102-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="58102-121">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="58102-122">Nástroj definice schématu XML a serializace XML</span><span class="sxs-lookup"><span data-stu-id="58102-122">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="58102-123">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="58102-123">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="58102-124">XmlSerializer – Třída</span><span class="sxs-lookup"><span data-stu-id="58102-124">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="58102-125">Atributy, které řídí serializaci XML</span><span class="sxs-lookup"><span data-stu-id="58102-125">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="58102-126">Postupy: Zadání alternativního názvu elementu pro XML stream</span><span class="sxs-lookup"><span data-stu-id="58102-126">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="58102-127">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="58102-127">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="58102-128">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="58102-128">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
