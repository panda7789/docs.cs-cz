---
title: Práce s globálním oborem názvů (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 93c7c654e43b579456633dea90ba6a362ff095f7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582362"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="53a7b-102">Práce s globálním oborem názvů (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="53a7b-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="53a7b-103">Jedna z klíčových funkcí literálů XML v Visual Basic je schopnost deklarovat obory názvů XML pomocí příkazu `Imports`.</span><span class="sxs-lookup"><span data-stu-id="53a7b-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="53a7b-104">Pomocí této funkce můžete deklarovat obor názvů XML, který používá předponu, nebo můžete deklarovat výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="53a7b-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="53a7b-105">Tato funkce je užitečná ve dvou situacích.</span><span class="sxs-lookup"><span data-stu-id="53a7b-105">This capability is useful in two situations.</span></span> <span data-ttu-id="53a7b-106">Nejprve se obory názvů deklarované v literálech XML nepřenášejí do vložených výrazů.</span><span class="sxs-lookup"><span data-stu-id="53a7b-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="53a7b-107">Deklarace globálních oborů názvů snižuje množství práce, které je třeba provést, aby bylo možné použít vložené výrazy s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="53a7b-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="53a7b-108">Za druhé musíte deklarovat globální obory názvů, aby bylo možné používat obory názvů s vlastnostmi XML.</span><span class="sxs-lookup"><span data-stu-id="53a7b-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="53a7b-109">Globální obory názvů můžete deklarovat na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="53a7b-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="53a7b-110">Můžete také deklarovat globální obory názvů na úrovni modulu, který přepíše globální obory názvů na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="53a7b-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="53a7b-111">Nakonec můžete přepsat globální obory názvů v literálu XML.</span><span class="sxs-lookup"><span data-stu-id="53a7b-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="53a7b-112">Při použití literálů XML nebo vlastností XML, které jsou v globálně deklarovaných oborech názvů, můžete zobrazit rozbalený název literálů XML nebo vlastností tak, že na ně najedete myší v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53a7b-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="53a7b-113">Rozbalený název se zobrazí v popisu tlačítka.</span><span class="sxs-lookup"><span data-stu-id="53a7b-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="53a7b-114">Můžete získat objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá globálnímu oboru názvů pomocí metody `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="53a7b-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="53a7b-115">Příklady globálních oborů názvů</span><span class="sxs-lookup"><span data-stu-id="53a7b-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="53a7b-116">Následující příklad deklaruje výchozí globální obor názvů pomocí příkazu `Imports` a poté používá literál XML pro inicializaci objektu <xref:System.Xml.Linq.XElement> v tomto oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="53a7b-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="53a7b-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a7b-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="53a7b-118">Následující příklad deklaruje globální obor názvů s předponou a poté používá literál XML pro inicializaci elementu:</span><span class="sxs-lookup"><span data-stu-id="53a7b-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="53a7b-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a7b-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="53a7b-120">Globální obory názvů a vložené výrazy</span><span class="sxs-lookup"><span data-stu-id="53a7b-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="53a7b-121">Obory názvů, které jsou deklarovány v literálech XML, se nepřenášejí do vložených výrazů.</span><span class="sxs-lookup"><span data-stu-id="53a7b-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="53a7b-122">Následující příklad deklaruje výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="53a7b-122">The following example declares a default namespace.</span></span> <span data-ttu-id="53a7b-123">Potom používá vložený výraz pro prvek `Child`.</span><span class="sxs-lookup"><span data-stu-id="53a7b-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="53a7b-124">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a7b-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="53a7b-125">Jak vidíte, výsledný kód XML obsahuje deklaraci výchozího oboru názvů tak, aby `Child` element není v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="53a7b-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="53a7b-126">Můžete znovu deklarovat obor názvů ve vloženém výrazu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="53a7b-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="53a7b-127">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a7b-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="53a7b-128">Je to ale více náročný na použití než globální výchozí obor názvů, což je lepší přístup.</span><span class="sxs-lookup"><span data-stu-id="53a7b-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="53a7b-129">S globálním výchozím oborem názvů můžete použít literály XML bez deklarování oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="53a7b-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="53a7b-130">Výsledný kód XML bude v globálně deklarovaném výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="53a7b-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
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
  
 <span data-ttu-id="53a7b-131">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a7b-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="53a7b-132">Používání oborů názvů s vlastnostmi XML</span><span class="sxs-lookup"><span data-stu-id="53a7b-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="53a7b-133">Pokud pracujete se stromovou strukturou XML, která je v oboru názvů a používáte vlastnosti XML, je nutné použít globální obor názvů tak, aby vlastnosti XML byly také ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="53a7b-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="53a7b-134">Následující příklad deklaruje strom XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="53a7b-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="53a7b-135">Pak vytiskne počet `Child` prvků.</span><span class="sxs-lookup"><span data-stu-id="53a7b-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="53a7b-136">Tento příklad označuje, že nejsou k dispozici žádné prvky `Child`.</span><span class="sxs-lookup"><span data-stu-id="53a7b-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="53a7b-137">Generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a7b-137">It produces the following output:</span></span>  
  
```console  
0  
```  
  
 <span data-ttu-id="53a7b-138">Pokud však deklarujete výchozí globální obor názvů, pak je literál XML i vlastnost XML ve výchozím globálním oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="53a7b-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
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
  
 <span data-ttu-id="53a7b-139">Tento příklad označuje, že existuje jeden `Child` element.</span><span class="sxs-lookup"><span data-stu-id="53a7b-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="53a7b-140">Generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a7b-140">It produces the following output:</span></span>  
  
```console  
1  
```  
  
 <span data-ttu-id="53a7b-141">Pokud deklarujete globální obor názvů, který má předponu, můžete použít předponu pro literály XML a vlastnosti XML:</span><span class="sxs-lookup"><span data-stu-id="53a7b-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="53a7b-142">XNamespace a globální obory názvů</span><span class="sxs-lookup"><span data-stu-id="53a7b-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="53a7b-143">Objekt <xref:System.Xml.Linq.XNamespace> můžete získat pomocí metody `GetXmlNamespace`:</span><span class="sxs-lookup"><span data-stu-id="53a7b-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
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
  
 <span data-ttu-id="53a7b-144">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a7b-144">This example produces the following output:</span></span>  
  
```console  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="53a7b-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53a7b-145">See also</span></span>

- [<span data-ttu-id="53a7b-146">Přehled oborů názvů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53a7b-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
