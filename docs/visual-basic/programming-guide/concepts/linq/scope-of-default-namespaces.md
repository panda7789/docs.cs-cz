---
title: Rozsah výchozích oborů názvů v Visual Basic
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: af868454c9d1dce7d8bf5a1902f64eff8db8780c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710359"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="76c01-102">Rozsah výchozích oborů názvů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="76c01-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="76c01-103">Výchozí obory názvů jako reprezentované ve stromu XML nejsou v oboru pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="76c01-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="76c01-104">Pokud máte XML, které je ve výchozím oboru názvů, je stále nutné deklarovat <xref:System.Xml.Linq.XNamespace> proměnnou a zkombinovat ji s místním názvem, aby bylo možné použít kvalifikovaný název v dotazu.</span><span class="sxs-lookup"><span data-stu-id="76c01-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="76c01-105">Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by kód XML nebyl v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="76c01-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="76c01-106">První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten XML ve výchozím oboru názvů, ale dotaz je nesprávně zadán.</span><span class="sxs-lookup"><span data-stu-id="76c01-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="76c01-107">Druhá sada příkladů ukazuje nezbytné opravy, aby bylo možné dotazovat XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="76c01-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76c01-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="76c01-108">Example</span></span>  
 <span data-ttu-id="76c01-109">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdnou sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="76c01-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="76c01-110">Kód</span><span class="sxs-lookup"><span data-stu-id="76c01-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="76c01-111">Komentáře</span><span class="sxs-lookup"><span data-stu-id="76c01-111">Comments</span></span>  
 <span data-ttu-id="76c01-112">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="76c01-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="76c01-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="76c01-113">Example</span></span>  
 <span data-ttu-id="76c01-114">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je správně kódován.</span><span class="sxs-lookup"><span data-stu-id="76c01-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="76c01-115">Na rozdíl od nesprávně uvedeného kódovaného příkladu je správný přístup při použití Visual Basic deklarovat a inicializovat globální výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="76c01-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="76c01-116">Tím se umístí všechny vlastnosti XML ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="76c01-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="76c01-117">V příkladu nejsou k dispozici žádné další úpravy, aby mohla správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="76c01-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="76c01-118">Kód</span><span class="sxs-lookup"><span data-stu-id="76c01-118">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="76c01-119">Komentáře</span><span class="sxs-lookup"><span data-stu-id="76c01-119">Comments</span></span>  
 <span data-ttu-id="76c01-120">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="76c01-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="76c01-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76c01-121">See also</span></span>

- [<span data-ttu-id="76c01-122">Přehled oborů názvů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76c01-122">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
