---
title: Běžné atributy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 58de23280f2e8765d945ac765d9455a89c45c9cb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642394"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="43c0a-102">Běžné atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43c0a-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="43c0a-103">Toto téma popisuje atributy, které se běžně používají v aplikacích jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43c0a-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
- [<span data-ttu-id="43c0a-104">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="43c0a-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="43c0a-105">Zastaralé atribut</span><span class="sxs-lookup"><span data-stu-id="43c0a-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="43c0a-106">Atribut Conditional.</span><span class="sxs-lookup"><span data-stu-id="43c0a-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="43c0a-107">Atributy informace o volajícím</span><span class="sxs-lookup"><span data-stu-id="43c0a-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
- [<span data-ttu-id="43c0a-108">Visual Basic – atributy</span><span class="sxs-lookup"><span data-stu-id="43c0a-108">Visual Basic Attributes</span></span>](#VB)  
  
## <a name="Global"></a> <span data-ttu-id="43c0a-109">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="43c0a-109">Global Attributes</span></span>  
 <span data-ttu-id="43c0a-110">Většina atributy se použijí na konkrétní jazykové prvky, jako jsou třídy nebo metody; Nicméně některé atributy jsou globální, se vztahují na celé sestavení nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="43c0a-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="43c0a-111">Například <xref:System.Reflection.AssemblyVersionAttribute> atribut lze použít k vložení informací o verzi do sestavení, například takto:</span><span class="sxs-lookup"><span data-stu-id="43c0a-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="43c0a-112">Globální atributy se zobrazí ve zdrojovém kódu po všech nejvyšší úrovně `Imports` příkazy a před všemi deklaracemi typu, modul nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="43c0a-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="43c0a-113">Globální atributy lze zobrazit ve více zdrojových souborech, ale soubory musí být zkompilovány při průchodu kompilace.</span><span class="sxs-lookup"><span data-stu-id="43c0a-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="43c0a-114">Pro projekty jazyka Visual Basic jsou globálními atributy obecně umístěny v souboru AssemblyInfo.vb (soubor se vytvoří automaticky při vytvoření projektu v sadě Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="43c0a-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="43c0a-115">Atributy sestavení jsou hodnoty, které obsahují informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="43c0a-116">Spadají do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="43c0a-116">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="43c0a-117">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="43c0a-117">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="43c0a-118">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="43c0a-118">Informational attributes</span></span>  
  
- <span data-ttu-id="43c0a-119">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="43c0a-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="43c0a-120">Atributy Identity sestavení</span><span class="sxs-lookup"><span data-stu-id="43c0a-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="43c0a-121">Tři atributy (se silným názvem, pokud je k dispozici) určují identitu sestavení: název, verzi a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="43c0a-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="43c0a-122">Tyto atributy tvoří úplný název sestavení, jsou povinné, když odkazujete v kódu.</span><span class="sxs-lookup"><span data-stu-id="43c0a-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="43c0a-123">Můžete nastavit verzi a jazykovou verzi pomocí atributů sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="43c0a-124">Je však nastavena hodnota názvu kompilátorem v sadě Visual Studio IDE [dialogové okno informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box), nebo Assembly Linker (Al.exe), když se vytvoří sestavení, na základě souboru, který obsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="43c0a-125"><xref:System.Reflection.AssemblyFlagsAttribute> Atribut určuje, zda mohou existovat vedle sebe více kopií daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="43c0a-126">V následující tabulce jsou uvedeny atributy identity.</span><span class="sxs-lookup"><span data-stu-id="43c0a-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="43c0a-127">Atribut</span><span class="sxs-lookup"><span data-stu-id="43c0a-127">Attribute</span></span>|<span data-ttu-id="43c0a-128">Účel</span><span class="sxs-lookup"><span data-stu-id="43c0a-128">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="43c0a-129">Plně popisuje identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-129">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="43c0a-130">Určuje verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-130">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="43c0a-131">Určuje, který jazyková verze sestavení podporuje.</span><span class="sxs-lookup"><span data-stu-id="43c0a-131">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="43c0a-132">Určuje, zda sestavení podporuje spuštění vedle sebe na stejném počítači, ve stejném procesu, nebo ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="43c0a-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="43c0a-133">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="43c0a-133">Informational Attributes</span></span>  
 <span data-ttu-id="43c0a-134">Informační atributy můžete zadat další společnosti nebo informace o produktu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="43c0a-135">V následující tabulce jsou uvedeny informační atributy definované ve <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="43c0a-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="43c0a-136">Atribut</span><span class="sxs-lookup"><span data-stu-id="43c0a-136">Attribute</span></span>|<span data-ttu-id="43c0a-137">Účel</span><span class="sxs-lookup"><span data-stu-id="43c0a-137">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="43c0a-138">Definuje vlastní atribut, který určuje název produktu pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="43c0a-139">Definuje vlastní atribut, který určuje ochranná známka pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="43c0a-140">Definuje vlastní atribut, který určuje informační verze pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="43c0a-141">Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="43c0a-142">Definuje vlastní atribut, který určuje copyright pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="43c0a-143">Instruuje kompilátor, aby používali konkrétní verzi pro prostředek verze souboru Win32.</span><span class="sxs-lookup"><span data-stu-id="43c0a-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="43c0a-144">Označuje, zda je sestavení kompatibilních s specifikace CLS (Common Language).</span><span class="sxs-lookup"><span data-stu-id="43c0a-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="43c0a-145">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="43c0a-145">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="43c0a-146">Atributy manifestu sestavení můžete použít k zadání informací v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="43c0a-147">Jedná se o název, popis, výchozí aliasu a konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="43c0a-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="43c0a-148">V následující tabulce jsou uvedeny atributy manifestu sestavení definované v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="43c0a-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="43c0a-149">Atribut</span><span class="sxs-lookup"><span data-stu-id="43c0a-149">Attribute</span></span>|<span data-ttu-id="43c0a-150">Účel</span><span class="sxs-lookup"><span data-stu-id="43c0a-150">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="43c0a-151">Definuje vlastní atribut, který určuje nadpisech sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="43c0a-152">Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="43c0a-153">Definuje vlastní atribut, který určuje konfiguraci služby sestavení (například prodejní nebo ladicí) pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="43c0a-154">Definuje výchozí popisný alias pro manifest sestavení</span><span class="sxs-lookup"><span data-stu-id="43c0a-154">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a> <span data-ttu-id="43c0a-155">Zastaralé atribut</span><span class="sxs-lookup"><span data-stu-id="43c0a-155">Obsolete Attribute</span></span>  
 <span data-ttu-id="43c0a-156">`Obsolete` Atribut určí program entity jako ten, který už se nedoporučuje používat.</span><span class="sxs-lookup"><span data-stu-id="43c0a-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="43c0a-157">Každé použití klíčového entity označený jako zastaralý. následně vygeneruje upozornění nebo chybu, v závislosti na konfiguraci atributu.</span><span class="sxs-lookup"><span data-stu-id="43c0a-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="43c0a-158">Příklad:</span><span class="sxs-lookup"><span data-stu-id="43c0a-158">For example:</span></span>  
  
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
  
 <span data-ttu-id="43c0a-159">V tomto příkladu `Obsolete` atribut aplikován na třídu `A` a metodě `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="43c0a-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="43c0a-160">Protože druhý argument konstruktoru atributu pro `B.OldMethod` je nastavena na `true`, tato metoda způsobí chybu kompilátoru, že horizontálních oddílů pomocí třídy `A` se jen vytvoří upozornění.</span><span class="sxs-lookup"><span data-stu-id="43c0a-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="43c0a-161">Volání `B.NewMethod`, ale vytváří žádná upozornění ani chyby.</span><span class="sxs-lookup"><span data-stu-id="43c0a-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="43c0a-162">Jako součást upozornění nebo chyby se zobrazí jako první argument pro konstruktor atributu v zadaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="43c0a-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="43c0a-163">Například když ji použijete s předchozí definice, následující kód vygeneruje dvě upozornění a jednu chybu:</span><span class="sxs-lookup"><span data-stu-id="43c0a-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="43c0a-164">Dvě upozornění pro třídu `A` jsou generovány: jeden pro deklaraci odkazech na třídy rozhraní a jeden pro konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="43c0a-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="43c0a-165">`Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení, proč položky je zastaralá a co se má použít místo toho se doporučuje.</span><span class="sxs-lookup"><span data-stu-id="43c0a-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="43c0a-166">`Obsolete` Atribut je jedno použití atributu a lze použít u Každá entita, která umožňuje atributy.</span><span class="sxs-lookup"><span data-stu-id="43c0a-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="43c0a-167">`Obsolete` je alias pro <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="43c0a-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a> <span data-ttu-id="43c0a-168">Atribut Conditional.</span><span class="sxs-lookup"><span data-stu-id="43c0a-168">Conditional Attribute</span></span>  
 <span data-ttu-id="43c0a-169">`Conditional` Atribut umožňuje provádění metody závislé na identifikátor předzpracování.</span><span class="sxs-lookup"><span data-stu-id="43c0a-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="43c0a-170">`Conditional` Atribut je alias pro <xref:System.Diagnostics.ConditionalAttribute>a můžete použít u metody nebo třídy atributu.</span><span class="sxs-lookup"><span data-stu-id="43c0a-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="43c0a-171">V tomto příkladu `Conditional` je použít pro metodu k povolení nebo zakázání zobrazování diagnostické informace specifické pro aplikace:</span><span class="sxs-lookup"><span data-stu-id="43c0a-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```vb  
#Const TRACE_ON = True  
Imports System  
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
  
 <span data-ttu-id="43c0a-172">Pokud `TRACE_ON` identifikátor není definován, nezobrazí se žádný výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="43c0a-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="43c0a-173">`Conditional` Atribut se často používá s `DEBUG` identifikátor povolit trasování a protokolování funkce pro ladění ale není ve verzi sestavení, tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="43c0a-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="43c0a-174">Při volání metody označené jako podmíněný přítomnosti nebo nepřítomnosti zadaného symbolu předzpracování Určuje, jestli je volání zahrnuté nebo vynechán.</span><span class="sxs-lookup"><span data-stu-id="43c0a-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="43c0a-175">Pokud je definován symbol, je součástí; volání v opačném případě je vynechána, volání.</span><span class="sxs-lookup"><span data-stu-id="43c0a-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="43c0a-176">Pomocí `Conditional` je čistější, více elegantnímu a méně náchylný alternativou k nadřazené metody uvnitř `#if…#endif` bloků, například takto:</span><span class="sxs-lookup"><span data-stu-id="43c0a-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="43c0a-177">Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="43c0a-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="43c0a-178">Použití více identifikátorů</span><span class="sxs-lookup"><span data-stu-id="43c0a-178">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="43c0a-179">Pokud metoda má více `Conditional` atributy, volání metody je zahrnuta, pokud je definován alespoň jeden z podmíněné symboly (jinými slovy, symboly jsou logicky spojeny operátorem OR).</span><span class="sxs-lookup"><span data-stu-id="43c0a-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="43c0a-180">V tomto příkladu přítomnost buď `A` nebo `B` bude výsledkem volání metody:</span><span class="sxs-lookup"><span data-stu-id="43c0a-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="43c0a-181">Pokud chcete dosáhnout logicky propojení symboly pomocí operátoru AND, můžete definovat sériového portu podmíněné metody.</span><span class="sxs-lookup"><span data-stu-id="43c0a-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="43c0a-182">Například níže druhá metoda spustí, pouze pokud mají oba `A` a `B` jsou definovány:</span><span class="sxs-lookup"><span data-stu-id="43c0a-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="43c0a-183">Podmíněné pomocí třídy atributů</span><span class="sxs-lookup"><span data-stu-id="43c0a-183">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="43c0a-184">`Conditional` Atribut lze použít také pro třídy definice atributu.</span><span class="sxs-lookup"><span data-stu-id="43c0a-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="43c0a-185">V tomto příkladu je vlastní atribut `Documentation` se přidat pouze informace metadat je definován DEBUG.</span><span class="sxs-lookup"><span data-stu-id="43c0a-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
## <a name="CallerInfo"></a> <span data-ttu-id="43c0a-186">Atributy informace o volajícím</span><span class="sxs-lookup"><span data-stu-id="43c0a-186">Caller Info Attributes</span></span>  
 <span data-ttu-id="43c0a-187">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="43c0a-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="43c0a-188">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a členské jméno volajícího.</span><span class="sxs-lookup"><span data-stu-id="43c0a-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="43c0a-189">Pokud chcete získat informace o subjektu volajícím člen, použijte atributy, které jsou použity na volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="43c0a-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="43c0a-190">Každý volitelný parametr určuje výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="43c0a-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="43c0a-191">V následující tabulce jsou uvedeny atributy informace o volajícím, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="43c0a-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="43c0a-192">Atribut</span><span class="sxs-lookup"><span data-stu-id="43c0a-192">Attribute</span></span>|<span data-ttu-id="43c0a-193">Popis</span><span class="sxs-lookup"><span data-stu-id="43c0a-193">Description</span></span>|<span data-ttu-id="43c0a-194">Type</span><span class="sxs-lookup"><span data-stu-id="43c0a-194">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="43c0a-195">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="43c0a-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="43c0a-196">Toto je cesta v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="43c0a-196">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="43c0a-197">Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="43c0a-197">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="43c0a-198">Název metody nebo názvu vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="43c0a-198">Method name or property name of the caller.</span></span> <span data-ttu-id="43c0a-199">Další informace najdete v tématu [informace o volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="43c0a-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="43c0a-200">Další informace o atributech informace o volajícím, naleznete v tématu [informace o volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="43c0a-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="VB"></a> <span data-ttu-id="43c0a-201">Visual Basic – atributy</span><span class="sxs-lookup"><span data-stu-id="43c0a-201">Visual Basic Attributes</span></span>  
 <span data-ttu-id="43c0a-202">V následující tabulce jsou uvedeny atributy, které jsou specifické pro Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43c0a-202">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="43c0a-203">Atribut</span><span class="sxs-lookup"><span data-stu-id="43c0a-203">Attribute</span></span>|<span data-ttu-id="43c0a-204">Účel</span><span class="sxs-lookup"><span data-stu-id="43c0a-204">Purpose</span></span>|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="43c0a-205">Označuje kompilátoru, že jako objekt modelu COM by měly být vystaveny třídy.</span><span class="sxs-lookup"><span data-stu-id="43c0a-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="43c0a-206">Umožňuje členům modulu přistupovat pomocí pouze kvalifikace potřebné pro modul.</span><span class="sxs-lookup"><span data-stu-id="43c0a-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="43c0a-207">Určuje velikost řetězce pevné délky struktury pro použití se souborem vstupu a výstupu funkcí.</span><span class="sxs-lookup"><span data-stu-id="43c0a-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="43c0a-208">Určuje velikost pole s pevnou struktury pro použití se souborem vstupu a výstupu funkcí.</span><span class="sxs-lookup"><span data-stu-id="43c0a-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="43c0a-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="43c0a-209">COMClassAttribute</span></span>  
 <span data-ttu-id="43c0a-210">Použití `COMClassAttribute` ke zjednodušení procesu vytváření komponent modelu COM z jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43c0a-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="43c0a-211">Objekty COM se výrazně liší od sestavení rozhraní .NET Framework a bez `COMClassAttribute`, musíte použít celou řadou kroků vygenerujete objekt modelu COM z jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43c0a-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="43c0a-212">Pro třídy označené `COMClassAttribute`, kompilátor provádí mnoho z těchto kroků automaticky.</span><span class="sxs-lookup"><span data-stu-id="43c0a-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="43c0a-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="43c0a-213">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="43c0a-214">Použití `HideModuleNameAttribute` umožníte členům modulu je přístupný pouze kvalifikace potřebné pro modul.</span><span class="sxs-lookup"><span data-stu-id="43c0a-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="43c0a-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="43c0a-215">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="43c0a-216">Použití `VBFixedStringAttribute` vynucení jazyka Visual Basic pro vytvoření řetězce pevné délky.</span><span class="sxs-lookup"><span data-stu-id="43c0a-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="43c0a-217">Jsou řetězce proměnné délky ve výchozím nastavení, a tento atribut je užitečné při ukládání řetězců do souborů.</span><span class="sxs-lookup"><span data-stu-id="43c0a-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="43c0a-218">Následující kód ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="43c0a-218">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="43c0a-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="43c0a-219">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="43c0a-220">Použití `VBFixedArrayAttribute` Chcete-li deklarovat pole, které mají pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="43c0a-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="43c0a-221">Podobně jako řetězce jazyka Visual Basic jsou pole s proměnnou délkou ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="43c0a-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="43c0a-222">Tento atribut je užitečné při serializaci nebo zápis dat do souborů.</span><span class="sxs-lookup"><span data-stu-id="43c0a-222">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c0a-223">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43c0a-223">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="43c0a-224">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43c0a-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="43c0a-225">Atributy</span><span class="sxs-lookup"><span data-stu-id="43c0a-225">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="43c0a-226">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43c0a-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="43c0a-227">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43c0a-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
