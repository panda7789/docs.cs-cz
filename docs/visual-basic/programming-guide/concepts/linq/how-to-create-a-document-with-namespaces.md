---
title: 'Postupy: vytvoření dokumentu s obory názvů (technologie LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 204d8a9cbb6ce47c6334c7309d27910c75b90ae0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643075"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="df662-102">Postupy: vytvoření dokumentu s obory názvů (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df662-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="df662-103">Toto téma ukazuje, jak vytvořit dokument s obory názvů v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="df662-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="df662-104">Pokud používáte literálů XML v jazyce Visual Basic, uživatelé mohou definovat jeden globální výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="df662-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="df662-105">Tento obor názvů je výchozí obor názvů pro literály XML a vlastnosti XML.</span><span class="sxs-lookup"><span data-stu-id="df662-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="df662-106">Výchozí obor názvů XML lze definovat na úrovni projektu nebo úrovni souborů.</span><span class="sxs-lookup"><span data-stu-id="df662-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="df662-107">Pokud je definován na úrovni souborů, přepíše výchozí obor názvů na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="df662-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="df662-108">Můžete také definovat další obory názvů a zadejte předpony oboru názvů pro obory názvů.</span><span class="sxs-lookup"><span data-stu-id="df662-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="df662-109">Definovat výchozí obory názvů a obory názvů s předponou pomocí `Imports` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="df662-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="df662-110">Další informace najdete v tématu [Úvod do literálů XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="df662-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="df662-111">Všimněte si, že výchozí obor názvů XML se vztahuje pouze na elementy a atributy.</span><span class="sxs-lookup"><span data-stu-id="df662-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="df662-112">Atributy jsou ve výchozím nastavení vždy v žádné oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="df662-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="df662-113">Můžete však použít předponu oboru názvů uvést atribut v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="df662-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df662-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="df662-114">Example</span></span>  
 <span data-ttu-id="df662-115">Tento příklad vytvoří dokument, který obsahuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="df662-115">This example creates a document that contains a namespace.</span></span>  
  
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
  
 <span data-ttu-id="df662-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="df662-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="df662-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="df662-117">Example</span></span>  
 <span data-ttu-id="df662-118">Tento příklad vytvoří dokument, který obsahuje dva obory názvů, z nichž jeden je výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="df662-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
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
  
 <span data-ttu-id="df662-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="df662-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="df662-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="df662-120">Example</span></span>  
 <span data-ttu-id="df662-121">Následující příklad vytvoří dokument, který obsahuje více oborů názvů, jak pomocí předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="df662-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="df662-122">Při serializaci strom XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vysílá deklarace oboru názvů podle potřeby tak, aby každý prvek v jeho určené oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="df662-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
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
  
 <span data-ttu-id="df662-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="df662-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df662-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="df662-124">See Also</span></span>  
 [<span data-ttu-id="df662-125">Práce s obory názvů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df662-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
