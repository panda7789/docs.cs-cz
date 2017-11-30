---
title: Atomized XName a XNamespace objekty (technologie LINQ to XML) (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d3c0b1278411c41d002c546f4b1a3be9975a801
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="18a2d-102">Atomized XName a XNamespace objekty (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18a2d-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="18a2d-103"><xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> objekty jsou *atomized*; to znamená, pokud obsahují stejný kvalifikovaný název, se vztahují ke stejnému objektu.</span><span class="sxs-lookup"><span data-stu-id="18a2d-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="18a2d-104">Dostaneme výkonnostních výhod pro dotazy: při porovnávání rovnosti dvou atomized názvy základní převodní jazyk má jenom k určení, zda dva odkazy odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="18a2d-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="18a2d-105">Kód základní nemusí řetězec porovnání, které by byly časově náročná.</span><span class="sxs-lookup"><span data-stu-id="18a2d-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="18a2d-106">Sémantika atomizace</span><span class="sxs-lookup"><span data-stu-id="18a2d-106">Atomization Semantics</span></span>  
 <span data-ttu-id="18a2d-107">Atomizace znamená, že pokud dva <xref:System.Xml.Linq.XName> objekty mají stejnou místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="18a2d-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="18a2d-108">Stejným způsobem, pokud dva <xref:System.Xml.Linq.XNamespace> objekty mají stejný obor názvů URI, které sdílejí stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="18a2d-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="18a2d-109">Pro třídu povolit atomized objekty musí být v konstruktoru pro třídu privátní, není veřejné.</span><span class="sxs-lookup"><span data-stu-id="18a2d-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="18a2d-110">Je to proto, pokud byly veřejný konstruktor, můžete vytvořit objekt neatomizovaném.</span><span class="sxs-lookup"><span data-stu-id="18a2d-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="18a2d-111"><xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> operátor implicitní převod převést řetězec do implementace třídy <xref:System.Xml.Linq.XName> nebo <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="18a2d-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="18a2d-112">Toto je, jak získat instanci tyto objekty.</span><span class="sxs-lookup"><span data-stu-id="18a2d-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="18a2d-113">Pomocí konstruktoru, nelze získat instanci, protože konstruktoru je nedostupná.</span><span class="sxs-lookup"><span data-stu-id="18a2d-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="18a2d-114"><xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> taky implementovat operátory rovnosti a nerovnosti k určení, zda dva objekty porovnávané jsou odkazy na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="18a2d-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18a2d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="18a2d-115">Example</span></span>  
 <span data-ttu-id="18a2d-116">Následující kód vytvoří některé <xref:System.Xml.Linq.XElement> objekty a ukazuje, že identické názvy sdílet stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="18a2d-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="18a2d-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="18a2d-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="18a2d-118">Jak už bylo zmíněno dříve, výhodou atomized objektů je, že když použijete jednu z metod osy, které berou <xref:System.Xml.Linq.XName> jako parametr, metoda osy má jenom k určení, že dva názvy odkaz na stejnou instanci a vyberte požadované prvky.</span><span class="sxs-lookup"><span data-stu-id="18a2d-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="18a2d-119">Následující příklad předá <xref:System.Xml.Linq.XName> k <xref:System.Xml.Linq.XContainer.Descendants%2A> volání metody, která pak má lepší výkon z důvodu atomizace vzor.</span><span class="sxs-lookup"><span data-stu-id="18a2d-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 <span data-ttu-id="18a2d-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="18a2d-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18a2d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="18a2d-121">See Also</span></span>  
 [<span data-ttu-id="18a2d-122">Výkon (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18a2d-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
