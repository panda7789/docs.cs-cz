---
title: Obor výchozích názvových prostorů v jazyce Visual Basic
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: e33505dd8e8ad94e3c758f15f245d0cbaf6987bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786799"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="b4128-102">Obor výchozích názvových prostorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4128-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="b4128-103">Výchozí obory názvů, jak je ve stromové struktuře XML nejsou v oboru pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="b4128-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="b4128-104">Pokud budete mít soubor XML, který je ve výchozím oboru názvů, je stále třeba deklarovat <xref:System.Xml.Linq.XNamespace> proměnnou a sloučit s místním názvem vytvořit kvalifikovaný název, který se má použít v dotazu.</span><span class="sxs-lookup"><span data-stu-id="b4128-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="b4128-105">Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotaz jakoby nebyly v oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="b4128-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="b4128-106">První sada příklady v tomto tématu ukazuje obvyklým způsobem, že je načteno XML ve výchozím oboru názvů, ale je dotazován nesprávně.</span><span class="sxs-lookup"><span data-stu-id="b4128-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="b4128-107">Druhá sada příklady ukazují potřebné opravy tak, aby můžete dát dotaz na XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b4128-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4128-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4128-108">Example</span></span>  
 <span data-ttu-id="b4128-109">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdný výsledek sadu.</span><span class="sxs-lookup"><span data-stu-id="b4128-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b4128-110">Kód</span><span class="sxs-lookup"><span data-stu-id="b4128-110">Code</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
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
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="b4128-111">Komentáře</span><span class="sxs-lookup"><span data-stu-id="b4128-111">Comments</span></span>  
 <span data-ttu-id="b4128-112">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="b4128-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="b4128-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4128-113">Example</span></span>  
 <span data-ttu-id="b4128-114">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je zakódovaný správně.</span><span class="sxs-lookup"><span data-stu-id="b4128-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="b4128-115">Na rozdíl od nesprávně programové výše uvedeném příkladu správný přístup při použití jazyka Visual Basic je deklarovat a inicializovat globální výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b4128-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="b4128-116">To umístí všechny vlastnosti XML ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b4128-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="b4128-117">Žádné úpravy jsou požadovány v příkladu, aby to fungovalo správně.</span><span class="sxs-lookup"><span data-stu-id="b4128-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b4128-118">Kód</span><span class="sxs-lookup"><span data-stu-id="b4128-118">Code</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
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
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="b4128-119">Komentáře</span><span class="sxs-lookup"><span data-stu-id="b4128-119">Comments</span></span>  
 <span data-ttu-id="b4128-120">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="b4128-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4128-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4128-121">See also</span></span>

- [<span data-ttu-id="b4128-122">Práce s názvovými prostory XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4128-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
