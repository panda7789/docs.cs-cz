---
title: Using – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 6ec0e228b3898f66f27e322b5db2dd7f3bf3d7d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352760"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="6c1bf-102">Using – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c1bf-102">Using Statement (Visual Basic)</span></span>

<span data-ttu-id="6c1bf-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c1bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c1bf-104">Syntax</span></span>

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a><span data-ttu-id="6c1bf-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6c1bf-105">Parts</span></span>

|<span data-ttu-id="6c1bf-106">Termín</span><span class="sxs-lookup"><span data-stu-id="6c1bf-106">Term</span></span>|<span data-ttu-id="6c1bf-107">Definice</span><span class="sxs-lookup"><span data-stu-id="6c1bf-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="6c1bf-108">Required if you do not supply `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="6c1bf-109">List of one or more system resources that this `Using` block controls, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="6c1bf-110">Required if you do not supply `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="6c1bf-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="6c1bf-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-112">Optional.</span></span> <span data-ttu-id="6c1bf-113">Block of statements that the `Using` block runs.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="6c1bf-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-114">Required.</span></span> <span data-ttu-id="6c1bf-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  

 <span data-ttu-id="6c1bf-116">Each resource in the `resourcelist` part has the following syntax and parts:</span><span class="sxs-lookup"><span data-stu-id="6c1bf-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 <span data-ttu-id="6c1bf-117">-nebo-</span><span class="sxs-lookup"><span data-stu-id="6c1bf-117">-or-</span></span>

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a><span data-ttu-id="6c1bf-118">resourcelist Parts</span><span class="sxs-lookup"><span data-stu-id="6c1bf-118">resourcelist Parts</span></span>

|<span data-ttu-id="6c1bf-119">Termín</span><span class="sxs-lookup"><span data-stu-id="6c1bf-119">Term</span></span>|<span data-ttu-id="6c1bf-120">Definice</span><span class="sxs-lookup"><span data-stu-id="6c1bf-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="6c1bf-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-121">Required.</span></span> <span data-ttu-id="6c1bf-122">Reference variable that refers to a system resource that the `Using` block controls.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="6c1bf-123">Required if the `Using` statement acquires the resource.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="6c1bf-124">If you have already acquired the resource, use the second syntax alternative.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="6c1bf-125">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-125">Required.</span></span> <span data-ttu-id="6c1bf-126">The class of the resource.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-126">The class of the resource.</span></span> <span data-ttu-id="6c1bf-127">The class must implement the <xref:System.IDisposable> interface.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="6c1bf-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-128">Optional.</span></span> <span data-ttu-id="6c1bf-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="6c1bf-130">See [Parameter List](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="6c1bf-130">See [Parameter List](parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="6c1bf-131">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-131">Required.</span></span> <span data-ttu-id="6c1bf-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="6c1bf-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c1bf-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c1bf-134">Remarks</span></span>

 <span data-ttu-id="6c1bf-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="6c1bf-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="6c1bf-137">This makes them available for other code to use.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-137">This makes them available for other code to use.</span></span>

 <span data-ttu-id="6c1bf-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="6c1bf-139">You do not need a `Using` block for managed resources.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="6c1bf-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

 <span data-ttu-id="6c1bf-141">A `Using` block has three parts: acquisition, usage, and disposal.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>

- <span data-ttu-id="6c1bf-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="6c1bf-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="6c1bf-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>

- <span data-ttu-id="6c1bf-145">*Usage* means accessing the resources and performing actions with them.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="6c1bf-146">The statements between `Using` and `End Using` represent the usage of the resources.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>

- <span data-ttu-id="6c1bf-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="6c1bf-148">This allows the object to cleanly terminate its resources.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="6c1bf-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>

## <a name="behavior"></a><span data-ttu-id="6c1bf-150">Behavior</span><span class="sxs-lookup"><span data-stu-id="6c1bf-150">Behavior</span></span>

 <span data-ttu-id="6c1bf-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="6c1bf-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="6c1bf-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>

 <span data-ttu-id="6c1bf-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>

 <span data-ttu-id="6c1bf-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>

 <span data-ttu-id="6c1bf-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>

## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="6c1bf-157">Structured Exception Handling Within a Using Block</span><span class="sxs-lookup"><span data-stu-id="6c1bf-157">Structured Exception Handling Within a Using Block</span></span>

 <span data-ttu-id="6c1bf-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="6c1bf-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>

## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="6c1bf-160">Structured Exception Handling Instead of a Using Block</span><span class="sxs-lookup"><span data-stu-id="6c1bf-160">Structured Exception Handling Instead of a Using Block</span></span>

 <span data-ttu-id="6c1bf-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="6c1bf-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> <span data-ttu-id="6c1bf-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="6c1bf-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>

## <a name="example"></a><span data-ttu-id="6c1bf-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c1bf-165">Example</span></span>

 <span data-ttu-id="6c1bf-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="6c1bf-167">The example also reads that same file and displays the lines of text:</span><span class="sxs-lookup"><span data-stu-id="6c1bf-167">The example also reads that same file and displays the lines of text:</span></span>

 <span data-ttu-id="6c1bf-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span><span class="sxs-lookup"><span data-stu-id="6c1bf-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a><span data-ttu-id="6c1bf-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c1bf-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="6c1bf-170">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="6c1bf-170">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="6c1bf-171">Postupy: Odstranění systémového prostředku</span><span class="sxs-lookup"><span data-stu-id="6c1bf-171">How to: Dispose of a System Resource</span></span>](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
