---
title: Načtení uzlů bez stanoveného pořadí podle názvu nebo indexu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 577de6b60e579b37eb54ea69de72f3534f1d23ac
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628901"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="3c8e2-102">Načtení uzlů bez stanoveného pořadí podle názvu nebo indexu</span><span class="sxs-lookup"><span data-stu-id="3c8e2-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="3c8e2-103">**XmlNamedNodeMap** je popsána ve specifikaci konsorcium World Wide Web (W3C) jako NamedNodeMap a je vyžadována pro zpracování neuspořádané sady uzlů s možností odkazovat uzly podle jejich názvu nebo indexu.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="3c8e2-104">Jediným způsobem, jakým máte přístup k **XmlNamedNodeMap** , je, že **XmlNamedNodeMap** je vrácen prostřednictvím metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="3c8e2-105">Existují tři metody nebo vlastnosti, které vracejí **XmlNamedNodeMap**:</span><span class="sxs-lookup"><span data-stu-id="3c8e2-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
- <span data-ttu-id="3c8e2-106">XmlElement. Attributes</span><span class="sxs-lookup"><span data-stu-id="3c8e2-106">XmlElement.Attributes</span></span>  
  
- <span data-ttu-id="3c8e2-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="3c8e2-107">XmlDocumentType.Entities</span></span>  
  
- <span data-ttu-id="3c8e2-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="3c8e2-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="3c8e2-109">Například vlastnost **XmlDocumentType. Entities** Získá kolekci uzlů **XmlEntity** deklarovaných v deklaraci typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="3c8e2-110">Tato kolekce se vrátí jako **XmlNamedNodeMap**a můžete iterovat v rámci kolekce s použitím vlastnosti **Count** a informací o zobrazení entity.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="3c8e2-111">Příklad iterace prostřednictvím **XmlNamedNodeMap**naleznete v tématu <xref:System.Xml.XmlDocumentType.Entities%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="3c8e2-112">**Atribut XmlAttributeCollection** je odvozen z **XmlNamedNodeMap** a pouze atributy lze upravovat, zatímco zápisy a entity jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="3c8e2-113">Pomocí **XmlNamedNodeMap** pro atributy můžete získat uzly pro tyto atributy na základě jejich názvů XML.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="3c8e2-114">To poskytuje snadnou metodu pro manipulaci s kolekcí atributů v uzlu element.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="3c8e2-115">To může být kontrast přímo s **XmlNodeList**, které také implementuje rozhraní **IEnumerable** , ale s objektem pro přístup k indexu místo řetězce.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="3c8e2-116">Metody **RemoveNamedItem** a **SetNamedItem** se používají pouze proti **atributu XmlAttributeCollection**.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="3c8e2-117">Přidání nebo odebrání kolekce atributů bez ohledu na to, zda použití **atributucollection** nebo implementace **XmlNamedNodeMap** , upraví kolekci atributů na elementu.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="3c8e2-118">Následující příklad kódu ukazuje, jak přesunout atribut a vytvořit nový atribut.</span><span class="sxs-lookup"><span data-stu-id="3c8e2-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );           
  
    }  
}  
```  
  
 <span data-ttu-id="3c8e2-119">Chcete-li zobrazit další příklad kódu, který ukazuje odebrání atributu zcollection **atributucollection**, viz [Metoda XmlNamedNodeMap. RemoveNamedItem](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span><span class="sxs-lookup"><span data-stu-id="3c8e2-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span></span> <span data-ttu-id="3c8e2-120">Další informace o metodách a vlastnostech naleznete v tématu [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).</span><span class="sxs-lookup"><span data-stu-id="3c8e2-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c8e2-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c8e2-121">See also</span></span>

- [<span data-ttu-id="3c8e2-122">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="3c8e2-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
