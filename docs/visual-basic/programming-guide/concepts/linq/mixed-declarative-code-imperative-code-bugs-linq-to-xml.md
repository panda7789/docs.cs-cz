---
title: Chyby smíšeného deklarativního a imperativního kódu (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: 369fae59516df785ac686645d47e74e69a8f1457
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331650"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a><span data-ttu-id="8aba1-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8aba1-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="8aba1-103">contains various methods that allow you to modify an XML tree directly.</span><span class="sxs-lookup"><span data-stu-id="8aba1-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="8aba1-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span><span class="sxs-lookup"><span data-stu-id="8aba1-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="8aba1-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8aba1-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="8aba1-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span><span class="sxs-lookup"><span data-stu-id="8aba1-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="8aba1-107">This problem is sometimes known as "The Halloween Problem".</span><span class="sxs-lookup"><span data-stu-id="8aba1-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="8aba1-108">Definition of the Problem</span><span class="sxs-lookup"><span data-stu-id="8aba1-108">Definition of the Problem</span></span>  
 <span data-ttu-id="8aba1-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span><span class="sxs-lookup"><span data-stu-id="8aba1-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="8aba1-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span><span class="sxs-lookup"><span data-stu-id="8aba1-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="8aba1-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span><span class="sxs-lookup"><span data-stu-id="8aba1-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="8aba1-112">You are telling the computer *how* to do what you want done.</span><span class="sxs-lookup"><span data-stu-id="8aba1-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="8aba1-113">Mixing these styles of code in the same operation is what leads to problems.</span><span class="sxs-lookup"><span data-stu-id="8aba1-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="8aba1-114">Consider the following:</span><span class="sxs-lookup"><span data-stu-id="8aba1-114">Consider the following:</span></span>  
  
 <span data-ttu-id="8aba1-115">Suppose you have a linked list with three items in it (a, b, and c):</span><span class="sxs-lookup"><span data-stu-id="8aba1-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="8aba1-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span><span class="sxs-lookup"><span data-stu-id="8aba1-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="8aba1-117">You want the resulting linked list to look like this:</span><span class="sxs-lookup"><span data-stu-id="8aba1-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="8aba1-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span><span class="sxs-lookup"><span data-stu-id="8aba1-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="8aba1-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span><span class="sxs-lookup"><span data-stu-id="8aba1-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="8aba1-120">Now, your code will move to the next node in the list, which is now `a'`!</span><span class="sxs-lookup"><span data-stu-id="8aba1-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="8aba1-121">It happily adds a new item to the list, `a''`.</span><span class="sxs-lookup"><span data-stu-id="8aba1-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="8aba1-122">How would you solve this in the real world?</span><span class="sxs-lookup"><span data-stu-id="8aba1-122">How would you solve this in the real world?</span></span> <span data-ttu-id="8aba1-123">Well, you might make a copy of the original linked list, and create a completely new list.</span><span class="sxs-lookup"><span data-stu-id="8aba1-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="8aba1-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span><span class="sxs-lookup"><span data-stu-id="8aba1-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="8aba1-125">Adding While Iterating</span><span class="sxs-lookup"><span data-stu-id="8aba1-125">Adding While Iterating</span></span>  
 <span data-ttu-id="8aba1-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span><span class="sxs-lookup"><span data-stu-id="8aba1-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
```  
  
 <span data-ttu-id="8aba1-127">This code goes into an infinite loop.</span><span class="sxs-lookup"><span data-stu-id="8aba1-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="8aba1-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span><span class="sxs-lookup"><span data-stu-id="8aba1-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="8aba1-129">It ends up iterating also through the elements it just added.</span><span class="sxs-lookup"><span data-stu-id="8aba1-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="8aba1-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span><span class="sxs-lookup"><span data-stu-id="8aba1-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="8aba1-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span><span class="sxs-lookup"><span data-stu-id="8aba1-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="8aba1-132">Now the code works.</span><span class="sxs-lookup"><span data-stu-id="8aba1-132">Now the code works.</span></span> <span data-ttu-id="8aba1-133">The resulting XML tree is the following:</span><span class="sxs-lookup"><span data-stu-id="8aba1-133">The resulting XML tree is the following:</span></span>  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="8aba1-134">Deleting While Iterating</span><span class="sxs-lookup"><span data-stu-id="8aba1-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="8aba1-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span><span class="sxs-lookup"><span data-stu-id="8aba1-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="8aba1-136">However, this does not do what you want.</span><span class="sxs-lookup"><span data-stu-id="8aba1-136">However, this does not do what you want.</span></span> <span data-ttu-id="8aba1-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span><span class="sxs-lookup"><span data-stu-id="8aba1-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="8aba1-138">The preceding code produces the following output:</span><span class="sxs-lookup"><span data-stu-id="8aba1-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="8aba1-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span><span class="sxs-lookup"><span data-stu-id="8aba1-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="8aba1-140">This produces the following output:</span><span class="sxs-lookup"><span data-stu-id="8aba1-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="8aba1-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span><span class="sxs-lookup"><span data-stu-id="8aba1-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
root.RemoveAll()  
Console.WriteLine(root)  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="8aba1-142">Why Can't LINQ Automatically Handle This?</span><span class="sxs-lookup"><span data-stu-id="8aba1-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="8aba1-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span><span class="sxs-lookup"><span data-stu-id="8aba1-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="8aba1-144">However, it would be very expensive in terms of performance and memory use.</span><span class="sxs-lookup"><span data-stu-id="8aba1-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="8aba1-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span><span class="sxs-lookup"><span data-stu-id="8aba1-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="8aba1-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span><span class="sxs-lookup"><span data-stu-id="8aba1-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="8aba1-147">However, attempting to determine all code that has side-effects is incredibly complex.</span><span class="sxs-lookup"><span data-stu-id="8aba1-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="8aba1-148">Consider the following code:</span><span class="sxs-lookup"><span data-stu-id="8aba1-148">Consider the following code:</span></span>  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 <span data-ttu-id="8aba1-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span><span class="sxs-lookup"><span data-stu-id="8aba1-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="8aba1-150">But the analysis code could not just look for any code that had side-effects.</span><span class="sxs-lookup"><span data-stu-id="8aba1-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="8aba1-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span><span class="sxs-lookup"><span data-stu-id="8aba1-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="8aba1-152">LINQ to XML does not attempt to do any such analysis.</span><span class="sxs-lookup"><span data-stu-id="8aba1-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="8aba1-153">It is up to you to avoid these problems.</span><span class="sxs-lookup"><span data-stu-id="8aba1-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="8aba1-154">Doprovodné materiály</span><span class="sxs-lookup"><span data-stu-id="8aba1-154">Guidance</span></span>  
 <span data-ttu-id="8aba1-155">First, do not mix declarative and imperative code.</span><span class="sxs-lookup"><span data-stu-id="8aba1-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="8aba1-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span><span class="sxs-lookup"><span data-stu-id="8aba1-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="8aba1-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span><span class="sxs-lookup"><span data-stu-id="8aba1-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="8aba1-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span><span class="sxs-lookup"><span data-stu-id="8aba1-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="8aba1-159">Second, if performance and other considerations allow, use only declarative code.</span><span class="sxs-lookup"><span data-stu-id="8aba1-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="8aba1-160">Don't modify your existing XML tree.</span><span class="sxs-lookup"><span data-stu-id="8aba1-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="8aba1-161">Generate a new one.</span><span class="sxs-lookup"><span data-stu-id="8aba1-161">Generate a new one.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
Dim newRoot As XElement = New XElement("Root", _  
    root.Elements(), root.Elements())  
Console.WriteLine(newRoot)  
```  
  
## <a name="see-also"></a><span data-ttu-id="8aba1-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8aba1-162">See also</span></span>

- [<span data-ttu-id="8aba1-163">Advanced LINQ to XML Programming (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8aba1-163">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
