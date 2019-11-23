---
title: Metody rozšíření
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: a88756fce9137f89db1b6b8b007d528e98381830
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341179"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="231f0-102">Metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="231f0-102">Extension Methods (Visual Basic)</span></span>

<span data-ttu-id="231f0-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span><span class="sxs-lookup"><span data-stu-id="231f0-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="231f0-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span><span class="sxs-lookup"><span data-stu-id="231f0-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>

## <a name="remarks"></a><span data-ttu-id="231f0-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="231f0-105">Remarks</span></span>

<span data-ttu-id="231f0-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="231f0-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="231f0-107">You cannot define an extension property, field, or event.</span><span class="sxs-lookup"><span data-stu-id="231f0-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="231f0-108">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="231f0-108">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="231f0-109">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span><span class="sxs-lookup"><span data-stu-id="231f0-109">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span></span>

<span data-ttu-id="231f0-110">The first parameter in an extension method definition specifies which data type the method extends.</span><span class="sxs-lookup"><span data-stu-id="231f0-110">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="231f0-111">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span><span class="sxs-lookup"><span data-stu-id="231f0-111">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>

<span data-ttu-id="231f0-112">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="231f0-112">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="231f0-113">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span><span class="sxs-lookup"><span data-stu-id="231f0-113">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span></span>

## <a name="example"></a><span data-ttu-id="231f0-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="231f0-114">Example</span></span>

<span data-ttu-id="231f0-115">The following example defines a `Print` extension to the <xref:System.String> data type.</span><span class="sxs-lookup"><span data-stu-id="231f0-115">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="231f0-116">The method uses `Console.WriteLine` to display a string.</span><span class="sxs-lookup"><span data-stu-id="231f0-116">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="231f0-117">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span><span class="sxs-lookup"><span data-stu-id="231f0-117">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

<span data-ttu-id="231f0-118">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="231f0-118">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="231f0-119">Marking the module in which the method is defined is optional, but each extension method must be marked.</span><span class="sxs-lookup"><span data-stu-id="231f0-119">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="231f0-120"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span><span class="sxs-lookup"><span data-stu-id="231f0-120"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>

<span data-ttu-id="231f0-121">Extension methods can be declared only within modules.</span><span class="sxs-lookup"><span data-stu-id="231f0-121">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="231f0-122">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span><span class="sxs-lookup"><span data-stu-id="231f0-122">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="231f0-123">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span><span class="sxs-lookup"><span data-stu-id="231f0-123">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="231f0-124">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="231f0-124">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

<span data-ttu-id="231f0-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span><span class="sxs-lookup"><span data-stu-id="231f0-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="231f0-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="231f0-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="231f0-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span><span class="sxs-lookup"><span data-stu-id="231f0-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="231f0-128">The method displays the string followed by the punctuation marks.</span><span class="sxs-lookup"><span data-stu-id="231f0-128">The method displays the string followed by the punctuation marks.</span></span>

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

<span data-ttu-id="231f0-129">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="231f0-129">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>

<span data-ttu-id="231f0-130">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span><span class="sxs-lookup"><span data-stu-id="231f0-130">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="231f0-131"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span><span class="sxs-lookup"><span data-stu-id="231f0-131"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

<span data-ttu-id="231f0-132">Next, the extension methods are brought into scope and called:</span><span class="sxs-lookup"><span data-stu-id="231f0-132">Next, the extension methods are brought into scope and called:</span></span>

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

<span data-ttu-id="231f0-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span><span class="sxs-lookup"><span data-stu-id="231f0-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="231f0-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span><span class="sxs-lookup"><span data-stu-id="231f0-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>

<span data-ttu-id="231f0-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span><span class="sxs-lookup"><span data-stu-id="231f0-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="231f0-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span><span class="sxs-lookup"><span data-stu-id="231f0-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="231f0-137">The compiler will use `example` as the argument sent to the first parameter.</span><span class="sxs-lookup"><span data-stu-id="231f0-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>

<span data-ttu-id="231f0-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span><span class="sxs-lookup"><span data-stu-id="231f0-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="231f0-139">This does not apply to ordinary instance methods.</span><span class="sxs-lookup"><span data-stu-id="231f0-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="231f0-140">You can explicitly check for `Nothing` in the extension method.</span><span class="sxs-lookup"><span data-stu-id="231f0-140">You can explicitly check for `Nothing` in the extension method.</span></span>

