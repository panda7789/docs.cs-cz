---
title: 'Postupy: načtení hodnoty atributu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 693746c24488029415e68a7c954143a86b7dbb16
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352403"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="c3cd0-102">Postupy: načtení hodnoty atributu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3cd0-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c3cd0-103">V tomto tématu se dozvíte, jak získat hodnotu atributů.</span><span class="sxs-lookup"><span data-stu-id="c3cd0-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="c3cd0-104">Existují dva hlavní způsoby: <xref:System.Xml.Linq.XAttribute> můžete přetypovat na požadovaný typ; operátor explicitního převodu pak převede obsah elementu nebo atributu na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="c3cd0-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="c3cd0-105">Alternativně můžete použít vlastnost <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3cd0-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="c3cd0-106">Přetypování je však všeobecně lepším přístupem.</span><span class="sxs-lookup"><span data-stu-id="c3cd0-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="c3cd0-107">Pokud přetypování atributu na typ s možnou hodnotou null, kód je jednodušší zapsat při načítání hodnoty atributu, který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="c3cd0-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="c3cd0-108">Příklady této techniky naleznete v tématu [How to: načtení hodnoty elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c3cd0-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3cd0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3cd0-109">Example</span></span>  
 <span data-ttu-id="c3cd0-110">V Visual Basic můžete použít vlastnost integrovaného atributu k načtení hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="c3cd0-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="c3cd0-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c3cd0-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="c3cd0-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3cd0-112">Example</span></span>  
 <span data-ttu-id="c3cd0-113">V Visual Basic můžete použít vlastnost integrovaného atributu k nastavení hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="c3cd0-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="c3cd0-114">Pokud použijete vlastnost integrovaného atributu k nastavení hodnoty atributu, který neexistuje, bude vytvořen atribut.</span><span class="sxs-lookup"><span data-stu-id="c3cd0-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="c3cd0-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c3cd0-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="c3cd0-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3cd0-116">Example</span></span>  
 <span data-ttu-id="c3cd0-117">Následující příklad ukazuje, jak načíst hodnotu atributu, kde je atribut v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c3cd0-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="c3cd0-118">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c3cd0-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="c3cd0-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c3cd0-119">This example produces the following output:</span></span>  
  
```console  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3cd0-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3cd0-120">See also</span></span>

- [<span data-ttu-id="c3cd0-121">LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3cd0-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
