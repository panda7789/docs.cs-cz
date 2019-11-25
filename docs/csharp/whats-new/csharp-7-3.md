---
title: What's new in C# 7.3
description: An overview of new features in C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204557"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="83f8b-103">What's new in C# 7.3</span><span class="sxs-lookup"><span data-stu-id="83f8b-103">What's new in C# 7.3</span></span>

<span data-ttu-id="83f8b-104">There are two main themes to the C# 7.3 release.</span><span class="sxs-lookup"><span data-stu-id="83f8b-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="83f8b-105">One theme provides features that enable safe code to be as performant as unsafe code.</span><span class="sxs-lookup"><span data-stu-id="83f8b-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="83f8b-106">The second theme provides incremental improvements to existing features.</span><span class="sxs-lookup"><span data-stu-id="83f8b-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="83f8b-107">In addition, new compiler options were added in this release.</span><span class="sxs-lookup"><span data-stu-id="83f8b-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="83f8b-108">The following new features support the theme of better performance for safe code:</span><span class="sxs-lookup"><span data-stu-id="83f8b-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="83f8b-109">You can access fixed fields without pinning.</span><span class="sxs-lookup"><span data-stu-id="83f8b-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="83f8b-110">You can reassign `ref` local variables.</span><span class="sxs-lookup"><span data-stu-id="83f8b-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="83f8b-111">You can use initializers on `stackalloc` arrays.</span><span class="sxs-lookup"><span data-stu-id="83f8b-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="83f8b-112">You can use `fixed` statements with any type that supports a pattern.</span><span class="sxs-lookup"><span data-stu-id="83f8b-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="83f8b-113">You can use additional generic constraints.</span><span class="sxs-lookup"><span data-stu-id="83f8b-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="83f8b-114">The following enhancements were made to existing features:</span><span class="sxs-lookup"><span data-stu-id="83f8b-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="83f8b-115">You can test `==` and `!=` with tuple types.</span><span class="sxs-lookup"><span data-stu-id="83f8b-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="83f8b-116">You can use expression variables in more locations.</span><span class="sxs-lookup"><span data-stu-id="83f8b-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="83f8b-117">You may attach attributes to the backing field of auto-implemented properties.</span><span class="sxs-lookup"><span data-stu-id="83f8b-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="83f8b-118">Method resolution when arguments differ by `in` has been improved.</span><span class="sxs-lookup"><span data-stu-id="83f8b-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="83f8b-119">Overload resolution now has fewer ambiguous cases.</span><span class="sxs-lookup"><span data-stu-id="83f8b-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="83f8b-120">The new compiler options are:</span><span class="sxs-lookup"><span data-stu-id="83f8b-120">The new compiler options are:</span></span>