## <a name="types-that-can-be-extended"></a><span data-ttu-id="231f0-141">Types that can be extended</span><span class="sxs-lookup"><span data-stu-id="231f0-141">Types that can be extended</span></span>

<span data-ttu-id="231f0-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span><span class="sxs-lookup"><span data-stu-id="231f0-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>

- <span data-ttu-id="231f0-143">Classes (reference types)</span><span class="sxs-lookup"><span data-stu-id="231f0-143">Classes (reference types)</span></span>
- <span data-ttu-id="231f0-144">Structures (value types)</span><span class="sxs-lookup"><span data-stu-id="231f0-144">Structures (value types)</span></span>
- <span data-ttu-id="231f0-145">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="231f0-145">Interfaces</span></span>
- <span data-ttu-id="231f0-146">Delegáty</span><span class="sxs-lookup"><span data-stu-id="231f0-146">Delegates</span></span>
- <span data-ttu-id="231f0-147">ByRef and ByVal arguments</span><span class="sxs-lookup"><span data-stu-id="231f0-147">ByRef and ByVal arguments</span></span>
- <span data-ttu-id="231f0-148">Generic method parameters</span><span class="sxs-lookup"><span data-stu-id="231f0-148">Generic method parameters</span></span>
- <span data-ttu-id="231f0-149">Pole</span><span class="sxs-lookup"><span data-stu-id="231f0-149">Arrays</span></span>

<span data-ttu-id="231f0-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span><span class="sxs-lookup"><span data-stu-id="231f0-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="231f0-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span><span class="sxs-lookup"><span data-stu-id="231f0-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>

<span data-ttu-id="231f0-152">Extension methods are not considered in late binding.</span><span class="sxs-lookup"><span data-stu-id="231f0-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="231f0-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span><span class="sxs-lookup"><span data-stu-id="231f0-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a><span data-ttu-id="231f0-154">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="231f0-154">Best practices</span></span>

<span data-ttu-id="231f0-155">Extension methods provide a convenient and powerful way to extend an existing type.</span><span class="sxs-lookup"><span data-stu-id="231f0-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="231f0-156">However, to use them successfully, there are some points to consider.</span><span class="sxs-lookup"><span data-stu-id="231f0-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="231f0-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span><span class="sxs-lookup"><span data-stu-id="231f0-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>

<span data-ttu-id="231f0-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span><span class="sxs-lookup"><span data-stu-id="231f0-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="231f0-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span><span class="sxs-lookup"><span data-stu-id="231f0-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>

- <span data-ttu-id="231f0-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span><span class="sxs-lookup"><span data-stu-id="231f0-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="231f0-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span><span class="sxs-lookup"><span data-stu-id="231f0-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>

- <span data-ttu-id="231f0-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span><span class="sxs-lookup"><span data-stu-id="231f0-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>

- <span data-ttu-id="231f0-163">You can improve robustness by putting extension methods in their own namespace.</span><span class="sxs-lookup"><span data-stu-id="231f0-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="231f0-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span><span class="sxs-lookup"><span data-stu-id="231f0-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>

- <span data-ttu-id="231f0-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span><span class="sxs-lookup"><span data-stu-id="231f0-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="231f0-166">A change in an interface affects every class that implements it.</span><span class="sxs-lookup"><span data-stu-id="231f0-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="231f0-167">Therefore, the author may be less likely to add or change methods in an interface.</span><span class="sxs-lookup"><span data-stu-id="231f0-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="231f0-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span><span class="sxs-lookup"><span data-stu-id="231f0-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>

- <span data-ttu-id="231f0-169">Extend the most specific type you can.</span><span class="sxs-lookup"><span data-stu-id="231f0-169">Extend the most specific type you can.</span></span> <span data-ttu-id="231f0-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span><span class="sxs-lookup"><span data-stu-id="231f0-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>

## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="231f0-171">Extension methods, instance methods, and properties</span><span class="sxs-lookup"><span data-stu-id="231f0-171">Extension methods, instance methods, and properties</span></span>

