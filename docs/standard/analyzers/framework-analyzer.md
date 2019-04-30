---
title: Analýzu zabezpečení pro .NET – .NET
description: Další informace o použití analyzátory .NET zabezpečení v rozhraní .NET Framework analyzátory balíčku k vyhledávání a řešení bezpečnostních rizik
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: cbd9bcdb12a423f54aa4ff82d88f07c20023c48f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947295"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="3ad79-103">Analyzátor rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ad79-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="3ad79-104">Analyzátor rozhraní .NET Framework můžete použít k vyhledání potenciálních problémů v kódu aplikace založené na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ad79-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="3ad79-105">Tento analyzátor vyhledá potenciální problémy a navrhne opravy na ně.</span><span class="sxs-lookup"><span data-stu-id="3ad79-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="3ad79-106">Analyzátor spuštěn v interaktivním režimu v sadě Visual Studio vám při psaní kódu nebo jako součást sestavení CI.</span><span class="sxs-lookup"><span data-stu-id="3ad79-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="3ad79-107">Měli byste přidat analyzátor do svého projektu co nejdříve při vývoji.</span><span class="sxs-lookup"><span data-stu-id="3ad79-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="3ad79-108">Rychleji najít všechny potenciální problémy v kódu, tím snazší opravit.</span><span class="sxs-lookup"><span data-stu-id="3ad79-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="3ad79-109">Ale můžete přidat kdykoli v cyklu vývoje.</span><span class="sxs-lookup"><span data-stu-id="3ad79-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="3ad79-110">Vyhledá všechny problémy s existující kód a upozorní o nových problémech, jak zachovat vývoj.</span><span class="sxs-lookup"><span data-stu-id="3ad79-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="3ad79-111">Instalace a konfigurace analyzátor rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ad79-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="3ad79-112">Analyzátory .NET zabezpečení musí být nainstalován jako balíček NuGet na každý projekt, kam chcete, aby běžela.</span><span class="sxs-lookup"><span data-stu-id="3ad79-112">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="3ad79-113">Pouze jeden vývojář je potřeba je přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="3ad79-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="3ad79-114">Balíček analyzátoru, představuje závislost projektu a bude spuštěn na počítači každý vývojář, jakmile má aktualizované řešení.</span><span class="sxs-lookup"><span data-stu-id="3ad79-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="3ad79-115">Analyzátor rozhraní .NET Framework se doručí do [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3ad79-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="3ad79-116">Tento balíček poskytuje pouze analyzátory specifické pro rozhraní .NET Framework, která zahrnuje analýzu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3ad79-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="3ad79-117">Ve většině případů je vhodné [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3ad79-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="3ad79-118">FxCopAnalyzers agregační balíček obsahuje všechny analyzátory framework součástí balíčku Framework.Analyzers, jakož i analyzátory následující:</span><span class="sxs-lookup"><span data-stu-id="3ad79-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="3ad79-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Obsahuje obecné pokyny a doprovodné materiály k rozhraní API pro .NET Standard</span><span class="sxs-lookup"><span data-stu-id="3ad79-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="3ad79-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Poskytuje analyzátory konkrétní rozhraní API pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ad79-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="3ad79-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Obsahuje pokyny pro text součástí kódu, včetně komentářů.</span><span class="sxs-lookup"><span data-stu-id="3ad79-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="3ad79-122">K jeho instalaci, klikněte pravým tlačítkem na projekt a vyberte "Spravovat závislosti".</span><span class="sxs-lookup"><span data-stu-id="3ad79-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="3ad79-123">Z Průzkumníka NuGet, vyhledejte "NetFramework analyzátor", nebo pokud dáváte přednost, "Fx Cop analyzátor".</span><span class="sxs-lookup"><span data-stu-id="3ad79-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="3ad79-124">Nainstalujte nejnovější stabilní verze ve všech projektech v řešení.</span><span class="sxs-lookup"><span data-stu-id="3ad79-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="3ad79-125">Pomocí Analyzéru rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ad79-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="3ad79-126">Po instalaci balíčku NuGet, sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="3ad79-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="3ad79-127">Analyzátor ohlásí problémů, na které je možné vyhledat ve vašem základu kódu.</span><span class="sxs-lookup"><span data-stu-id="3ad79-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="3ad79-128">Problémy označené jako upozornění v okně Seznam chyb Visual Studio, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="3ad79-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problémech ohlášených analyzátor architektury](./media/framework-analyzers-2.png)

<span data-ttu-id="3ad79-130">Při psaní kódu, uvidíte podtržení vlnovkou pod případné potíže v kódu.</span><span class="sxs-lookup"><span data-stu-id="3ad79-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="3ad79-131">Najeďte myší jakýkoli problém a zobrazit podrobnosti o problému a návrhy pro všechny možné opravu, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="3ad79-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interaktivní sestavy problémů zjištěných aplikací analyzátor architektury](./media/framework-analyzers-1.png)

