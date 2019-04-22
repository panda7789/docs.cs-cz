---
title: 'Postupy: Načtení hodnoty elementu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: 490e98134497836e0751e48949d4dceda41bcbf3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814078"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a><span data-ttu-id="c620a-102">Postupy: Načtení hodnoty elementu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c620a-102">How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c620a-103">Toto téma ukazuje, jak má být získána hodnota prvků.</span><span class="sxs-lookup"><span data-stu-id="c620a-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="c620a-104">Chcete-li to provést dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="c620a-104">There are two main ways to do this.</span></span> <span data-ttu-id="c620a-105">Jedním ze způsobů je přetypování <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> do požadovaného typu.</span><span class="sxs-lookup"><span data-stu-id="c620a-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="c620a-106">Operátor explicitního převodu potom převede obsah elementu nebo atributu na zadaný typ a přiřadí ji do proměnné.</span><span class="sxs-lookup"><span data-stu-id="c620a-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="c620a-107">Alternativně můžete použít <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost nebo <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c620a-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="c620a-108">Pomocí jazyka Visual Basic, nejlepším řešením je použít <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c620a-108">With Visual Basic, the best approach is to use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c620a-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c620a-109">Example</span></span>  
 <span data-ttu-id="c620a-110">K načtení hodnoty prvku, jenom udělíte <xref:System.Xml.Linq.XElement> objekt požadovaného typu.</span><span class="sxs-lookup"><span data-stu-id="c620a-110">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="c620a-111">Element na řetězec, můžete přetypovat vždy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c620a-111">You can always cast an element to a string, as follows:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="c620a-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c620a-112">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="c620a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c620a-113">Example</span></span>  
 <span data-ttu-id="c620a-114">Také můžete přetypovat prvky na typy jiné než řetězec.</span><span class="sxs-lookup"><span data-stu-id="c620a-114">You can also cast elements to types other than string.</span></span> <span data-ttu-id="c620a-115">Například pokud máte element, který obsahuje celé číslo, lze jej přetypovat na `int`, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="c620a-115">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 <span data-ttu-id="c620a-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c620a-116">This example produces the following output:</span></span>  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c620a-117">poskytuje explicitní přetypování operátory pro následující typy dat: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?` , `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, a `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="c620a-117">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c620a-118">poskytuje stejné operátory přetypování pro <xref:System.Xml.Linq.XAttribute> objekty.</span><span class="sxs-lookup"><span data-stu-id="c620a-118">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c620a-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="c620a-119">Example</span></span>  
 <span data-ttu-id="c620a-120">Můžete použít <xref:System.Xml.Linq.XElement.Value%2A> vlastnost načíst obsah elementu:</span><span class="sxs-lookup"><span data-stu-id="c620a-120">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="c620a-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c620a-121">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="c620a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="c620a-122">Example</span></span>  
 <span data-ttu-id="c620a-123">Někdy pokusu o načtení hodnoty elementu, i když si nejste jisti, že objekt že existuje.</span><span class="sxs-lookup"><span data-stu-id="c620a-123">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="c620a-124">V takovém případě když přiřadíte elementu převedena na typ s možnou hodnotou Null (buď `string` nebo jeden z typů s povolenou hodnotou Null v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), pokud element neexistuje přiřazená proměnná je nastavená pouze na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c620a-124">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `Nothing`.</span></span> <span data-ttu-id="c620a-125">Následující kód ukazuje, že když element může nebo nemusí existovat, je jednodušší použít přetypování než <xref:System.Xml.Linq.XElement.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c620a-125">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 <span data-ttu-id="c620a-126">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c620a-126">This code produces the following output:</span></span>  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="c620a-127">Obecně platí můžete napsat kód jednodušší při použití přetypování načíst obsah elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="c620a-127">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c620a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c620a-128">See also</span></span>

- [<span data-ttu-id="c620a-129">Osy LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c620a-129">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
