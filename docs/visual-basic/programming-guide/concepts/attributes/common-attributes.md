---
title: Běžné atributy
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 57ef8f103d64a51d896f46d2889d78ec99ff3223
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400716"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="1cf18-102">Společné atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cf18-102">Common Attributes (Visual Basic)</span></span>

<span data-ttu-id="1cf18-103">Toto téma popisuje atributy, které se nejčastěji používají v Visual Basicch programech.</span><span class="sxs-lookup"><span data-stu-id="1cf18-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>

- [<span data-ttu-id="1cf18-104">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="1cf18-104">Global Attributes</span></span>](#Global)

- [<span data-ttu-id="1cf18-105">Zastaralý atribut</span><span class="sxs-lookup"><span data-stu-id="1cf18-105">Obsolete Attribute</span></span>](#Obsolete)

- [<span data-ttu-id="1cf18-106">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="1cf18-106">Conditional Attribute</span></span>](#Conditional)

- [<span data-ttu-id="1cf18-107">Atributy informací o volajícím</span><span class="sxs-lookup"><span data-stu-id="1cf18-107">Caller Info Attributes</span></span>](#CallerInfo)

- [<span data-ttu-id="1cf18-108">Atributy Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cf18-108">Visual Basic Attributes</span></span>](#VB)

## <a name="global-attributes"></a><a name="Global"></a><span data-ttu-id="1cf18-109">Globální atributy</span><span class="sxs-lookup"><span data-stu-id="1cf18-109">Global Attributes</span></span>

<span data-ttu-id="1cf18-110">Většina atributů je aplikována na konkrétní prvky jazyka, jako jsou třídy nebo metody. Některé atributy jsou však globální – platí pro celé sestavení nebo modul.</span><span class="sxs-lookup"><span data-stu-id="1cf18-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="1cf18-111">Například <xref:System.Reflection.AssemblyVersionAttribute> atribut lze použít k vložení informací o verzi do sestavení, jako je:</span><span class="sxs-lookup"><span data-stu-id="1cf18-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

<span data-ttu-id="1cf18-112">Globální atributy se zobrazí ve zdrojovém kódu po všech `Imports` příkazech nejvyšší úrovně a před všemi deklaracemi typu, modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1cf18-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="1cf18-113">Globální atributy se mohou objevit ve více zdrojových souborech, ale soubory musí být kompilovány v rámci jedné kompilační fáze.</span><span class="sxs-lookup"><span data-stu-id="1cf18-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="1cf18-114">U Visual Basic projektů jsou globální atributy obecně vloženy do souboru AssemblyInfo. vb (soubor je vytvořen automaticky při vytvoření projektu v aplikaci Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="1cf18-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>

<span data-ttu-id="1cf18-115">Atributy sestavení jsou hodnoty, které poskytují informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="1cf18-116">Spadají do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="1cf18-116">They fall into the following categories:</span></span>

- <span data-ttu-id="1cf18-117">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="1cf18-117">Assembly identity attributes</span></span>

- <span data-ttu-id="1cf18-118">Informativní atributy</span><span class="sxs-lookup"><span data-stu-id="1cf18-118">Informational attributes</span></span>

- <span data-ttu-id="1cf18-119">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="1cf18-119">Assembly manifest attributes</span></span>

### <a name="assembly-identity-attributes"></a><span data-ttu-id="1cf18-120">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="1cf18-120">Assembly Identity Attributes</span></span>

<span data-ttu-id="1cf18-121">Tři atributy (se silným názvem, pokud jsou k dispozici) určují identitu sestavení: název, verze a jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="1cf18-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="1cf18-122">Tyto atributy tvoří úplný název sestavení a jsou vyžadovány při odkazování v kódu.</span><span class="sxs-lookup"><span data-stu-id="1cf18-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="1cf18-123">Můžete nastavit verzi a jazykovou verzi sestavení pomocí atributů.</span><span class="sxs-lookup"><span data-stu-id="1cf18-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="1cf18-124">Hodnota name je však nastavena kompilátorem, rozhraním IDE sady Visual Studio v [dialogovém okně informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box)nebo linker sestavení (Al. exe), když je sestavení vytvořeno, na základě souboru, který obsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="1cf18-125"><xref:System.Reflection.AssemblyFlagsAttribute>Atribut určuje, zda více kopií sestavení může existovat současně.</span><span class="sxs-lookup"><span data-stu-id="1cf18-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="1cf18-126">V následující tabulce jsou uvedeny atributy identity.</span><span class="sxs-lookup"><span data-stu-id="1cf18-126">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="1cf18-127">Atribut</span><span class="sxs-lookup"><span data-stu-id="1cf18-127">Attribute</span></span>|<span data-ttu-id="1cf18-128">Účel</span><span class="sxs-lookup"><span data-stu-id="1cf18-128">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="1cf18-129">Plně popisuje identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-129">Fully describes the identity of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="1cf18-130">Určuje verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-130">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="1cf18-131">Určuje jazykovou verzi, kterou sestavení podporuje.</span><span class="sxs-lookup"><span data-stu-id="1cf18-131">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="1cf18-132">Určuje, zda sestavení podporuje souběžné spouštění ve stejném počítači, ve stejném procesu nebo ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cf18-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

### <a name="informational-attributes"></a><span data-ttu-id="1cf18-133">Informativní atributy</span><span class="sxs-lookup"><span data-stu-id="1cf18-133">Informational Attributes</span></span>

<span data-ttu-id="1cf18-134">Pomocí informativních atributů lze poskytnout další informace o společnosti nebo produktu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="1cf18-135">V následující tabulce jsou uvedeny informativní atributy definované v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1cf18-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="1cf18-136">Atribut</span><span class="sxs-lookup"><span data-stu-id="1cf18-136">Attribute</span></span>|<span data-ttu-id="1cf18-137">Účel</span><span class="sxs-lookup"><span data-stu-id="1cf18-137">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="1cf18-138">Definuje vlastní atribut, který určuje název produktu pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="1cf18-139">Definuje vlastní atribut, který určuje ochrannou známku pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="1cf18-140">Definuje vlastní atribut, který určuje informační verzi manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="1cf18-141">Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="1cf18-142">Definuje vlastní atribut, který určuje autorská práva pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="1cf18-143">Instruuje kompilátor, aby pro prostředek verze souboru Win32 použil konkrétní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="1cf18-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="1cf18-144">Určuje, zda je sestavení kompatibilní se specifikací CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="1cf18-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

### <a name="assembly-manifest-attributes"></a><span data-ttu-id="1cf18-145">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="1cf18-145">Assembly Manifest Attributes</span></span>

<span data-ttu-id="1cf18-146">Atributy manifestu sestavení lze použít k poskytnutí informací v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="1cf18-147">Patří sem název, popis, výchozí alias a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1cf18-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="1cf18-148">V následující tabulce jsou uvedeny atributy manifestu sestavení definované v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1cf18-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="1cf18-149">Atribut</span><span class="sxs-lookup"><span data-stu-id="1cf18-149">Attribute</span></span>|<span data-ttu-id="1cf18-150">Účel</span><span class="sxs-lookup"><span data-stu-id="1cf18-150">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="1cf18-151">Definuje vlastní atribut, který určuje název sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="1cf18-152">Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="1cf18-153">Definuje vlastní atribut, který určuje konfiguraci sestavení (například maloobchodní nebo ladicí) pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="1cf18-154">Definuje popisný výchozí alias pro manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cf18-154">Defines a friendly default alias for an assembly manifest</span></span>|

## <a name="obsolete-attribute"></a><a name="Obsolete"></a><span data-ttu-id="1cf18-155">Zastaralý atribut</span><span class="sxs-lookup"><span data-stu-id="1cf18-155">Obsolete Attribute</span></span>

<span data-ttu-id="1cf18-156">`Obsolete`Atribut označuje entitu programu jako tu, která se už nedoporučuje používat.</span><span class="sxs-lookup"><span data-stu-id="1cf18-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="1cf18-157">Každé použití entity označené jako zastaralé bude následně generovat upozornění nebo chybu v závislosti na tom, jak je atribut nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="1cf18-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="1cf18-158">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1cf18-158">For example:</span></span>

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

<span data-ttu-id="1cf18-159">V tomto příkladu `Obsolete` je atribut použit pro třídu `A` a na metodu `B.OldMethod` .</span><span class="sxs-lookup"><span data-stu-id="1cf18-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="1cf18-160">Vzhledem k tomu, že druhý argument konstruktoru atributu použité pro `B.OldMethod` je nastaven na `true` , tato metoda způsobí chybu kompilátoru, zatímco použití třídy `A` bude pouze generovat upozornění.</span><span class="sxs-lookup"><span data-stu-id="1cf18-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="1cf18-161">Volání `B.NewMethod` však negeneruje žádné upozornění nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="1cf18-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>

<span data-ttu-id="1cf18-162">Řetězec poskytnutý jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="1cf18-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="1cf18-163">Například když použijete s předchozími definicemi, následující kód vygeneruje dvě upozornění a jednu chybu:</span><span class="sxs-lookup"><span data-stu-id="1cf18-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

<span data-ttu-id="1cf18-164">Dvě upozornění pro třídu `A` jsou vygenerována: jedna pro deklaraci odkazu na třídu a druhá pro konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="1cf18-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>

<span data-ttu-id="1cf18-165">`Obsolete`Atribut lze použít bez argumentů, ale včetně vysvětlení, proč je položka zastaralá a co použít místo toho se doporučuje.</span><span class="sxs-lookup"><span data-stu-id="1cf18-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>

<span data-ttu-id="1cf18-166">`Obsolete`Atribut je atribut s jedním použitím a lze jej použít pro libovolnou entitu, která povoluje atributy.</span><span class="sxs-lookup"><span data-stu-id="1cf18-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="1cf18-167">`Obsolete`je alias pro <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1cf18-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

## <a name="conditional-attribute"></a><a name="Conditional"></a><span data-ttu-id="1cf18-168">Podmíněný atribut</span><span class="sxs-lookup"><span data-stu-id="1cf18-168">Conditional Attribute</span></span>

<span data-ttu-id="1cf18-169">`Conditional`Atribut provádí provádění metody závislé na identifikátoru předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="1cf18-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="1cf18-170">`Conditional`Atribut je alias pro <xref:System.Diagnostics.ConditionalAttribute> a lze jej použít pro metodu nebo třídu atributu.</span><span class="sxs-lookup"><span data-stu-id="1cf18-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="1cf18-171">V tomto příkladu `Conditional` se použije na metodu, která povolí nebo zakáže zobrazení diagnostických informací specifických pro program:</span><span class="sxs-lookup"><span data-stu-id="1cf18-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

```vb
#Const TRACE_ON = True
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

<span data-ttu-id="1cf18-172">Pokud `TRACE_ON` identifikátor není definován, nebude zobrazen žádný výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="1cf18-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>

<span data-ttu-id="1cf18-173">`Conditional`Atribut se často používá s `DEBUG` identifikátorem pro povolení funkcí trasování a protokolování pro sestavení ladění, ale ne v sestaveních vydaných verzí, jako je:</span><span class="sxs-lookup"><span data-stu-id="1cf18-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

<span data-ttu-id="1cf18-174">Když je volána metoda označená jako podmíněná, přítomnost nebo absence zadaného symbolu předzpracování určuje, zda je volání zahrnuto nebo vynecháno.</span><span class="sxs-lookup"><span data-stu-id="1cf18-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="1cf18-175">Pokud je symbol definován, volání je zahrnuto; v opačném případě je volání vynecháno.</span><span class="sxs-lookup"><span data-stu-id="1cf18-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="1cf18-176">Použití `Conditional` je čisticí, jasnější a méně náchylné k chybám, které lze použít jako alternativu k uzavření metod uvnitř `#if…#endif` bloků, například:</span><span class="sxs-lookup"><span data-stu-id="1cf18-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

<span data-ttu-id="1cf18-177">Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1cf18-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>

### <a name="using-multiple-identifiers"></a><span data-ttu-id="1cf18-178">Použití více identifikátorů</span><span class="sxs-lookup"><span data-stu-id="1cf18-178">Using Multiple Identifiers</span></span>

<span data-ttu-id="1cf18-179">Pokud má metoda více `Conditional` atributů, volání metody je zahrnuto, pokud je definován alespoň jeden z podmíněných symbolů (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR).</span><span class="sxs-lookup"><span data-stu-id="1cf18-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="1cf18-180">V tomto příkladu přítomnost buď `A` nebo, `B` způsobí volání metody:</span><span class="sxs-lookup"><span data-stu-id="1cf18-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

<span data-ttu-id="1cf18-181">Chcete-li dosáhnout vlivu logického propojení symbolů pomocí operátoru AND, můžete definovat sériové podmíněné metody.</span><span class="sxs-lookup"><span data-stu-id="1cf18-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="1cf18-182">Například druhá metoda níže se spustí pouze v případě `A` , že `B` jsou definovány obě i:</span><span class="sxs-lookup"><span data-stu-id="1cf18-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>

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

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="1cf18-183">Použití podmíněné s třídami atributů</span><span class="sxs-lookup"><span data-stu-id="1cf18-183">Using Conditional with Attribute Classes</span></span>

<span data-ttu-id="1cf18-184">`Conditional`Atribut lze použít také pro definici třídy atributu.</span><span class="sxs-lookup"><span data-stu-id="1cf18-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="1cf18-185">V tomto příkladu vlastní atribut `Documentation` přidá informace do metadat pouze v případě, že je definován ladění.</span><span class="sxs-lookup"><span data-stu-id="1cf18-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>

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

## <a name="caller-info-attributes"></a><a name="CallerInfo"></a><span data-ttu-id="1cf18-186">Atributy informací o volajícím</span><span class="sxs-lookup"><span data-stu-id="1cf18-186">Caller Info Attributes</span></span>

<span data-ttu-id="1cf18-187">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="1cf18-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="1cf18-188">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.</span><span class="sxs-lookup"><span data-stu-id="1cf18-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>

<span data-ttu-id="1cf18-189">Chcete-li získat informace o volajícím členu, použijte atributy, které se použijí na volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="1cf18-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="1cf18-190">Každý volitelný parametr určuje výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1cf18-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="1cf18-191">V následující tabulce jsou uvedeny atributy informací o volajícím, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="1cf18-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="1cf18-192">Atribut</span><span class="sxs-lookup"><span data-stu-id="1cf18-192">Attribute</span></span>|<span data-ttu-id="1cf18-193">Description</span><span class="sxs-lookup"><span data-stu-id="1cf18-193">Description</span></span>|<span data-ttu-id="1cf18-194">Typ</span><span class="sxs-lookup"><span data-stu-id="1cf18-194">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="1cf18-195">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="1cf18-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="1cf18-196">Toto je cesta v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="1cf18-196">This is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="1cf18-197">Číslo řádku ve zdrojovém souboru, ze kterého je metoda volána.</span><span class="sxs-lookup"><span data-stu-id="1cf18-197">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="1cf18-198">Název metody nebo název vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="1cf18-198">Method name or property name of the caller.</span></span> <span data-ttu-id="1cf18-199">Další informace najdete v tématu [informace o volajícím (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="1cf18-199">For more information, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>|`String`|

<span data-ttu-id="1cf18-200">Další informace o atributech informace o volajícím naleznete v tématu [informace o volajícím (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="1cf18-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>

## <a name="visual-basic-attributes"></a><a name="VB"></a><span data-ttu-id="1cf18-201">Atributy Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cf18-201">Visual Basic Attributes</span></span>

<span data-ttu-id="1cf18-202">V následující tabulce jsou uvedeny atributy, které jsou specifické pro Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cf18-202">The following table lists the attributes that are specific to Visual Basic.</span></span>

|<span data-ttu-id="1cf18-203">Atribut</span><span class="sxs-lookup"><span data-stu-id="1cf18-203">Attribute</span></span>|<span data-ttu-id="1cf18-204">Účel</span><span class="sxs-lookup"><span data-stu-id="1cf18-204">Purpose</span></span>|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="1cf18-205">Určuje kompilátoru, že by měla být třída vystavena jako objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="1cf18-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="1cf18-206">Umožňuje, aby byly členy modulu dostupné pouze pomocí kvalifikace potřebné pro modul.</span><span class="sxs-lookup"><span data-stu-id="1cf18-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="1cf18-207">Určuje velikost řetězce s pevnou délkou ve struktuře pro použití s funkcemi vstupu a výstupu souboru.</span><span class="sxs-lookup"><span data-stu-id="1cf18-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="1cf18-208">Určuje velikost fixního pole ve struktuře pro použití s funkcemi vstupu a výstupu souboru.</span><span class="sxs-lookup"><span data-stu-id="1cf18-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|

### <a name="comclassattribute"></a><span data-ttu-id="1cf18-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="1cf18-209">COMClassAttribute</span></span>

<span data-ttu-id="1cf18-210">Slouží `COMClassAttribute` ke zjednodušení procesu vytváření komponent modelu COM z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cf18-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="1cf18-211">Objekty modelu COM se výrazně liší od .NET Framework sestavení a bez nutnosti použít `COMClassAttribute` k vygenerování objektu COM z Visual Basic několik kroků.</span><span class="sxs-lookup"><span data-stu-id="1cf18-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="1cf18-212">Pro třídy označené pomocí `COMClassAttribute` kompilátor provede mnoho z těchto kroků automaticky.</span><span class="sxs-lookup"><span data-stu-id="1cf18-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>

### <a name="hidemodulenameattribute"></a><span data-ttu-id="1cf18-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="1cf18-213">HideModuleNameAttribute</span></span>

<span data-ttu-id="1cf18-214">Slouží `HideModuleNameAttribute` k povolení, aby členové modulu měli k dispozici pouze kvalifikaci potřebnou pro modul.</span><span class="sxs-lookup"><span data-stu-id="1cf18-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>

### <a name="vbfixedstringattribute"></a><span data-ttu-id="1cf18-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="1cf18-215">VBFixedStringAttribute</span></span>

<span data-ttu-id="1cf18-216">Použijte `VBFixedStringAttribute` k vynucení Visual Basic vytvoření řetězce s pevnou délkou.</span><span class="sxs-lookup"><span data-stu-id="1cf18-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="1cf18-217">Řetězce mají ve výchozím nastavení proměnlivou délku a tento atribut je užitečný při ukládání řetězců do souborů.</span><span class="sxs-lookup"><span data-stu-id="1cf18-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="1cf18-218">Následující kód demonstruje:</span><span class="sxs-lookup"><span data-stu-id="1cf18-218">The following code demonstrates this:</span></span>

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a><span data-ttu-id="1cf18-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="1cf18-219">VBFixedArrayAttribute</span></span>

<span data-ttu-id="1cf18-220">Použijte `VBFixedArrayAttribute` k deklaraci polí, která mají pevně danou velikost.</span><span class="sxs-lookup"><span data-stu-id="1cf18-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="1cf18-221">Stejně jako řetězce Visual Basic, pole mají ve výchozím nastavení proměnlivou délku.</span><span class="sxs-lookup"><span data-stu-id="1cf18-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="1cf18-222">Tento atribut je užitečný při serializaci nebo zápisu dat do souborů.</span><span class="sxs-lookup"><span data-stu-id="1cf18-222">This attribute is useful when serializing or writing data to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cf18-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cf18-223">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="1cf18-224">Příručka k programování v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cf18-224">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="1cf18-225">Atributy</span><span class="sxs-lookup"><span data-stu-id="1cf18-225">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="1cf18-226">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cf18-226">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="1cf18-227">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cf18-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
