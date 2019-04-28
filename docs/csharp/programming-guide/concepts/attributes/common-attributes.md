---
title: Běžné atributy (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: d5d56fff82fb552f42f72c18b8c3b907c5bc113c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702578"
---
# <a name="common-attributes-c"></a><span data-ttu-id="4580d-102">Běžné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="4580d-102">Common Attributes (C#)</span></span>
<span data-ttu-id="4580d-103">Toto téma popisuje atributy, které se běžně používají v aplikacích jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4580d-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
- [<span data-ttu-id="4580d-104">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="4580d-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="4580d-105">Zastaralé atribut</span><span class="sxs-lookup"><span data-stu-id="4580d-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="4580d-106">Atribut Conditional.</span><span class="sxs-lookup"><span data-stu-id="4580d-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="4580d-107">Atributy informace o volajícím</span><span class="sxs-lookup"><span data-stu-id="4580d-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
## <a name="Global"></a> <span data-ttu-id="4580d-108">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="4580d-108">Global Attributes</span></span>  
 <span data-ttu-id="4580d-109">Většina atributy se použijí na konkrétní jazykové prvky, jako jsou třídy nebo metody; Nicméně některé atributy jsou globální, se vztahují na celé sestavení nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="4580d-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="4580d-110">Například <xref:System.Reflection.AssemblyVersionAttribute> atribut lze použít k vložení informací o verzi do sestavení, například takto:</span><span class="sxs-lookup"><span data-stu-id="4580d-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="4580d-111">Globální atributy se zobrazí ve zdrojovém kódu po všech nejvyšší úrovně `using` direktivy a před všemi deklaracemi typu, modul nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="4580d-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="4580d-112">Globální atributy lze zobrazit ve více zdrojových souborech, ale soubory musí být zkompilovány při průchodu kompilace.</span><span class="sxs-lookup"><span data-stu-id="4580d-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="4580d-113">V projektech C# globální atributy jsou umístěny v souboru AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="4580d-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="4580d-114">Atributy sestavení jsou hodnoty, které obsahují informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="4580d-115">Spadají do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="4580d-115">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="4580d-116">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="4580d-116">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="4580d-117">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="4580d-117">Informational attributes</span></span>  
  
- <span data-ttu-id="4580d-118">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="4580d-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="4580d-119">Atributy Identity sestavení</span><span class="sxs-lookup"><span data-stu-id="4580d-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="4580d-120">Tři atributy (se silným názvem, pokud je k dispozici) určují identitu sestavení: název, verzi a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="4580d-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="4580d-121">Tyto atributy tvoří úplný název sestavení, jsou povinné, když odkazujete v kódu.</span><span class="sxs-lookup"><span data-stu-id="4580d-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="4580d-122">Můžete nastavit verzi a jazykovou verzi pomocí atributů sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="4580d-123">Je však nastavena hodnota názvu kompilátorem v sadě Visual Studio IDE [dialogové okno informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box), nebo Assembly Linker (Al.exe), když se vytvoří sestavení, na základě souboru, který obsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="4580d-124"><xref:System.Reflection.AssemblyFlagsAttribute> Atribut určuje, zda mohou existovat vedle sebe více kopií daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="4580d-125">V následující tabulce jsou uvedeny atributy identity.</span><span class="sxs-lookup"><span data-stu-id="4580d-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="4580d-126">Atribut</span><span class="sxs-lookup"><span data-stu-id="4580d-126">Attribute</span></span>|<span data-ttu-id="4580d-127">Účel</span><span class="sxs-lookup"><span data-stu-id="4580d-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="4580d-128">Plně popisuje identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="4580d-129">Určuje verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="4580d-130">Určuje, který jazyková verze sestavení podporuje.</span><span class="sxs-lookup"><span data-stu-id="4580d-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="4580d-131">Určuje, zda sestavení podporuje spuštění vedle sebe na stejném počítači, ve stejném procesu, nebo ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="4580d-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="4580d-132">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="4580d-132">Informational Attributes</span></span>  
 <span data-ttu-id="4580d-133">Informační atributy můžete zadat další společnosti nebo informace o produktu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="4580d-134">V následující tabulce jsou uvedeny informační atributy definované ve <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4580d-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="4580d-135">Atribut</span><span class="sxs-lookup"><span data-stu-id="4580d-135">Attribute</span></span>|<span data-ttu-id="4580d-136">Účel</span><span class="sxs-lookup"><span data-stu-id="4580d-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="4580d-137">Definuje vlastní atribut, který určuje název produktu pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="4580d-138">Definuje vlastní atribut, který určuje ochranná známka pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="4580d-139">Definuje vlastní atribut, který určuje informační verze pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="4580d-140">Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="4580d-141">Definuje vlastní atribut, který určuje copyright pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="4580d-142">Instruuje kompilátor, aby používali konkrétní verzi pro prostředek verze souboru Win32.</span><span class="sxs-lookup"><span data-stu-id="4580d-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="4580d-143">Označuje, zda je sestavení kompatibilních s specifikace CLS (Common Language).</span><span class="sxs-lookup"><span data-stu-id="4580d-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="4580d-144">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="4580d-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="4580d-145">Atributy manifestu sestavení můžete použít k zadání informací v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="4580d-146">Jedná se o název, popis, výchozí aliasu a konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4580d-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="4580d-147">V následující tabulce jsou uvedeny atributy manifestu sestavení definované v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4580d-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="4580d-148">Atribut</span><span class="sxs-lookup"><span data-stu-id="4580d-148">Attribute</span></span>|<span data-ttu-id="4580d-149">Účel</span><span class="sxs-lookup"><span data-stu-id="4580d-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="4580d-150">Definuje vlastní atribut, který určuje nadpisech sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="4580d-151">Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="4580d-152">Definuje vlastní atribut, který určuje konfiguraci služby sestavení (například prodejní nebo ladicí) pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4580d-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="4580d-153">Definuje výchozí popisný alias pro manifest sestavení</span><span class="sxs-lookup"><span data-stu-id="4580d-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a> <span data-ttu-id="4580d-154">Zastaralé atribut</span><span class="sxs-lookup"><span data-stu-id="4580d-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="4580d-155">`Obsolete` Atribut určí program entity jako ten, který už se nedoporučuje používat.</span><span class="sxs-lookup"><span data-stu-id="4580d-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="4580d-156">Každé použití klíčového entity označený jako zastaralý. následně vygeneruje upozornění nebo chybu, v závislosti na konfiguraci atributu.</span><span class="sxs-lookup"><span data-stu-id="4580d-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="4580d-157">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4580d-157">For example:</span></span>  
  
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
  
 <span data-ttu-id="4580d-158">V tomto příkladu `Obsolete` atribut aplikován na třídu `A` a metodě `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="4580d-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="4580d-159">Protože druhý argument konstruktoru atributu pro `B.OldMethod` je nastavena na `true`, tato metoda způsobí chybu kompilátoru, že horizontálních oddílů pomocí třídy `A` se jen vytvoří upozornění.</span><span class="sxs-lookup"><span data-stu-id="4580d-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="4580d-160">Volání `B.NewMethod`, ale vytváří žádná upozornění ani chyby.</span><span class="sxs-lookup"><span data-stu-id="4580d-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="4580d-161">Jako součást upozornění nebo chyby se zobrazí jako první argument pro konstruktor atributu v zadaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="4580d-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="4580d-162">Například když ji použijete s předchozí definice, následující kód vygeneruje dvě upozornění a jednu chybu:</span><span class="sxs-lookup"><span data-stu-id="4580d-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="4580d-163">Dvě upozornění pro třídu `A` jsou generovány: jeden pro deklaraci odkazech na třídy rozhraní a jeden pro konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="4580d-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="4580d-164">`Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení, proč položky je zastaralá a co se má použít místo toho se doporučuje.</span><span class="sxs-lookup"><span data-stu-id="4580d-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="4580d-165">`Obsolete` Atribut je jedno použití atributu a lze použít u Každá entita, která umožňuje atributy.</span><span class="sxs-lookup"><span data-stu-id="4580d-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="4580d-166">`Obsolete` je alias pro <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4580d-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a> <span data-ttu-id="4580d-167">Atribut Conditional.</span><span class="sxs-lookup"><span data-stu-id="4580d-167">Conditional Attribute</span></span>  
 <span data-ttu-id="4580d-168">`Conditional` Atribut umožňuje provádění metody závislé na identifikátor předzpracování.</span><span class="sxs-lookup"><span data-stu-id="4580d-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="4580d-169">`Conditional` Atribut je alias pro <xref:System.Diagnostics.ConditionalAttribute>a můžete použít u metody nebo třídy atributu.</span><span class="sxs-lookup"><span data-stu-id="4580d-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="4580d-170">V tomto příkladu `Conditional` je použít pro metodu k povolení nebo zakázání zobrazování diagnostické informace specifické pro aplikace:</span><span class="sxs-lookup"><span data-stu-id="4580d-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="4580d-171">Pokud `TRACE_ON` identifikátor není definován, nezobrazí se žádný výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="4580d-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="4580d-172">`Conditional` Atribut se často používá s `DEBUG` identifikátor povolit trasování a protokolování funkce pro ladění ale není ve verzi sestavení, tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="4580d-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="4580d-173">Při volání metody označené jako podmíněný přítomnosti nebo nepřítomnosti zadaného symbolu předzpracování Určuje, jestli je volání zahrnuté nebo vynechán.</span><span class="sxs-lookup"><span data-stu-id="4580d-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="4580d-174">Pokud je definován symbol, je součástí; volání v opačném případě je vynechána, volání.</span><span class="sxs-lookup"><span data-stu-id="4580d-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="4580d-175">Pomocí `Conditional` je čistější, více elegantnímu a méně náchylný alternativou k nadřazené metody uvnitř `#if…#endif` bloků, například takto:</span><span class="sxs-lookup"><span data-stu-id="4580d-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="4580d-176">Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4580d-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="4580d-177">Použití více identifikátorů</span><span class="sxs-lookup"><span data-stu-id="4580d-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="4580d-178">Pokud metoda má více `Conditional` atributy, volání metody je zahrnuta, pokud je definován alespoň jeden z podmíněné symboly (jinými slovy, symboly jsou logicky spojeny operátorem OR).</span><span class="sxs-lookup"><span data-stu-id="4580d-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="4580d-179">V tomto příkladu přítomnost buď `A` nebo `B` bude výsledkem volání metody:</span><span class="sxs-lookup"><span data-stu-id="4580d-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="4580d-180">Pokud chcete dosáhnout logicky propojení symboly pomocí operátoru AND, můžete definovat sériového portu podmíněné metody.</span><span class="sxs-lookup"><span data-stu-id="4580d-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="4580d-181">Například níže druhá metoda spustí, pouze pokud mají oba `A` a `B` jsou definovány:</span><span class="sxs-lookup"><span data-stu-id="4580d-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="4580d-182">Podmíněné pomocí třídy atributů</span><span class="sxs-lookup"><span data-stu-id="4580d-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="4580d-183">`Conditional` Atribut lze použít také pro třídy definice atributu.</span><span class="sxs-lookup"><span data-stu-id="4580d-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="4580d-184">V tomto příkladu je vlastní atribut `Documentation` se přidat pouze informace metadat je definován DEBUG.</span><span class="sxs-lookup"><span data-stu-id="4580d-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
## <a name="CallerInfo"></a> <span data-ttu-id="4580d-185">Atributy informace o volajícím</span><span class="sxs-lookup"><span data-stu-id="4580d-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="4580d-186">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="4580d-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="4580d-187">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a členské jméno volajícího.</span><span class="sxs-lookup"><span data-stu-id="4580d-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="4580d-188">Pokud chcete získat informace o subjektu volajícím člen, použijte atributy, které jsou použity na volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="4580d-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="4580d-189">Každý volitelný parametr určuje výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4580d-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="4580d-190">V následující tabulce jsou uvedeny atributy informace o volajícím, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="4580d-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="4580d-191">Atribut</span><span class="sxs-lookup"><span data-stu-id="4580d-191">Attribute</span></span>|<span data-ttu-id="4580d-192">Popis</span><span class="sxs-lookup"><span data-stu-id="4580d-192">Description</span></span>|<span data-ttu-id="4580d-193">Type</span><span class="sxs-lookup"><span data-stu-id="4580d-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="4580d-194">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="4580d-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="4580d-195">Toto je cesta v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4580d-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="4580d-196">Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="4580d-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="4580d-197">Název metody nebo názvu vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="4580d-197">Method name or property name of the caller.</span></span> <span data-ttu-id="4580d-198">Další informace najdete v tématu [informace o volajícím (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="4580d-198">For more information, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="4580d-199">Další informace o atributech informace o volajícím, naleznete v tématu [informace o volajícím (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="4580d-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4580d-200">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4580d-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="4580d-201">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4580d-201">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4580d-202">Atributy</span><span class="sxs-lookup"><span data-stu-id="4580d-202">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="4580d-203">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="4580d-203">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="4580d-204">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="4580d-204">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
