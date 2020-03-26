---
title: 'Postup: Načtení hodnoty prvku (LINQ do XML)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: b1a61091dc59b403c5d967609e8870492c24347f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248931"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a><span data-ttu-id="ebb05-102">Postup: Načtení hodnoty prvku (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebb05-102">How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ebb05-103">Toto téma ukazuje, jak získat hodnotu prvků.</span><span class="sxs-lookup"><span data-stu-id="ebb05-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="ebb05-104">Existují dva hlavní způsoby, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="ebb05-104">There are two main ways to do this.</span></span> <span data-ttu-id="ebb05-105">Jedním ze způsobů <xref:System.Xml.Linq.XElement> je <xref:System.Xml.Linq.XAttribute> obsazení nebo na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="ebb05-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="ebb05-106">Explicitní operátor převodu pak převede obsah prvku nebo atributu na zadaný typ a přiřadí jej proměnné.</span><span class="sxs-lookup"><span data-stu-id="ebb05-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="ebb05-107">Případně můžete využít <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> ubytování nebo <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> ubytovací zařízení.</span><span class="sxs-lookup"><span data-stu-id="ebb05-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="ebb05-108">S Visual Basic, nejlepší přístup <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> je použití vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ebb05-108">With Visual Basic, the best approach is to use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebb05-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebb05-109">Example</span></span>  
 <span data-ttu-id="ebb05-110">Chcete-li načíst hodnotu prvku, <xref:System.Xml.Linq.XElement> stačí přetypovat objekt na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="ebb05-110">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="ebb05-111">Vždy můžete přetypovat prvek do řetězce takto:</span><span class="sxs-lookup"><span data-stu-id="ebb05-111">You can always cast an element to a string, as follows:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="ebb05-112">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ebb05-112">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="ebb05-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebb05-113">Example</span></span>  
 <span data-ttu-id="ebb05-114">Prvky můžete také přetypovat na jiné typy než řetězec.</span><span class="sxs-lookup"><span data-stu-id="ebb05-114">You can also cast elements to types other than string.</span></span> <span data-ttu-id="ebb05-115">Například pokud máte prvek, který obsahuje celé číslo, můžete `int`přetypovat do , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="ebb05-115">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 <span data-ttu-id="ebb05-116">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ebb05-116">This example produces the following output:</span></span>  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ebb05-117">poskytuje explicitní operátory přetypádky pro `int?` `uint`následující `uint?` `long`datové `long?` `ulong` `ulong?`typy: `float` `float?` `double` `double?` `decimal` `decimal?` `DateTime` `DateTime?` `string` `bool`, , `bool?` `int`, , , , , , , , , , , , , `TimeSpan`, `TimeSpan?`, `GUID`, , , a `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="ebb05-117">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ebb05-118">poskytuje stejné operátory <xref:System.Xml.Linq.XAttribute> přetypádku pro objekty.</span><span class="sxs-lookup"><span data-stu-id="ebb05-118">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebb05-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebb05-119">Example</span></span>  
 <span data-ttu-id="ebb05-120"><xref:System.Xml.Linq.XElement.Value%2A> Vlastnost můžete použít k načtení obsahu prvku:</span><span class="sxs-lookup"><span data-stu-id="ebb05-120">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="ebb05-121">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ebb05-121">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="ebb05-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebb05-122">Example</span></span>  
 <span data-ttu-id="ebb05-123">Někdy se pokusíte načíst hodnotu prvku, i když si nejste jisti, že existuje.</span><span class="sxs-lookup"><span data-stu-id="ebb05-123">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="ebb05-124">V tomto případě při přiřazení přetypovaného prvku typu `string` s možnou hodnotou null (jeden nebo jeden z typů hodnot s možnou hodnotou null v rozhraní .NET Framework), pokud prvek neexistuje, je přiřazená proměnná pouze nastavena na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ebb05-124">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable value types in the .NET Framework), if the element does not exist the assigned variable is just set to `Nothing`.</span></span> <span data-ttu-id="ebb05-125">Následující kód ukazuje, že když prvek může nebo nemusí existovat, je <xref:System.Xml.Linq.XElement.Value%2A> jednodušší použít přetypování než použít vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ebb05-125">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="ebb05-126">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ebb05-126">This code produces the following output:</span></span>  
  
```console  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="ebb05-127">Obecně můžete napsat jednodušší kód při použití přetypování k načtení obsahu prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="ebb05-127">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb05-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebb05-128">See also</span></span>

- [<span data-ttu-id="ebb05-129">LINQ na osy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebb05-129">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
