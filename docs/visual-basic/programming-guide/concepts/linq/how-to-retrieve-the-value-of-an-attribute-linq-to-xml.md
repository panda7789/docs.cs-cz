---
title: 'How to: Retrieve the Value of an Attribute (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 693746c24488029415e68a7c954143a86b7dbb16
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352403"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="d6b9e-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6b9e-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d6b9e-103">This topic shows how to obtain the value of attributes.</span><span class="sxs-lookup"><span data-stu-id="d6b9e-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="d6b9e-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span><span class="sxs-lookup"><span data-stu-id="d6b9e-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="d6b9e-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span><span class="sxs-lookup"><span data-stu-id="d6b9e-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="d6b9e-106">However, casting is generally the better approach.</span><span class="sxs-lookup"><span data-stu-id="d6b9e-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="d6b9e-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span><span class="sxs-lookup"><span data-stu-id="d6b9e-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="d6b9e-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d6b9e-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6b9e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b9e-109">Example</span></span>  
 <span data-ttu-id="d6b9e-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span><span class="sxs-lookup"><span data-stu-id="d6b9e-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="d6b9e-111">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="d6b9e-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="d6b9e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b9e-112">Example</span></span>  
 <span data-ttu-id="d6b9e-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span><span class="sxs-lookup"><span data-stu-id="d6b9e-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="d6b9e-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span><span class="sxs-lookup"><span data-stu-id="d6b9e-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="d6b9e-115">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="d6b9e-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="d6b9e-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b9e-116">Example</span></span>  
 <span data-ttu-id="d6b9e-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span><span class="sxs-lookup"><span data-stu-id="d6b9e-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="d6b9e-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d6b9e-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d6b9e-119">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="d6b9e-119">This example produces the following output:</span></span>  
  
```console  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6b9e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6b9e-120">See also</span></span>

- [<span data-ttu-id="d6b9e-121">LINQ to XML Axes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6b9e-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
