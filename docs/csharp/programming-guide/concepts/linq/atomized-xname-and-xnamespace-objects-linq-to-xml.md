---
title: Atomované XName a objekty XNamespace (LINQ to XML) (C#)
description: Přečtěte si o atomicky XName a XNamespace objektech a o tom, jak poskytují výkonnostní výhody pro dotazy.
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 305a233adab5c860b5f9509ae25ccc5d633e7957
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104278"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="edb43-103">Atomované XName a objekty XNamespace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="edb43-103">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="edb43-104"><xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> objekty jsou *atomické*; to znamená, že pokud obsahují stejný kvalifikovaný název, odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="edb43-104"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="edb43-105">To má vliv na výkon pro dotazy: Když porovnáte dva atomické názvy pro rovnost, má základní zprostředkující jazyk pouze určit, zda dva odkazy odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="edb43-105">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="edb43-106">Podkladový kód nemusí provádět porovnávání řetězců, což by mohlo být časově náročné.</span><span class="sxs-lookup"><span data-stu-id="edb43-106">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="edb43-107">Sémantika atoming</span><span class="sxs-lookup"><span data-stu-id="edb43-107">Atomization Semantics</span></span>  
 <span data-ttu-id="edb43-108">Atoming znamená, že pokud <xref:System.Xml.Linq.XName> mají dva objekty stejný místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="edb43-108">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="edb43-109">Stejným způsobem, pokud <xref:System.Xml.Linq.XNamespace> mají dva objekty stejný identifikátor URI oboru názvů, sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="edb43-109">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="edb43-110">Pro třídu, která povoluje atomované objekty, konstruktor třídy musí být privátní, nikoli Public.</span><span class="sxs-lookup"><span data-stu-id="edb43-110">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="edb43-111">Důvodem je, že pokud byl konstruktor veřejný, mohli byste vytvořit neatomické objekty.</span><span class="sxs-lookup"><span data-stu-id="edb43-111">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="edb43-112"><xref:System.Xml.Linq.XName>Třídy a <xref:System.Xml.Linq.XNamespace> implementují implicitní operátor převodu pro převod řetězce na <xref:System.Xml.Linq.XName> nebo <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="edb43-112">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="edb43-113">Tímto způsobem získáte instanci těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="edb43-113">This is how you get an instance of these objects.</span></span> <span data-ttu-id="edb43-114">Nelze získat instanci pomocí konstruktoru, protože konstruktor je nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="edb43-114">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="edb43-115"><xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> také implementujte operátory rovnosti a nerovnosti, abyste zjistili, zda jsou dva porovnávané objekty odkazy na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="edb43-115"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edb43-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="edb43-116">Example</span></span>  
 <span data-ttu-id="edb43-117">Následující kód vytvoří některé <xref:System.Xml.Linq.XElement> objekty a demonstruje, že stejné názvy sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="edb43-117">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 <span data-ttu-id="edb43-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="edb43-118">This example produces the following output:</span></span>  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="edb43-119">Jak bylo zmíněno dříve, výhodou objektů Atom je, že pokud použijete jednu z metod osy, která přijímá <xref:System.Xml.Linq.XName> jako parametr, metoda Axis má pouze určit, že dva názvy odkazují na stejnou instanci, aby vybraly požadované prvky.</span><span class="sxs-lookup"><span data-stu-id="edb43-119">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="edb43-120">Následující příklad předává <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> volání metody, které pak má lepší výkon, protože se jedná o model atoming.</span><span class="sxs-lookup"><span data-stu-id="edb43-120">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 <span data-ttu-id="edb43-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="edb43-121">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
