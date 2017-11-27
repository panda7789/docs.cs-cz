---
title: "Rozsah výchozí obory názvů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aaf5395f1216b0cb56f2d1f003e42ed30790012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="5da34-102">Rozsah výchozí obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5da34-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="5da34-103">Výchozí obory názvů, jak je přestavováno ve stromové struktuře XML nejsou v oboru pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="5da34-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="5da34-104">Pokud máte XML, který je ve výchozí obor názvů, je stále potřeba deklarovat <xref:System.Xml.Linq.XNamespace> proměnnou a zkombinovat s místní název, aby kvalifikovaný název, který se má použít v dotazu.</span><span class="sxs-lookup"><span data-stu-id="5da34-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="5da34-105">Jeden z nejběžnějších problémů při dotazování stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotazu, jako by soubor XML není v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5da34-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="5da34-106">První sadu příklady v tomto tématu ukazuje obvyklý způsob, že je načteno kód XML v výchozí obor názvů, ale je dotazován nesprávně.</span><span class="sxs-lookup"><span data-stu-id="5da34-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="5da34-107">Druhá sada příklady zobrazit potřebné opravy tak, aby v oboru názvů se můžete dotazovat XML.</span><span class="sxs-lookup"><span data-stu-id="5da34-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5da34-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5da34-108">Example</span></span>  
 <span data-ttu-id="5da34-109">Tento příklad ukazuje vytvoření XML v oboru názvů a nastavte dotaz, který vrací prázdný výsledek.</span><span class="sxs-lookup"><span data-stu-id="5da34-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5da34-110">Kód</span><span class="sxs-lookup"><span data-stu-id="5da34-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="5da34-111">Komentáře</span><span class="sxs-lookup"><span data-stu-id="5da34-111">Comments</span></span>  
 <span data-ttu-id="5da34-112">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="5da34-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="5da34-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="5da34-113">Example</span></span>  
 <span data-ttu-id="5da34-114">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je zakódovaný správně.</span><span class="sxs-lookup"><span data-stu-id="5da34-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="5da34-115">Na rozdíl od nesprávně programové příkladu nahoře je správný přístup prostřednictvím jazyka Visual Basic deklarace a inicializace globální výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5da34-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="5da34-116">Tato výchozí obor názvů umístí všechny vlastnosti XML.</span><span class="sxs-lookup"><span data-stu-id="5da34-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="5da34-117">Žádné další úpravy jsou požadovány v příkladu, aby byla správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="5da34-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5da34-118">Kód</span><span class="sxs-lookup"><span data-stu-id="5da34-118">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="5da34-119">Komentáře</span><span class="sxs-lookup"><span data-stu-id="5da34-119">Comments</span></span>  
 <span data-ttu-id="5da34-120">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="5da34-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="5da34-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5da34-121">See Also</span></span>  
 [<span data-ttu-id="5da34-122">Práce s obory názvů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5da34-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
