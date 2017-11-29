---
title: "Postupy: načtení hodnoty atributu (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5eed0c34f79a4a338dda7b26049f2c1510443736
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="1d01a-102">Postupy: načtení hodnoty atributu (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d01a-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="1d01a-103">Toto téma ukazuje, jak získat hodnotu atributů.</span><span class="sxs-lookup"><span data-stu-id="1d01a-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="1d01a-104">Existují dva hlavní způsoby: může odevzdat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitní převod potom převede obsah elementu nebo atributu zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="1d01a-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="1d01a-105">Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1d01a-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="1d01a-106">Přetypování je ale obecně lepší přístup.</span><span class="sxs-lookup"><span data-stu-id="1d01a-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="1d01a-107">Pokud jste přetypovat atribut typu s povolenou hodnotou Null, kód je jednodušší při načítání hodnoty atributu, který může nebo nemusí existovat zápis.</span><span class="sxs-lookup"><span data-stu-id="1d01a-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="1d01a-108">Příklady tento postup najdete v tématu [postupy: načtení hodnoty elementu (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1d01a-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d01a-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d01a-109">Example</span></span>  
 <span data-ttu-id="1d01a-110">Vlastnost integrované atribut v jazyce Visual Basic slouží k načtení hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="1d01a-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="1d01a-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1d01a-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="1d01a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d01a-112">Example</span></span>  
 <span data-ttu-id="1d01a-113">Vlastnost integrované atribut v jazyce Visual Basic slouží k nastavení hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="1d01a-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="1d01a-114">Dál platí Pokud použijete vlastnost integrované atribut nastavit hodnotu atributu, který ještě neexistuje, bude vytvořena atribut.</span><span class="sxs-lookup"><span data-stu-id="1d01a-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="1d01a-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1d01a-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="1d01a-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d01a-116">Example</span></span>  
 <span data-ttu-id="1d01a-117">Následující příklad ukazuje, jak načíst hodnotu atributu kde atributu je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d01a-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="1d01a-118">Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="1d01a-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="1d01a-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1d01a-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d01a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d01a-120">See Also</span></span>  
 [<span data-ttu-id="1d01a-121">Technologie LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d01a-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
