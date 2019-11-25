---
title: .NET Framework Analyzers - .NET
description: Learn how to use the .NET Framework Analyzers in the .NET Framework Analyzers package to find and address security risks
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 7e64b00eb6fd2c2dbb12c54a2c725590b4d22e15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345948"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="84af9-103">The .NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="84af9-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="84af9-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span><span class="sxs-lookup"><span data-stu-id="84af9-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="84af9-105">This analyzer finds potential issues and suggests fixes to them.</span><span class="sxs-lookup"><span data-stu-id="84af9-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="84af9-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span><span class="sxs-lookup"><span data-stu-id="84af9-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="84af9-107">You should add the analyzer to your project as early as possible in your development.</span><span class="sxs-lookup"><span data-stu-id="84af9-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="84af9-108">The sooner you find any potential issues in your code, the easier they are to fix.</span><span class="sxs-lookup"><span data-stu-id="84af9-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="84af9-109">However, you can add it at any time in the development cycle.</span><span class="sxs-lookup"><span data-stu-id="84af9-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="84af9-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span><span class="sxs-lookup"><span data-stu-id="84af9-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="84af9-111">Installing and configuring the .NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="84af9-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="84af9-112">The .NET Framework Analyzers must be installed as a NuGet package on every project where you want them to run.</span><span class="sxs-lookup"><span data-stu-id="84af9-112">The .NET Framework Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="84af9-113">Only one developer needs to add them to the project.</span><span class="sxs-lookup"><span data-stu-id="84af9-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="84af9-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span><span class="sxs-lookup"><span data-stu-id="84af9-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="84af9-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span><span class="sxs-lookup"><span data-stu-id="84af9-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="84af9-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span><span class="sxs-lookup"><span data-stu-id="84af9-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="84af9-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span><span class="sxs-lookup"><span data-stu-id="84af9-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="84af9-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span><span class="sxs-lookup"><span data-stu-id="84af9-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>

- <span data-ttu-id="84af9-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span><span class="sxs-lookup"><span data-stu-id="84af9-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="84af9-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span><span class="sxs-lookup"><span data-stu-id="84af9-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="84af9-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span><span class="sxs-lookup"><span data-stu-id="84af9-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="84af9-122">To install it, right-click on the project, and select "Manage Dependencies".</span><span class="sxs-lookup"><span data-stu-id="84af9-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="84af9-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span><span class="sxs-lookup"><span data-stu-id="84af9-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="84af9-124">Install the latest stable version in all projects in your solution.</span><span class="sxs-lookup"><span data-stu-id="84af9-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="84af9-125">Using the .NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="84af9-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="84af9-126">Once the NuGet package is installed, build your solution.</span><span class="sxs-lookup"><span data-stu-id="84af9-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="84af9-127">The analyzer will report any issues it locates in your codebase.</span><span class="sxs-lookup"><span data-stu-id="84af9-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="84af9-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span><span class="sxs-lookup"><span data-stu-id="84af9-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![issues reported by the framework analyzer](./media/framework-analyzers-2.png)

<span data-ttu-id="84af9-130">As you write code, you see squiggles underneath any potential issue in your code.</span><span class="sxs-lookup"><span data-stu-id="84af9-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="84af9-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span><span class="sxs-lookup"><span data-stu-id="84af9-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interactive report of issues found by the framework analyzer](./media/framework-analyzers-1.png)

<span data-ttu-id="84af9-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span><span class="sxs-lookup"><span data-stu-id="84af9-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="84af9-134">CA1058: Typy by neměly rozšířit určité základní typy</span><span class="sxs-lookup"><span data-stu-id="84af9-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="84af9-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span><span class="sxs-lookup"><span data-stu-id="84af9-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="84af9-136">**Category:** Design</span><span class="sxs-lookup"><span data-stu-id="84af9-136">**Category:** Design</span></span>

<span data-ttu-id="84af9-137">**Severity:** Warning</span><span class="sxs-lookup"><span data-stu-id="84af9-137">**Severity:** Warning</span></span>

<span data-ttu-id="84af9-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="84af9-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="84af9-139">CA2153: Do not catch corrupted state exceptions</span><span class="sxs-lookup"><span data-stu-id="84af9-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="84af9-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span><span class="sxs-lookup"><span data-stu-id="84af9-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="84af9-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span><span class="sxs-lookup"><span data-stu-id="84af9-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="84af9-142">**Category:** Security</span><span class="sxs-lookup"><span data-stu-id="84af9-142">**Category:** Security</span></span>

<span data-ttu-id="84af9-143">**Severity:** Warning</span><span class="sxs-lookup"><span data-stu-id="84af9-143">**Severity:** Warning</span></span>

