---
title: Analyzátory rozhraní .NET Framework - .NET
description: Zjistěte, jak pomocí analyzátorů rozhraní .NET Framework v balíčku analyzátorů rozhraní .NET Framework vyhledat a řešit rizika zabezpečení.
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: dd69671e709549fe0ad0f582e4d09b43f7321df2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155994"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="61ab4-103">Analyzátor rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="61ab4-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="61ab4-104">Analyzátor rozhraní .NET Framework můžete použít k vyhledání potenciálních problémů v kódu aplikace založené na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61ab4-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="61ab4-105">Tento analyzátor vyhledá potenciální problémy a navrhne jejich opravy.</span><span class="sxs-lookup"><span data-stu-id="61ab4-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="61ab4-106">Analyzátor běží interaktivně v sadě Visual Studio při psaní kódu nebo jako součást sestavení CI.</span><span class="sxs-lookup"><span data-stu-id="61ab4-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="61ab4-107">Analyzátor byste měli přidat do projektu co nejdříve ve vašem vývoji.</span><span class="sxs-lookup"><span data-stu-id="61ab4-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="61ab4-108">Čím dříve najdete potenciální problémy ve vašem kódu, tím snadněji se opravují.</span><span class="sxs-lookup"><span data-stu-id="61ab4-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="61ab4-109">Můžete jej však přidat kdykoli ve vývojovém cyklu.</span><span class="sxs-lookup"><span data-stu-id="61ab4-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="61ab4-110">Najde všechny problémy s existující kód a varuje před novými problémy, jak budete pokračovat v rozvoji.</span><span class="sxs-lookup"><span data-stu-id="61ab4-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="61ab4-111">Instalace a konfigurace analyzátoru rozhraní .NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="61ab4-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="61ab4-112">Analyzátory rozhraní .NET Framework musí být nainstalovány jako balíček NuGet v každém projektu, kde je chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="61ab4-112">The .NET Framework Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="61ab4-113">Do projektu je musí přidat pouze jeden vývojář.</span><span class="sxs-lookup"><span data-stu-id="61ab4-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="61ab4-114">Balíček analyzátoru je závislost projektu a bude spuštěn na každém počítači vývojáře, jakmile bude mít aktualizované řešení.</span><span class="sxs-lookup"><span data-stu-id="61ab4-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="61ab4-115">Analyzátor rozhraní .NET Framework je dodáván v balíčku [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet.</span><span class="sxs-lookup"><span data-stu-id="61ab4-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="61ab4-116">Tento balíček obsahuje pouze analyzátory specifické pro rozhraní .NET Framework, který zahrnuje analyzátory zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61ab4-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="61ab4-117">Ve většině případů budete chtít [Balíček NuGet Microsoft.CodeAnalysis.FxCopAnalyzers.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)</span><span class="sxs-lookup"><span data-stu-id="61ab4-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span>
<span data-ttu-id="61ab4-118">Agregační balíček FxCopAnalyzers obsahuje všechny rámcové analyzátory obsažené v balíčku Framework.Analyzers, stejně jako následující analyzátory:</span><span class="sxs-lookup"><span data-stu-id="61ab4-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>

- <span data-ttu-id="61ab4-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Poskytuje obecné pokyny a pokyny pro rozhraní API standardu .NET</span><span class="sxs-lookup"><span data-stu-id="61ab4-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="61ab4-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Poskytuje analyzátory specifické pro rozhraní API .NET Core.</span><span class="sxs-lookup"><span data-stu-id="61ab4-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="61ab4-121">[Text.Analyzátory](https://www.nuget.org/packages/Text.Analyzers): Poskytuje pokyny pro text zahrnutý jako kód, včetně komentářů.</span><span class="sxs-lookup"><span data-stu-id="61ab4-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="61ab4-122">Chcete-li jej nainstalovat, klikněte pravým tlačítkem myši na projekt a vyberte možnost Spravovat závislosti.</span><span class="sxs-lookup"><span data-stu-id="61ab4-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="61ab4-123">Z NuGet explorer, hledat "NetFramework Analyzer", nebo pokud dáváte přednost, "Fx Cop Analyzer".</span><span class="sxs-lookup"><span data-stu-id="61ab4-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="61ab4-124">Nainstalujte nejnovější stabilní verzi ve všech projektech ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="61ab4-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="61ab4-125">Použití analyzátoru rozhraní .NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="61ab4-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="61ab4-126">Po instalaci balíčku NuGet, sestavení řešení.</span><span class="sxs-lookup"><span data-stu-id="61ab4-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="61ab4-127">Analyzátor ohlásí všechny problémy, které najde ve vašem základu kódu.</span><span class="sxs-lookup"><span data-stu-id="61ab4-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="61ab4-128">Problémy jsou hlášeny jako upozornění v okně Seznam chyb sady Visual Studio, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="61ab4-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problémy hlášené rámcovým analyzátorem](./media/framework-analyzers-2.png)

<span data-ttu-id="61ab4-130">Při psaní kódu, vidíte vlnovky pod jakýkoli potenciální problém v kódu.</span><span class="sxs-lookup"><span data-stu-id="61ab4-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="61ab4-131">Najeďte na libovolný problém a zobrazí se podrobnosti o problému a návrhy na možnou opravu, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="61ab4-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interaktivní zpráva o problémech zjištěných rámcovým analyzátorem](./media/framework-analyzers-1.png)

