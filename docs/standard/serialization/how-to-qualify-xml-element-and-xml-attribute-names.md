---
title: "Postupy: určení – Element XML a názvy atributů XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e94b9022e6da29f0aa8deb5534fec6e89d40152a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="c3d8f-102">Postupy: určení – Element XML a názvy atributů XML</span><span class="sxs-lookup"><span data-stu-id="c3d8f-102">How to: Qualify XML Element and XML Attribute Names</span></span>
[<span data-ttu-id="c3d8f-103">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="c3d8f-103">Code Example</span></span>](#cpconworkingwithxmlnamespacesanchor1)  
  
 <span data-ttu-id="c3d8f-104">Obory názvů XML, které obsahují touto instancí <xref:System.Xml.Serialization.XmlSerializerNamespaces> třída musí odpovídat specifikaci W3c (www.w3.org), která je volána "Obory názvů ve formátu XML."</span><span class="sxs-lookup"><span data-stu-id="c3d8f-104">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (www.w3.org) specification called "Namespaces in XML."</span></span>  
  
 <span data-ttu-id="c3d8f-105">Obory názvů XML poskytuje metodu pro kvalifikované názvy elementů XML a atributy ve formátu XML v dokumentech XML.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-105">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="c3d8f-106">Úplný název se skládá z předpony a názvu místní, oddělených středníkem.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-106">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="c3d8f-107">Předpona, která funguje pouze jako zástupný symbol; je mapován na identifikátor URI, který určuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-107">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="c3d8f-108">Kombinace oboru názvů univerzálně spravované identifikátoru URI a místní název vytváří název, který je musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-108">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>  
  
 <span data-ttu-id="c3d8f-109">Po vytvoření instance `XmlSerializerNamespaces` a přidání dvojice názvů do objektu, můžete zadat předpony použitý v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-109">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>  
  
### <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="c3d8f-110">Chcete-li vytvořit kvalifikované názvy v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="c3d8f-110">To create qualified names in an XML document</span></span>  
  
1.  <span data-ttu-id="c3d8f-111">Vytvořit instanci `XmlSerializerNamespaces` třídy.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-111">Create an instance of the `XmlSerializerNamespaces` class.</span></span>  
  
2.  <span data-ttu-id="c3d8f-112">Všechny předpony a dvojice názvů chcete přidat `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-112">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>  
  
3.  <span data-ttu-id="c3d8f-113">Použít odpovídající `System.Xml.Serialization` atribut pro každého člena nebo třída, která <xref:System.Xml.Serialization.XmlSerializer> je k serializaci do dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-113">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>  
  
     <span data-ttu-id="c3d8f-114">Jsou dostupné atributy: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, a <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-114">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>  
  
4.  <span data-ttu-id="c3d8f-115">Nastavte `Namespace` vlastnost každý atribut na jednu z oboru názvů hodnot z `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-115">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>  
  
5.  <span data-ttu-id="c3d8f-116">Předat `XmlSerializerNamespaces` k `Serialize` metodu `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-116">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3d8f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3d8f-117">Example</span></span>  
 <span data-ttu-id="c3d8f-118">Následující příklad vytvoří `XmlSerializerNamespaces`, a přidá dvě dvojice předpony a oboru názvů do objektu.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-118">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="c3d8f-119">Kód vytvoří `XmlSerializer` která je použita k serializaci instancí `Books` třídy.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-119">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="c3d8f-120">Volání kódu `Serialize` metodu se `XmlSerializerNamespaces`, povolení XML tak, aby obsahovala s předponou obory názvů.</span><span class="sxs-lookup"><span data-stu-id="c3d8f-120">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3d8f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3d8f-121">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="c3d8f-122">Nástroj definice schématu XML a serializace XML</span><span class="sxs-lookup"><span data-stu-id="c3d8f-122">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 [<span data-ttu-id="c3d8f-123">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="c3d8f-123">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="c3d8f-124">Třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="c3d8f-124">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)  
 [<span data-ttu-id="c3d8f-125">Atributy, které řídí serializace XML</span><span class="sxs-lookup"><span data-stu-id="c3d8f-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 [<span data-ttu-id="c3d8f-126">Postupy: Zadejte název alternativní elementu pro datový proud XML</span><span class="sxs-lookup"><span data-stu-id="c3d8f-126">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [<span data-ttu-id="c3d8f-127">Postupy: serializaci objektu</span><span class="sxs-lookup"><span data-stu-id="c3d8f-127">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="c3d8f-128">Postupy: deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="c3d8f-128">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
