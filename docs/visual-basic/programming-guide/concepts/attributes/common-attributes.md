---
title: Běžné atributy
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 2889411779a275baa8c91862d4cac2f820d660d0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353532"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="34bf8-102">Common Attributes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34bf8-102">Common Attributes (Visual Basic)</span></span>

<span data-ttu-id="34bf8-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span><span class="sxs-lookup"><span data-stu-id="34bf8-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>

- [<span data-ttu-id="34bf8-104">Global Attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-104">Global Attributes</span></span>](#Global)

- [<span data-ttu-id="34bf8-105">Obsolete Attribute</span><span class="sxs-lookup"><span data-stu-id="34bf8-105">Obsolete Attribute</span></span>](#Obsolete)

- [<span data-ttu-id="34bf8-106">Conditional Attribute</span><span class="sxs-lookup"><span data-stu-id="34bf8-106">Conditional Attribute</span></span>](#Conditional)

- [<span data-ttu-id="34bf8-107">Caller Info Attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-107">Caller Info Attributes</span></span>](#CallerInfo)

- [<span data-ttu-id="34bf8-108">Visual Basic Attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-108">Visual Basic Attributes</span></span>](#VB)

## <a name="Global"></a> <span data-ttu-id="34bf8-109">Global Attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-109">Global Attributes</span></span>

<span data-ttu-id="34bf8-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span><span class="sxs-lookup"><span data-stu-id="34bf8-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="34bf8-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span><span class="sxs-lookup"><span data-stu-id="34bf8-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

<span data-ttu-id="34bf8-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span><span class="sxs-lookup"><span data-stu-id="34bf8-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="34bf8-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span><span class="sxs-lookup"><span data-stu-id="34bf8-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="34bf8-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="34bf8-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>

<span data-ttu-id="34bf8-115">Assembly attributes are values that provide information about an assembly.</span><span class="sxs-lookup"><span data-stu-id="34bf8-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="34bf8-116">They fall into the following categories:</span><span class="sxs-lookup"><span data-stu-id="34bf8-116">They fall into the following categories:</span></span>

- <span data-ttu-id="34bf8-117">Assembly identity attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-117">Assembly identity attributes</span></span>

- <span data-ttu-id="34bf8-118">Informational attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-118">Informational attributes</span></span>

- <span data-ttu-id="34bf8-119">Assembly manifest attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-119">Assembly manifest attributes</span></span>

### <a name="assembly-identity-attributes"></a><span data-ttu-id="34bf8-120">Assembly Identity Attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-120">Assembly Identity Attributes</span></span>

<span data-ttu-id="34bf8-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span><span class="sxs-lookup"><span data-stu-id="34bf8-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="34bf8-122">These attributes form the full name of the assembly and are required when you reference it in code.</span><span class="sxs-lookup"><span data-stu-id="34bf8-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="34bf8-123">You can set an assembly's version and culture using attributes.</span><span class="sxs-lookup"><span data-stu-id="34bf8-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="34bf8-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="34bf8-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span><span class="sxs-lookup"><span data-stu-id="34bf8-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="34bf8-126">The following table shows the identity attributes.</span><span class="sxs-lookup"><span data-stu-id="34bf8-126">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="34bf8-127">Atribut</span><span class="sxs-lookup"><span data-stu-id="34bf8-127">Attribute</span></span>|<span data-ttu-id="34bf8-128">Účel</span><span class="sxs-lookup"><span data-stu-id="34bf8-128">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="34bf8-129">Fully describes the identity of an assembly.</span><span class="sxs-lookup"><span data-stu-id="34bf8-129">Fully describes the identity of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="34bf8-130">Specifies the version of an assembly.</span><span class="sxs-lookup"><span data-stu-id="34bf8-130">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="34bf8-131">Specifies which culture the assembly supports.</span><span class="sxs-lookup"><span data-stu-id="34bf8-131">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="34bf8-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span><span class="sxs-lookup"><span data-stu-id="34bf8-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

### <a name="informational-attributes"></a><span data-ttu-id="34bf8-133">Informational Attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-133">Informational Attributes</span></span>

<span data-ttu-id="34bf8-134">You can use informational attributes to provide additional company or product information for an assembly.</span><span class="sxs-lookup"><span data-stu-id="34bf8-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="34bf8-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="34bf8-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="34bf8-136">Atribut</span><span class="sxs-lookup"><span data-stu-id="34bf8-136">Attribute</span></span>|<span data-ttu-id="34bf8-137">Účel</span><span class="sxs-lookup"><span data-stu-id="34bf8-137">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="34bf8-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="34bf8-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="34bf8-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="34bf8-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="34bf8-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="34bf8-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span><span class="sxs-lookup"><span data-stu-id="34bf8-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="34bf8-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span><span class="sxs-lookup"><span data-stu-id="34bf8-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

### <a name="assembly-manifest-attributes"></a><span data-ttu-id="34bf8-145">Assembly Manifest Attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-145">Assembly Manifest Attributes</span></span>

<span data-ttu-id="34bf8-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="34bf8-147">This includes title, description, default alias, and configuration.</span><span class="sxs-lookup"><span data-stu-id="34bf8-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="34bf8-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="34bf8-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="34bf8-149">Atribut</span><span class="sxs-lookup"><span data-stu-id="34bf8-149">Attribute</span></span>|<span data-ttu-id="34bf8-150">Účel</span><span class="sxs-lookup"><span data-stu-id="34bf8-150">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="34bf8-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="34bf8-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="34bf8-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="34bf8-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="34bf8-154">Defines a friendly default alias for an assembly manifest</span><span class="sxs-lookup"><span data-stu-id="34bf8-154">Defines a friendly default alias for an assembly manifest</span></span>|

## <a name="Obsolete"></a> <span data-ttu-id="34bf8-155">Obsolete Attribute</span><span class="sxs-lookup"><span data-stu-id="34bf8-155">Obsolete Attribute</span></span>

<span data-ttu-id="34bf8-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span><span class="sxs-lookup"><span data-stu-id="34bf8-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="34bf8-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span><span class="sxs-lookup"><span data-stu-id="34bf8-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="34bf8-158">Příklad:</span><span class="sxs-lookup"><span data-stu-id="34bf8-158">For example:</span></span>

```vb
<System.Obsolete("use class B")>
Class A
    Sub Method()
    End Sub
End Class

Class B
    <System.Obsolete("use NewMethod", True)>
    Sub OldMethod()
    End Sub

    Sub NewMethod()
    End Sub
End Class
```

<span data-ttu-id="34bf8-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="34bf8-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="34bf8-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span><span class="sxs-lookup"><span data-stu-id="34bf8-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="34bf8-161">Calling `B.NewMethod`, however, produces no warning or error.</span><span class="sxs-lookup"><span data-stu-id="34bf8-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>

<span data-ttu-id="34bf8-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span><span class="sxs-lookup"><span data-stu-id="34bf8-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="34bf8-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span><span class="sxs-lookup"><span data-stu-id="34bf8-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

<span data-ttu-id="34bf8-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span><span class="sxs-lookup"><span data-stu-id="34bf8-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>

<span data-ttu-id="34bf8-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span><span class="sxs-lookup"><span data-stu-id="34bf8-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>

<span data-ttu-id="34bf8-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span><span class="sxs-lookup"><span data-stu-id="34bf8-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="34bf8-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="34bf8-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

## <a name="Conditional"></a> <span data-ttu-id="34bf8-168">Conditional Attribute</span><span class="sxs-lookup"><span data-stu-id="34bf8-168">Conditional Attribute</span></span>

<span data-ttu-id="34bf8-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span><span class="sxs-lookup"><span data-stu-id="34bf8-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="34bf8-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span><span class="sxs-lookup"><span data-stu-id="34bf8-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="34bf8-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span><span class="sxs-lookup"><span data-stu-id="34bf8-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

```vb
#Const TRACE_ON = True
Imports System.Diagnostics

Module TestConditionalAttribute
    Public Class Trace
        <Conditional("TRACE_ON")>
        Public Shared Sub Msg(ByVal msg As String)
            Console.WriteLine(msg)
        End Sub

    End Class

    Sub Main()
        Trace.Msg("Now in Main...")
        Console.WriteLine("Done.")
    End Sub
End Module
```

<span data-ttu-id="34bf8-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span><span class="sxs-lookup"><span data-stu-id="34bf8-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>

<span data-ttu-id="34bf8-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span><span class="sxs-lookup"><span data-stu-id="34bf8-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

<span data-ttu-id="34bf8-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span><span class="sxs-lookup"><span data-stu-id="34bf8-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="34bf8-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span><span class="sxs-lookup"><span data-stu-id="34bf8-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="34bf8-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span><span class="sxs-lookup"><span data-stu-id="34bf8-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

<span data-ttu-id="34bf8-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span><span class="sxs-lookup"><span data-stu-id="34bf8-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>

### <a name="using-multiple-identifiers"></a><span data-ttu-id="34bf8-178">Using Multiple Identifiers</span><span class="sxs-lookup"><span data-stu-id="34bf8-178">Using Multiple Identifiers</span></span>

<span data-ttu-id="34bf8-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span><span class="sxs-lookup"><span data-stu-id="34bf8-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="34bf8-180">In this example, the presence of either `A` or `B` will result in a method call:</span><span class="sxs-lookup"><span data-stu-id="34bf8-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

<span data-ttu-id="34bf8-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span><span class="sxs-lookup"><span data-stu-id="34bf8-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="34bf8-182">For example, the second method below will execute only if both `A` and `B` are defined:</span><span class="sxs-lookup"><span data-stu-id="34bf8-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>

```vb
<Conditional("A")>
Shared Sub DoIfA()
    DoIfAandB()
End Sub

<Conditional("B")>
Shared Sub DoIfAandB()
    ' Code to execute when both A and B are defined...
End Sub
```

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="34bf8-183">Using Conditional with Attribute Classes</span><span class="sxs-lookup"><span data-stu-id="34bf8-183">Using Conditional with Attribute Classes</span></span>

<span data-ttu-id="34bf8-184">The `Conditional` attribute can also be applied to an attribute class definition.</span><span class="sxs-lookup"><span data-stu-id="34bf8-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="34bf8-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span><span class="sxs-lookup"><span data-stu-id="34bf8-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>

```vb
<Conditional("DEBUG")>
Public Class Documentation
    Inherits System.Attribute
    Private text As String
    Sub New(ByVal doc_text As String)
        text = doc_text
    End Sub
End Class

Class SampleClass
    ' This attribute will only be included if DEBUG is defined.
    <Documentation("This method displays an integer.")>
    Shared Sub DoWork(ByVal i As Integer)
        System.Console.WriteLine(i)
    End Sub
End Class
```

## <a name="CallerInfo"></a> <span data-ttu-id="34bf8-186">Caller Info Attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-186">Caller Info Attributes</span></span>

<span data-ttu-id="34bf8-187">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="34bf8-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="34bf8-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span><span class="sxs-lookup"><span data-stu-id="34bf8-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>

<span data-ttu-id="34bf8-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span><span class="sxs-lookup"><span data-stu-id="34bf8-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="34bf8-190">Each optional parameter specifies a default value.</span><span class="sxs-lookup"><span data-stu-id="34bf8-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="34bf8-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span><span class="sxs-lookup"><span data-stu-id="34bf8-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="34bf8-192">Atribut</span><span class="sxs-lookup"><span data-stu-id="34bf8-192">Attribute</span></span>|<span data-ttu-id="34bf8-193">Popis</span><span class="sxs-lookup"><span data-stu-id="34bf8-193">Description</span></span>|<span data-ttu-id="34bf8-194">Typ</span><span class="sxs-lookup"><span data-stu-id="34bf8-194">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="34bf8-195">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="34bf8-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="34bf8-196">This is the path at compile time.</span><span class="sxs-lookup"><span data-stu-id="34bf8-196">This is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="34bf8-197">Line number in the source file from which the method is called.</span><span class="sxs-lookup"><span data-stu-id="34bf8-197">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="34bf8-198">Method name or property name of the caller.</span><span class="sxs-lookup"><span data-stu-id="34bf8-198">Method name or property name of the caller.</span></span> <span data-ttu-id="34bf8-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="34bf8-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|

<span data-ttu-id="34bf8-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="34bf8-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>

## <a name="VB"></a> <span data-ttu-id="34bf8-201">Visual Basic Attributes</span><span class="sxs-lookup"><span data-stu-id="34bf8-201">Visual Basic Attributes</span></span>

<span data-ttu-id="34bf8-202">The following table lists the attributes that are specific to Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="34bf8-202">The following table lists the attributes that are specific to Visual Basic.</span></span>

|<span data-ttu-id="34bf8-203">Atribut</span><span class="sxs-lookup"><span data-stu-id="34bf8-203">Attribute</span></span>|<span data-ttu-id="34bf8-204">Účel</span><span class="sxs-lookup"><span data-stu-id="34bf8-204">Purpose</span></span>|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="34bf8-205">Indicates to the compiler that the class should be exposed as a COM object.</span><span class="sxs-lookup"><span data-stu-id="34bf8-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="34bf8-206">Allows module members to be accessed using only the qualification needed for the module.</span><span class="sxs-lookup"><span data-stu-id="34bf8-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="34bf8-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span><span class="sxs-lookup"><span data-stu-id="34bf8-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="34bf8-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span><span class="sxs-lookup"><span data-stu-id="34bf8-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|

### <a name="comclassattribute"></a><span data-ttu-id="34bf8-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="34bf8-209">COMClassAttribute</span></span>

<span data-ttu-id="34bf8-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="34bf8-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="34bf8-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="34bf8-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="34bf8-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span><span class="sxs-lookup"><span data-stu-id="34bf8-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>

### <a name="hidemodulenameattribute"></a><span data-ttu-id="34bf8-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="34bf8-213">HideModuleNameAttribute</span></span>

<span data-ttu-id="34bf8-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span><span class="sxs-lookup"><span data-stu-id="34bf8-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>

### <a name="vbfixedstringattribute"></a><span data-ttu-id="34bf8-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="34bf8-215">VBFixedStringAttribute</span></span>

<span data-ttu-id="34bf8-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span><span class="sxs-lookup"><span data-stu-id="34bf8-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="34bf8-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span><span class="sxs-lookup"><span data-stu-id="34bf8-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="34bf8-218">The following code demonstrates this:</span><span class="sxs-lookup"><span data-stu-id="34bf8-218">The following code demonstrates this:</span></span>

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a><span data-ttu-id="34bf8-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="34bf8-219">VBFixedArrayAttribute</span></span>

<span data-ttu-id="34bf8-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span><span class="sxs-lookup"><span data-stu-id="34bf8-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="34bf8-221">Like Visual Basic strings, arrays are of variable length by default.</span><span class="sxs-lookup"><span data-stu-id="34bf8-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="34bf8-222">This attribute is useful when serializing or writing data to files.</span><span class="sxs-lookup"><span data-stu-id="34bf8-222">This attribute is useful when serializing or writing data to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="34bf8-223">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34bf8-223">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="34bf8-224">Visual Basic Programming Guide</span><span class="sxs-lookup"><span data-stu-id="34bf8-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="34bf8-225">Atributy</span><span class="sxs-lookup"><span data-stu-id="34bf8-225">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="34bf8-226">Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34bf8-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="34bf8-227">Accessing Attributes by Using Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34bf8-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