<span data-ttu-id="61ab4-133">Analyzátory zkontroluje kód ve vašem řešení a poskytují vám seznam upozornění pro všechny z těchto problémů:</span><span class="sxs-lookup"><span data-stu-id="61ab4-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="61ab4-134">CA1058: Typy by neměly rozšířit určité základní typy</span><span class="sxs-lookup"><span data-stu-id="61ab4-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="61ab4-135">Existuje malý počet typů v rozhraní .NET Framework, které byste neměli odvodit přímo.</span><span class="sxs-lookup"><span data-stu-id="61ab4-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span>

<span data-ttu-id="61ab4-136">**Kategorie:** Design</span><span class="sxs-lookup"><span data-stu-id="61ab4-136">**Category:** Design</span></span>

<span data-ttu-id="61ab4-137">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="61ab4-137">**Severity:** Warning</span></span>

<span data-ttu-id="61ab4-138">Další informace: [CA:1058: Typy by neměly rozšiřovat určité základní typy.](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="61ab4-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="61ab4-139">CA2153: Nezachytit výjimky poškozeného stavu</span><span class="sxs-lookup"><span data-stu-id="61ab4-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="61ab4-140">Zachycení výjimky poškozeného stavu může maskovat chyby (například narušení přístupu), což má za následek nekonzistentní stav spuštění nebo usnadňuje útočníkům ohrožení systému.</span><span class="sxs-lookup"><span data-stu-id="61ab4-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="61ab4-141">Místo toho zachyťte a zpracovat konkrétnější sadu typů výjimek nebo znovu vyvolat výjimku</span><span class="sxs-lookup"><span data-stu-id="61ab4-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="61ab4-142">**Kategorie:** Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="61ab4-142">**Category:** Security</span></span>

<span data-ttu-id="61ab4-143">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="61ab4-143">**Severity:** Warning</span></span>

<span data-ttu-id="61ab4-144">Další informace: [## CA2153: Nezachytát výjimky poškozeného stavu](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="61ab4-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="61ab4-145">CA2229: Implementovat serializační konstruktory</span><span class="sxs-lookup"><span data-stu-id="61ab4-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="61ab4-146">Analyzátor generuje toto upozornění při vytváření typu, <xref:System.Runtime.Serialization.ISerializable> který implementuje rozhraní, ale nedefinuje požadovaný konstruktor serializace.</span><span class="sxs-lookup"><span data-stu-id="61ab4-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="61ab4-147">Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="61ab4-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="61ab4-148">Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný.</span><span class="sxs-lookup"><span data-stu-id="61ab4-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="61ab4-149">Konstruktor serializace má následující podpis:</span><span class="sxs-lookup"><span data-stu-id="61ab4-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="61ab4-150">**Kategorie:** Použití</span><span class="sxs-lookup"><span data-stu-id="61ab4-150">**Category:** Usage</span></span>

<span data-ttu-id="61ab4-151">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="61ab4-151">**Severity:** Warning</span></span>

<span data-ttu-id="61ab4-152">Další informace: [CA2229: Implementace konstruktorů serializace](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="61ab4-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="61ab4-153">CA2235: Označte všechna neserializovatelná pole</span><span class="sxs-lookup"><span data-stu-id="61ab4-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="61ab4-154">Neserializovatelný typ pole instance je deklarován v serializovatelném typu.</span><span class="sxs-lookup"><span data-stu-id="61ab4-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="61ab4-155">Chcete-li toto upozornění <xref:System.NonSerializedAttribute> opravit, je nutné toto pole explicitně označit.</span><span class="sxs-lookup"><span data-stu-id="61ab4-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="61ab4-156">**Kategorie:** Použití</span><span class="sxs-lookup"><span data-stu-id="61ab4-156">**Category:** Usage</span></span>

<span data-ttu-id="61ab4-157">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="61ab4-157">**Severity:** Warning</span></span>

<span data-ttu-id="61ab4-158">Další informace: [CA2235: Označení všech neserializovatelných polí](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="61ab4-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="61ab4-159">CA2237: Označit iSerializable typy s serializovatelné</span><span class="sxs-lookup"><span data-stu-id="61ab4-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="61ab4-160">Chcete-li být rozpoznán modulu runtime společného jazyka jako <xref:System.SerializableAttribute> serializovatelný, musí být typy označeny pomocí <xref:System.Runtime.Serialization.ISerializable> atributu i v případě, že typ používá vlastní serializační rutinu implementací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="61ab4-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="61ab4-161">**Kategorie:** Použití</span><span class="sxs-lookup"><span data-stu-id="61ab4-161">**Category:** Usage</span></span>

<span data-ttu-id="61ab4-162">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="61ab4-162">**Severity:** Warning</span></span>

<span data-ttu-id="61ab4-163">Další informace: [CA2237: Označit iSerializable typy s serializovatelný](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="61ab4-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="61ab4-164">CA3075: Nezabezpečené zpracování DTD v XML</span><span class="sxs-lookup"><span data-stu-id="61ab4-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="61ab4-165">Pokud použijete <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> nezabezpečené instance nebo odkazujete na zdroje externích entit, analyzátor může přijmout nedůvěryhodný vstup a zpřístupnit citlivé informace útočníkům.</span><span class="sxs-lookup"><span data-stu-id="61ab4-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="61ab4-166">**Kategorie:** Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="61ab4-166">**Category:** Security</span></span>

<span data-ttu-id="61ab4-167">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="61ab4-167">**Severity:** Warning</span></span>

<span data-ttu-id="61ab4-168">Další informace: [A3075: Nezabezpečené zpracování DTD v XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="61ab4-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="61ab4-169">CA5350: Nepoužívejte slabé kryptografické algoritmy</span><span class="sxs-lookup"><span data-stu-id="61ab4-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="61ab4-170">Kryptografické algoritmy se časem znehodnocují s tím, jak se útoky stávají pokročilejšími.</span><span class="sxs-lookup"><span data-stu-id="61ab4-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="61ab4-171">V závislosti na typu a použití tohoto kryptografického algoritmu může další degradace jeho kryptografické síly umožnit útočníkům číst šifrované zprávy, manipulovat se šifrovanými zprávami, falšovat digitální podpisy, manipulovat s obsahem hash nebo jinak ohrozit jakýkoli kryptosystém založený na tomto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="61ab4-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="61ab4-172">Pro šifrování použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelné) s délkou klíče větší nebo rovnou 128 bitům.</span><span class="sxs-lookup"><span data-stu-id="61ab4-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="61ab4-173">Pro zahasování použijte funkci hash v rodině SHA-2, například SHA-2 512, SHA-2 384 nebo SHA-2 256.</span><span class="sxs-lookup"><span data-stu-id="61ab4-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="61ab4-174">**Kategorie:** Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="61ab4-174">**Category:** Security</span></span>

<span data-ttu-id="61ab4-175">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="61ab4-175">**Severity:** Warning</span></span>

<span data-ttu-id="61ab4-176">Další informace: [CA5350: Nepoužívejte slabé kryptografické algoritmy](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="61ab4-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="61ab4-177">CA5351: Nepoužívejte nefunkční kryptografické algoritmy</span><span class="sxs-lookup"><span data-stu-id="61ab4-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="61ab4-178">Existuje útok, který je technicky proveditelný k přerušení tohoto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="61ab4-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="61ab4-179">To umožňuje útočníkům přerušit kryptografické záruky, které je určen k poskytování.</span><span class="sxs-lookup"><span data-stu-id="61ab4-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="61ab4-180">V závislosti na typu a použití tohoto kryptografického algoritmu to může útočníkům umožnit číst šifrované zprávy, manipulovat s šifrovanými zprávami, falšovat digitální podpisy, manipulovat s obsahem hash nebo jinak ohrozit jakýkoli kryptosystém založený na tomto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="61ab4-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="61ab4-181">Pro šifrování použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelné) s délkou klíče větší nebo rovnou 128 bitům.</span><span class="sxs-lookup"><span data-stu-id="61ab4-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="61ab4-182">Pro zahasování použijte funkci hash v rodině SHA-2, například SHA512, SHA384 nebo SHA256.</span><span class="sxs-lookup"><span data-stu-id="61ab4-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="61ab4-183">Pro digitální podpisy použijte RSA s délkou klíče větší nebo rovnou 2048 bitům nebo ECDSA s délkou klíče větší nebo rovnou 256 bitům.</span><span class="sxs-lookup"><span data-stu-id="61ab4-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="61ab4-184">**Kategorie:** Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="61ab4-184">**Category:** Security</span></span>

<span data-ttu-id="61ab4-185">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="61ab4-185">**Severity:** Warning</span></span>

<span data-ttu-id="61ab4-186">Další informace: [CA5351: Nepoužívejte nefunkční kryptografické algoritmy](/visualstudio/code-quality/ca5351)</span><span class="sxs-lookup"><span data-stu-id="61ab4-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span></span>
