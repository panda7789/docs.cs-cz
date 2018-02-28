---
title: "Rozhraní .NET zabezpečení analyzátorů - rozhraní .NET"
description: "Další informace o použití analyzátorů zabezpečení rozhraní .NET v rozhraní .NET Framework analyzátorů balíčku můžete najít a řešit rizika zabezpečení"
keywords: "Rozhraní .NET, .NET core"
author: billwagner
ms.author: billwagner
ms.date: 01/25/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 06a387d72d06609182c8894dd874b241a5d7b69c
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2018
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="6c9b6-104">Nástroje rozhraní .NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="6c9b6-104">The .NET Framework Analyzer</span></span>

<span data-ttu-id="6c9b6-105">Nástroje rozhraní .NET Framework Analyzer můžete najít potenciální problémy v kódu aplikace založené na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-105">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="6c9b6-106">Tento analyzátor vyhledá potenciální problémy a navrhne opravy k nim.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-106">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="6c9b6-107">Nástroje analyzer spuštěn v interaktivním režimu v sadě Visual Studio při psaní kódu nebo jako součást položky konfigurace sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-107">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="6c9b6-108">Měli byste přidat nástroje analyzer do projektu co nejdříve vývoj.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-108">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="6c9b6-109">Tím dříve najít všechny potenciální problémy ve vašem kódu, tím snazší jsou opravit.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-109">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="6c9b6-110">Ale můžete přidat kdykoli v cyklu vývoje.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-110">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="6c9b6-111">Ho vyhledá všechny problémy s stávající kód a upozorňuje o nové problémy jako zachovat vývoj.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-111">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="6c9b6-112">Instalace a konfigurace nástroje Analyzer rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6c9b6-112">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="6c9b6-113">Jako balíčku NuGet, na každém projektu, kam chcete, aby se spouštěly musí být nainstalován analyzátorů zabezpečení rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-113">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="6c9b6-114">Pouze jeden vývojář musí je přidejte do projektu.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-114">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="6c9b6-115">Balíček Analyzátor je závislost projektu a bude spuštěn na počítači každý vývojář, jakmile je aktualizovaný řešení.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-115">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="6c9b6-116">Nástroje rozhraní .NET Framework Analyzer doručuje v [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-116">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="6c9b6-117">Tento balíček poskytuje jenom analyzátorů specifické pro rozhraní .NET Framework, který obsahuje analyzátory zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-117">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="6c9b6-118">Ve většině případů je výhodné [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-118">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="6c9b6-119">Agregační balíček FxCopAnalyzers obsahuje všechny analyzátory framework součástí balíčku Framework.Analyzers, jakož i analyzátorů následující:</span><span class="sxs-lookup"><span data-stu-id="6c9b6-119">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="6c9b6-120">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): poskytuje obecné pokyny a doporučené postupy pro standardní rozhraní API technologie .NET</span><span class="sxs-lookup"><span data-stu-id="6c9b6-120">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="6c9b6-121">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): poskytuje analyzátorů konkrétní k rozhraní API .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-121">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="6c9b6-122">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): poskytuje pokyny pro text zahrnuty jako kód, včetně komentář.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-122">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="6c9b6-123">K její instalaci, klikněte pravým tlačítkem na projekt a vyberte "Závislosti spravovat".</span><span class="sxs-lookup"><span data-stu-id="6c9b6-123">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="6c9b6-124">V Průzkumníku NuGet, vyhledejte "NetFramework Analyzer", nebo pokud dáváte přednost, "Fx Cop Analyzer".</span><span class="sxs-lookup"><span data-stu-id="6c9b6-124">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="6c9b6-125">Nejnovější stabilní verze nainstalujte na všechny projekty v řešení.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-125">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="6c9b6-126">Pomocí Analyzéru rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6c9b6-126">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="6c9b6-127">Po instalaci balíčku NuGet, sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-127">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="6c9b6-128">Analyzátoru oznámí jakýchkoliv problémů, které je možné vyhledat ve vašem základu kódu.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-128">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="6c9b6-129">Tyto problémy jsou hlášeny jako upozornění v okně Seznam chyb Visual Studio, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="6c9b6-129">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problémy hlášené analyzátor framework](./media/framework-analyzers-2.png)

<span data-ttu-id="6c9b6-131">Při psaní kódu zobrazí podtržení vlnovkou pod všechny potenciální problém ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-131">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="6c9b6-132">Najeďte myší na jakýkoli problém a zobrazit podrobnosti o problému a návrhy pro všechny možné opravu, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="6c9b6-132">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interaktivní sestavy problémy nalezené pomocí analyzátoru framework](./media/framework-analyzers-1.png)

