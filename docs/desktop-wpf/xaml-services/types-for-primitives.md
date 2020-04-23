---
title: Předdefinované typy obecných primitiv jazyka XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: 3bd486ee66c5f9a32621416638bb7575025f7dee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071834"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="e556e-102">Předdefinované typy pro běžné jazykové primitivy XAML</span><span class="sxs-lookup"><span data-stu-id="e556e-102">Built-in types for common XAML language primitives</span></span>

<span data-ttu-id="e556e-103">XAML 2009 zavádí podporu na jazykové úrovni XAML pro několik datových typů, které se často používají primitiva v cltime společného jazyka (CLR) a v jiných programovacích jazycích.</span><span class="sxs-lookup"><span data-stu-id="e556e-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="e556e-104">XAML 2009 přidává podporu pro `x:Object` `x:Boolean`tyto `x:Char` `x:String`primitiva: , , , `x:Decimal` `x:Single` `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, , a`x:Array`</span><span class="sxs-lookup"><span data-stu-id="e556e-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="e556e-105">Předchozí techniky pro jazykové primitivy v přeznačce XAML</span><span class="sxs-lookup"><span data-stu-id="e556e-105">Previous Techniques for Language Primitives in XAML Markup</span></span>

 <span data-ttu-id="e556e-106">V jazyce XAML pro předchozí verze WPF můžete odkazovat na základní jazykCLR mapováním sestavení a oboru názvů, které obsahovaly třídu primitivní definice CLR pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e556e-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="e556e-107">Většina z nich jsou v sestavení <xref:System> mscorlib a oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e556e-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="e556e-108">Chcete-li například použít <xref:System.Int32>, můžete deklarovat následující mapování (s příklad použití je uvedeno poté):</span><span class="sxs-lookup"><span data-stu-id="e556e-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="e556e-109">Jazyková primitiva XAML 2009</span><span class="sxs-lookup"><span data-stu-id="e556e-109">XAML 2009 Language Primitives</span></span>

<span data-ttu-id="e556e-110">Podle konvence jsou zobrazeny jazykové primitivy pro XAML a `x:` všechny ostatní prvky jazyka XAML, včetně předpony.</span><span class="sxs-lookup"><span data-stu-id="e556e-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="e556e-111">To je, jak xAML prvky jazyka se obvykle používají v reálném světě značky.</span><span class="sxs-lookup"><span data-stu-id="e556e-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="e556e-112">Tato konvence je dodržována v koncepční dokumentaci pro XAML v WPF a také ve specifikaci XAML.</span><span class="sxs-lookup"><span data-stu-id="e556e-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>

### <a name="xobject"></a><span data-ttu-id="e556e-113">x:Objekt</span><span class="sxs-lookup"><span data-stu-id="e556e-113">x:Object</span></span>

<span data-ttu-id="e556e-114">Pro podporu CLR `x:Object` primitivní odpovídá <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="e556e-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>

<span data-ttu-id="e556e-115">Tento primitiv se obvykle nepoužívá v aplikaci značky, ale může být užitečné pro některé scénáře, jako je například kontrola přiřaditelnostva v systému typu XAML.</span><span class="sxs-lookup"><span data-stu-id="e556e-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>

### <a name="xboolean"></a><span data-ttu-id="e556e-116">x:Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="e556e-116">x:Boolean</span></span>

<span data-ttu-id="e556e-117">Pro podporu CLR `x:Boolean` primitivní odpovídá <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="e556e-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>

<span data-ttu-id="e556e-118">XAML analyzuje hodnoty `x:Boolean` jako malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e556e-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="e556e-119">Všimněte `x:Bool` si, že není přijatou alternativou.</span><span class="sxs-lookup"><span data-stu-id="e556e-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="e556e-120">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.17 a 5.4.11 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xchar"></a><span data-ttu-id="e556e-121">x:Znak</span><span class="sxs-lookup"><span data-stu-id="e556e-121">x:Char</span></span>

<span data-ttu-id="e556e-122">Pro podporu CLR `x:Char` primitivní odpovídá <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="e556e-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>

<span data-ttu-id="e556e-123">Typy řetězců a znaků mají interakci s celkovým kódováním souboru na úrovni XML.</span><span class="sxs-lookup"><span data-stu-id="e556e-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="e556e-124">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.7 a 5.4.1 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xstring"></a><span data-ttu-id="e556e-125">x:Řetězec</span><span class="sxs-lookup"><span data-stu-id="e556e-125">x:String</span></span>

