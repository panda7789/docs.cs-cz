---
title: Analyzátory .NET Framework – .NET
description: Naučte se používat analyzátory .NET Framework v balíčku .NET Framework Analyzer k hledání a adresování rizik zabezpečení.
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
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="242e6-103">Analyzátor .NET Framework</span><span class="sxs-lookup"><span data-stu-id="242e6-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="242e6-104">K nalezení potenciálních problémů v kódu aplikace založeném na .NET Framework můžete použít analyzátor .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="242e6-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="242e6-105">Tento analyzátor vyhledá možné problémy a navrhne jejich opravy.</span><span class="sxs-lookup"><span data-stu-id="242e6-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="242e6-106">Analyzátor se spustí interaktivně v aplikaci Visual Studio při psaní kódu nebo jako součást sestavení CI.</span><span class="sxs-lookup"><span data-stu-id="242e6-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="242e6-107">Analyzátor byste měli přidat do projektu co nejdříve ve vašem vývoji.</span><span class="sxs-lookup"><span data-stu-id="242e6-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="242e6-108">Dříve najdete případné problémy v kódu, což je snazší opravit.</span><span class="sxs-lookup"><span data-stu-id="242e6-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="242e6-109">Můžete ho ale kdykoli přidat do vývojového cyklu.</span><span class="sxs-lookup"><span data-stu-id="242e6-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="242e6-110">Vyhledá všechny problémy s existujícím kódem a upozorní na nové problémy při vývoji.</span><span class="sxs-lookup"><span data-stu-id="242e6-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="242e6-111">Instalace a konfigurace analyzátoru .NET Framework</span><span class="sxs-lookup"><span data-stu-id="242e6-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="242e6-112">Analyzátory .NET Framework musí být nainstalovány jako balíček NuGet v každém projektu, kde je chcete spouštět.</span><span class="sxs-lookup"><span data-stu-id="242e6-112">The .NET Framework Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="242e6-113">Pouze jeden vývojář potřebuje přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="242e6-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="242e6-114">Balíček analyzátoru je závislý na projektu a spustí se na každém počítači vývojáře, jakmile bude mít aktualizované řešení.</span><span class="sxs-lookup"><span data-stu-id="242e6-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="242e6-115">Analyzátor .NET Framework je dodán v balíčku NuGet [Microsoft. NETFramework. analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) .</span><span class="sxs-lookup"><span data-stu-id="242e6-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="242e6-116">Tento balíček poskytuje jenom analyzátory, které jsou specifické pro .NET Framework, které zahrnují analyzátory zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="242e6-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="242e6-117">Ve většině případů budete chtít balíček NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .</span><span class="sxs-lookup"><span data-stu-id="242e6-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="242e6-118">FxCopAnalyzers agregovaný balíček obsahuje všechny analyzátory rozhraní, které jsou součástí balíčku Framework. Analyzers a také následující analyzátory:</span><span class="sxs-lookup"><span data-stu-id="242e6-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>

- <span data-ttu-id="242e6-119">[Microsoft. CodeQuality. analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): poskytuje obecné pokyny a pokyny pro rozhraní api pro .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="242e6-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="242e6-120">[Microsoft. Netcore. analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): poskytuje analyzátory specifické pro rozhraní API .NET Core.</span><span class="sxs-lookup"><span data-stu-id="242e6-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="242e6-121">[Text. analyzers](https://www.nuget.org/packages/Text.Analyzers): poskytuje pokyny pro text zahrnutý jako kód včetně komentářů.</span><span class="sxs-lookup"><span data-stu-id="242e6-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="242e6-122">Pokud ho chcete nainstalovat, klikněte pravým tlačítkem na projekt a vyberte spravovat závislosti.</span><span class="sxs-lookup"><span data-stu-id="242e6-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="242e6-123">V Průzkumníku NuGet vyhledejte "NetFramework Analyzer", nebo pokud dáváte přednost, "FX VPP Analyzer".</span><span class="sxs-lookup"><span data-stu-id="242e6-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="242e6-124">Nainstalujte nejnovější stabilní verzi do všech projektů ve vašem řešení.</span><span class="sxs-lookup"><span data-stu-id="242e6-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="242e6-125">Použití analyzátoru .NET Framework</span><span class="sxs-lookup"><span data-stu-id="242e6-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="242e6-126">Po instalaci balíčku NuGet si sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="242e6-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="242e6-127">Analyzátor ohlásí všechny problémy, které najde ve vašem základu kódu.</span><span class="sxs-lookup"><span data-stu-id="242e6-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="242e6-128">Problémy jsou hlášeny jako upozornění v okně Visual Studio Seznam chyb, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="242e6-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problémy hlášené analyzátorem rozhraní Framework](./media/framework-analyzers-2.png)

<span data-ttu-id="242e6-130">Při psaní kódu se zobrazí vlnovky pod jakýmkoli potenciálním problémem v kódu.</span><span class="sxs-lookup"><span data-stu-id="242e6-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="242e6-131">Najeďte myší na libovolný problém a zobrazí se podrobnosti o problému a návrhy na případné opravy, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="242e6-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interaktivní sestava problémů zjištěných analyzátorem rozhraní](./media/framework-analyzers-1.png)

