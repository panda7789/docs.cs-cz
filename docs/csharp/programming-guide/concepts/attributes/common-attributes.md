---
title: "Mezi běžné atributy (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aded9c9b2e8c253eebd6c71782f0bff6ca0104ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="common-attributes-c"></a><span data-ttu-id="d2962-102">Mezi běžné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="d2962-102">Common Attributes (C#)</span></span>
<span data-ttu-id="d2962-103">Toto téma popisuje atributy, které se běžně používají v C# programy.</span><span class="sxs-lookup"><span data-stu-id="d2962-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
-   [<span data-ttu-id="d2962-104">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="d2962-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="d2962-105">Zastaralé atribut</span><span class="sxs-lookup"><span data-stu-id="d2962-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="d2962-106">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="d2962-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="d2962-107">Volající – atributy s informacemi</span><span class="sxs-lookup"><span data-stu-id="d2962-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
##  <a name="Global"></a><span data-ttu-id="d2962-108">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="d2962-108">Global Attributes</span></span>  
 <span data-ttu-id="d2962-109">Většina atributy platí pro konkrétní jazyk prvky, jako jsou například třídy nebo metody; ale některé atributy jsou globální – se vztahují na modul nebo celý sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="d2962-110">Například <xref:System.Reflection.AssemblyVersionAttribute> atribut slouží k vložení informací o verzi do sestavení, například takto:</span><span class="sxs-lookup"><span data-stu-id="d2962-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="d2962-111">Globální atributy se zobrazí ve zdrojovém kódu po všech nejvyšší úrovně `using` direktivy a před všechny deklarace typu, modul nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d2962-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="d2962-112">Globální atributy lze zobrazit v několika zdrojových souborů, ale soubory musí být zkompilovány při průchodu kompilace.</span><span class="sxs-lookup"><span data-stu-id="d2962-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="d2962-113">V jazyce C# projekty jsou v souboru AssemblyInfo.cs uveďte globálními atributy.</span><span class="sxs-lookup"><span data-stu-id="d2962-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="d2962-114">Atributů sestavení jsou hodnoty, které obsahují informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="d2962-115">Spadají do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="d2962-115">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="d2962-116">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="d2962-116">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="d2962-117">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="d2962-117">Informational attributes</span></span>  
  
-   <span data-ttu-id="d2962-118">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="d2962-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="d2962-119">Atributy Identity sestavení</span><span class="sxs-lookup"><span data-stu-id="d2962-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="d2962-120">Zjistit identitu sestavení tři atributy (se silným názvem, pokud je k dispozici): název, verzi a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="d2962-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="d2962-121">Tyto atributy tvoří úplný název sestavení a jsou povinné, pokud odkazujete v kódu.</span><span class="sxs-lookup"><span data-stu-id="d2962-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="d2962-122">Můžete nastavit verze a jazykové verze pomocí atributů sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="d2962-123">Hodnota názvu je ale nastavená kompilátorem prostředí Visual Studio IDE v [dialogové okno informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box), nebo na soubor, který obsahuje manifest sestavení na základě Linker sestavení (Al.exe) při vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="d2962-124"><xref:System.Reflection.AssemblyFlagsAttribute> Atribut určuje, zda více kopií sestavení mohou existovat vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="d2962-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="d2962-125">V následující tabulce jsou uvedeny atributy identity.</span><span class="sxs-lookup"><span data-stu-id="d2962-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="d2962-126">Atribut</span><span class="sxs-lookup"><span data-stu-id="d2962-126">Attribute</span></span>|<span data-ttu-id="d2962-127">Účel</span><span class="sxs-lookup"><span data-stu-id="d2962-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="d2962-128">Popisuje plně identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="d2962-129">Určuje verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="d2962-130">Určuje, které jazykovou verzi sestavení podporuje.</span><span class="sxs-lookup"><span data-stu-id="d2962-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="d2962-131">Určuje, zda sestavení podporuje spuštění vedle sebe na stejném počítači, v rámci jednoho procesu, nebo ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2962-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="d2962-132">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="d2962-132">Informational Attributes</span></span>  
 <span data-ttu-id="d2962-133">Informační atributy můžete zadat další společnosti nebo informace o produktu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="d2962-134">V následující tabulce jsou definované v informační atributy <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d2962-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="d2962-135">Atribut</span><span class="sxs-lookup"><span data-stu-id="d2962-135">Attribute</span></span>|<span data-ttu-id="d2962-136">Účel</span><span class="sxs-lookup"><span data-stu-id="d2962-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="d2962-137">Definuje vlastní atribut, který určuje název produktu manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="d2962-138">Definuje vlastní atribut, který určuje ochrannou známku pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="d2962-139">Definuje vlastní atribut, který určuje informační verze pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="d2962-140">Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="d2962-141">Definuje vlastní atribut, který určuje copyright pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="d2962-142">Dá pokyn kompilátoru použít konkrétní verzi číslo pro prostředek verze souboru Win32.</span><span class="sxs-lookup"><span data-stu-id="d2962-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="d2962-143">Určuje, zda je sestavení kompatibilní s specifikace CLS (Common Language).</span><span class="sxs-lookup"><span data-stu-id="d2962-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="d2962-144">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="d2962-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="d2962-145">Atributy manifestu sestavení můžete použít k poskytování informací v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="d2962-146">To zahrnuje název, popis, výchozí alias a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d2962-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="d2962-147">V následující tabulce jsou definované atributy manifestu sestavení v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d2962-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="d2962-148">Atribut</span><span class="sxs-lookup"><span data-stu-id="d2962-148">Attribute</span></span>|<span data-ttu-id="d2962-149">Účel</span><span class="sxs-lookup"><span data-stu-id="d2962-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="d2962-150">Definuje vlastní atribut, který určuje název sestavení manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="d2962-151">Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2962-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="d2962-152">Manifest sestavení definuje vlastní atribut, který určuje konfigurace aplikace sestavení (například instalačních nebo ladicích).</span><span class="sxs-lookup"><span data-stu-id="d2962-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="d2962-153">Definuje výchozí popisný aliasu pro manifest sestavení</span><span class="sxs-lookup"><span data-stu-id="d2962-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a><span data-ttu-id="d2962-154">Zastaralé atribut</span><span class="sxs-lookup"><span data-stu-id="d2962-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="d2962-155">`Obsolete` Atribut určí program entity jako ten, který již není doporučeno pro použití.</span><span class="sxs-lookup"><span data-stu-id="d2962-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="d2962-156">Každý použijte entity označeny jako zastaralé následně vydá upozornění nebo chybu, v závislosti na konfiguraci atributu.</span><span class="sxs-lookup"><span data-stu-id="d2962-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="d2962-157">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d2962-157">For example:</span></span>  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 <span data-ttu-id="d2962-158">V tomto příkladu `Obsolete` atribut se používá pro třídu `A` a metoda `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="d2962-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="d2962-159">Protože druhý argument konstruktoru atributu aplikovat `B.OldMethod` je nastaven na `true`, tato metoda způsobí chybu kompilátoru, zatímco použití třídy `A` bude jenom produktu upozornění.</span><span class="sxs-lookup"><span data-stu-id="d2962-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="d2962-160">Volání metody `B.NewMethod`, ale vytváří žádná upozornění ani chyby.</span><span class="sxs-lookup"><span data-stu-id="d2962-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="d2962-161">Daný řetězec jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="d2962-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="d2962-162">Například pokud ji používáte s předchozí definice, generuje následující kód, dvě upozornění a jednu chybu:</span><span class="sxs-lookup"><span data-stu-id="d2962-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="d2962-163">Dva upozornění pro třídu `A` jsou generovány: jeden pro deklaraci referenci třídy a jeden pro konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="d2962-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="d2962-164">`Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení důvod, proč je zastaralé položky a doporučuje se co místo toho chcete použít.</span><span class="sxs-lookup"><span data-stu-id="d2962-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="d2962-165">`Obsolete` Atribut je jedno použití atribut a dají se použít k Každá entita, která umožňuje atributy.</span><span class="sxs-lookup"><span data-stu-id="d2962-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="d2962-166">`Obsolete`je alias <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d2962-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a><span data-ttu-id="d2962-167">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="d2962-167">Conditional Attribute</span></span>  
 <span data-ttu-id="d2962-168">`Conditional` Atribut umožňuje provádění metody závisí na identifikátor předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="d2962-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="d2962-169">`Conditional` Atribut je alias <xref:System.Diagnostics.ConditionalAttribute>a dají se použít metody nebo třídy atributu.</span><span class="sxs-lookup"><span data-stu-id="d2962-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="d2962-170">V tomto příkladu `Conditional` je použitý na metodu, pokud chcete povolit nebo zakázat zobrazení diagnostické informace specifické pro aplikace:</span><span class="sxs-lookup"><span data-stu-id="d2962-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 <span data-ttu-id="d2962-171">Pokud `TRACE_ON` identifikátor není definován, nezobrazí se žádný výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="d2962-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="d2962-172">`Conditional` Atribut se často používá u `DEBUG` identifikátor povolení trasování a protokolování funkce pro ladění ale není ve verzi sestavení, jako jsou to:</span><span class="sxs-lookup"><span data-stu-id="d2962-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="d2962-173">Při volání metody označené jako podmíněného existenci nebo neexistenci těchto zadaný symbol předběžného zpracování určuje, zda je volání zahrnuty nebo tento parametr vynechán.</span><span class="sxs-lookup"><span data-stu-id="d2962-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="d2962-174">Pokud je definována symbol, volání je zahrnuté; volání, jinak je vynechán.</span><span class="sxs-lookup"><span data-stu-id="d2962-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="d2962-175">Pomocí `Conditional` je je automaticky více elegantní a méně náchylný alternativa k uzavření metody uvnitř `#if…#endif` bloků, například takto:</span><span class="sxs-lookup"><span data-stu-id="d2962-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="d2962-176">Podmíněné metoda musí být metody ve třídě nebo struktuře prohlášení a nesmí mít návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d2962-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="d2962-177">Použití více identifikátorů</span><span class="sxs-lookup"><span data-stu-id="d2962-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="d2962-178">Pokud metoda obsahuje více `Conditional` atributy, volání do metody je zahrnuta, pokud je definována alespoň jeden z podmíněného symboly (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR).</span><span class="sxs-lookup"><span data-stu-id="d2962-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="d2962-179">V tomto příkladu přítomnost buď `A` nebo `B` bude výsledkem volání metody:</span><span class="sxs-lookup"><span data-stu-id="d2962-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="d2962-180">K dosažení účinku logicky propojení symboly pomocí operátoru AND, můžete definovat sériové podmíněného metody.</span><span class="sxs-lookup"><span data-stu-id="d2962-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="d2962-181">Například druhé metody níže spustí, pouze pokud obě `A` a `B` jsou definovány:</span><span class="sxs-lookup"><span data-stu-id="d2962-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="d2962-182">Pomocí podmíněného třídy atributů</span><span class="sxs-lookup"><span data-stu-id="d2962-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="d2962-183">`Conditional` Atribut lze použít také k – třída definice atributu.</span><span class="sxs-lookup"><span data-stu-id="d2962-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="d2962-184">V tomto příkladu vlastní atribut `Documentation` pouze přidá informace k metadatům Pokud je definována ladění.</span><span class="sxs-lookup"><span data-stu-id="d2962-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
##  <a name="CallerInfo"></a><span data-ttu-id="d2962-185">Volající – atributy s informacemi</span><span class="sxs-lookup"><span data-stu-id="d2962-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="d2962-186">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="d2962-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="d2962-187">Můžete získat cestu k souboru zdrojového kódu, číslo řádku v zdrojový kód a název člena volajícího.</span><span class="sxs-lookup"><span data-stu-id="d2962-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="d2962-188">Chcete-li získat informace o subjektu volajícím člen, použijte atributy, které se použijí pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="d2962-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="d2962-189">Každý volitelný parametr určí výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d2962-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="d2962-190">Následující tabulka uvádí informace o volajícím atributy, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="d2962-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="d2962-191">Atribut</span><span class="sxs-lookup"><span data-stu-id="d2962-191">Attribute</span></span>|<span data-ttu-id="d2962-192">Popis</span><span class="sxs-lookup"><span data-stu-id="d2962-192">Description</span></span>|<span data-ttu-id="d2962-193">Typ</span><span class="sxs-lookup"><span data-stu-id="d2962-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="d2962-194">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="d2962-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="d2962-195">Je to cesta ke v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="d2962-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="d2962-196">Číslo řádku v souboru zdroj, ze kterého je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="d2962-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="d2962-197">Název metody nebo vlastnosti název volajícího.</span><span class="sxs-lookup"><span data-stu-id="d2962-197">Method name or property name of the caller.</span></span> <span data-ttu-id="d2962-198">Další informace najdete v tématu [informace o subjektu volajícím (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="d2962-198">For more information, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="d2962-199">Další informace o atributech volající informace najdete v tématu [informace o subjektu volajícím (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="d2962-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2962-200">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2962-200">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="d2962-201">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d2962-201">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d2962-202">Atributy</span><span class="sxs-lookup"><span data-stu-id="d2962-202">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="d2962-203">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="d2962-203">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="d2962-204">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="d2962-204">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