<span data-ttu-id="6c9b6-134">Analyzátory Kontrola kódu ve vašem řešení a poskytují seznam upozornění pro některý z těchto problémů:</span><span class="sxs-lookup"><span data-stu-id="6c9b6-134">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="6c9b6-135">CA1058: Typy by neměly rozšířit určité základní typy</span><span class="sxs-lookup"><span data-stu-id="6c9b6-135">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="6c9b6-136">Existuje několik typů v rozhraní .NET Framework, které byste měli není odvozen od přímo.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-136">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="6c9b6-137">**Kategorie:** návrhu</span><span class="sxs-lookup"><span data-stu-id="6c9b6-137">**Category:** Design</span></span>

<span data-ttu-id="6c9b6-138">**Závažnost:** upozornění</span><span class="sxs-lookup"><span data-stu-id="6c9b6-138">**Severity:** Warning</span></span>

<span data-ttu-id="6c9b6-139">Další informace: [CA:1058: typy by neměly rozšířit určité základní typy](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="6c9b6-139">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="6c9b6-140">CA2153: Zachytávat výjimky v poškozeném stavu</span><span class="sxs-lookup"><span data-stu-id="6c9b6-140">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="6c9b6-141">Chyby (například porušení přístupu), což je v nekonzistentním stavu spuštění nebo usnadnit útočník ohrozit systém může masku zachycení výjimky v poškozeném stavu.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-141">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="6c9b6-142">Místo toho catch a popisovač další konkrétní nastavit výjimka typu (typů) nebo znovu vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="6c9b6-142">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="6c9b6-143">**Kategorie:** zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6c9b6-143">**Category:** Security</span></span>

<span data-ttu-id="6c9b6-144">**Závažnost:** upozornění</span><span class="sxs-lookup"><span data-stu-id="6c9b6-144">**Severity:** Warning</span></span>

<span data-ttu-id="6c9b6-145">Další informace: [## CA2153: zachytávat výjimky v poškozeném stavu](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="6c9b6-145">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="6c9b6-146">CA2229: Implementovat serializační konstruktory</span><span class="sxs-lookup"><span data-stu-id="6c9b6-146">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="6c9b6-147">Analyzátoru generuje toto upozornění, když vytvoříte typ, který implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní ale nedefinuje konstruktor požadované serializace.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-147">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="6c9b6-148">Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-148">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="6c9b6-149">Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-149">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="6c9b6-150">Konstruktor serializace má následující podpis:</span><span class="sxs-lookup"><span data-stu-id="6c9b6-150">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="6c9b6-151">**Kategorie:** využití</span><span class="sxs-lookup"><span data-stu-id="6c9b6-151">**Category:** Usage</span></span>

<span data-ttu-id="6c9b6-152">**Závažnost:** upozornění</span><span class="sxs-lookup"><span data-stu-id="6c9b6-152">**Severity:** Warning</span></span>

<span data-ttu-id="6c9b6-153">Další informace: [CA2229: implementovat Serializační konstruktory](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="6c9b6-153">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="6c9b6-154">CA2235: Označte všechna neserializovatelná pole</span><span class="sxs-lookup"><span data-stu-id="6c9b6-154">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="6c9b6-155">Neserializovatelný typ pole instance je deklarován v serializovatelném typu.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-155">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="6c9b6-156">Je třeba explicitně označit toto pole se <xref:System.NonSerializedAttribute> opravit toto upozornění.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-156">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="6c9b6-157">**Kategorie:** využití</span><span class="sxs-lookup"><span data-stu-id="6c9b6-157">**Category:** Usage</span></span>

<span data-ttu-id="6c9b6-158">**Závažnost:** upozornění</span><span class="sxs-lookup"><span data-stu-id="6c9b6-158">**Severity:** Warning</span></span>

<span data-ttu-id="6c9b6-159">Další informace: [CA2235: označte všechna neserializovatelná pole](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="6c9b6-159">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="6c9b6-160">CA2237: Označte typy ISerializable pomocí serializovatelný</span><span class="sxs-lookup"><span data-stu-id="6c9b6-160">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="6c9b6-161">Rozpoznala modul common language runtime jako serializable, musí být označen typy pomocí <xref:System.SerializableAttribute> atribut i v případě, že typ používá vlastní serializace rutiny implementací <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-161">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="6c9b6-162">**Kategorie:** využití</span><span class="sxs-lookup"><span data-stu-id="6c9b6-162">**Category:** Usage</span></span>

<span data-ttu-id="6c9b6-163">**Závažnost:** upozornění</span><span class="sxs-lookup"><span data-stu-id="6c9b6-163">**Severity:** Warning</span></span>

<span data-ttu-id="6c9b6-164">Další informace: [CA2237: typy označit ISerializable pomocí serializovatelný](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="6c9b6-164">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="6c9b6-165">CA3075: Nezabezpečené DTD zpracování v kódu XML</span><span class="sxs-lookup"><span data-stu-id="6c9b6-165">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="6c9b6-166">Pokud používáte nezabezpečené <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instance nebo odkaz na externí entity zdroje, analyzátor může přijímat nedůvěryhodná pro vstup a prozrazeny citlivé informace útočníci.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-166">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="6c9b6-167">**Kategorie:** zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6c9b6-167">**Category:** Security</span></span>

<span data-ttu-id="6c9b6-168">**Závažnost:** upozornění</span><span class="sxs-lookup"><span data-stu-id="6c9b6-168">**Severity:** Warning</span></span>

<span data-ttu-id="6c9b6-169">Další informace: [A3075: nezabezpečené DTD zpracování v kódu XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="6c9b6-169">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="6c9b6-170">CA5350: Nepoužívejte slabé kryptografické algoritmy</span><span class="sxs-lookup"><span data-stu-id="6c9b6-170">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="6c9b6-171">Kryptografické algoritmy snížit časem jako stát pokročilejší útoky.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-171">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="6c9b6-172">V závislosti na typu a použití této kryptografických algoritmů, další snížení jeho síly kryptografického může útočníkovi umožnit, aby číst zprávy typu enciphered, manipulovat s enciphered zprávy, forge digitální podpisy, manipulovat s hash obsahu, nebo v opačném případě ohrozit zabezpečení jakékoli cryptosystem podle tento algoritmus.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-172">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="6c9b6-173">Pro šifrování, použít algoritmus standardu AES (AES 256, AES-192 a AES-128 jsou přijatelná) s délkou klíče větší než nebo rovna hodnotě 128 bitů.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-173">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="6c9b6-174">Pro použití algoritmu hash, použijte funkce algoritmu hash řady SHA-2, jako je například 512 SHA-2, 384 SHA-2 a SHA-2 256.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-174">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="6c9b6-175">**Kategorie:** zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6c9b6-175">**Category:** Security</span></span>

<span data-ttu-id="6c9b6-176">**Závažnost:** upozornění</span><span class="sxs-lookup"><span data-stu-id="6c9b6-176">**Severity:** Warning</span></span>

<span data-ttu-id="6c9b6-177">Další informace: [CA5350: Nepoužívejte slabé kryptografické algoritmy](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="6c9b6-177">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="6c9b6-178">CA5351: Nepoužívejte porušený kryptografické algoritmy</span><span class="sxs-lookup"><span data-stu-id="6c9b6-178">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="6c9b6-179">Útok provedení výpočetně vhodný pro tento algoritmus přerušení existuje.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-179">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="6c9b6-180">To umožňuje útočníkům rozdělit kryptografických záruky, které je určená k poskytnutí.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-180">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="6c9b6-181">V závislosti na typu a použití této kryptografických algoritmů to může útočníkovi umožnit, aby enciphered zprávy číst, manipulovat s enciphered zprávy, forge digitální podpisy, manipulovat s hash obsahu nebo jinak ohrozit zabezpečení jakékoli cryptosystem na základě na tento algoritmus.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-181">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="6c9b6-182">Pro šifrování, použít algoritmus standardu AES (AES 256, AES-192 a AES-128 jsou přijatelná) s délkou klíče větší než nebo rovna hodnotě 128 bitů.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-182">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="6c9b6-183">Pro použití algoritmu hash, použijte funkce algoritmu hash řady SHA-2, jako je například SHA512, SHA384 nebo SHA256.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-183">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="6c9b6-184">Pro digitální podpisy použijte RSA s délkou klíče větší než nebo rovna hodnotě 2048 bitů nebo ECDSA s délkou klíče větší než nebo rovna 256 bitů.</span><span class="sxs-lookup"><span data-stu-id="6c9b6-184">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="6c9b6-185">**Kategorie:** zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6c9b6-185">**Category:** Security</span></span>

<span data-ttu-id="6c9b6-186">**Závažnost:** upozornění</span><span class="sxs-lookup"><span data-stu-id="6c9b6-186">**Severity:** Warning</span></span>

<span data-ttu-id="6c9b6-187">Další informace: [CA5351: Nepoužívejte porušený kryptografické algoritmy](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="6c9b6-187">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>


