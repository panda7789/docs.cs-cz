---
title: Jak načíst hodnotu prvku (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805830"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="7c20e-102">Jak načíst hodnotu prvku (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7c20e-102">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>

<span data-ttu-id="7c20e-103">Tento článek ukazuje, jak získat hodnotu prvků.</span><span class="sxs-lookup"><span data-stu-id="7c20e-103">This article shows how to get the value of elements.</span></span> <span data-ttu-id="7c20e-104">Existují dva hlavní způsoby, jak získat hodnotu:</span><span class="sxs-lookup"><span data-stu-id="7c20e-104">There are two main ways to get the value:</span></span>

- <span data-ttu-id="7c20e-105">Přetypovat <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> nebo na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="7c20e-105">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="7c20e-106">Explicitní operátor převodu pak převede obsah prvku nebo atributu na zadaný typ a přiřadí jej proměnné.</span><span class="sxs-lookup"><span data-stu-id="7c20e-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="7c20e-107">Použijte <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti nebo. <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7c20e-107">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="7c20e-108">Můžete také nastavit hodnotu pomocí těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="7c20e-108">You can also set the value using these properties.</span></span>

<span data-ttu-id="7c20e-109">S C#, casting je obecně lepší přístup.</span><span class="sxs-lookup"><span data-stu-id="7c20e-109">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="7c20e-110">Pokud přetypování prvku nebo atributu na typ hodnoty s možnou hodnotou, kterou lze použít s nulou, je jednodušší zapisovat kód při načítání hodnoty elementu (nebo atributu), který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="7c20e-110">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="7c20e-111">[Poslední příklad](#element-might-not-exist-example) v tomto článku ukazuje, že obsazení je jednodušší v případě, kdy prvek nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="7c20e-111">The [last example](#element-might-not-exist-example) in this article demonstrates that casting is simpler in the case where the element might not exist.</span></span> <span data-ttu-id="7c20e-112">Však nelze nastavit obsah prvku prostřednictvím přetypování, jak můžete prostřednictvím <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7c20e-112">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="string-cast-example"></a><span data-ttu-id="7c20e-113">Příklad přetypování řetězců</span><span class="sxs-lookup"><span data-stu-id="7c20e-113">String cast example</span></span>  
 <span data-ttu-id="7c20e-114">Chcete-li načíst hodnotu <xref:System.Xml.Linq.XElement> prvku, přetypujte objekt na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="7c20e-114">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="7c20e-115">Prvek můžete přetypovat do řetězce takto:</span><span class="sxs-lookup"><span data-stu-id="7c20e-115">You can cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="7c20e-116">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7c20e-116">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a><span data-ttu-id="7c20e-117">Příklad podčísla obsazení</span><span class="sxs-lookup"><span data-stu-id="7c20e-117">Integer cast example</span></span>  
 <span data-ttu-id="7c20e-118">Prvky můžete také přetypovat na jiné typy než řetězec.</span><span class="sxs-lookup"><span data-stu-id="7c20e-118">You can also cast elements to types other than string.</span></span> <span data-ttu-id="7c20e-119">Například pokud máte prvek, který obsahuje celé číslo, můžete `int`přetypovat do , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="7c20e-119">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="7c20e-120">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7c20e-120">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7c20e-121">poskytuje explicitní operátory přetypádky pro `int?` `uint`následující `uint?` `long`datové `long?` `ulong` `ulong?`typy: `float` `float?` `double` `double?` `decimal` `decimal?` `DateTime` `DateTime?` `string` `bool`, , `bool?` `int`, , , , , , , , , , , , , `TimeSpan`, `TimeSpan?`, `GUID`, , , a `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="7c20e-121">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7c20e-122">poskytuje stejné operátory <xref:System.Xml.Linq.XAttribute> přetypádku pro objekty.</span><span class="sxs-lookup"><span data-stu-id="7c20e-122">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="value-property-example"></a><span data-ttu-id="7c20e-123">Příklad vlastnosti hodnoty</span><span class="sxs-lookup"><span data-stu-id="7c20e-123">Value property example</span></span>  
 <span data-ttu-id="7c20e-124"><xref:System.Xml.Linq.XElement.Value%2A> Vlastnost můžete použít k načtení obsahu prvku:</span><span class="sxs-lookup"><span data-stu-id="7c20e-124">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="7c20e-125">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7c20e-125">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a><span data-ttu-id="7c20e-126">Prvek pravděpodobně neexistuje příklad</span><span class="sxs-lookup"><span data-stu-id="7c20e-126">Element might not exist example</span></span>
 <span data-ttu-id="7c20e-127">Někdy se pokusíte načíst hodnotu prvku, i když si nejste jisti, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="7c20e-127">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="7c20e-128">V tomto případě při přiřazení odevzdaného prvku k typu odkazu s možnou hodnotou s možnou hodnotou `null`null nebo typu hodnoty s možnou hodnotou, pokud prvek neexistuje, je přiřazená proměnná nastavena na .</span><span class="sxs-lookup"><span data-stu-id="7c20e-128">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element does not exist, the assigned variable is set to `null`.</span></span> <span data-ttu-id="7c20e-129">Následující kód ukazuje, že když prvek může nebo nemusí existovat, je <xref:System.Xml.Linq.XElement.Value%2A> jednodušší použít přetypování než použít vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7c20e-129">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="7c20e-130">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7c20e-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="7c20e-131">Obecně můžete napsat jednodušší kód při použití přetypování k načtení obsahu prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="7c20e-131">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c20e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c20e-132">See also</span></span>

- [<span data-ttu-id="7c20e-133">LINQ na osy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7c20e-133">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
