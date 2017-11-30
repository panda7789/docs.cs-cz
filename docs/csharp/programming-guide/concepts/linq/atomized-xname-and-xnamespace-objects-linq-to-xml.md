---
title: Atomized XName a XNamespace objekty (technologie LINQ to XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc3fdb907c46cf77ff6560b68ebc449380947e1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="0e563-102">Atomized XName a XNamespace objekty (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0e563-102">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0e563-103"><xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> objekty jsou *atomized*; to znamená, pokud obsahují stejný kvalifikovaný název, se vztahují ke stejnému objektu.</span><span class="sxs-lookup"><span data-stu-id="0e563-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="0e563-104">Dostaneme výkonnostních výhod pro dotazy: při porovnávání rovnosti dvou atomized názvy základní převodní jazyk má jenom k určení, zda dva odkazy odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="0e563-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="0e563-105">Kód základní nemusí řetězec porovnání, které by byly časově náročná.</span><span class="sxs-lookup"><span data-stu-id="0e563-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="0e563-106">Sémantika atomizace</span><span class="sxs-lookup"><span data-stu-id="0e563-106">Atomization Semantics</span></span>  
 <span data-ttu-id="0e563-107">Atomizace znamená, že pokud dva <xref:System.Xml.Linq.XName> objekty mají stejnou místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="0e563-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="0e563-108">Stejným způsobem, pokud dva <xref:System.Xml.Linq.XNamespace> objekty mají stejný obor názvů URI, které sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="0e563-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="0e563-109">Pro třídu povolit atomized objekty musí být v konstruktoru pro třídu privátní, není veřejné.</span><span class="sxs-lookup"><span data-stu-id="0e563-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="0e563-110">Je to proto, pokud byly veřejný konstruktor, můžete vytvořit objekt neatomizovaném.</span><span class="sxs-lookup"><span data-stu-id="0e563-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="0e563-111"><xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> operátor implicitní převod převést řetězec do implementace třídy <xref:System.Xml.Linq.XName> nebo <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="0e563-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="0e563-112">Toto je, jak získat instanci tyto objekty.</span><span class="sxs-lookup"><span data-stu-id="0e563-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="0e563-113">Pomocí konstruktoru, nelze získat instanci, protože konstruktoru je nedostupná.</span><span class="sxs-lookup"><span data-stu-id="0e563-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="0e563-114"><xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> taky implementovat operátory rovnosti a nerovnosti k určení, zda dva objekty porovnávané jsou odkazy na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="0e563-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e563-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e563-115">Example</span></span>  
 <span data-ttu-id="0e563-116">Následující kód vytvoří některé <xref:System.Xml.Linq.XElement> objekty a ukazuje, že identické názvy sdílet stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="0e563-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="0e563-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0e563-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="0e563-118">Jak už bylo zmíněno dříve, výhodou atomized objektů je, že když použijete jednu z metod osy, které berou <xref:System.Xml.Linq.XName> jako parametr, metoda osy má jenom k určení, že dva názvy odkaz na stejnou instanci a vyberte požadované prvky.</span><span class="sxs-lookup"><span data-stu-id="0e563-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="0e563-119">Následující příklad předá <xref:System.Xml.Linq.XName> k <xref:System.Xml.Linq.XContainer.Descendants%2A> volání metody, která pak má lepší výkon z důvodu atomizace vzor.</span><span class="sxs-lookup"><span data-stu-id="0e563-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
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
  
 <span data-ttu-id="0e563-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0e563-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e563-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e563-121">See Also</span></span>  
 [<span data-ttu-id="0e563-122">Výkon (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0e563-122">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
