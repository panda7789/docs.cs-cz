---
title: "Práce s globální obory názvů (Visual Basic) (technologie LINQ to XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 376a6d2dfbca22fb8efc6395f478839d716e14d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="84c85-102">Práce s globální obory názvů (Visual Basic) (technologie LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="84c85-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="84c85-103">Jedním z klíčových funkcích služby literálů XML v jazyce Visual Basic je schopnost deklarace oborů názvů XML pomocí `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="84c85-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="84c85-104">Pomocí této funkce lze deklarovat na obor názvů XML, který používá předpony nebo můžou deklarovat výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="84c85-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="84c85-105">Tato možnost je užitečná ve dvou situacích.</span><span class="sxs-lookup"><span data-stu-id="84c85-105">This capability is useful in two situations.</span></span> <span data-ttu-id="84c85-106">Nejprve obory názvů, které jsou deklarované v literálech XML se nepřenesou do vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="84c85-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="84c85-107">Deklarace oborů názvů globální snižuje množství práce, kterou je třeba udělat, aby používat vložené výrazy s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="84c85-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="84c85-108">Druhý je potřeba deklarovat globální obory názvů chcete-li použít obory názvů XML vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="84c85-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="84c85-109">Je možné deklarovat globální obory názvů na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="84c85-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="84c85-110">Můžete také deklarovat globální obory názvů na úrovni modulu, která přepisuje obory názvů globální úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="84c85-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="84c85-111">Nakonec můžete přepsat globální obory názvů v literál XML.</span><span class="sxs-lookup"><span data-stu-id="84c85-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="84c85-112">Při použití literálů XML nebo XML vlastnosti, které jsou v oborech názvů globálně deklarovat, zobrazí se název rozšířené vlastnosti nebo XML – literály ukázáním v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84c85-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="84c85-113">Zobrazí se název rozšířené ve formě popisu tlačítka.</span><span class="sxs-lookup"><span data-stu-id="84c85-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="84c85-114">Můžete získat <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá globální obor názvů pomocí `GetXmlNamespace` metoda.</span><span class="sxs-lookup"><span data-stu-id="84c85-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="84c85-115">Příklady globální obory názvů</span><span class="sxs-lookup"><span data-stu-id="84c85-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="84c85-116">Následující příklad uvádí výchozí globální obor názvů pomocí `Imports` příkaz a pak používá literál XML k chybě při inicializaci <xref:System.Xml.Linq.XElement> objekt v daném oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="84c85-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="84c85-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="84c85-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="84c85-118">Následující příklad prohlašuje globální obor názvů s předponou a pak použije literál XML k chybě při inicializaci elementu.</span><span class="sxs-lookup"><span data-stu-id="84c85-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="84c85-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="84c85-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="84c85-120">Globální obory názvů a vložené výrazy</span><span class="sxs-lookup"><span data-stu-id="84c85-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="84c85-121">Obory názvů, které jsou deklarované v literálech XML se nepřenesou do vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="84c85-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="84c85-122">Následující příklad uvádí výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="84c85-122">The following example declares a default namespace.</span></span> <span data-ttu-id="84c85-123">Poté použije embedded výrazu pro `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="84c85-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="84c85-124">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="84c85-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="84c85-125">Jak vidíte, výsledná XML zahrnuje deklaraci výchozí obor názvů tak, aby `Child` elementu je žádný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="84c85-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="84c85-126">Obor názvů embedded výrazu může deklarovat znovu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="84c85-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="84c85-127">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="84c85-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="84c85-128">To je však těžkopádnější používat než globální výchozí obor názvů, který je lepší přístup.</span><span class="sxs-lookup"><span data-stu-id="84c85-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="84c85-129">V globální výchozí obor názvů můžete použít literálů XML bez deklarace oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="84c85-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="84c85-130">Výsledný soubor XML se bude v globálně deklarovaný výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="84c85-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
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
  
 <span data-ttu-id="84c85-131">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="84c85-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="84c85-132">Obory názvů pomocí vlastnosti XML.</span><span class="sxs-lookup"><span data-stu-id="84c85-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="84c85-133">Pokud pracujete s XML stromové struktury, která je v oboru názvů, a pomocí vlastnosti XML, pak musíte použít globální obor názvů tak, aby vlastností XML bude taky v správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="84c85-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="84c85-134">Následující příklad deklaruje strom XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="84c85-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="84c85-135">Potom vytiskne počet `Child` elementy.</span><span class="sxs-lookup"><span data-stu-id="84c85-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="84c85-136">Tento příklad určuje, že neexistují žádné `Child` elementy.</span><span class="sxs-lookup"><span data-stu-id="84c85-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="84c85-137">Vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="84c85-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="84c85-138">Pokud však deklarovat výchozí globální obor názvů, pak literál XML a vlastnosti XML v jsou výchozí globální obor názvů:</span><span class="sxs-lookup"><span data-stu-id="84c85-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
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
  
 <span data-ttu-id="84c85-139">Tento příklad znamená, že existuje jedna `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="84c85-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="84c85-140">Vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="84c85-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="84c85-141">Pokud je deklarovat globální obor názvů, který má předponu, můžete použít předponu pro literály XML a vlastnosti XML:</span><span class="sxs-lookup"><span data-stu-id="84c85-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="84c85-142">XNamespace a globálních oborech názvů</span><span class="sxs-lookup"><span data-stu-id="84c85-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="84c85-143">Můžete získat <xref:System.Xml.Linq.XNamespace> objekt pomocí `GetXmlNamespace` metoda:</span><span class="sxs-lookup"><span data-stu-id="84c85-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
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
  
 <span data-ttu-id="84c85-144">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="84c85-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="84c85-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="84c85-145">See Also</span></span>  
 [<span data-ttu-id="84c85-146">Práce s obory názvů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84c85-146">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