<span data-ttu-id="242e6-133">Analyzátory prozkoumají kód ve vašem řešení a poskytnou vám seznam upozornění pro některý z těchto problémů:</span><span class="sxs-lookup"><span data-stu-id="242e6-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="242e6-134">CA1058: Typy by neměly rozšířit určité základní typy</span><span class="sxs-lookup"><span data-stu-id="242e6-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="242e6-135">V .NET Framework existuje malý počet typů, které byste neměli odvozovat přímo.</span><span class="sxs-lookup"><span data-stu-id="242e6-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="242e6-136">**Kategorie:** Vytvořit</span><span class="sxs-lookup"><span data-stu-id="242e6-136">**Category:** Design</span></span>

<span data-ttu-id="242e6-137">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="242e6-137">**Severity:** Warning</span></span>

<span data-ttu-id="242e6-138">Další informace: [certifikační autorita: 1058: typy by neměly rozkrývat určité základní typy](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="242e6-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="242e6-139">CA2153: nezachytit poškozené výjimky stavu</span><span class="sxs-lookup"><span data-stu-id="242e6-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="242e6-140">Výsledkem zachycení poškozených výjimek stavu mohou být chyby maskování (například porušení přístupu), což vede k nekonzistentnímu stavu provádění nebo je snazší útočníkům napadnout systém.</span><span class="sxs-lookup"><span data-stu-id="242e6-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="242e6-141">Místo toho Zachyťte a zpracujte konkrétnější sadu typů výjimek nebo znovu vyvolejte výjimku.</span><span class="sxs-lookup"><span data-stu-id="242e6-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="242e6-142">**Kategorie:** Bezpečnost</span><span class="sxs-lookup"><span data-stu-id="242e6-142">**Category:** Security</span></span>

<span data-ttu-id="242e6-143">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="242e6-143">**Severity:** Warning</span></span>

<span data-ttu-id="242e6-144">Další informace: [# # CA2153: nezachytit poškozené výjimky stavu](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="242e6-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="242e6-145">CA2229: Implementovat serializační konstruktory</span><span class="sxs-lookup"><span data-stu-id="242e6-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="242e6-146">Analyzátor vygeneruje toto upozornění, když vytvoříte typ, který implementuje rozhraní <xref:System.Runtime.Serialization.ISerializable>, ale nedefinuje požadovaný konstruktor serializace.</span><span class="sxs-lookup"><span data-stu-id="242e6-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="242e6-147">Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="242e6-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="242e6-148">Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný.</span><span class="sxs-lookup"><span data-stu-id="242e6-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="242e6-149">Konstruktor serializace má následující signaturu:</span><span class="sxs-lookup"><span data-stu-id="242e6-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="242e6-150">**Kategorie:** Využívání</span><span class="sxs-lookup"><span data-stu-id="242e6-150">**Category:** Usage</span></span>

<span data-ttu-id="242e6-151">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="242e6-151">**Severity:** Warning</span></span>

<span data-ttu-id="242e6-152">Další informace: [CA2229: implementace serializacch konstruktorů](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="242e6-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="242e6-153">CA2235: Označte všechna neserializovatelná pole</span><span class="sxs-lookup"><span data-stu-id="242e6-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="242e6-154">Neserializovatelný typ pole instance je deklarován v serializovatelném typu.</span><span class="sxs-lookup"><span data-stu-id="242e6-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="242e6-155">Chcete-li toto upozornění vyřešit, musíte toto pole explicitně označit <xref:System.NonSerializedAttribute>.</span><span class="sxs-lookup"><span data-stu-id="242e6-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="242e6-156">**Kategorie:** Využívání</span><span class="sxs-lookup"><span data-stu-id="242e6-156">**Category:** Usage</span></span>

<span data-ttu-id="242e6-157">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="242e6-157">**Severity:** Warning</span></span>

<span data-ttu-id="242e6-158">Další informace: [CA2235: Označte všechna Neserializovatelný pole](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="242e6-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="242e6-159">CA2237: Označte typy ISerializable pomocí serializovatelných</span><span class="sxs-lookup"><span data-stu-id="242e6-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="242e6-160">Aby je bylo možné rozpoznat modulem CLR (Common Language Runtime) jako serializovatelný, musí být typy označeny pomocí atributu <xref:System.SerializableAttribute>, i když typ používá vlastní rutinu serializace implementací rozhraní <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="242e6-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="242e6-161">**Kategorie:** Využívání</span><span class="sxs-lookup"><span data-stu-id="242e6-161">**Category:** Usage</span></span>

<span data-ttu-id="242e6-162">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="242e6-162">**Severity:** Warning</span></span>

<span data-ttu-id="242e6-163">Další informace: [CA2237: Označte typy ISerializable s serializovatelným](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="242e6-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="242e6-164">CA3075: nezabezpečené zpracování DTD v XML</span><span class="sxs-lookup"><span data-stu-id="242e6-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="242e6-165">Pokud používáte nezabezpečené <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instance nebo odkazujete na zdroje externích entit, může analyzátor přijmout nedůvěryhodné vstupní a únik citlivých informací útočníkům.</span><span class="sxs-lookup"><span data-stu-id="242e6-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="242e6-166">**Kategorie:** Bezpečnost</span><span class="sxs-lookup"><span data-stu-id="242e6-166">**Category:** Security</span></span>

<span data-ttu-id="242e6-167">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="242e6-167">**Severity:** Warning</span></span>

<span data-ttu-id="242e6-168">Další informace: [A3075: nezabezpečené zpracování DTD v XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="242e6-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="242e6-169">CA5350: Nepoužívejte slabé kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="242e6-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="242e6-170">Kryptografické algoritmy se v průběhu času degradují, jakmile se útoky stanou pokročilejší.</span><span class="sxs-lookup"><span data-stu-id="242e6-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="242e6-171">V závislosti na typu a aplikaci tohoto kryptografického algoritmu může další degradace jeho kryptografické síly umožnit útočníkům číst enciphered zprávy, manipulovat s enciphered, zfalšovat digitální podpisy, manipulovat s obsahem s hashy nebo v opačném případě ohrožení všech cryptosystem na základě tohoto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="242e6-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="242e6-172">Pro šifrování použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelné) s délkou klíče větší nebo rovnou 128 bitů.</span><span class="sxs-lookup"><span data-stu-id="242e6-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="242e6-173">V případě hashování použijte funkci hash v rodině SHA-2, například SHA-2 512, SHA-2 384 nebo SHA-2 256.</span><span class="sxs-lookup"><span data-stu-id="242e6-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="242e6-174">**Kategorie:** Bezpečnost</span><span class="sxs-lookup"><span data-stu-id="242e6-174">**Category:** Security</span></span>

<span data-ttu-id="242e6-175">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="242e6-175">**Severity:** Warning</span></span>

<span data-ttu-id="242e6-176">Další informace: [CA5350: Nepoužívejte slabé kryptografické algoritmy](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms) .</span><span class="sxs-lookup"><span data-stu-id="242e6-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="242e6-177">CA5351: Nepoužívejte nefunkční kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="242e6-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="242e6-178">Útok, který provádí výpočetně vhodným důvodem pro přerušení tohoto algoritmu, existuje.</span><span class="sxs-lookup"><span data-stu-id="242e6-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="242e6-179">To umožňuje útočníkům přerušit kryptografické záruky, které je navržena pro poskytování.</span><span class="sxs-lookup"><span data-stu-id="242e6-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="242e6-180">V závislosti na typu a aplikaci tohoto kryptografického algoritmu může útočníkům umožnit čtení zpráv enciphered, manipulace s enciphered zprávami, zfalšovat digitálních podpisů, manipulace s hash obsahem nebo jiné ohrožení zabezpečení založeného na cryptosystem. u tohoto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="242e6-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="242e6-181">Pro šifrování použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelné) s délkou klíče větší nebo rovnou 128 bitů.</span><span class="sxs-lookup"><span data-stu-id="242e6-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="242e6-182">V případě hashování použijte funkci hash, která je v rodině SHA-2, například SHA512, SHA384 nebo SHA256.</span><span class="sxs-lookup"><span data-stu-id="242e6-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="242e6-183">U digitálních podpisů použijte RSA s délkou klíče větší nebo rovnou 2048 bitů nebo ECDSA s délkou klíče větší nebo rovnou 256 bitů.</span><span class="sxs-lookup"><span data-stu-id="242e6-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="242e6-184">**Kategorie:** Bezpečnost</span><span class="sxs-lookup"><span data-stu-id="242e6-184">**Category:** Security</span></span>

<span data-ttu-id="242e6-185">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="242e6-185">**Severity:** Warning</span></span>

<span data-ttu-id="242e6-186">Další informace: [CA5351: Nepoužívejte nefunkční kryptografické algoritmy](/visualstudio/code-quality/ca5351) .</span><span class="sxs-lookup"><span data-stu-id="242e6-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span></span>