- <span data-ttu-id="83f8b-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span><span class="sxs-lookup"><span data-stu-id="83f8b-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="83f8b-122">`-pathmap` to provide a mapping for source directories.</span><span class="sxs-lookup"><span data-stu-id="83f8b-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="83f8b-123">The remainder of this article provides details and links to learn more about each of the improvements.</span><span class="sxs-lookup"><span data-stu-id="83f8b-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="83f8b-124">You can explore these features in your environment using the `dotnet try` global tool:</span><span class="sxs-lookup"><span data-stu-id="83f8b-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="83f8b-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span><span class="sxs-lookup"><span data-stu-id="83f8b-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="83f8b-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span><span class="sxs-lookup"><span data-stu-id="83f8b-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="83f8b-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span><span class="sxs-lookup"><span data-stu-id="83f8b-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="83f8b-128">Run `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="83f8b-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="83f8b-129">Enabling more efficient safe code</span><span class="sxs-lookup"><span data-stu-id="83f8b-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="83f8b-130">You should be able to write C# code safely that performs as well as unsafe code.</span><span class="sxs-lookup"><span data-stu-id="83f8b-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="83f8b-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span><span class="sxs-lookup"><span data-stu-id="83f8b-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="83f8b-132">These new features expand the capabilities of verifiable safe code.</span><span class="sxs-lookup"><span data-stu-id="83f8b-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="83f8b-133">Strive to write more of your code using safe constructs.</span><span class="sxs-lookup"><span data-stu-id="83f8b-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="83f8b-134">These features make that easier.</span><span class="sxs-lookup"><span data-stu-id="83f8b-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="83f8b-135">Indexing `fixed` fields does not require pinning</span><span class="sxs-lookup"><span data-stu-id="83f8b-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="83f8b-136">Consider this struct:</span><span class="sxs-lookup"><span data-stu-id="83f8b-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="83f8b-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="83f8b-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="83f8b-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span><span class="sxs-lookup"><span data-stu-id="83f8b-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="83f8b-139">The variable `p` accesses one element in `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="83f8b-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="83f8b-140">You don't need to declare a separate `int*` variable.</span><span class="sxs-lookup"><span data-stu-id="83f8b-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="83f8b-141">Note that you still need an `unsafe` context.</span><span class="sxs-lookup"><span data-stu-id="83f8b-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="83f8b-142">In earlier versions of C#, you need to declare a second fixed pointer:</span><span class="sxs-lookup"><span data-stu-id="83f8b-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="83f8b-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="83f8b-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="83f8b-144">`ref` local variables may be reassigned</span><span class="sxs-lookup"><span data-stu-id="83f8b-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="83f8b-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span><span class="sxs-lookup"><span data-stu-id="83f8b-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="83f8b-146">The following code now compiles:</span><span class="sxs-lookup"><span data-stu-id="83f8b-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="83f8b-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="83f8b-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="83f8b-148">`stackalloc` arrays support initializers</span><span class="sxs-lookup"><span data-stu-id="83f8b-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="83f8b-149">You've been able to specify the values for elements in an array when you initialize it:</span><span class="sxs-lookup"><span data-stu-id="83f8b-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="83f8b-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="83f8b-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="83f8b-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span><span class="sxs-lookup"><span data-stu-id="83f8b-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="83f8b-152">More types support the `fixed` statement</span><span class="sxs-lookup"><span data-stu-id="83f8b-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="83f8b-153">The `fixed` statement supported a limited set of types.</span><span class="sxs-lookup"><span data-stu-id="83f8b-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="83f8b-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span><span class="sxs-lookup"><span data-stu-id="83f8b-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="83f8b-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span><span class="sxs-lookup"><span data-stu-id="83f8b-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="83f8b-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span><span class="sxs-lookup"><span data-stu-id="83f8b-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="83f8b-157">Enhanced generic constraints</span><span class="sxs-lookup"><span data-stu-id="83f8b-157">Enhanced generic constraints</span></span>

<span data-ttu-id="83f8b-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span><span class="sxs-lookup"><span data-stu-id="83f8b-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="83f8b-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="83f8b-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="83f8b-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="83f8b-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="83f8b-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="83f8b-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="83f8b-162">Closed generic types may no longer meet these new constraints.</span><span class="sxs-lookup"><span data-stu-id="83f8b-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="83f8b-163">Make existing features better</span><span class="sxs-lookup"><span data-stu-id="83f8b-163">Make existing features better</span></span>

