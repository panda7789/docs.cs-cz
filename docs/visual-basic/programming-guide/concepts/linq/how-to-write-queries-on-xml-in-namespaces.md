---
title: 'Postupy: zápis dotazů do XML v oborech názvů'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 496cf8daf5136e8aafff000312bbd730a5152e9f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344462"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="fdd03-102">Postupy: zápis dotazů na XML v oborech názvů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdd03-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="fdd03-103">Chcete-li zapsat dotaz na XML, který je v oboru názvů, je nutné použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="fdd03-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="fdd03-104">V Visual Basic Nejběžnějším přístupem je definování globálního oboru názvů a pak použití literálů XML a vlastností XML, které používají globální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="fdd03-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="fdd03-105">Můžete definovat globální výchozí obor názvů. v takovém případě prvky v literálech XML budou ve výchozím nastavení v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fdd03-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="fdd03-106">Alternativně můžete definovat globální obor názvů s předponou a potom použít předponu podle požadavků v literálech XML a ve vlastnostech XML.</span><span class="sxs-lookup"><span data-stu-id="fdd03-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="fdd03-107">Stejně jako u jiných forem XML nejsou atributy ve výchozím nastavení vždy v žádném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fdd03-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="fdd03-108">První sada příkladů v tomto tématu ukazuje, jak vytvořit strom XML ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fdd03-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="fdd03-109">Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="fdd03-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdd03-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdd03-110">Example</span></span>  
 <span data-ttu-id="fdd03-111">Následující příklad vytvoří strom XML, který je ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fdd03-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="fdd03-112">Poté načte kolekci prvků.</span><span class="sxs-lookup"><span data-stu-id="fdd03-112">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="fdd03-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fdd03-113">This example produces the following output:</span></span>  
  
```console  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="fdd03-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdd03-114">Example</span></span>  
 <span data-ttu-id="fdd03-115">V Visual Basic však zápis dotazů ve stromu XML, který používá obor názvů s předponou, je poměrně jiný než dotazování stromu XML ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fdd03-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="fdd03-116">Obvykle se používá příkaz `Imports` pro import oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="fdd03-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="fdd03-117">Pak použijte předponu v názvu elementu a atributu při vytváření stromu XML.</span><span class="sxs-lookup"><span data-stu-id="fdd03-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="fdd03-118">Také použijte předponu při dotazování stromu XML pomocí vlastností XML.</span><span class="sxs-lookup"><span data-stu-id="fdd03-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="fdd03-119">Následující příklad vytvoří strom XML, který je v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="fdd03-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="fdd03-120">Poté načte kolekci prvků.</span><span class="sxs-lookup"><span data-stu-id="fdd03-120">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="fdd03-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fdd03-121">This example produces the following output:</span></span>  
  
```console  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="fdd03-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdd03-122">See also</span></span>

- [<span data-ttu-id="fdd03-123">Přehled oborů názvů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdd03-123">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