<span data-ttu-id="3ad79-133">Analyzátory prozkoumat kód v rámci vašeho řešení a poskytneme vám seznam upozornění pro některý z těchto problémů:</span><span class="sxs-lookup"><span data-stu-id="3ad79-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="3ad79-134">CA1058: Typy by neměly rozšiřovat určité základní typy</span><span class="sxs-lookup"><span data-stu-id="3ad79-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="3ad79-135">Existuje několik malých typů v rozhraní .NET Framework, které byste měli není odvozeno od přímo.</span><span class="sxs-lookup"><span data-stu-id="3ad79-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="3ad79-136">**Kategorie:** Návrh</span><span class="sxs-lookup"><span data-stu-id="3ad79-136">**Category:** Design</span></span>

<span data-ttu-id="3ad79-137">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="3ad79-137">**Severity:** Warning</span></span>

<span data-ttu-id="3ad79-138">Další informace: [CA:1058: Typy by neměly rozšířit určité základní typy](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="3ad79-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="3ad79-139">CA2153: Nezachycujte výjimky v poškozeném stavu</span><span class="sxs-lookup"><span data-stu-id="3ad79-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="3ad79-140">Chyby (například porušení přístupu), což vede k nekonzistentnímu stavu spuštění nebo snadnější útočník napadnout počítač může maskovat zachycení výjimek v poškozeném stavu.</span><span class="sxs-lookup"><span data-stu-id="3ad79-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="3ad79-141">Místo toho catch a popisovač další konkrétní sadu výjimek typy nebo opětovné vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="3ad79-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="3ad79-142">**Kategorie:** Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3ad79-142">**Category:** Security</span></span>

<span data-ttu-id="3ad79-143">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="3ad79-143">**Severity:** Warning</span></span>

<span data-ttu-id="3ad79-144">Další informace: [## CA2153: Nezachycujte výjimky v poškozeném stavu](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="3ad79-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="3ad79-145">CA2229: Implementujte serializační konstruktory</span><span class="sxs-lookup"><span data-stu-id="3ad79-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="3ad79-146">Analyzátor generuje toto upozornění, když vytvoříte typ, který implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, ale vyžaduje Serializační konstruktor není definován.</span><span class="sxs-lookup"><span data-stu-id="3ad79-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="3ad79-147">Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="3ad79-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="3ad79-148">Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný.</span><span class="sxs-lookup"><span data-stu-id="3ad79-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="3ad79-149">Serializační konstruktor má následující podpis:</span><span class="sxs-lookup"><span data-stu-id="3ad79-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="3ad79-150">**Kategorie:** Použití</span><span class="sxs-lookup"><span data-stu-id="3ad79-150">**Category:** Usage</span></span>

<span data-ttu-id="3ad79-151">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="3ad79-151">**Severity:** Warning</span></span>

<span data-ttu-id="3ad79-152">Další informace: [CA2229: Implementovat Serializační konstruktory](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="3ad79-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="3ad79-153">CA2235: Označte všechna neserializovatelná pole</span><span class="sxs-lookup"><span data-stu-id="3ad79-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="3ad79-154">Neserializovatelný typ pole instance je deklarován v serializovatelném typu.</span><span class="sxs-lookup"><span data-stu-id="3ad79-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="3ad79-155">Je třeba explicitně označit toto pole se <xref:System.NonSerializedAttribute> opravit toto upozornění.</span><span class="sxs-lookup"><span data-stu-id="3ad79-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="3ad79-156">**Kategorie:** Použití</span><span class="sxs-lookup"><span data-stu-id="3ad79-156">**Category:** Usage</span></span>

<span data-ttu-id="3ad79-157">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="3ad79-157">**Severity:** Warning</span></span>

<span data-ttu-id="3ad79-158">Další informace: [CA2235: Označte všechna neserializovatelná pole](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="3ad79-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="3ad79-159">CA2237: Označte typy ISerializable pomocí serializovatelného</span><span class="sxs-lookup"><span data-stu-id="3ad79-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="3ad79-160">Chcete-li rozpoznán modulem common language runtime jako serializovatelný, musí být označen pomocí <xref:System.SerializableAttribute> atribut i v případě, že se typ používá vlastní rutinu serializace prostřednictvím implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3ad79-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="3ad79-161">**Kategorie:** Použití</span><span class="sxs-lookup"><span data-stu-id="3ad79-161">**Category:** Usage</span></span>

<span data-ttu-id="3ad79-162">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="3ad79-162">**Severity:** Warning</span></span>

<span data-ttu-id="3ad79-163">Další informace: [CA2237: Označte typy ISerializable pomocí serializovatelného](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="3ad79-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="3ad79-164">CA3075: Nezabezpečené specifikace DTD zpracování ve formátu XML</span><span class="sxs-lookup"><span data-stu-id="3ad79-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="3ad79-165">Pokud používáte nezabezpečené <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instance nebo odkaz na externí entity zdroje, analyzátor může přijmout nedůvěryhodné vstupní tak zveřejnit citlivé informace, které útočníci.</span><span class="sxs-lookup"><span data-stu-id="3ad79-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="3ad79-166">**Kategorie:** Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3ad79-166">**Category:** Security</span></span>

<span data-ttu-id="3ad79-167">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="3ad79-167">**Severity:** Warning</span></span>

<span data-ttu-id="3ad79-168">Další informace: [A3075: Nezabezpečené specifikace DTD zpracování ve formátu XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="3ad79-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="3ad79-169">CA5350: Nepoužívejte slabé kryptografické algoritmy</span><span class="sxs-lookup"><span data-stu-id="3ad79-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="3ad79-170">Postupem času degradovat kryptografické algoritmy, budou další pokročilé útoky.</span><span class="sxs-lookup"><span data-stu-id="3ad79-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="3ad79-171">V závislosti na typu a použití tohoto kryptografický algoritmus dále snížení jeho kryptografická můžou útočníkům umožnit, aby číst enciphered zprávy, manipulovat s enciphered zprávy, forge digitální podpisy, manipulovat s hodnotu hash obsahu, nebo v opačném případě ohrozit zabezpečení jakékoli cryptosystem podle algoritmu.</span><span class="sxs-lookup"><span data-stu-id="3ad79-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="3ad79-172">Pro šifrování, použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelná) s délkou klíče větší než nebo rovna hodnotě 128 bitů.</span><span class="sxs-lookup"><span data-stu-id="3ad79-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="3ad79-173">Pro vytvoření hodnoty hash, pomocí funkce algoritmu hash řady SHA-2, jako je 512 SHA-2, SHA-2 384 nebo 256 SHA-2.</span><span class="sxs-lookup"><span data-stu-id="3ad79-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="3ad79-174">**Kategorie:** Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3ad79-174">**Category:** Security</span></span>

<span data-ttu-id="3ad79-175">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="3ad79-175">**Severity:** Warning</span></span>

<span data-ttu-id="3ad79-176">Další informace: [CA5350: Nepoužívejte slabé kryptografické algoritmy](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="3ad79-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="3ad79-177">CA5351: Nepoužívejte poškozené kryptografické algoritmy</span><span class="sxs-lookup"><span data-stu-id="3ad79-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="3ad79-178">Díky tomu výpočetně přerušení tento algoritmus útoku existuje.</span><span class="sxs-lookup"><span data-stu-id="3ad79-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="3ad79-179">To útočníkům umožňuje rozdělit kryptografických záruky, které je navržené pro poskytování.</span><span class="sxs-lookup"><span data-stu-id="3ad79-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="3ad79-180">V závislosti na typu a použití tohoto kryptografických algoritmů to můžou útočníkům umožnit, aby číst enciphered zprávy, manipulovat s enciphered zprávy, forge digitální podpisy, manipulovat s hodnotu hash obsahu nebo jinak ohrozit zabezpečení jakékoli cryptosystem na základě na tento algoritmus.</span><span class="sxs-lookup"><span data-stu-id="3ad79-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="3ad79-181">Pro šifrování, použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelná) s délkou klíče větší než nebo rovna hodnotě 128 bitů.</span><span class="sxs-lookup"><span data-stu-id="3ad79-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="3ad79-182">Pro vytvoření hodnoty hash, pomocí funkce algoritmu hash řady SHA-2, jako je například SHA512, SHA384 nebo SHA256.</span><span class="sxs-lookup"><span data-stu-id="3ad79-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="3ad79-183">Pro digitální podpisy použijte RSA s délkou klíče větší než nebo rovna hodnotě 2 048 bitů nebo ECDSA s délkou klíče větší než nebo rovna 256 bitů.</span><span class="sxs-lookup"><span data-stu-id="3ad79-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="3ad79-184">**Kategorie:** Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3ad79-184">**Category:** Security</span></span>

<span data-ttu-id="3ad79-185">**Závažnost:** Upozornění</span><span class="sxs-lookup"><span data-stu-id="3ad79-185">**Severity:** Warning</span></span>

<span data-ttu-id="3ad79-186">Další informace: [CA5351: Nepoužívejte poškozené kryptografické algoritmy](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="3ad79-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>