<span data-ttu-id="84af9-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="84af9-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="84af9-145">CA2229: Implementovat serializační konstruktory</span><span class="sxs-lookup"><span data-stu-id="84af9-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="84af9-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span><span class="sxs-lookup"><span data-stu-id="84af9-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="84af9-147">Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="84af9-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="84af9-148">Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný.</span><span class="sxs-lookup"><span data-stu-id="84af9-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="84af9-149">The serialization constructor has the following signature:</span><span class="sxs-lookup"><span data-stu-id="84af9-149">The serialization constructor has the following signature:</span></span>

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

<span data-ttu-id="84af9-150">**Category:** Usage</span><span class="sxs-lookup"><span data-stu-id="84af9-150">**Category:** Usage</span></span>

<span data-ttu-id="84af9-151">**Severity:** Warning</span><span class="sxs-lookup"><span data-stu-id="84af9-151">**Severity:** Warning</span></span>

<span data-ttu-id="84af9-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="84af9-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="84af9-153">CA2235: Označte všechna neserializovatelná pole</span><span class="sxs-lookup"><span data-stu-id="84af9-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="84af9-154">Neserializovatelný typ pole instance je deklarován v serializovatelném typu.</span><span class="sxs-lookup"><span data-stu-id="84af9-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="84af9-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span><span class="sxs-lookup"><span data-stu-id="84af9-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="84af9-156">**Category:** Usage</span><span class="sxs-lookup"><span data-stu-id="84af9-156">**Category:** Usage</span></span>

<span data-ttu-id="84af9-157">**Severity:** Warning</span><span class="sxs-lookup"><span data-stu-id="84af9-157">**Severity:** Warning</span></span>

<span data-ttu-id="84af9-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="84af9-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="84af9-159">CA2237: Mark ISerializable types with serializable</span><span class="sxs-lookup"><span data-stu-id="84af9-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="84af9-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span><span class="sxs-lookup"><span data-stu-id="84af9-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="84af9-161">**Category:** Usage</span><span class="sxs-lookup"><span data-stu-id="84af9-161">**Category:** Usage</span></span>

<span data-ttu-id="84af9-162">**Severity:** Warning</span><span class="sxs-lookup"><span data-stu-id="84af9-162">**Severity:** Warning</span></span>

<span data-ttu-id="84af9-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="84af9-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="84af9-164">CA3075: Insecure DTD processing in XML</span><span class="sxs-lookup"><span data-stu-id="84af9-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="84af9-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span><span class="sxs-lookup"><span data-stu-id="84af9-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="84af9-166">**Category:** Security</span><span class="sxs-lookup"><span data-stu-id="84af9-166">**Category:** Security</span></span>

<span data-ttu-id="84af9-167">**Severity:** Warning</span><span class="sxs-lookup"><span data-stu-id="84af9-167">**Severity:** Warning</span></span>

<span data-ttu-id="84af9-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="84af9-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="84af9-169">CA5350: Do not use weak cryptographic algorithms</span><span class="sxs-lookup"><span data-stu-id="84af9-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="84af9-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span><span class="sxs-lookup"><span data-stu-id="84af9-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="84af9-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span><span class="sxs-lookup"><span data-stu-id="84af9-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="84af9-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span><span class="sxs-lookup"><span data-stu-id="84af9-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="84af9-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span><span class="sxs-lookup"><span data-stu-id="84af9-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="84af9-174">**Category:** Security</span><span class="sxs-lookup"><span data-stu-id="84af9-174">**Category:** Security</span></span>

<span data-ttu-id="84af9-175">**Severity:** Warning</span><span class="sxs-lookup"><span data-stu-id="84af9-175">**Severity:** Warning</span></span>

<span data-ttu-id="84af9-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="84af9-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="84af9-177">CA5351: Do not use broken cryptographic algorithms</span><span class="sxs-lookup"><span data-stu-id="84af9-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="84af9-178">An attack making it computationally feasible to break this algorithm exists.</span><span class="sxs-lookup"><span data-stu-id="84af9-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="84af9-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span><span class="sxs-lookup"><span data-stu-id="84af9-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="84af9-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span><span class="sxs-lookup"><span data-stu-id="84af9-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="84af9-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span><span class="sxs-lookup"><span data-stu-id="84af9-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="84af9-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span><span class="sxs-lookup"><span data-stu-id="84af9-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="84af9-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span><span class="sxs-lookup"><span data-stu-id="84af9-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="84af9-184">**Category:** Security</span><span class="sxs-lookup"><span data-stu-id="84af9-184">**Category:** Security</span></span>

<span data-ttu-id="84af9-185">**Severity:** Warning</span><span class="sxs-lookup"><span data-stu-id="84af9-185">**Severity:** Warning</span></span>

<span data-ttu-id="84af9-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span><span class="sxs-lookup"><span data-stu-id="84af9-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span></span>
