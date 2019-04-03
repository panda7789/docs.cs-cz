---
title: Práce s globálními názvovými prostory (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: d8e74e949815d36f06f522460cc31ca6c3ccabb3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827377"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="61a72-102">Práce s globálními názvovými prostory (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="61a72-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="61a72-103">Jednou z klíčových funkcí literálů XML v jazyce Visual Basic je možnost deklarovat obory názvů XML pomocí `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="61a72-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="61a72-104">Díky této funkci lze deklarovat obor názvů XML, který používá předponu nebo je možné deklarovat výchozí názvový prostor XML.</span><span class="sxs-lookup"><span data-stu-id="61a72-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="61a72-105">Tato možnost je užitečná ve dvou situacích.</span><span class="sxs-lookup"><span data-stu-id="61a72-105">This capability is useful in two situations.</span></span> <span data-ttu-id="61a72-106">Nejprve obory názvů deklarovaný v literálech XML se nepřenesou do vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="61a72-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="61a72-107">Deklarace oborů názvů globální snižuje množství práce, které budete muset udělat, abyste použijte vložené výrazy s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="61a72-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="61a72-108">Za druhé je třeba deklarovat globálními názvovými prostory k použití oborů názvů pomocí vlastnosti XML.</span><span class="sxs-lookup"><span data-stu-id="61a72-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="61a72-109">Je možné deklarovat globální obory názvů na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="61a72-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="61a72-110">Můžete také deklarovat globální obory názvů na úrovni modulu, který přepíše globálními názvovými prostory na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="61a72-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="61a72-111">Nakonec můžete přepsat globální obory názvů v literálu XML.</span><span class="sxs-lookup"><span data-stu-id="61a72-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="61a72-112">Při použití literály XML a vlastnosti XML, které jsou v oborech názvů globálně deklarované, zobrazí se rozbalený název vlastnosti nebo literály XML podržením ukazatele nad nich v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="61a72-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="61a72-113">Rozbalený název v popisku se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="61a72-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="61a72-114">Můžete získat <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá globálního oboru názvů pomocí `GetXmlNamespace` metody.</span><span class="sxs-lookup"><span data-stu-id="61a72-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="61a72-115">Příklady globálními názvovými prostory</span><span class="sxs-lookup"><span data-stu-id="61a72-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="61a72-116">Následující příklad deklaruje s použitím výchozí globální obor názvů `Imports` příkazu a použití literálu XML k inicializaci <xref:System.Xml.Linq.XElement> objekt v tomto oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="61a72-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="61a72-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61a72-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="61a72-118">Následující příklad deklaruje globální obor názvů s předponou a potom použije literál XML elementu inicializace:</span><span class="sxs-lookup"><span data-stu-id="61a72-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="61a72-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61a72-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="61a72-120">Globální obory názvů a vložené výrazy</span><span class="sxs-lookup"><span data-stu-id="61a72-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="61a72-121">Obory názvů, které jsou deklarovány v literálech XML není přenesou do vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="61a72-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="61a72-122">Následující příklad deklaruje výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="61a72-122">The following example declares a default namespace.</span></span> <span data-ttu-id="61a72-123">Poté použije pro vložený výraz `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="61a72-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="61a72-124">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61a72-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="61a72-125">Jak je vidět, výsledný XML obsahuje deklaraci výchozí obor názvů tak, aby `Child` elementu je bez oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="61a72-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="61a72-126">Obor názvů v vložený výraz může znovu deklarovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="61a72-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="61a72-127">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61a72-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="61a72-128">Je to ale těžkopádnější použití než globální výchozí obor názvů, který není lepším řešením.</span><span class="sxs-lookup"><span data-stu-id="61a72-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="61a72-129">Globální výchozí obor názvů můžete pomocí literálů XML bez deklarace oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="61a72-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="61a72-130">Výsledného kódu XML se bude v globálně deklarované výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="61a72-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="61a72-131">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61a72-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="61a72-132">Použití oboru názvů s vlastností XML</span><span class="sxs-lookup"><span data-stu-id="61a72-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="61a72-133">Pokud pracujete s stromu XML, který je v oboru názvů, a použití vlastností XML, pak musíte použít globální obor názvů tak, aby vlastností XML bude mít i správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="61a72-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="61a72-134">Následující příklad deklaruje stromu XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="61a72-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="61a72-135">Potom zobrazí počet `Child` elementy.</span><span class="sxs-lookup"><span data-stu-id="61a72-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="61a72-136">V tomto příkladu znamená, že neexistují žádné `Child` elementy.</span><span class="sxs-lookup"><span data-stu-id="61a72-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="61a72-137">Vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61a72-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="61a72-138">Pokud však deklarovat výchozí globální obor názvů, pak literál XML a vlastnosti XML jsou ve výchozím globálním oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="61a72-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="61a72-139">V tomto příkladu znamená, že existuje jedna `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="61a72-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="61a72-140">Vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61a72-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="61a72-141">Pokud deklarujete globální obor názvů, který má předponu, můžete použít předponu pro literály XML a vlastnosti XML:</span><span class="sxs-lookup"><span data-stu-id="61a72-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="61a72-142">XNamespace a globálními názvovými prostory</span><span class="sxs-lookup"><span data-stu-id="61a72-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="61a72-143">Můžete získat <xref:System.Xml.Linq.XNamespace> s použitím `GetXmlNamespace` metody:</span><span class="sxs-lookup"><span data-stu-id="61a72-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="61a72-144">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61a72-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="61a72-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61a72-145">See also</span></span>

- [<span data-ttu-id="61a72-146">Práce s názvovými prostory XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61a72-146">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
