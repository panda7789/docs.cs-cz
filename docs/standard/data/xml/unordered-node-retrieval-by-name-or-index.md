---
title: "Neseřazený uzlu načítání podle názvu nebo Index"
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
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b80f48d425623c9e6cdf1431ceb4a37efe7f2465
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="7c097-102">Neseřazený uzlu načítání podle názvu nebo Index</span><span class="sxs-lookup"><span data-stu-id="7c097-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="7c097-103">**XmlNamedNodeMap** je popsána ve specifikaci World Wide Web Consortium (W3C) jako NamedNodeMap a je potřeba pro zpracování neuspořádaný sada uzlů možnost odkaz uzly index nebo název.</span><span class="sxs-lookup"><span data-stu-id="7c097-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="7c097-104">Jediným způsobem, jak máte přístup **XmlNamedNodeMap** je při **XmlNamedNodeMap** je vrácen prostřednictvím metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7c097-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="7c097-105">Existují tři metody nebo vlastnosti, které vracejí **XmlNamedNodeMap**:</span><span class="sxs-lookup"><span data-stu-id="7c097-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
-   <span data-ttu-id="7c097-106">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="7c097-106">XmlElement.Attributes</span></span>  
  
-   <span data-ttu-id="7c097-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="7c097-107">XmlDocumentType.Entities</span></span>  
  
-   <span data-ttu-id="7c097-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="7c097-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="7c097-109">Například **XmlDocumentType.Entities** vlastnost získá kolekci **XmlEntity** uzly deklarované v deklarace typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7c097-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="7c097-110">Tato kolekce se vrátí jako **XmlNamedNodeMap**, a můžete iteraci prostřednictvím kolekce s použitím **počet** vlastnost a zobrazení informací o entitě.</span><span class="sxs-lookup"><span data-stu-id="7c097-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="7c097-111">Příklad iterace v rámci **XmlNamedNodeMap**, najdete v části <xref:System.Xml.XmlDocumentType.Entities%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c097-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="7c097-112">**XmlAttributeCollection** je odvozený od **XmlNamedNodeMap** a pouze atributy lze měnit, zatímco zápisy a entity jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="7c097-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="7c097-113">Pomocí **XmlNamedNodeMap** pro atributy, můžete získat uzly pro tyto atributy založené na jejich názvy XML.</span><span class="sxs-lookup"><span data-stu-id="7c097-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="7c097-114">Tímto způsobem snadno pro manipulaci s kolekci atributů na uzlu elementu.</span><span class="sxs-lookup"><span data-stu-id="7c097-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="7c097-115">To může být rozdíl od aktualizovaného přímo **XmlNodeList**, který je navíc implementovaná **rozhraní IEnumerable** rozhraní, ale index přistupující objekt než řetězec.</span><span class="sxs-lookup"><span data-stu-id="7c097-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="7c097-116">**RemoveNamedItem** a **SetNamedItem** metody se používají pouze proti **XmlAttributeCollection**.</span><span class="sxs-lookup"><span data-stu-id="7c097-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="7c097-117">Přidání nebo odebrání z kolekce atributů, jestli se používá **AttributeCollection** nebo **XmlNamedNodeMap** implementace, upraví kolekce atributů v elementu.</span><span class="sxs-lookup"><span data-stu-id="7c097-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="7c097-118">Následující příklad kódu ukazuje, jak přesunout atribut a vytvořit nový atribut.</span><span class="sxs-lookup"><span data-stu-id="7c097-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
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
  
 <span data-ttu-id="7c097-119">Chcete-li zobrazit příklad další kód, který ukazuje atribut odebírán z **AttributeCollection**, najdete v části [XmlNamedNodeMap.RemoveNamedItem metoda](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span><span class="sxs-lookup"><span data-stu-id="7c097-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span></span> <span data-ttu-id="7c097-120">Další informace o vlastnostech a metody najdete v tématu [XmlNamedNodeMap členy](AllMembers.T:System.Xml.XmlNamedNodeMap).</span><span class="sxs-lookup"><span data-stu-id="7c097-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](AllMembers.T:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c097-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c097-121">See Also</span></span>  
 [<span data-ttu-id="7c097-122">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="7c097-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
