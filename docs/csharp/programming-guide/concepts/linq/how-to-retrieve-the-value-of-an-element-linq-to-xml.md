---
title: Jak načíst hodnotu elementu (LINQ to XML) (C#)
description: Přečtěte si, jak získat hodnotu prvků. Podívejte se na příklady použití přetypování řetězců, celočíselného přetypování a vlastnosti Value.
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: eb750927d74c3068d7ab06caba9835110bd77a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301538"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="fb80f-104">Jak načíst hodnotu elementu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="fb80f-104">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>

<span data-ttu-id="fb80f-105">Tento článek ukazuje, jak získat hodnotu prvků.</span><span class="sxs-lookup"><span data-stu-id="fb80f-105">This article shows how to get the value of elements.</span></span> <span data-ttu-id="fb80f-106">Existují dva hlavní způsoby, jak získat hodnotu:</span><span class="sxs-lookup"><span data-stu-id="fb80f-106">There are two main ways to get the value:</span></span>

- <span data-ttu-id="fb80f-107">Přetypování <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="fb80f-107">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="fb80f-108">Operátor explicitního převodu pak převede obsah elementu nebo atributu na zadaný typ a přiřadí ho k proměnné.</span><span class="sxs-lookup"><span data-stu-id="fb80f-108">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="fb80f-109">Použijte <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti nebo <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fb80f-109">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="fb80f-110">Tuto hodnotu můžete také nastavit pomocí těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="fb80f-110">You can also set the value using these properties.</span></span>

<span data-ttu-id="fb80f-111">V jazyce C# je přetypování všeobecně lepším přístupem.</span><span class="sxs-lookup"><span data-stu-id="fb80f-111">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="fb80f-112">Pokud přetypování elementu nebo atributu na typ hodnoty s možnou hodnotou null, kód je jednodušší zapsat při načítání hodnoty prvku (nebo atributu), který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="fb80f-112">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="fb80f-113">[Poslední příklad](#element-might-not-exist-example) v tomto článku ukazuje, že přetypování je jednodušší v případě, kdy element pravděpodobně neexistuje.</span><span class="sxs-lookup"><span data-stu-id="fb80f-113">The [last example](#element-might-not-exist-example) in this article demonstrates that casting is simpler in the case where the element might not exist.</span></span> <span data-ttu-id="fb80f-114">Nemůžete však nastavit obsah elementu prostřednictvím přetypování, jak můžete prostřednictvím <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fb80f-114">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="string-cast-example"></a><span data-ttu-id="fb80f-115">Příklad přetypování řetězců</span><span class="sxs-lookup"><span data-stu-id="fb80f-115">String cast example</span></span>  
 <span data-ttu-id="fb80f-116">Chcete-li načíst hodnotu prvku, přetypování <xref:System.Xml.Linq.XElement> objektu na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="fb80f-116">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="fb80f-117">Můžete přetypovat element na řetězec následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fb80f-117">You can cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="fb80f-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fb80f-118">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a><span data-ttu-id="fb80f-119">Příklad přetypování typu Integer</span><span class="sxs-lookup"><span data-stu-id="fb80f-119">Integer cast example</span></span>  
 <span data-ttu-id="fb80f-120">Prvky lze také přetypovat na jiné typy než řetězec.</span><span class="sxs-lookup"><span data-stu-id="fb80f-120">You can also cast elements to types other than string.</span></span> <span data-ttu-id="fb80f-121">Například pokud máte prvek, který obsahuje celé číslo, můžete jej přetypovat na `int` , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="fb80f-121">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="fb80f-122">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fb80f-122">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb80f-123">poskytuje operátory explicitního přetypování pro následující datové typy: `string` ,,,, `bool` `bool?` `int` `int?` , `uint` , `uint?` , `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` ,, `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,, a.</span><span class="sxs-lookup"><span data-stu-id="fb80f-123">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb80f-124">poskytuje stejné operátory přetypování pro <xref:System.Xml.Linq.XAttribute> objekty.</span><span class="sxs-lookup"><span data-stu-id="fb80f-124">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="value-property-example"></a><span data-ttu-id="fb80f-125">Vlastnost hodnoty – příklad</span><span class="sxs-lookup"><span data-stu-id="fb80f-125">Value property example</span></span>  
 <span data-ttu-id="fb80f-126">Vlastnost můžete použít <xref:System.Xml.Linq.XElement.Value%2A> k načtení obsahu prvku:</span><span class="sxs-lookup"><span data-stu-id="fb80f-126">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="fb80f-127">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fb80f-127">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a><span data-ttu-id="fb80f-128">Element nemusí existovat příklad.</span><span class="sxs-lookup"><span data-stu-id="fb80f-128">Element might not exist example</span></span>
 <span data-ttu-id="fb80f-129">Někdy se pokusíte načíst hodnotu prvku, i když si nejste jistí, jestli existuje.</span><span class="sxs-lookup"><span data-stu-id="fb80f-129">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="fb80f-130">V takovém případě, když přiřadíte předaný element na odkazový typ s možnou hodnotou null nebo typ hodnoty s možnou hodnotou null, pokud element neexistuje, přiřazená proměnná je nastavena na `null` .</span><span class="sxs-lookup"><span data-stu-id="fb80f-130">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element does not exist, the assigned variable is set to `null`.</span></span> <span data-ttu-id="fb80f-131">Následující kód ukazuje, že pokud element může nebo nemusí existovat, je snazší použít přetypování, než aby bylo možné použít <xref:System.Xml.Linq.XElement.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fb80f-131">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="fb80f-132">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fb80f-132">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="fb80f-133">Obecně lze psát jednodušší kód při použití přetypování k načtení obsahu prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="fb80f-133">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb80f-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb80f-134">See also</span></span>

- [<span data-ttu-id="fb80f-135">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="fb80f-135">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
