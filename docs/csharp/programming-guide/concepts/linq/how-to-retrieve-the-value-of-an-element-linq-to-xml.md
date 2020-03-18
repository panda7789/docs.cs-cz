---
title: Jak načíst hodnotu prvku (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 6f2d355eac9914cd4c03d3a4521992b346b92f0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168684"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="b0a5d-102">Jak načíst hodnotu prvku (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b0a5d-102">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b0a5d-103">Toto téma ukazuje, jak získat hodnotu prvků.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="b0a5d-104">Existují dva hlavní způsoby, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-104">There are two main ways to do this.</span></span> <span data-ttu-id="b0a5d-105">Jedním ze způsobů <xref:System.Xml.Linq.XElement> je <xref:System.Xml.Linq.XAttribute> obsazení nebo na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="b0a5d-106">Explicitní operátor převodu pak převede obsah prvku nebo atributu na zadaný typ a přiřadí jej proměnné.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="b0a5d-107">Případně můžete využít <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> ubytování nebo <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> ubytovací zařízení.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="b0a5d-108">S C#, nicméně, casting je obecně lepší přístup.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-108">With C#, however, casting is generally the better approach.</span></span> <span data-ttu-id="b0a5d-109">Pokud přetypování prvku nebo atributu na typ s možnou hodnotou null, kód je jednodušší psát při načítání hodnoty prvku (nebo atribut), který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-109">If you cast the element or attribute to a nullable type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="b0a5d-110">Poslední příklad v tomto tématu ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-110">The last example in this topic demonstrates this.</span></span> <span data-ttu-id="b0a5d-111">Však nelze nastavit obsah prvku prostřednictvím přetypování, jak můžete prostřednictvím <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-111">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0a5d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0a5d-112">Example</span></span>  
 <span data-ttu-id="b0a5d-113">Chcete-li načíst hodnotu prvku, <xref:System.Xml.Linq.XElement> stačí přetypovat objekt na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-113">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="b0a5d-114">Vždy můžete přetypovat prvek do řetězce takto:</span><span class="sxs-lookup"><span data-stu-id="b0a5d-114">You can always cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="b0a5d-115">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a5d-115">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="b0a5d-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0a5d-116">Example</span></span>  
 <span data-ttu-id="b0a5d-117">Prvky můžete také přetypovat na jiné typy než řetězec.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-117">You can also cast elements to types other than string.</span></span> <span data-ttu-id="b0a5d-118">Například pokud máte prvek, který obsahuje celé číslo, můžete `int`přetypovat do , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="b0a5d-118">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="b0a5d-119">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a5d-119">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b0a5d-120">poskytuje explicitní operátory přetypádky pro `int?` `uint`následující `uint?` `long`datové `long?` `ulong` `ulong?`typy: `float` `float?` `double` `double?` `decimal` `decimal?` `DateTime` `DateTime?` `string` `bool`, , `bool?` `int`, , , , , , , , , , , , , `TimeSpan`, `TimeSpan?`, `GUID`, , , a `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-120">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b0a5d-121">poskytuje stejné operátory <xref:System.Xml.Linq.XAttribute> přetypádku pro objekty.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-121">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0a5d-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0a5d-122">Example</span></span>  
 <span data-ttu-id="b0a5d-123"><xref:System.Xml.Linq.XElement.Value%2A> Vlastnost můžete použít k načtení obsahu prvku:</span><span class="sxs-lookup"><span data-stu-id="b0a5d-123">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="b0a5d-124">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a5d-124">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="b0a5d-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0a5d-125">Example</span></span>  
 <span data-ttu-id="b0a5d-126">Někdy se pokusíte načíst hodnotu prvku, i když si nejste jisti, že existuje.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-126">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="b0a5d-127">V tomto případě při přiřazení přetypovaného prvku typu `string` s možnou hodnotou null (jeden nebo jeden z typů s možnou `null`hodnotou null v rozhraní .NET Framework), pokud prvek neexistuje, je přiřazená proměnná nastavena pouze na .</span><span class="sxs-lookup"><span data-stu-id="b0a5d-127">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the .NET Framework), if the element does not exist the assigned variable is just set to `null`.</span></span> <span data-ttu-id="b0a5d-128">Následující kód ukazuje, že když prvek může nebo nemusí existovat, je <xref:System.Xml.Linq.XElement.Value%2A> jednodušší použít přetypování než použít vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-128">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 <span data-ttu-id="b0a5d-129">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a5d-129">This code produces the following output:</span></span>  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="b0a5d-130">Obecně můžete napsat jednodušší kód při použití přetypování k načtení obsahu prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="b0a5d-130">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a5d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0a5d-131">See also</span></span>

- [<span data-ttu-id="b0a5d-132">LINQ na osy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b0a5d-132">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
