---
title: 'Postupy: zápis dotazů na XML v oborech názvů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: f4e895e560d0fb11c128248e4f42d1d5124bc124
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645561"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="c9adc-102">Postupy: zápis dotazů na XML v oborech názvů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9adc-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="c9adc-103">Pokud chcete napsat dotaz na XML, který je v oboru názvů, je nutné použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c9adc-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="c9adc-104">Nejběžnější přístupem v jazyce Visual Basic je definovat globální obor názvů a pak použijte literály XML a vlastnosti XML, které používají globální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c9adc-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="c9adc-105">Můžete definovat výchozí globální obor názvů, v takovém případě se v oboru názvů ve výchozím nastavení bude elementy v literálech XML.</span><span class="sxs-lookup"><span data-stu-id="c9adc-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="c9adc-106">Alternativně můžete definovat globální obor názvů s předponou a pak použijte předponu podle potřeby v literálech XML a vlastnosti XML.</span><span class="sxs-lookup"><span data-stu-id="c9adc-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="c9adc-107">Stejně jako u jiných forem XML atributy se vždycky nacházejí v žádný obor názvů ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c9adc-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="c9adc-108">První sadu příklady v tomto tématu ukazuje, jak vytvořit strom XML ve výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c9adc-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="c9adc-109">Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="c9adc-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9adc-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9adc-110">Example</span></span>  
 <span data-ttu-id="c9adc-111">Následující příklad vytvoří ve stromu XML, který je ve výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c9adc-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="c9adc-112">Potom načte kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="c9adc-112">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c9adc-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c9adc-113">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="c9adc-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9adc-114">Example</span></span>  
 <span data-ttu-id="c9adc-115">V jazyce Visual Basic ale zápis dotazů ve stromové struktuře XML, který používá obor názvů s předponou se poměrně liší od dotazování strom XML v výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c9adc-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="c9adc-116">Obvykle použijete `Imports` příkaz pro import oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="c9adc-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="c9adc-117">Pak použijete předponu v názvech elementu a atributu při vytvoření stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="c9adc-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="c9adc-118">Můžete také používat předponu při dotazování strom XML pomocí vlastností XML.</span><span class="sxs-lookup"><span data-stu-id="c9adc-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="c9adc-119">Následující příklad vytvoří strom XML, který je v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="c9adc-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="c9adc-120">Potom načte kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="c9adc-120">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c9adc-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c9adc-121">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9adc-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9adc-122">See Also</span></span>  
 [<span data-ttu-id="c9adc-123">Práce s obory názvů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9adc-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
