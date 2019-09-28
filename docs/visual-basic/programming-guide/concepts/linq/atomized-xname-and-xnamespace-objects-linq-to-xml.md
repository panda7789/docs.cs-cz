---
title: Atomované XName a objekty XNamespace (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: ae6d21c21aac4455e7932015c131fb4295673056
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351839"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="a4900-102">Atomované XName a objekty XNamespace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4900-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="a4900-103">objekty <xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> jsou *atomické*; To znamená, že pokud obsahují stejný kvalifikovaný název, odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="a4900-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="a4900-104">To má za důsledek přínos pro dotazy: Když porovnáte dva atomické názvy pro rovnost, má základní zprostředkující jazyk pouze určit, zda dva odkazy odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="a4900-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="a4900-105">Podkladový kód nemusí provádět porovnávání řetězců, což by mohlo být časově náročné.</span><span class="sxs-lookup"><span data-stu-id="a4900-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="a4900-106">Sémantika atoming</span><span class="sxs-lookup"><span data-stu-id="a4900-106">Atomization Semantics</span></span>

<span data-ttu-id="a4900-107">Atoming znamená, že pokud dva objekty <xref:System.Xml.Linq.XName> mají stejný místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a4900-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="a4900-108">Stejným způsobem, pokud dva objekty <xref:System.Xml.Linq.XNamespace> mají stejný identifikátor URI oboru názvů, sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a4900-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="a4900-109">Pro třídu, která povoluje atomované objekty, konstruktor třídy musí být privátní, nikoli Public.</span><span class="sxs-lookup"><span data-stu-id="a4900-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="a4900-110">Důvodem je, že pokud byl konstruktor veřejný, mohli byste vytvořit neatomické objekty.</span><span class="sxs-lookup"><span data-stu-id="a4900-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="a4900-111">Třídy <xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> implementují implicitní operátor převodu pro převod řetězce na <xref:System.Xml.Linq.XName> nebo <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="a4900-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="a4900-112">Tímto způsobem získáte instanci těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="a4900-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="a4900-113">Nelze získat instanci pomocí konstruktoru, protože konstruktor je nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="a4900-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="a4900-114"><xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> také implementují operátory rovnosti a nerovnosti, aby bylo možné určit, zda jsou dva porovnávané objekty odkazy na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a4900-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example"></a><span data-ttu-id="a4900-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4900-115">Example</span></span>

<span data-ttu-id="a4900-116">Následující kód vytvoří některé objekty @no__t 0 a ukazuje, že stejné názvy sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a4900-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

<span data-ttu-id="a4900-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a4900-117">This example produces the following output:</span></span>

```console
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="a4900-118">Jak bylo zmíněno dříve, výhodou pro objekty atoming je, že pokud použijete jednu z metod osy, která jako parametr přebírá <xref:System.Xml.Linq.XName>, metoda Axis má pouze určit, že dva názvy odkazují na stejnou instanci, aby vybrala požadované prvky.</span><span class="sxs-lookup"><span data-stu-id="a4900-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="a4900-119">Následující příklad předává <xref:System.Xml.Linq.XName> do volání metody <xref:System.Xml.Linq.XContainer.Descendants%2A>, které pak má lepší výkon vzhledem ke schématu atoming.</span><span class="sxs-lookup"><span data-stu-id="a4900-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="a4900-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a4900-120">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a><span data-ttu-id="a4900-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4900-121">See also</span></span>

- [<span data-ttu-id="a4900-122">Výkon (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4900-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
