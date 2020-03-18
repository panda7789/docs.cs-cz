---
title: Běžné atributy (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399754"
---
# <a name="common-attributes-c"></a><span data-ttu-id="6b9b6-102">Běžné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="6b9b6-102">Common Attributes (C#)</span></span>
<span data-ttu-id="6b9b6-103">Toto téma popisuje atributy, které se nejčastěji používají v programech jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
- [<span data-ttu-id="6b9b6-104">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="6b9b6-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="6b9b6-105">Zastaralý atribut</span><span class="sxs-lookup"><span data-stu-id="6b9b6-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="6b9b6-106">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="6b9b6-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="6b9b6-107">Atributy informací o volajícím</span><span class="sxs-lookup"><span data-stu-id="6b9b6-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
## <a name="Global"></a><span data-ttu-id="6b9b6-108">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="6b9b6-108">Global Attributes</span></span>  
 <span data-ttu-id="6b9b6-109">Většina atributů je použita pro určité jazykové prvky, jako jsou třídy nebo metody; některé atributy jsou však globální – platí pro celé sestavení nebo modul.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="6b9b6-110"><xref:System.Reflection.AssemblyVersionAttribute> Atribut lze například použít k vložení informací o verzi do sestavení, například takto:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="6b9b6-111">Globální atributy se zobrazí ve zdrojovém kódu za všechny direktivy nejvyšší úrovně `using` a před jakýmkoli typem, modulem nebo deklaracemi oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="6b9b6-112">Globální atributy se mohou objevit ve více zdrojových souborech, ale soubory musí být zkompilovány v jednom průchodu kompilace.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="6b9b6-113">V projektech Jazyka C# jsou globální atributy vloženy do souboru AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="6b9b6-114">Atributy sestavení jsou hodnoty, které poskytují informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="6b9b6-115">Spadají do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-115">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="6b9b6-116">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="6b9b6-116">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="6b9b6-117">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="6b9b6-117">Informational attributes</span></span>  
  
- <span data-ttu-id="6b9b6-118">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="6b9b6-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="6b9b6-119">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="6b9b6-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="6b9b6-120">Identitu sestavení určují tři atributy (případně se silným názvem) název sestavení: název, verze a jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="6b9b6-121">Tyto atributy tvoří úplný název sestavení a jsou vyžadovány, když na něj odkazujete v kódu.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="6b9b6-122">Můžete nastavit verzi sestavení a jazykovou verzi pomocí atributů.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="6b9b6-123">Hodnota názvu je však nastavena kompilátorem, IDE sady Visual Studio v [dialogovém okně informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box)nebo propojovací množinu sestavení (Al.exe) při vytvoření sestavení na základě souboru, který obsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="6b9b6-124">Atribut <xref:System.Reflection.AssemblyFlagsAttribute> určuje, zda může existovat více kopií sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="6b9b6-125">V následující tabulce jsou uvedeny atributy identity.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="6b9b6-126">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b9b6-126">Attribute</span></span>|<span data-ttu-id="6b9b6-127">Účel</span><span class="sxs-lookup"><span data-stu-id="6b9b6-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="6b9b6-128">Plně popisuje identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="6b9b6-129">Určuje verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="6b9b6-130">Určuje, kterou jazykovou verzi sestavení podporuje.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="6b9b6-131">Určuje, zda sestavení podporuje souběžné spuštění ve stejném počítači, ve stejném procesu nebo ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="6b9b6-132">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="6b9b6-132">Informational Attributes</span></span>  
 <span data-ttu-id="6b9b6-133">Informační atributy můžete použít k poskytnutí dalších informací o společnosti nebo produktu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="6b9b6-134">V následující tabulce jsou uvedeny informační <xref:System.Reflection?displayProperty=nameWithType> atributy definované v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="6b9b6-135">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b9b6-135">Attribute</span></span>|<span data-ttu-id="6b9b6-136">Účel</span><span class="sxs-lookup"><span data-stu-id="6b9b6-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="6b9b6-137">Definuje vlastní atribut, který určuje název produktu pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="6b9b6-138">Definuje vlastní atribut, který určuje ochrannou známku pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="6b9b6-139">Definuje vlastní atribut, který určuje informační verzi manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="6b9b6-140">Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="6b9b6-141">Definuje vlastní atribut, který určuje autorská práva pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="6b9b6-142">Dává kompilátoru pokyn, aby pro prostředek verze souboru Win32 použil konkrétní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="6b9b6-143">Označuje, zda je sestavení kompatibilní se specifikací CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="6b9b6-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="6b9b6-144">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="6b9b6-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="6b9b6-145">Atributy manifestu sestavení můžete použít k poskytnutí informací v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="6b9b6-146">To zahrnuje název, popis, výchozí alias a konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="6b9b6-147">V následující tabulce jsou uvedeny atributy manifestu sestavení definované v oboru <xref:System.Reflection?displayProperty=nameWithType> názvů.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="6b9b6-148">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b9b6-148">Attribute</span></span>|<span data-ttu-id="6b9b6-149">Účel</span><span class="sxs-lookup"><span data-stu-id="6b9b6-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="6b9b6-150">Definuje vlastní atribut, který určuje název sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="6b9b6-151">Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="6b9b6-152">Definuje vlastní atribut, který určuje konfiguraci sestavení (například maloobchodní nebo ladicí) pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="6b9b6-153">Definuje popisný výchozí alias pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a><span data-ttu-id="6b9b6-154">Zastaralý atribut</span><span class="sxs-lookup"><span data-stu-id="6b9b6-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="6b9b6-155">Atribut `Obsolete` označí entitu programu jako entitu, která se již nedoporučuje používat.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="6b9b6-156">Každé použití entity označené jako zastaralé následně vygeneruje upozornění nebo chybu v závislosti na konfiguraci atributu.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="6b9b6-157">Například:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-157">For example:</span></span>  
  
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
  
 <span data-ttu-id="6b9b6-158">V tomto `Obsolete` příkladu je `A` atribut použit `B.OldMethod`pro třídu a metodu .</span><span class="sxs-lookup"><span data-stu-id="6b9b6-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="6b9b6-159">Vzhledem k tomu, že druhý `B.OldMethod` argument `true`konstruktoru atributu aplikovaný na je `A` nastavena na , tato metoda způsobí chybu kompilátoru, vzhledem k tomu, že pomocí třídy pouze vytvoří upozornění.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="6b9b6-160">Volání `B.NewMethod`, však nevytváří žádné upozornění nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="6b9b6-161">Řetězec zadaný jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="6b9b6-162">Například při použití s předchozími definicemi, následující kód generuje dvě upozornění a jednu chybu:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="6b9b6-163">Jsou generována `A` dvě upozornění pro třídu: jeden pro deklaraci odkazu třídy a jeden pro konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="6b9b6-164">Atribut `Obsolete` lze použít bez argumentů, ale včetně vysvětlení, proč je položka zastaralá a co použít místo toho se doporučuje.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="6b9b6-165">Atribut `Obsolete` je atribut na jedno použití a lze jej použít pro libovolnou entitu, která umožňuje atributy.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="6b9b6-166">`Obsolete`je alias <xref:System.ObsoleteAttribute>pro aplikaci .</span><span class="sxs-lookup"><span data-stu-id="6b9b6-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a><span data-ttu-id="6b9b6-167">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="6b9b6-167">Conditional Attribute</span></span>  
 <span data-ttu-id="6b9b6-168">Atribut `Conditional` umožňuje provádění metody závislé na identifikátor předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="6b9b6-169">Atribut `Conditional` je alias <xref:System.Diagnostics.ConditionalAttribute>pro aplikaci a lze jej použít na metodu nebo třídu atributu.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="6b9b6-170">V tomto `Conditional` příkladu se používá metoda povolení nebo zakázání zobrazení diagnostických informací specifických pro program:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="6b9b6-171">Pokud `TRACE_ON` identifikátor není definován, zobrazí se žádný výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="6b9b6-172">Atribut `Conditional` se často používá `DEBUG` s identifikátorem povolit trasování a protokolování funkce pro ladění sestavení, ale ne ve verzi sestavení, takto:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="6b9b6-173">Pokud je volána metoda označená jako podmíněná, přítomnost nebo nepřítomnost zadaného symbolu předběžného zpracování určuje, zda je volání zahrnuto nebo vynecháno.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="6b9b6-174">Pokud je definován symbol, je zahrnuto volání; v opačném případě je volání vynecháno.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="6b9b6-175">Použití `Conditional` je čistší, elegantnější a méně náchylná k chybám `#if…#endif` alternativa k ohraničování metod uvnitř bloků, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="6b9b6-176">Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="6b9b6-177">Použití více identifikátorů</span><span class="sxs-lookup"><span data-stu-id="6b9b6-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="6b9b6-178">Pokud má metoda `Conditional` více atributů, je zahrnuto volání metody, pokud je definován alespoň jeden z podmíněných symbolů (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR).</span><span class="sxs-lookup"><span data-stu-id="6b9b6-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="6b9b6-179">V tomto příkladu přítomnost `A` `B` buď nebo bude mít za následek volání metody:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="6b9b6-180">Chcete-li dosáhnout efektu logického propojení symbolů pomocí operátoru AND, můžete definovat sériové podmíněné metody.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="6b9b6-181">Například druhá metoda níže bude spuštěna pouze v případě, že jsou definovány obě `A` a `B` jsou definovány:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="6b9b6-182">Použití podmíněného s třídami atributů</span><span class="sxs-lookup"><span data-stu-id="6b9b6-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="6b9b6-183">Atribut `Conditional` lze také použít na definici třídy atributu.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="6b9b6-184">V tomto příkladu `Documentation` bude vlastní atribut přidávat informace pouze do metadat, pokud je definováno LADĚNÍ.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
## <a name="CallerInfo"></a><span data-ttu-id="6b9b6-185">Atributy informací o volajícím</span><span class="sxs-lookup"><span data-stu-id="6b9b6-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="6b9b6-186">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="6b9b6-187">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a jméno člena volajícího.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="6b9b6-188">Chcete-li získat informace o volajícím člena, použijte atributy, které jsou použity pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="6b9b6-189">Každý volitelný parametr určuje výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="6b9b6-190">V následující tabulce jsou uvedeny atributy <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> Informace o volajícím, které jsou definovány v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="6b9b6-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="6b9b6-191">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b9b6-191">Attribute</span></span>|<span data-ttu-id="6b9b6-192">Popis</span><span class="sxs-lookup"><span data-stu-id="6b9b6-192">Description</span></span>|<span data-ttu-id="6b9b6-193">Typ</span><span class="sxs-lookup"><span data-stu-id="6b9b6-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="6b9b6-194">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="6b9b6-195">Toto je cesta v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="6b9b6-196">Číslo řádku ve zdrojovém souboru, ze kterého je metoda volána.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="6b9b6-197">Název metody nebo název vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="6b9b6-197">Method name or property name of the caller.</span></span> <span data-ttu-id="6b9b6-198">Další informace naleznete v [tématu Informace o volajícím (C#)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="6b9b6-198">For more information, see [Caller Information (C#)](../caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="6b9b6-199">Další informace o atributech Informace o volajícím naleznete v [tématu Informace o volajícím (C#).](../caller-information.md)</span><span class="sxs-lookup"><span data-stu-id="6b9b6-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9b6-200">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b9b6-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="6b9b6-201">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6b9b6-201">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="6b9b6-202">Atributy</span><span class="sxs-lookup"><span data-stu-id="6b9b6-202">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="6b9b6-203">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="6b9b6-203">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="6b9b6-204">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="6b9b6-204">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