<span data-ttu-id="e556e-126">Pro podporu CLR `x:String` primitivní odpovídá <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e556e-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>

<span data-ttu-id="e556e-127">Typy řetězců a znaků mají interakci s celkovým kódováním souboru na úrovni XML.</span><span class="sxs-lookup"><span data-stu-id="e556e-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="e556e-128">Definice specifikace jazyka XAML naleznete [ \[v oddílech\] 5.2.6 jazyka MS-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdecimal"></a><span data-ttu-id="e556e-129">x:Desetinné místo</span><span class="sxs-lookup"><span data-stu-id="e556e-129">x:Decimal</span></span>

<span data-ttu-id="e556e-130">Pro podporu CLR `x:Decimal` primitivní odpovídá <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="e556e-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>

<span data-ttu-id="e556e-131">Analýza XAML se neodmyslitelně provádí v rámci `en-US` kultury.</span><span class="sxs-lookup"><span data-stu-id="e556e-131">XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="e556e-132">V `en-US` rámci jazykové verze je správný oddělovač pro součásti`.`desetinného místa vždy tečkou ( ) bez ohledu na nastavení jazykové verze vývojového prostředí nebo na případný cíl klienta, kde je xaml načten za běhu.</span><span class="sxs-lookup"><span data-stu-id="e556e-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>

<span data-ttu-id="e556e-133">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.14 a 5.4.8\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xsingle"></a><span data-ttu-id="e556e-134">x:Jednoduché</span><span class="sxs-lookup"><span data-stu-id="e556e-134">x:Single</span></span>

<span data-ttu-id="e556e-135">Pro podporu CLR `x:Single` primitivní odpovídá <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="e556e-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>

<span data-ttu-id="e556e-136">Kromě číselných hodnot umožňuje syntaxe `x:Single` textu také `Infinity` `-Infinity`tokeny `NaN`, a .</span><span class="sxs-lookup"><span data-stu-id="e556e-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="e556e-137">Tyto tokeny jsou považovány za malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e556e-137">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="e556e-138">`x:Single`může podporovat hodnoty ve formuláři vědeckého zápisu, `e` `E`pokud je první znak v syntaxi textu nebo .</span><span class="sxs-lookup"><span data-stu-id="e556e-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>

<span data-ttu-id="e556e-139">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.8 a 5.4.2 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdouble"></a><span data-ttu-id="e556e-140">x:Dvojitá</span><span class="sxs-lookup"><span data-stu-id="e556e-140">x:Double</span></span>

<span data-ttu-id="e556e-141">Pro podporu CLR `x:Double` primitivní odpovídá <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="e556e-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>

<span data-ttu-id="e556e-142">Kromě číselných hodnot umožňuje syntaxi textu `Infinity`pro `-Infinity` `x:Double` tokeny , a `NaN`.</span><span class="sxs-lookup"><span data-stu-id="e556e-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="e556e-143">Tyto tokeny jsou považovány za malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e556e-143">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="e556e-144">`x:Double`mohou podporovat hodnoty ve vědecké notační formě.</span><span class="sxs-lookup"><span data-stu-id="e556e-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="e556e-145">Použijte znak `e` `E` nebo zavést exponenciální část.</span><span class="sxs-lookup"><span data-stu-id="e556e-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>

<span data-ttu-id="e556e-146">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.9 a 5.4.3 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint16"></a><span data-ttu-id="e556e-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="e556e-147">x:Int16</span></span>

<span data-ttu-id="e556e-148">Pro podporu CLR `x:Int16` primitivární odpovídá <xref:System.Int16> a `x:Int16` je považován za podepsané.</span><span class="sxs-lookup"><span data-stu-id="e556e-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="e556e-149">V XAML je absence syntaxe textu přihlášení plus (`+`) implikována jako kladná podepsaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="e556e-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="e556e-150">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.11 a 5.4.5\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint32"></a><span data-ttu-id="e556e-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="e556e-151">x:Int32</span></span>

