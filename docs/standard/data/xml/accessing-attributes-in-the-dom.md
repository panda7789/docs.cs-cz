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
ms.openlocfilehash: 272c224c8a1c5061392856685f374237f8a10579
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956877"
---
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="0d4d2-102">Přístup k atributům v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="0d4d2-102">Accessing Attributes in the DOM</span></span>

<span data-ttu-id="0d4d2-103">Atributy jsou vlastnosti prvku, nikoli podřízené položky elementu.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="0d4d2-104">Toto rozlišení je důležité z důvodu metod, které slouží k navigaci na stejné úrovni, nadřazených a podřízených uzlech model DOM (Document Object Model) XML (DOM).</span><span class="sxs-lookup"><span data-stu-id="0d4d2-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="0d4d2-105">Například metody **PreviousSibling** a **NextSibling** se nepoužívají k přechodu z prvku na atribut nebo mezi atributy.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="0d4d2-106">Místo toho je atribut vlastností elementu a je vlastněn prvkem, má vlastnost **OwnerElement** , nikoli vlastnost **ParentNode** a má odlišné metody navigace.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>

<span data-ttu-id="0d4d2-107">Pokud je aktuální uzel prvkem, použijte metodu **HasAttribute** , abyste viděli, zda jsou k elementu přidruženy žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="0d4d2-108">Jakmile je známo, že element má atributy, existuje více metod pro přístup k atributům.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="0d4d2-109">Chcete-li načíst jediný atribut z prvku, můžete použít metody **GetAttribute** a **GetAttributeNode** třídy **XmlElement** nebo můžete získat všechny atributy do kolekce.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="0d4d2-110">Získání kolekce je užitečné, pokud potřebujete iterovat v kolekci.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="0d4d2-111">Pokud chcete všechny atributy z prvku, použijte vlastnost **atributů** elementu pro načtení všech atributů do kolekce.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>

## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="0d4d2-112">Načítání všech atributů do kolekce</span><span class="sxs-lookup"><span data-stu-id="0d4d2-112">Retrieving All Attributes into a Collection</span></span>

<span data-ttu-id="0d4d2-113">Chcete-li, aby všechny atributy uzlu elementu byly vloženy do kolekce, zavolejte vlastnost **XmlElement. Attributes** .</span><span class="sxs-lookup"><span data-stu-id="0d4d2-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="0d4d2-114">Tím se získá objekt **XmlAttributeCollection** , který obsahuje všechny atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="0d4d2-115">Třída **XmlAttributeCollection** dědí z mapy **XmlNamedNode** .</span><span class="sxs-lookup"><span data-stu-id="0d4d2-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="0d4d2-116">Proto metody a vlastnosti, které jsou k dispozici v kolekci, obsahují kromě metod a vlastností specifických pro třídu **XmlAttributeCollection** , jako je například vlastnost **ItemOf** nebo **Append** metoda.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="0d4d2-117">Každá položka v kolekci atributů představuje uzel **XmlAttribute** .</span><span class="sxs-lookup"><span data-stu-id="0d4d2-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="0d4d2-118">Chcete-li najít počet atributů prvku, získat kolekci **XmlAttribute**a použít vlastnost **Count** k zobrazení, kolik uzlů **XmlAttribute** je v kolekci.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>

<span data-ttu-id="0d4d2-119">Následující příklad kódu ukazuje, jak načíst kolekci atributů a pomocí metody **Count** pro index smyčky, iterovat přes něj.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="0d4d2-120">Kód pak ukazuje, jak načíst jediný atribut z kolekce a zobrazit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>

```vb
Imports System
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

<span data-ttu-id="0d4d2-121">V tomto příkladu se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0d4d2-121">This example displays the following output:</span></span>

<span data-ttu-id="0d4d2-122">**Output**</span><span class="sxs-lookup"><span data-stu-id="0d4d2-122">**Output**</span></span>

<span data-ttu-id="0d4d2-123">Zobrazí všechny atributy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-123">Display all the attributes in the collection.</span></span>

```console
genre = novel
ISBN = 1-861001-57-5
misc = sale item
Display the attribute information.
sale item
```

<span data-ttu-id="0d4d2-124">Informace v kolekci atributů lze načíst podle názvu nebo čísla indexu.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="0d4d2-125">Výše uvedený příklad ukazuje, jak načíst data podle názvu.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="0d4d2-126">Další příklad ukazuje, jak načíst data podle čísla indexu.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-126">The next example shows how to retrieve data by index number.</span></span>

<span data-ttu-id="0d4d2-127">Vzhledem k tomu, že objekt **XmlAttributeCollection** je kolekce a lze provést iteraci pomocí názvu nebo indexu, tento příklad ukazuje výběr prvního atributu z kolekce pomocí indexu založeného na nule a použití následujícího souboru **baseUri. XML**jako vstupu.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>

### <a name="input"></a><span data-ttu-id="0d4d2-128">Vstup</span><span class="sxs-lookup"><span data-stu-id="0d4d2-128">Input</span></span>

```xml
<!-- XML fragment -->
<book genre="novel">
  <title>Pride And Prejudice</title>
</book>
```

```vb
Option Explicit On
Option Strict On

Imports System
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

## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="0d4d2-129">Načtení jednotlivého uzlu atributu</span><span class="sxs-lookup"><span data-stu-id="0d4d2-129">Retrieving an Individual Attribute Node</span></span>

<span data-ttu-id="0d4d2-130">Chcete-li načíst jeden uzel atributu z prvku, je použita metoda <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="0d4d2-131">Vrátí objekt typu **XmlAttribute**.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="0d4d2-132">Po získání **atributu XmlAttribute**jsou všechny metody a vlastnosti, které jsou k dispozici ve třídě <xref:System.Xml.XmlAttribute?displayProperty=nameWithType>, k dispozici pro tento objekt, jako je například hledání **OwnerElement**.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>

```vb
Imports System
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

<span data-ttu-id="0d4d2-133">Můžete také provést jak je znázorněno v předchozím příkladu, kde je jeden uzel atributu načten z kolekce atributů.</span><span class="sxs-lookup"><span data-stu-id="0d4d2-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="0d4d2-134">Následující příklad kódu ukazuje, jak lze zapsat jeden řádek kódu pro načtení jednoho atributu pomocí čísla indexu z kořene stromu dokumentu XML, označovaného také jako vlastnost **DocumentElement** .</span><span class="sxs-lookup"><span data-stu-id="0d4d2-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>

```csharp
XmlAttribute attr = doc.DocumentElement.Attributes[0];
```

## <a name="see-also"></a><span data-ttu-id="0d4d2-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d4d2-135">See also</span></span>

- [<span data-ttu-id="0d4d2-136">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="0d4d2-136">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
