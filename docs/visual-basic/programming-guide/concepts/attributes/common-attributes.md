---
title: Mezi běžné atributy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 5a91b0aa48a22db4ea7fb56a9c632ff0cb44dce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644157"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="e4ce1-102">Mezi běžné atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4ce1-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="e4ce1-103">Toto téma popisuje atributy, které se běžně používají v aplikacích jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="e4ce1-104">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="e4ce1-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="e4ce1-105">Zastaralé atribut</span><span class="sxs-lookup"><span data-stu-id="e4ce1-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="e4ce1-106">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="e4ce1-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="e4ce1-107">Volající – atributy s informacemi</span><span class="sxs-lookup"><span data-stu-id="e4ce1-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="e4ce1-108">Visual Basic – atributy</span><span class="sxs-lookup"><span data-stu-id="e4ce1-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <a name="Global"></a> <span data-ttu-id="e4ce1-109">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="e4ce1-109">Global Attributes</span></span>  
 <span data-ttu-id="e4ce1-110">Většina atributy platí pro konkrétní jazyk prvky, jako jsou například třídy nebo metody; ale některé atributy jsou globální – se vztahují na modul nebo celý sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="e4ce1-111">Například <xref:System.Reflection.AssemblyVersionAttribute> atribut slouží k vložení informací o verzi do sestavení, například takto:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="e4ce1-112">Globální atributy se zobrazí ve zdrojovém kódu po všech nejvyšší úrovně `Imports` příkazy a před všechny deklarace typu, modul nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="e4ce1-113">Globální atributy lze zobrazit v několika zdrojových souborů, ale soubory musí být zkompilovány při průchodu kompilace.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="e4ce1-114">Pro projekty Visual Basic jsou obecně globálními atributy uveďte v souboru AssemblyInfo.vb (soubor se vytvoří automaticky při vytvoření projektu v sadě Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="e4ce1-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="e4ce1-115">Atributů sestavení jsou hodnoty, které obsahují informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="e4ce1-116">Spadají do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="e4ce1-117">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="e4ce1-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="e4ce1-118">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="e4ce1-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="e4ce1-119">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="e4ce1-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="e4ce1-120">Atributy Identity sestavení</span><span class="sxs-lookup"><span data-stu-id="e4ce1-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="e4ce1-121">Zjistit identitu sestavení tři atributy (se silným názvem, pokud je k dispozici): název, verzi a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="e4ce1-122">Tyto atributy tvoří úplný název sestavení a jsou povinné, pokud odkazujete v kódu.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="e4ce1-123">Můžete nastavit verze a jazykové verze pomocí atributů sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="e4ce1-124">Hodnota názvu je ale nastavená kompilátorem prostředí Visual Studio IDE v [dialogové okno informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box), nebo na soubor, který obsahuje manifest sestavení na základě Linker sestavení (Al.exe) při vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="e4ce1-125"><xref:System.Reflection.AssemblyFlagsAttribute> Atribut určuje, zda více kopií sestavení mohou existovat vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="e4ce1-126">V následující tabulce jsou uvedeny atributy identity.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="e4ce1-127">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4ce1-127">Attribute</span></span>|<span data-ttu-id="e4ce1-128">Účel</span><span class="sxs-lookup"><span data-stu-id="e4ce1-128">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="e4ce1-129">Popisuje plně identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-129">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="e4ce1-130">Určuje verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-130">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="e4ce1-131">Určuje, které jazykovou verzi sestavení podporuje.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-131">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="e4ce1-132">Určuje, zda sestavení podporuje spuštění vedle sebe na stejném počítači, v rámci jednoho procesu, nebo ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="e4ce1-133">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="e4ce1-133">Informational Attributes</span></span>  
 <span data-ttu-id="e4ce1-134">Informační atributy můžete zadat další společnosti nebo informace o produktu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="e4ce1-135">V následující tabulce jsou definované v informační atributy <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="e4ce1-136">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4ce1-136">Attribute</span></span>|<span data-ttu-id="e4ce1-137">Účel</span><span class="sxs-lookup"><span data-stu-id="e4ce1-137">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="e4ce1-138">Definuje vlastní atribut, který určuje název produktu manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="e4ce1-139">Definuje vlastní atribut, který určuje ochrannou známku pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="e4ce1-140">Definuje vlastní atribut, který určuje informační verze pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="e4ce1-141">Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="e4ce1-142">Definuje vlastní atribut, který určuje copyright pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="e4ce1-143">Dá pokyn kompilátoru použít konkrétní verzi číslo pro prostředek verze souboru Win32.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="e4ce1-144">Určuje, zda je sestavení kompatibilní s specifikace CLS (Common Language).</span><span class="sxs-lookup"><span data-stu-id="e4ce1-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="e4ce1-145">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="e4ce1-145">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="e4ce1-146">Atributy manifestu sestavení můžete použít k poskytování informací v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="e4ce1-147">To zahrnuje název, popis, výchozí alias a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="e4ce1-148">V následující tabulce jsou definované atributy manifestu sestavení v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="e4ce1-149">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4ce1-149">Attribute</span></span>|<span data-ttu-id="e4ce1-150">Účel</span><span class="sxs-lookup"><span data-stu-id="e4ce1-150">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="e4ce1-151">Definuje vlastní atribut, který určuje název sestavení manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="e4ce1-152">Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="e4ce1-153">Manifest sestavení definuje vlastní atribut, který určuje konfigurace aplikace sestavení (například instalačních nebo ladicích).</span><span class="sxs-lookup"><span data-stu-id="e4ce1-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="e4ce1-154">Definuje výchozí popisný aliasu pro manifest sestavení</span><span class="sxs-lookup"><span data-stu-id="e4ce1-154">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a> <span data-ttu-id="e4ce1-155">Zastaralé atribut</span><span class="sxs-lookup"><span data-stu-id="e4ce1-155">Obsolete Attribute</span></span>  
 <span data-ttu-id="e4ce1-156">`Obsolete` Atribut určí program entity jako ten, který již není doporučeno pro použití.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="e4ce1-157">Každý použijte entity označeny jako zastaralé následně vydá upozornění nebo chybu, v závislosti na konfiguraci atributu.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="e4ce1-158">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-158">For example:</span></span>  
  
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
  
 <span data-ttu-id="e4ce1-159">V tomto příkladu `Obsolete` atribut se používá pro třídu `A` a metoda `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="e4ce1-160">Protože druhý argument konstruktoru atributu aplikovat `B.OldMethod` je nastaven na `true`, tato metoda způsobí chybu kompilátoru, zatímco použití třídy `A` bude jenom produktu upozornění.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="e4ce1-161">Volání metody `B.NewMethod`, ale vytváří žádná upozornění ani chyby.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="e4ce1-162">Daný řetězec jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="e4ce1-163">Například pokud ji používáte s předchozí definice, generuje následující kód, dvě upozornění a jednu chybu:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="e4ce1-164">Dva upozornění pro třídu `A` jsou generovány: jeden pro deklaraci referenci třídy a jeden pro konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="e4ce1-165">`Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení důvod, proč je zastaralé položky a doporučuje se co místo toho chcete použít.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="e4ce1-166">`Obsolete` Atribut je jedno použití atribut a dají se použít k Každá entita, která umožňuje atributy.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="e4ce1-167">`Obsolete` je alias <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a> <span data-ttu-id="e4ce1-168">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="e4ce1-168">Conditional Attribute</span></span>  
 <span data-ttu-id="e4ce1-169">`Conditional` Atribut umožňuje provádění metody závisí na identifikátor předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="e4ce1-170">`Conditional` Atribut je alias <xref:System.Diagnostics.ConditionalAttribute>a dají se použít metody nebo třídy atributu.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="e4ce1-171">V tomto příkladu `Conditional` je použitý na metodu, pokud chcete povolit nebo zakázat zobrazení diagnostické informace specifické pro aplikace:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="e4ce1-172">Pokud `TRACE_ON` identifikátor není definován, nezobrazí se žádný výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="e4ce1-173">`Conditional` Atribut se často používá u `DEBUG` identifikátor povolení trasování a protokolování funkce pro ladění ale není ve verzi sestavení, jako jsou to:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="e4ce1-174">Při volání metody označené jako podmíněného existenci nebo neexistenci těchto zadaný symbol předběžného zpracování určuje, zda je volání zahrnuty nebo tento parametr vynechán.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="e4ce1-175">Pokud je definována symbol, volání je zahrnuté; volání, jinak je vynechán.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="e4ce1-176">Pomocí `Conditional` je je automaticky více elegantní a méně náchylný alternativa k uzavření metody uvnitř `#if…#endif` bloků, například takto:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="e4ce1-177">Podmíněné metoda musí být metody ve třídě nebo struktuře prohlášení a nesmí mít návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="e4ce1-178">Použití více identifikátorů</span><span class="sxs-lookup"><span data-stu-id="e4ce1-178">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="e4ce1-179">Pokud metoda obsahuje více `Conditional` atributy, volání do metody je zahrnuta, pokud je definována alespoň jeden z podmíněného symboly (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR).</span><span class="sxs-lookup"><span data-stu-id="e4ce1-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="e4ce1-180">V tomto příkladu přítomnost buď `A` nebo `B` bude výsledkem volání metody:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="e4ce1-181">K dosažení účinku logicky propojení symboly pomocí operátoru AND, můžete definovat sériové podmíněného metody.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="e4ce1-182">Například druhé metody níže spustí, pouze pokud obě `A` a `B` jsou definovány:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="e4ce1-183">Pomocí podmíněného třídy atributů</span><span class="sxs-lookup"><span data-stu-id="e4ce1-183">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="e4ce1-184">`Conditional` Atribut lze použít také k – třída definice atributu.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="e4ce1-185">V tomto příkladu vlastní atribut `Documentation` pouze přidá informace k metadatům Pokud je definována ladění.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
##  <a name="CallerInfo"></a> <span data-ttu-id="e4ce1-186">Volající – atributy s informacemi</span><span class="sxs-lookup"><span data-stu-id="e4ce1-186">Caller Info Attributes</span></span>  
 <span data-ttu-id="e4ce1-187">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="e4ce1-188">Můžete získat cestu k souboru zdrojového kódu, číslo řádku v zdrojový kód a název člena volajícího.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="e4ce1-189">Chcete-li získat informace o subjektu volajícím člen, použijte atributy, které se použijí pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="e4ce1-190">Každý volitelný parametr určí výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="e4ce1-191">Následující tabulka uvádí informace o volajícím atributy, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="e4ce1-192">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4ce1-192">Attribute</span></span>|<span data-ttu-id="e4ce1-193">Popis</span><span class="sxs-lookup"><span data-stu-id="e4ce1-193">Description</span></span>|<span data-ttu-id="e4ce1-194">Typ</span><span class="sxs-lookup"><span data-stu-id="e4ce1-194">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="e4ce1-195">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="e4ce1-196">Je to cesta ke v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-196">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="e4ce1-197">Číslo řádku v souboru zdroj, ze kterého je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-197">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="e4ce1-198">Název metody nebo vlastnosti název volajícího.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-198">Method name or property name of the caller.</span></span> <span data-ttu-id="e4ce1-199">Další informace najdete v tématu [informace o subjektu volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="e4ce1-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="e4ce1-200">Další informace o atributech volající informace najdete v tématu [informace o subjektu volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="e4ce1-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <a name="VB"></a> <span data-ttu-id="e4ce1-201">Visual Basic – atributy</span><span class="sxs-lookup"><span data-stu-id="e4ce1-201">Visual Basic Attributes</span></span>  
 <span data-ttu-id="e4ce1-202">Následující tabulka obsahuje seznam atributy, které jsou specifické pro Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-202">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="e4ce1-203">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4ce1-203">Attribute</span></span>|<span data-ttu-id="e4ce1-204">Účel</span><span class="sxs-lookup"><span data-stu-id="e4ce1-204">Purpose</span></span>|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="e4ce1-205">Kompilátoru označuje, že jako objekt modelu COM by měly být vystaveny třídy.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="e4ce1-206">Umožňuje členům modul přístup k použití pouze kvalifikace potřebné pro modul.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="e4ce1-207">Určuje velikost řetězce pevné délky souborem vstup a výstup do struktury pro použití funkce.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="e4ce1-208">Určuje velikost pevné pole do struktury pro použití s souboru vstup a výstup funkce.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="e4ce1-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="e4ce1-209">COMClassAttribute</span></span>  
 <span data-ttu-id="e4ce1-210">Použití `COMClassAttribute` zjednodušit proces vytváření komponenty modelu COM z jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="e4ce1-211">COM – objekty se podstatně liší od sestavení rozhraní .NET Framework a bez `COMClassAttribute`, je třeba provést několik kroků pro generování objektu COM z jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="e4ce1-212">Pro třídy označené jako `COMClassAttribute`, kompilátor nabízí mnoho z těchto kroků automaticky.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="e4ce1-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="e4ce1-213">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="e4ce1-214">Použití `HideModuleNameAttribute` umožníte členům modulu nelze přistupovat pomocí pouze kvalifikace potřebné pro modul.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="e4ce1-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="e4ce1-215">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="e4ce1-216">Použití `VBFixedStringAttribute` vynutit jazyka Visual Basic pro vytvoření řetězce pevné délky.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="e4ce1-217">S proměnnou délkou ve výchozím nastavení jsou řetězce, a tento atribut je užitečné, když ukládání řetězců do souborů.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="e4ce1-218">Následující kód ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="e4ce1-218">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="e4ce1-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="e4ce1-219">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="e4ce1-220">Použití `VBFixedArrayAttribute` deklarovat pole, které mají pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="e4ce1-221">Pole jsou stejně jako Visual Basic – řetězce, s proměnnou délkou ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="e4ce1-222">Tento atribut je užitečný při serializaci nebo zápis dat do souborů.</span><span class="sxs-lookup"><span data-stu-id="e4ce1-222">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ce1-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4ce1-223">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="e4ce1-224">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e4ce1-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="e4ce1-225">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4ce1-225">Attributes</span></span>](../../../../standard/attributes/index.md)  
 [<span data-ttu-id="e4ce1-226">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4ce1-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="e4ce1-227">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4ce1-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
