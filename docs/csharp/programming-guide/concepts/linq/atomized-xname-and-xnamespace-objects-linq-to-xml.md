---
title: Atomized XName a XNamespace objekty (LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc5066440d87f5485ae9099d7a7f4f5e9e66b4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204273"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="a7f57-102">Atomized XName a XNamespace objekty (LINQ na XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a7f57-102">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="a7f57-103"><xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> předměty jsou *rozprášeny*; to znamená, že pokud obsahují stejný kvalifikovaný název, odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="a7f57-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="a7f57-104">To přináší výhody výkonu pro dotazy: Při porovnání dvou atomized názvy pro rovnost, základní zprostředkující jazyk má pouze k určení, zda dva odkazy odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="a7f57-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="a7f57-105">Základní kód nemusí provést porovnání řetězců, což by bylo časově náročné.</span><span class="sxs-lookup"><span data-stu-id="a7f57-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="a7f57-106">Atomizace sémantiku</span><span class="sxs-lookup"><span data-stu-id="a7f57-106">Atomization Semantics</span></span>  
 <span data-ttu-id="a7f57-107">Atomizace znamená, <xref:System.Xml.Linq.XName> že pokud dva objekty mají stejný místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a7f57-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="a7f57-108">Stejným způsobem, pokud <xref:System.Xml.Linq.XNamespace> dva objekty mají stejný identifikátor URI oboru názvů, sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a7f57-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="a7f57-109">Pro třídu povolit atomized objekty konstruktor pro třídu musí být soukromé, nikoli veřejné.</span><span class="sxs-lookup"><span data-stu-id="a7f57-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="a7f57-110">Důvodem je, že pokud konstruktor byly veřejné, můžete vytvořit objekt bez rozprašovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="a7f57-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="a7f57-111"><xref:System.Xml.Linq.XName> Třídy <xref:System.Xml.Linq.XNamespace> a implementují implicitní operátor <xref:System.Xml.Linq.XName> převodu k převodu řetězce na nebo <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="a7f57-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="a7f57-112">Tímto způsobem získáte instanci těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="a7f57-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="a7f57-113">Nelze získat instanci pomocí konstruktoru, protože konstruktor je nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="a7f57-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="a7f57-114"><xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> také implementovat operátory rovnosti a nerovnosti, chcete-li určit, zda dva porovnávané objekty jsou odkazy na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a7f57-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7f57-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7f57-115">Example</span></span>  
 <span data-ttu-id="a7f57-116">Následující kód vytvoří <xref:System.Xml.Linq.XElement> některé objekty a ukazuje, že identické názvy sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a7f57-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="a7f57-117">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a7f57-117">This example produces the following output:</span></span>  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="a7f57-118">Jak již bylo zmíněno dříve, výhodou atomizovaných objektů je, že <xref:System.Xml.Linq.XName> při použití jedné z metod osy, které berou jako parametr, metoda osy má pouze určit, že dva názvy odkazují na stejnou instanci pro výběr požadovaných prvků.</span><span class="sxs-lookup"><span data-stu-id="a7f57-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="a7f57-119">Následující příklad předá <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> volání metody, která pak má lepší výkon z důvodu atomizace vzor.</span><span class="sxs-lookup"><span data-stu-id="a7f57-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
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
  
 <span data-ttu-id="a7f57-120">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a7f57-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
