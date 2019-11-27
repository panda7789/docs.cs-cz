---
title: 'Postupy: vytvoření dokumentu s oborem názvů (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: bbd23840b0356cf14d2c7d6cb71591fe6461a8bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332589"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="cbcca-102">Postupy: vytvoření dokumentu s oborem názvů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbcca-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="cbcca-103">V tomto tématu se dozvíte, jak vytvořit dokument s obory názvů v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cbcca-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="cbcca-104">Při použití literálů XML v Visual Basic mohou uživatelé definovat jeden globální výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="cbcca-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="cbcca-105">Tento obor názvů je výchozím oborem názvů pro literály XML a vlastnosti XML.</span><span class="sxs-lookup"><span data-stu-id="cbcca-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="cbcca-106">Výchozí obor názvů XML lze definovat buď na úrovni projektu, nebo na úrovni souboru.</span><span class="sxs-lookup"><span data-stu-id="cbcca-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="cbcca-107">Pokud je definována na úrovni souboru, přepisuje výchozí obor názvů na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="cbcca-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="cbcca-108">Můžete také definovat jiné obory názvů a zadat předpony oboru názvů pro tyto obory názvů.</span><span class="sxs-lookup"><span data-stu-id="cbcca-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="cbcca-109">Pomocí klíčového slova `Imports` definujete výchozí obory názvů a obory názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="cbcca-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="cbcca-110">Další informace naleznete v tématu [Úvod do literálů XML v Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="cbcca-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="cbcca-111">Všimněte si, že výchozí obor názvů XML se vztahuje pouze na elementy a nikoli na atributy.</span><span class="sxs-lookup"><span data-stu-id="cbcca-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="cbcca-112">Atributy jsou ve výchozím nastavení vždy v žádném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cbcca-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="cbcca-113">Můžete však použít předponu oboru názvů pro vložení atributu do oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cbcca-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbcca-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbcca-114">Example</span></span>  
 <span data-ttu-id="cbcca-115">Tento příklad vytvoří dokument, který obsahuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="cbcca-115">This example creates a document that contains a namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="cbcca-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cbcca-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="cbcca-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbcca-117">Example</span></span>  
 <span data-ttu-id="cbcca-118">Tento příklad vytvoří dokument, který obsahuje dva obory názvů, z nichž jeden je výchozím oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="cbcca-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="cbcca-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cbcca-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="cbcca-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbcca-120">Example</span></span>  
 <span data-ttu-id="cbcca-121">Následující příklad vytvoří dokument, který obsahuje více oborů názvů, s předponami oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cbcca-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="cbcca-122">Při serializaci stromu XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emituje deklarace oboru názvů podle potřeby, aby byl každý element v jeho určeném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cbcca-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="cbcca-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cbcca-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbcca-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbcca-124">See also</span></span>

- [<span data-ttu-id="cbcca-125">Přehled oborů názvů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbcca-125">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
