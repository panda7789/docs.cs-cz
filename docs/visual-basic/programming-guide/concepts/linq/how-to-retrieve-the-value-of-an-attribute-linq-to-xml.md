---
title: 'Postup: Načtení hodnoty atributu (LINQ do XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 6593639dcdc234ddda808cfdb5e85ebe1a771b62
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248944"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="926cb-102">Postup: Načtení hodnoty atributu (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="926cb-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="926cb-103">Toto téma ukazuje, jak získat hodnotu atributů.</span><span class="sxs-lookup"><span data-stu-id="926cb-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="926cb-104">Existují dva hlavní způsoby: <xref:System.Xml.Linq.XAttribute> Můžete přetypovat na požadovaný typ; explicitní operátor převodu pak převede obsah prvku nebo atributu na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="926cb-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="926cb-105">Případně můžete využít <xref:System.Xml.Linq.XAttribute.Value%2A> ubytování.</span><span class="sxs-lookup"><span data-stu-id="926cb-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="926cb-106">Nicméně, casting je obecně lepší přístup.</span><span class="sxs-lookup"><span data-stu-id="926cb-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="926cb-107">Pokud přetypování atributu s hodnotou s možnou hodnotou null, kód je jednodušší psát při načítání hodnoty atributu, který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="926cb-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="926cb-108">Příklady této techniky naleznete v tématu [How to: Retrieve the Value of a Element (LINQ to XML) (Visual Basic).](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="926cb-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="926cb-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="926cb-109">Example</span></span>  
 <span data-ttu-id="926cb-110">V jazyce Visual Basic můžete použít vlastnost integrovaného atributu k načtení hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="926cb-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="926cb-111">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="926cb-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="926cb-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="926cb-112">Example</span></span>  
 <span data-ttu-id="926cb-113">V jazyce Visual Basic můžete použít vlastnost integrated attribute k nastavení hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="926cb-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="926cb-114">Dále pokud použijete vlastnost integrated attribute k nastavení hodnoty atributu, který neexistuje, bude atribut vytvořen.</span><span class="sxs-lookup"><span data-stu-id="926cb-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="926cb-115">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="926cb-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="926cb-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="926cb-116">Example</span></span>  
 <span data-ttu-id="926cb-117">Následující příklad ukazuje, jak načíst hodnotu atributu, kde je atribut v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="926cb-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="926cb-118">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (Visual Basic).](namespaces-overview-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="926cb-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="926cb-119">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="926cb-119">This example produces the following output:</span></span>  
  
```console  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="926cb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="926cb-120">See also</span></span>

- [<span data-ttu-id="926cb-121">LINQ na osy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="926cb-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
