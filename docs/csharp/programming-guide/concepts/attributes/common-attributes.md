---
title: Společné atributy (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595457"
---
# <a name="common-attributes-c"></a><span data-ttu-id="5401b-102">Společné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="5401b-102">Common Attributes (C#)</span></span>
<span data-ttu-id="5401b-103">Toto téma popisuje atributy, které se nejčastěji používají v C# programech.</span><span class="sxs-lookup"><span data-stu-id="5401b-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
- [<span data-ttu-id="5401b-104">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="5401b-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="5401b-105">Zastaralý atribut</span><span class="sxs-lookup"><span data-stu-id="5401b-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="5401b-106">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="5401b-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="5401b-107">Atributy informací o volajícím</span><span class="sxs-lookup"><span data-stu-id="5401b-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
## <a name="Global"></a><span data-ttu-id="5401b-108">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="5401b-108">Global Attributes</span></span>  
 <span data-ttu-id="5401b-109">Většina atributů je aplikována na konkrétní prvky jazyka, jako jsou třídy nebo metody. Některé atributy jsou však globální – platí pro celé sestavení nebo modul.</span><span class="sxs-lookup"><span data-stu-id="5401b-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="5401b-110">Například <xref:System.Reflection.AssemblyVersionAttribute> atribut lze použít k vložení informací o verzi do sestavení, jako je:</span><span class="sxs-lookup"><span data-stu-id="5401b-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="5401b-111">Globální atributy se zobrazí ve zdrojovém kódu za všemi direktivami `using` nejvyšší úrovně a před všemi deklaracemi typu, modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5401b-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="5401b-112">Globální atributy se mohou objevit ve více zdrojových souborech, ale soubory musí být kompilovány v rámci jedné kompilační fáze.</span><span class="sxs-lookup"><span data-stu-id="5401b-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="5401b-113">V C# projektech jsou globální atributy vloženy do souboru AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="5401b-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="5401b-114">Atributy sestavení jsou hodnoty, které poskytují informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="5401b-115">Spadají do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="5401b-115">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="5401b-116">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="5401b-116">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="5401b-117">Informativní atributy</span><span class="sxs-lookup"><span data-stu-id="5401b-117">Informational attributes</span></span>  
  
- <span data-ttu-id="5401b-118">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="5401b-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="5401b-119">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="5401b-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="5401b-120">Tři atributy (se silným názvem, pokud jsou k dispozici) určují identitu sestavení: název, verze a jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="5401b-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="5401b-121">Tyto atributy tvoří úplný název sestavení a jsou vyžadovány při odkazování v kódu.</span><span class="sxs-lookup"><span data-stu-id="5401b-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="5401b-122">Můžete nastavit verzi a jazykovou verzi sestavení pomocí atributů.</span><span class="sxs-lookup"><span data-stu-id="5401b-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="5401b-123">Hodnota name je však nastavena kompilátorem, rozhraním IDE sady Visual Studio v [dialogovém okně informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box)nebo linker sestavení (Al. exe), když je sestavení vytvořeno, na základě souboru, který obsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="5401b-124"><xref:System.Reflection.AssemblyFlagsAttribute> Atribut určuje, zda více kopií sestavení může existovat současně.</span><span class="sxs-lookup"><span data-stu-id="5401b-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="5401b-125">V následující tabulce jsou uvedeny atributy identity.</span><span class="sxs-lookup"><span data-stu-id="5401b-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="5401b-126">Atribut</span><span class="sxs-lookup"><span data-stu-id="5401b-126">Attribute</span></span>|<span data-ttu-id="5401b-127">Účel</span><span class="sxs-lookup"><span data-stu-id="5401b-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="5401b-128">Plně popisuje identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="5401b-129">Určuje verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="5401b-130">Určuje jazykovou verzi, kterou sestavení podporuje.</span><span class="sxs-lookup"><span data-stu-id="5401b-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="5401b-131">Určuje, zda sestavení podporuje souběžné spouštění ve stejném počítači, ve stejném procesu nebo ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="5401b-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="5401b-132">Informativní atributy</span><span class="sxs-lookup"><span data-stu-id="5401b-132">Informational Attributes</span></span>  
 <span data-ttu-id="5401b-133">Pomocí informativních atributů lze poskytnout další informace o společnosti nebo produktu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="5401b-134">V následující tabulce jsou uvedeny informativní atributy definované v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5401b-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="5401b-135">Atribut</span><span class="sxs-lookup"><span data-stu-id="5401b-135">Attribute</span></span>|<span data-ttu-id="5401b-136">Účel</span><span class="sxs-lookup"><span data-stu-id="5401b-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="5401b-137">Definuje vlastní atribut, který určuje název produktu pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="5401b-138">Definuje vlastní atribut, který určuje ochrannou známku pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="5401b-139">Definuje vlastní atribut, který určuje informační verzi manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="5401b-140">Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="5401b-141">Definuje vlastní atribut, který určuje autorská práva pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="5401b-142">Instruuje kompilátor, aby pro prostředek verze souboru Win32 použil konkrétní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="5401b-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="5401b-143">Určuje, zda je sestavení kompatibilní se specifikací CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="5401b-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="5401b-144">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="5401b-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="5401b-145">Atributy manifestu sestavení lze použít k poskytnutí informací v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="5401b-146">Patří sem název, popis, výchozí alias a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5401b-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="5401b-147">V následující tabulce jsou uvedeny atributy manifestu sestavení definované v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5401b-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="5401b-148">Atribut</span><span class="sxs-lookup"><span data-stu-id="5401b-148">Attribute</span></span>|<span data-ttu-id="5401b-149">Účel</span><span class="sxs-lookup"><span data-stu-id="5401b-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="5401b-150">Definuje vlastní atribut, který určuje název sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="5401b-151">Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="5401b-152">Definuje vlastní atribut, který určuje konfiguraci sestavení (například maloobchodní nebo ladicí) pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="5401b-153">Definuje popisný výchozí alias pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="5401b-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a><span data-ttu-id="5401b-154">Zastaralý atribut</span><span class="sxs-lookup"><span data-stu-id="5401b-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="5401b-155">`Obsolete` Atribut označuje entitu programu jako tu, která se už nedoporučuje používat.</span><span class="sxs-lookup"><span data-stu-id="5401b-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="5401b-156">Každé použití entity označené jako zastaralé bude následně generovat upozornění nebo chybu v závislosti na tom, jak je atribut nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="5401b-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="5401b-157">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5401b-157">For example:</span></span>  
  
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
  
 <span data-ttu-id="5401b-158">V tomto příkladu `Obsolete` je atribut použit pro třídu `A` a na metodu `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="5401b-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="5401b-159">Vzhledem k tomu, že druhý argument konstruktoru atributu použité `B.OldMethod` pro je nastaven `true`na, tato metoda způsobí chybu kompilátoru, zatímco použití třídy `A` bude pouze generovat upozornění.</span><span class="sxs-lookup"><span data-stu-id="5401b-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="5401b-160">Volání `B.NewMethod`však negeneruje žádné upozornění nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="5401b-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="5401b-161">Řetězec poskytnutý jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="5401b-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="5401b-162">Například když použijete s předchozími definicemi, následující kód vygeneruje dvě upozornění a jednu chybu:</span><span class="sxs-lookup"><span data-stu-id="5401b-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="5401b-163">Dvě upozornění pro třídu `A` jsou vygenerována: jedna pro deklaraci odkazu na třídu a druhá pro konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="5401b-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="5401b-164">`Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení, proč je položka zastaralá a co použít místo toho se doporučuje.</span><span class="sxs-lookup"><span data-stu-id="5401b-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="5401b-165">`Obsolete` Atribut je atribut s jedním použitím a lze jej použít pro libovolnou entitu, která povoluje atributy.</span><span class="sxs-lookup"><span data-stu-id="5401b-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="5401b-166">`Obsolete`je alias pro <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5401b-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a><span data-ttu-id="5401b-167">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="5401b-167">Conditional Attribute</span></span>  
 <span data-ttu-id="5401b-168">`Conditional` Atribut provádí provádění metody závislé na identifikátoru předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="5401b-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="5401b-169">Atribut je alias pro <xref:System.Diagnostics.ConditionalAttribute>a lze jej použít pro metodu nebo třídu atributu. `Conditional`</span><span class="sxs-lookup"><span data-stu-id="5401b-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="5401b-170">V tomto příkladu se `Conditional` použije na metodu, která povolí nebo zakáže zobrazení diagnostických informací specifických pro program:</span><span class="sxs-lookup"><span data-stu-id="5401b-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="5401b-171">`TRACE_ON` Pokud identifikátor není definován, nebude zobrazen žádný výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="5401b-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="5401b-172">Atribut se často používá `DEBUG` s identifikátorem pro povolení funkcí trasování a protokolování pro sestavení ladění, ale ne v sestaveních vydaných verzí, jako je: `Conditional`</span><span class="sxs-lookup"><span data-stu-id="5401b-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="5401b-173">Když je volána metoda označená jako podmíněná, přítomnost nebo absence zadaného symbolu předzpracování určuje, zda je volání zahrnuto nebo vynecháno.</span><span class="sxs-lookup"><span data-stu-id="5401b-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="5401b-174">Pokud je symbol definován, volání je zahrnuto; v opačném případě je volání vynecháno.</span><span class="sxs-lookup"><span data-stu-id="5401b-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="5401b-175">Použití `Conditional` je čisticí, jasnější a méně náchylné k chybám, které lze použít jako alternativu k `#if…#endif` uzavření metod uvnitř bloků, například:</span><span class="sxs-lookup"><span data-stu-id="5401b-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="5401b-176">Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5401b-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="5401b-177">Použití více identifikátorů</span><span class="sxs-lookup"><span data-stu-id="5401b-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="5401b-178">Pokud má metoda více `Conditional` atributů, volání metody je zahrnuto, pokud je definován alespoň jeden z podmíněných symbolů (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR).</span><span class="sxs-lookup"><span data-stu-id="5401b-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="5401b-179">V tomto příkladu přítomnost buď `A` nebo `B` , způsobí volání metody:</span><span class="sxs-lookup"><span data-stu-id="5401b-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="5401b-180">Chcete-li dosáhnout vlivu logického propojení symbolů pomocí operátoru AND, můžete definovat sériové podmíněné metody.</span><span class="sxs-lookup"><span data-stu-id="5401b-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="5401b-181">Například druhá metoda níže se spustí pouze v případě, že jsou `A` definovány `B` obě i:</span><span class="sxs-lookup"><span data-stu-id="5401b-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="5401b-182">Použití podmíněné s třídami atributů</span><span class="sxs-lookup"><span data-stu-id="5401b-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="5401b-183">`Conditional` Atribut lze použít také pro definici třídy atributu.</span><span class="sxs-lookup"><span data-stu-id="5401b-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="5401b-184">V tomto příkladu vlastní atribut `Documentation` přidá informace do metadat pouze v případě, že je definován ladění.</span><span class="sxs-lookup"><span data-stu-id="5401b-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
## <a name="CallerInfo"></a><span data-ttu-id="5401b-185">Atributy informací o volajícím</span><span class="sxs-lookup"><span data-stu-id="5401b-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="5401b-186">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="5401b-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="5401b-187">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.</span><span class="sxs-lookup"><span data-stu-id="5401b-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="5401b-188">Chcete-li získat informace o volajícím členu, použijte atributy, které se použijí na volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="5401b-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="5401b-189">Každý volitelný parametr určuje výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5401b-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="5401b-190">V následující tabulce jsou uvedeny atributy informací o volajícím, které jsou <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> definovány v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="5401b-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="5401b-191">Atribut</span><span class="sxs-lookup"><span data-stu-id="5401b-191">Attribute</span></span>|<span data-ttu-id="5401b-192">Popis</span><span class="sxs-lookup"><span data-stu-id="5401b-192">Description</span></span>|<span data-ttu-id="5401b-193">type</span><span class="sxs-lookup"><span data-stu-id="5401b-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="5401b-194">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="5401b-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="5401b-195">Toto je cesta v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="5401b-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="5401b-196">Číslo řádku ve zdrojovém souboru, ze kterého je metoda volána.</span><span class="sxs-lookup"><span data-stu-id="5401b-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="5401b-197">Název metody nebo název vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="5401b-197">Method name or property name of the caller.</span></span> <span data-ttu-id="5401b-198">Další informace naleznete v tématu [informace o volajícímC#()](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="5401b-198">For more information, see [Caller Information (C#)](../caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="5401b-199">Další informace o atributech informace o volajícím naleznete v tématu [informaceC#o volajícím ()](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="5401b-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5401b-200">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5401b-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="5401b-201">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5401b-201">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="5401b-202">Atributy</span><span class="sxs-lookup"><span data-stu-id="5401b-202">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="5401b-203">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="5401b-203">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="5401b-204">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="5401b-204">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
