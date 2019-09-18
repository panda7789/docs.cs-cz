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
ms.openlocfilehash: 85fd0c04a40b9de64979e4da1459dbf8953a93bf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053883"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="8549a-102">Předdefinované typy obecných primitiv jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="8549a-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="8549a-103">XAML 2009 zavádí podporu na úrovni jazyka XAML pro několik datových typů, které jsou často používány primitivními prvky v modulu CLR (Common Language Runtime) a v jiných programovacích jazycích.</span><span class="sxs-lookup"><span data-stu-id="8549a-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="8549a-104">XAML 2009 přidává podporu pro tyto primitivní prvky: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, ,`x:TimeSpan` `x:Uri`, a`x:Byte``x:Array`</span><span class="sxs-lookup"><span data-stu-id="8549a-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="8549a-105">Předchozí techniky pro jazykové primitivy v kódu XAML</span><span class="sxs-lookup"><span data-stu-id="8549a-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="8549a-106">V jazyce XAML pro předchozí verze WPF můžete odkazovat na primitivní prvky jazyka CLR mapováním sestavení a oboru názvů, který obsahoval třídu primitivní definice CLR pro .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8549a-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="8549a-107">Většina z nich je v sestavení a <xref:System> oboru názvů mscorlib.</span><span class="sxs-lookup"><span data-stu-id="8549a-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="8549a-108">Například chcete-li použít <xref:System.Int32>, můžete deklarovat následující mapování (s příkladem použití zobrazeného po):</span><span class="sxs-lookup"><span data-stu-id="8549a-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```xaml  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="8549a-109">Primitiva jazyka XAML 2009</span><span class="sxs-lookup"><span data-stu-id="8549a-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="8549a-110">Podle konvence se zobrazí primitivní jazyky pro XAML a všechny ostatní prvky jazyka XAML, včetně `x:` předpony.</span><span class="sxs-lookup"><span data-stu-id="8549a-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="8549a-111">Toto je způsob, jakým jsou obvykle použity prvky jazyka XAML ve značkách reálného světa.</span><span class="sxs-lookup"><span data-stu-id="8549a-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="8549a-112">Tato konvence je následována v Koncepční dokumentaci pro jazyk XAML v subsystému WPF a také ve specifikaci jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="8549a-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="8549a-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="8549a-113">x:Object</span></span>  
 <span data-ttu-id="8549a-114">Pro zálohování `x:Object` CLR primitiva odpovídá <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8549a-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="8549a-115">Tento primitivní kód se obvykle nepoužívá v kódu aplikace, ale může být užitečný pro některé scénáře, jako je například kontrola přiřazení v systému typů XAML.</span><span class="sxs-lookup"><span data-stu-id="8549a-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="8549a-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="8549a-116">x:Boolean</span></span>  
 <span data-ttu-id="8549a-117">Pro zálohování `x:Boolean` CLR primitiva odpovídá <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="8549a-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="8549a-118">XAML analyzuje hodnoty pro `x:Boolean` nerozlišování velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="8549a-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="8549a-119">Všimněte si `x:Bool` , že se nejedná o přijatou alternativu.</span><span class="sxs-lookup"><span data-stu-id="8549a-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="8549a-120">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.17 a 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="8549a-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="8549a-121">x:Char</span></span>  
 <span data-ttu-id="8549a-122">Pro zálohování `x:Char` CLR primitiva odpovídá <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="8549a-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="8549a-123">Typy řetězců a znaků mají v interakci s celkovým kódováním souboru na úrovni XML.</span><span class="sxs-lookup"><span data-stu-id="8549a-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="8549a-124">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.7 a 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="8549a-125">x:String</span><span class="sxs-lookup"><span data-stu-id="8549a-125">x:String</span></span>  
 <span data-ttu-id="8549a-126">Pro zálohování `x:String` CLR primitiva odpovídá <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="8549a-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="8549a-127">Typy řetězců a znaků mají v interakci s celkovým kódováním souboru na úrovni XML.</span><span class="sxs-lookup"><span data-stu-id="8549a-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="8549a-128">Definice specifikace jazyka XAML naleznete v [ \[části MS-\] XAML 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="8549a-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="8549a-129">x:Decimal</span></span>  
 <span data-ttu-id="8549a-130">Pro zálohování `x:Decimal` CLR primitiva odpovídá <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="8549a-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="8549a-131">Všimněte si, že analýza XAML je v podstatě provedena v rámci `en-US` kultury.</span><span class="sxs-lookup"><span data-stu-id="8549a-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="8549a-132">V `en-US` rámci jazykové verze je správný oddělovač pro součásti desetinné čárky vždy tečka (`.`) bez ohledu na nastavení jazykové verze vývojového prostředí nebo na konečném cíli klienta, kde je XAML načten v době běhu.</span><span class="sxs-lookup"><span data-stu-id="8549a-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="8549a-133">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.14 a 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="8549a-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="8549a-134">x:Single</span></span>  
 <span data-ttu-id="8549a-135">Pro zálohování `x:Single` CLR primitiva odpovídá <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="8549a-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="8549a-136">Kromě `x:Single` číselných hodnot, syntaxe textu pro také povoluje tokeny `Infinity`, `-Infinity`a `NaN`.</span><span class="sxs-lookup"><span data-stu-id="8549a-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="8549a-137">Tyto tokeny se považují za rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="8549a-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="8549a-138">`x:Single`může podporovat hodnoty ve formě vědeckého zápisu, pokud je `e` první znak v syntaxi textu nebo. `E`</span><span class="sxs-lookup"><span data-stu-id="8549a-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="8549a-139">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.8 a 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="8549a-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="8549a-140">x:Double</span></span>  
 <span data-ttu-id="8549a-141">Pro zálohování `x:Double` CLR primitiva odpovídá <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="8549a-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="8549a-142">Kromě číselných hodnot, syntaxe `x:Double` textu pro povoluje tokeny `Infinity`, `-Infinity`a `NaN`.</span><span class="sxs-lookup"><span data-stu-id="8549a-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="8549a-143">Tyto tokeny se považují za rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="8549a-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="8549a-144">`x:Double`může podporovat hodnoty ve formě vědeckého zápisu.</span><span class="sxs-lookup"><span data-stu-id="8549a-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="8549a-145">Použijte znak `e` nebo `E` k představení části exponentu.</span><span class="sxs-lookup"><span data-stu-id="8549a-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="8549a-146">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.9 a 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="8549a-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="8549a-147">x:Int16</span></span>  
 <span data-ttu-id="8549a-148">V `x:Int16` případě zálohování CLR primitiva odpovídá <xref:System.Int16> a `x:Int16` je považována za signed.</span><span class="sxs-lookup"><span data-stu-id="8549a-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="8549a-149">V jazyce XAML není absence znaku plus (`+`) v syntaxi textu odvozena jako kladná podepsaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8549a-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="8549a-150">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.11 a 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="8549a-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="8549a-151">x:Int32</span></span>  
 <span data-ttu-id="8549a-152">Pro zálohování `x:Int32` CLR primitiva odpovídá <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="8549a-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="8549a-153">`x:Int32`je považován za podepsaný.</span><span class="sxs-lookup"><span data-stu-id="8549a-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="8549a-154">V jazyce XAML není absence znaku plus (`+`) v syntaxi textu odvozena jako kladná podepsaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8549a-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="8549a-155">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.12 a 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="8549a-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="8549a-156">x:Int64</span></span>  
 <span data-ttu-id="8549a-157">Pro zálohování `x:Int64` CLR primitiva odpovídá <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="8549a-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="8549a-158">`x:Int64`je považován za podepsaný.</span><span class="sxs-lookup"><span data-stu-id="8549a-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="8549a-159">V jazyce XAML není absence znaku plus (`+`) v syntaxi textu odvozena jako kladná podepsaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8549a-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="8549a-160">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.13 a 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="8549a-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="8549a-161">x:TimeSpan</span></span>  
 <span data-ttu-id="8549a-162">Pro zálohování `x:TimeSpan` CLR primitiva odpovídá <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="8549a-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="8549a-163">Analýza jazyka XAML pro formát data a času je v podstatě provedena v rámci `en-US` kultury.</span><span class="sxs-lookup"><span data-stu-id="8549a-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="8549a-164">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.16 a 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="8549a-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="8549a-165">x:Uri</span></span>  
 <span data-ttu-id="8549a-166">Pro zálohování `x:Uri` CLR primitiva odpovídá <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="8549a-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="8549a-167">Kontrola protokolů není součástí definice XAML pro `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="8549a-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="8549a-168">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.15 a 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="8549a-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="8549a-169">x:Byte</span></span>  
 <span data-ttu-id="8549a-170">Pro zálohování `x:Byte` CLR primitiva odpovídá <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="8549a-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="8549a-171">Jepovažovánzanepodepsaný<xref:System.Byte>.  /  `x:Byte`</span><span class="sxs-lookup"><span data-stu-id="8549a-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="8549a-172">Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.10 a 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="8549a-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="8549a-173">x:Array</span></span>  
 <span data-ttu-id="8549a-174">Pro zálohování `x:Array` CLR primitiva odpovídá <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="8549a-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="8549a-175">Pole v jazyce XAML 2006 můžete definovat pomocí syntaxe rozšíření značek; Syntaxe XAML 2009 však je jazykově definovaná primitiva, která nevyžaduje přístup k rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="8549a-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="8549a-176">Další informace o podpoře XAML 2006 naleznete v tématu [X:Array Markup Extension](x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="8549a-176">For more information about XAML 2006 support, see [x:Array Markup Extension](x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="8549a-177">Definice specifikace jazyka XAML naleznete v [ \[části MS-\] XAML 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8549a-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="8549a-178">Podpora WPF</span><span class="sxs-lookup"><span data-stu-id="8549a-178">WPF Support</span></span>  
 <span data-ttu-id="8549a-179">V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, které nejsou kompilovány pomocí značek.</span><span class="sxs-lookup"><span data-stu-id="8549a-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="8549a-180">XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="8549a-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="8549a-181">Scénář, ve kterém můžete použít funkce XAML 2009 společně s WPF, je, pokud vytvoříte volný kód XAML a potom tento kód XAML nahrajete do modulu runtime WPF <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>a grafu objektů pomocí.</span><span class="sxs-lookup"><span data-stu-id="8549a-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8549a-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a jeho <xref:System.Windows.Markup.XamlReader.Load%2A> aplikace mohou zpracovat klíčová slova a funkce jazyka XAML 2009 do platného reprezentace grafu objektu.</span><span class="sxs-lookup"><span data-stu-id="8549a-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