<span data-ttu-id="231f0-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span><span class="sxs-lookup"><span data-stu-id="231f0-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="231f0-173">The instance method has precedence even if the extension method is a better match.</span><span class="sxs-lookup"><span data-stu-id="231f0-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="231f0-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span><span class="sxs-lookup"><span data-stu-id="231f0-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="231f0-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span><span class="sxs-lookup"><span data-stu-id="231f0-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

<span data-ttu-id="231f0-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span><span class="sxs-lookup"><span data-stu-id="231f0-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="231f0-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span><span class="sxs-lookup"><span data-stu-id="231f0-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

<span data-ttu-id="231f0-178">Now reverse the data types of the parameters in the two methods:</span><span class="sxs-lookup"><span data-stu-id="231f0-178">Now reverse the data types of the parameters in the two methods:</span></span>

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

<span data-ttu-id="231f0-179">This time the code in `Main` calls the instance method both times.</span><span class="sxs-lookup"><span data-stu-id="231f0-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="231f0-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span><span class="sxs-lookup"><span data-stu-id="231f0-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

<span data-ttu-id="231f0-181">Therefore, an extension method cannot replace an existing instance method.</span><span class="sxs-lookup"><span data-stu-id="231f0-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="231f0-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span><span class="sxs-lookup"><span data-stu-id="231f0-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="231f0-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span><span class="sxs-lookup"><span data-stu-id="231f0-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

<span data-ttu-id="231f0-184">The output from this code is as follows:</span><span class="sxs-lookup"><span data-stu-id="231f0-184">The output from this code is as follows:</span></span>

```console
Extension method
Instance method
```

<span data-ttu-id="231f0-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span><span class="sxs-lookup"><span data-stu-id="231f0-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>

## <a name="extension-method-precedence"></a><span data-ttu-id="231f0-186">Extension method precedence</span><span class="sxs-lookup"><span data-stu-id="231f0-186">Extension method precedence</span></span>

<span data-ttu-id="231f0-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span><span class="sxs-lookup"><span data-stu-id="231f0-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="231f0-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span><span class="sxs-lookup"><span data-stu-id="231f0-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="231f0-189">The following list shows the precedence hierarchy, from highest to lowest.</span><span class="sxs-lookup"><span data-stu-id="231f0-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>

1. <span data-ttu-id="231f0-190">Extension methods defined inside the current module.</span><span class="sxs-lookup"><span data-stu-id="231f0-190">Extension methods defined inside the current module.</span></span>

2. <span data-ttu-id="231f0-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span><span class="sxs-lookup"><span data-stu-id="231f0-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>

3. <span data-ttu-id="231f0-192">Extension methods defined inside any type imports in the current file.</span><span class="sxs-lookup"><span data-stu-id="231f0-192">Extension methods defined inside any type imports in the current file.</span></span>

4. <span data-ttu-id="231f0-193">Extension methods defined inside any namespace imports in the current file.</span><span class="sxs-lookup"><span data-stu-id="231f0-193">Extension methods defined inside any namespace imports in the current file.</span></span>

5. <span data-ttu-id="231f0-194">Extension methods defined inside any project-level type imports.</span><span class="sxs-lookup"><span data-stu-id="231f0-194">Extension methods defined inside any project-level type imports.</span></span>

6. <span data-ttu-id="231f0-195">Extension methods defined inside any project-level namespace imports.</span><span class="sxs-lookup"><span data-stu-id="231f0-195">Extension methods defined inside any project-level namespace imports.</span></span>

<span data-ttu-id="231f0-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span><span class="sxs-lookup"><span data-stu-id="231f0-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="231f0-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="231f0-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>

## <a name="see-also"></a><span data-ttu-id="231f0-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="231f0-198">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="231f0-199">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="231f0-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="231f0-200">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="231f0-200">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="231f0-201">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="231f0-201">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="231f0-202">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="231f0-202">Optional Parameters</span></span>](optional-parameters.md)
- [<span data-ttu-id="231f0-203">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="231f0-203">Parameter Arrays</span></span>](parameter-arrays.md)
- [<span data-ttu-id="231f0-204">Attributes overview</span><span class="sxs-lookup"><span data-stu-id="231f0-204">Attributes overview</span></span>](../../concepts/attributes/index.md)
- [<span data-ttu-id="231f0-205">Scope in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="231f0-205">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