<span data-ttu-id="83f8b-164">The second theme provides improvements to features in the language.</span><span class="sxs-lookup"><span data-stu-id="83f8b-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="83f8b-165">These features improve productivity when writing C#.</span><span class="sxs-lookup"><span data-stu-id="83f8b-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="83f8b-166">Tuples support `==` and `!=`</span><span class="sxs-lookup"><span data-stu-id="83f8b-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="83f8b-167">The C# tuple types now support `==` and `!=`.</span><span class="sxs-lookup"><span data-stu-id="83f8b-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="83f8b-168">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="83f8b-168">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="83f8b-169">Attach attributes to the backing fields for auto-implemented properties</span><span class="sxs-lookup"><span data-stu-id="83f8b-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="83f8b-170">This syntax is now supported:</span><span class="sxs-lookup"><span data-stu-id="83f8b-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="83f8b-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="83f8b-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="83f8b-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span><span class="sxs-lookup"><span data-stu-id="83f8b-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="83f8b-173">`in` method overload resolution tiebreaker</span><span class="sxs-lookup"><span data-stu-id="83f8b-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="83f8b-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span><span class="sxs-lookup"><span data-stu-id="83f8b-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="83f8b-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span><span class="sxs-lookup"><span data-stu-id="83f8b-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="83f8b-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span><span class="sxs-lookup"><span data-stu-id="83f8b-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="83f8b-177">This was implemented as a bug fix.</span><span class="sxs-lookup"><span data-stu-id="83f8b-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="83f8b-178">This no longer is ambiguous even with the language version set to "7.2".</span><span class="sxs-lookup"><span data-stu-id="83f8b-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="83f8b-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="83f8b-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="83f8b-180">Extend expression variables in initializers</span><span class="sxs-lookup"><span data-stu-id="83f8b-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="83f8b-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span><span class="sxs-lookup"><span data-stu-id="83f8b-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="83f8b-182">It enables code such as the following example:</span><span class="sxs-lookup"><span data-stu-id="83f8b-182">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="83f8b-183">Vylepšení kandidátů přetížení</span><span class="sxs-lookup"><span data-stu-id="83f8b-183">Improved overload candidates</span></span>

<span data-ttu-id="83f8b-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span><span class="sxs-lookup"><span data-stu-id="83f8b-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="83f8b-185">This release adds three new rules to help the compiler pick the obvious choice:</span><span class="sxs-lookup"><span data-stu-id="83f8b-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="83f8b-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span><span class="sxs-lookup"><span data-stu-id="83f8b-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="83f8b-187">The compiler discards the static members if the method was invoked with an instance receiver.</span><span class="sxs-lookup"><span data-stu-id="83f8b-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="83f8b-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span><span class="sxs-lookup"><span data-stu-id="83f8b-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="83f8b-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span><span class="sxs-lookup"><span data-stu-id="83f8b-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="83f8b-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span><span class="sxs-lookup"><span data-stu-id="83f8b-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="83f8b-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span><span class="sxs-lookup"><span data-stu-id="83f8b-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="83f8b-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span><span class="sxs-lookup"><span data-stu-id="83f8b-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="83f8b-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span><span class="sxs-lookup"><span data-stu-id="83f8b-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="83f8b-194">New compiler options</span><span class="sxs-lookup"><span data-stu-id="83f8b-194">New compiler options</span></span>

<span data-ttu-id="83f8b-195">New compiler options support new build and DevOps scenarios for C# programs.</span><span class="sxs-lookup"><span data-stu-id="83f8b-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="83f8b-196">Public or Open Source signing</span><span class="sxs-lookup"><span data-stu-id="83f8b-196">Public or Open Source signing</span></span>

<span data-ttu-id="83f8b-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span><span class="sxs-lookup"><span data-stu-id="83f8b-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="83f8b-198">The assembly is marked as signed, but the signature is taken from the public key.</span><span class="sxs-lookup"><span data-stu-id="83f8b-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="83f8b-199">This option enables you to build signed assemblies from open-source projects using a public key.</span><span class="sxs-lookup"><span data-stu-id="83f8b-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="83f8b-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span><span class="sxs-lookup"><span data-stu-id="83f8b-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="83f8b-201">pathmap</span><span class="sxs-lookup"><span data-stu-id="83f8b-201">pathmap</span></span>

<span data-ttu-id="83f8b-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span><span class="sxs-lookup"><span data-stu-id="83f8b-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="83f8b-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="83f8b-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="83f8b-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span><span class="sxs-lookup"><span data-stu-id="83f8b-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
