---
title: "Přístup k atributům v modelu DOM"
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
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f134761c4dadcef4692194293c8c99899bb6be2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="63589-102">Přístup k atributům v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="63589-102">Accessing Attributes in the DOM</span></span>
<span data-ttu-id="63589-103">Atributy jsou vlastnosti elementu, ne podřízených objektů daného elementu.</span><span class="sxs-lookup"><span data-stu-id="63589-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="63589-104">Tento rozdíl je důležitý kvůli metody použité k přejděte na stejné úrovni, nadřazené a podřízené uzly z XML modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="63589-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="63589-105">Například **PreviousSibling** a **NextSibling** metody nepoužívají se k přejděte z prvku, atributu nebo mezi atributy.</span><span class="sxs-lookup"><span data-stu-id="63589-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="63589-106">Místo toho atribut je vlastnost elementu a vlastní element, má **OwnerElement** vlastnost a ne **parentNode** vlastnost, a má odlišné metody navigace.</span><span class="sxs-lookup"><span data-stu-id="63589-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>  
  
 <span data-ttu-id="63589-107">Je-li aktuální uzel elementu, použijte **HasAttribute** metoda, pokud jsou k dispozici žádné atributy přidružené k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="63589-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="63589-108">Jakmile se ví, že element má atributy, existuje více metod pro přístup k atributům.</span><span class="sxs-lookup"><span data-stu-id="63589-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="63589-109">Chcete-li získat jeden atribut z elementu, můžete použít **GetAttribute** a **GetAttributeNode** metody **XmlElement** nebo můžete získat všechny atributy do kolekce.</span><span class="sxs-lookup"><span data-stu-id="63589-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="63589-110">Získání kolekce je užitečné, pokud potřebujete Iterujte přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="63589-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="63589-111">Pokud chcete, aby všechny atributy z elementu, použijte **atributy** vlastnost elementu pro načtení všech atributů do kolekce.</span><span class="sxs-lookup"><span data-stu-id="63589-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>  
  
## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="63589-112">Načítání všechny atributy do kolekce</span><span class="sxs-lookup"><span data-stu-id="63589-112">Retrieving All Attributes into a Collection</span></span>  
 <span data-ttu-id="63589-113">Pokud chcete, všechny atributy uzlu elementu uvést do kolekce, zavolejte **XmlElement.Attributes** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="63589-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="63589-114">To získá **XmlAttributeCollection** obsahující všechny atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="63589-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="63589-115">**XmlAttributeCollection** třída dědí z **XmlNamedNode** mapy.</span><span class="sxs-lookup"><span data-stu-id="63589-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="63589-116">Proto metody a vlastnosti, které jsou k dispozici v kolekci zahrnují ty, které jsou k dispozici na mapě pojmenované uzlu kromě metody a vlastnosti specifické pro **XmlAttributeCollection** třídy, jako **ItemOf**  vlastnost nebo **připojení** metoda.</span><span class="sxs-lookup"><span data-stu-id="63589-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="63589-117">Představuje každou položku v kolekci atributů **XmlAttribute** uzlu.</span><span class="sxs-lookup"><span data-stu-id="63589-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="63589-118">Počet atributů v elementu najdete získat **XmlAttributeCollection**a použít **počet** vlastnosti kolik **XmlAttribute** jsou uzly v kolekci.</span><span class="sxs-lookup"><span data-stu-id="63589-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>  
  
 <span data-ttu-id="63589-119">Následující příklad kódu ukazuje, jak načíst atribut kolekce a pomocí **počet** metoda pro opakování index iteraci nad ním.</span><span class="sxs-lookup"><span data-stu-id="63589-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="63589-120">Kód pak ukazuje, jak načíst jeden atribut z kolekce a zobrazit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="63589-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>  
  
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
  
 <span data-ttu-id="63589-121">Tento příklad zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="63589-121">This example displays the following output:</span></span>  
  
 <span data-ttu-id="63589-122">**Output**</span><span class="sxs-lookup"><span data-stu-id="63589-122">**Output**</span></span>  
  
 <span data-ttu-id="63589-123">Zobrazte všechny atributy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="63589-123">Display all the attributes in the collection.</span></span>  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 <span data-ttu-id="63589-124">Informace v kolekci atributů může načíst název nebo číslo indexu.</span><span class="sxs-lookup"><span data-stu-id="63589-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="63589-125">Výše uvedený příklad ukazuje, jak načíst data podle názvu.</span><span class="sxs-lookup"><span data-stu-id="63589-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="63589-126">Další příklad ukazuje, jak načíst data tak, že číslo indexu.</span><span class="sxs-lookup"><span data-stu-id="63589-126">The next example shows how to retrieve data by index number.</span></span>  
  
 <span data-ttu-id="63589-127">Protože **XmlAttributeCollection** je kolekce a můžete vstupní nepřevezme index nebo název tento příklad ukazuje, výběrem první atribut z kolekce pomocí index počítaný od nuly nebo pomocí následující soubor, **baseuri.xml**, jako vstupní.</span><span class="sxs-lookup"><span data-stu-id="63589-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>  
  
### <a name="input"></a><span data-ttu-id="63589-128">Vstup</span><span class="sxs-lookup"><span data-stu-id="63589-128">Input</span></span>  
  
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
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
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
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="63589-129">Načítání uzlu jednotlivých atributu.</span><span class="sxs-lookup"><span data-stu-id="63589-129">Retrieving an Individual Attribute Node</span></span>  
 <span data-ttu-id="63589-130">Načíst uzlu jeden atribut z elementu, <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> metoda se používá.</span><span class="sxs-lookup"><span data-stu-id="63589-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="63589-131">Vrátí objekt typu **XmlAttribute**.</span><span class="sxs-lookup"><span data-stu-id="63589-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="63589-132">Až budete mít **XmlAttribute**, všechny metody a vlastnosti, které jsou k dispozici v <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> třídy jsou k dispozici na tento objekt, jako je hledání **OwnerElement**.</span><span class="sxs-lookup"><span data-stu-id="63589-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>  
  
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
  
 <span data-ttu-id="63589-133">Můžete také provést jak je znázorněno v předchozím příkladu, kde jeden atribut uzlu se načítají z kolekce atributů.</span><span class="sxs-lookup"><span data-stu-id="63589-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="63589-134">Následující příklad kódu ukazuje způsob, jakým jeden řádek kódu je možné zapsat do načíst jeden atribut číslem indexu z kořene dokumentu XML stromu, označované také jako **prvek DocumentElement** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="63589-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a><span data-ttu-id="63589-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="63589-135">See Also</span></span>  
 [<span data-ttu-id="63589-136">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="63589-136">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