<span data-ttu-id="e556e-152">Pro podporu CLR `x:Int32` primitivní odpovídá <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="e556e-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="e556e-153">`x:Int32`považována za podepsanou.</span><span class="sxs-lookup"><span data-stu-id="e556e-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="e556e-154">V XAML je absence syntaxe textu přihlášení plus (`+`) implikována jako kladná podepsaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="e556e-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="e556e-155">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.12 a 5.4.6\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint64"></a><span data-ttu-id="e556e-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="e556e-156">x:Int64</span></span>

<span data-ttu-id="e556e-157">Pro podporu CLR `x:Int64` primitivní odpovídá <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="e556e-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="e556e-158">`x:Int64`považována za podepsanou.</span><span class="sxs-lookup"><span data-stu-id="e556e-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="e556e-159">V XAML je absence syntaxe textu přihlášení plus (`+`) implikována jako kladná podepsaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="e556e-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="e556e-160">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.13 a 5.4.7\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xtimespan"></a><span data-ttu-id="e556e-161">x:Časový posun</span><span class="sxs-lookup"><span data-stu-id="e556e-161">x:TimeSpan</span></span>

<span data-ttu-id="e556e-162">Pro podporu CLR `x:TimeSpan` primitivní odpovídá <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="e556e-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>

<span data-ttu-id="e556e-163">Analýza XAML pro formát časového data se `en-US` neodmyslitelně provádí v rámci jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="e556e-163">XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>

<span data-ttu-id="e556e-164">Definice specifikace jazyka XAML naleznete [ \[v oddílech\] 5.2.16 a 5.4.10 ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xuri"></a><span data-ttu-id="e556e-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="e556e-165">x:Uri</span></span>

<span data-ttu-id="e556e-166">Pro podporu CLR `x:Uri` primitivní odpovídá <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="e556e-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>

<span data-ttu-id="e556e-167">Kontrola protokolů není součástí definice XAML `x:Uri`pro .</span><span class="sxs-lookup"><span data-stu-id="e556e-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>

<span data-ttu-id="e556e-168">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.15 a 5.4.9\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xbyte"></a><span data-ttu-id="e556e-169">x:Bajt</span><span class="sxs-lookup"><span data-stu-id="e556e-169">x:Byte</span></span>

<span data-ttu-id="e556e-170">Pro podporu CLR `x:Byte` primitivní odpovídá <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="e556e-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="e556e-171"><xref:System.Byte>  /  A `x:Byte` je považován za nepodepsané.</span><span class="sxs-lookup"><span data-stu-id="e556e-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>

<span data-ttu-id="e556e-172">Definice specifikace jazyka XAML viz [ \[oddíly 5.2.10 a 5.4.4\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xarray"></a><span data-ttu-id="e556e-173">x:Pole</span><span class="sxs-lookup"><span data-stu-id="e556e-173">x:Array</span></span>

<span data-ttu-id="e556e-174">Pro podporu CLR `x:Array` primitivní odpovídá <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="e556e-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>

<span data-ttu-id="e556e-175">Pole v xaml 2006 můžete definovat pomocí syntaxe rozšíření značek; Syntaxe XAML 2009 je však jazykově definované primitivum, které nevyžaduje přístup k rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="e556e-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="e556e-176">Další informace o podpoře XAML 2006 naleznete v [tématu x:Array Markup Extension](xarray-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="e556e-176">For more information about XAML 2006 support, see [x:Array Markup Extension](xarray-markup-extension.md).</span></span>

<span data-ttu-id="e556e-177">Definice specifikace jazyka XAML naleznete [ \[v oddílech\] 5.2.18 jazyka MS-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e556e-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="wpf-support"></a><span data-ttu-id="e556e-178">Podpora WPF</span><span class="sxs-lookup"><span data-stu-id="e556e-178">WPF Support</span></span>

<span data-ttu-id="e556e-179">V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není zkompilován značkami.</span><span class="sxs-lookup"><span data-stu-id="e556e-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="e556e-180">XAML kompilované značkami pro WPF a formu BAML XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="e556e-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

<span data-ttu-id="e556e-181">Scénář, kde můžete použít funkce XAML 2009 spolu s WPF je, pokud autor volné XAML a potom <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>načíst, že XAML do wpf runtime a objektový graf s .</span><span class="sxs-lookup"><span data-stu-id="e556e-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e556e-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a <xref:System.Windows.Markup.XamlReader.Load%2A> jeho může zpracovat XAML 2009 jazyk klíčová slova a funkce do platného objektu grafu reprezentace.</span><span class="sxs-lookup"><span data-stu-id="e556e-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
