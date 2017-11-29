---
title: "Předdefinované typy obecných primitiv jazyka XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 2b960e52d8d7dca590411f1c5f096a6942e1ade9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="400bb-102">Předdefinované typy obecných primitiv jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="400bb-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="400bb-103">XAML 2009 zavádí podporu úroveň jazyka XAML pro několik typů dat, které jsou často používané základní prvky v common language runtime (CLR) a ostatní programovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="400bb-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="400bb-104">Přidává podporu pro tyto primitiv jazyka XAML 2009: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, a`x:Array`</span><span class="sxs-lookup"><span data-stu-id="400bb-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="400bb-105">Předchozí techniky pro primitiva jazyka XAML značek</span><span class="sxs-lookup"><span data-stu-id="400bb-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="400bb-106">V jazyce XAML pro předchozí verze WPF může odkazovat primitiv jazyka CLR tak, že mapuje sestavení a obor názvů, který obsažené primitivní definice třídy CLR pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="400bb-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="400bb-107">Většina z nich jsou v sestavení mscorlib a <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="400bb-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="400bb-108">Chcete-li například použít <xref:System.Int32>, může deklarovat následující mapování (s příklady použití, zobrazí po tomto datu):</span><span class="sxs-lookup"><span data-stu-id="400bb-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="400bb-109">Primitiva jazyka XAML 2009</span><span class="sxs-lookup"><span data-stu-id="400bb-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="400bb-110">Podle konvence, jsou zobrazeny primitiv jazyka XAML a všechny další elementy jazyka XAML, včetně `x:` předponu.</span><span class="sxs-lookup"><span data-stu-id="400bb-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="400bb-111">Toto je, jak jsou obvykle používány elementů jazyka XAML v reálných značek.</span><span class="sxs-lookup"><span data-stu-id="400bb-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="400bb-112">Touto konvencí je následovaný v rámcová dokumentace pro jazyk XAML v grafickém subsystému WPF a také ve specifikaci XAML.</span><span class="sxs-lookup"><span data-stu-id="400bb-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="400bb-113">x: objekt</span><span class="sxs-lookup"><span data-stu-id="400bb-113">x:Object</span></span>  
 <span data-ttu-id="400bb-114">Pro zálohování CLR `x:Object` primitivní odpovídá <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="400bb-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="400bb-115">Tato primitivní není obvykle se používá v kódu aplikace, ale mohou být užitečné pro některé scénáře, jako je kontrola assignability typ systému XAML.</span><span class="sxs-lookup"><span data-stu-id="400bb-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="400bb-116">x: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="400bb-116">x:Boolean</span></span>  
 <span data-ttu-id="400bb-117">Pro zálohování CLR `x:Boolean` primitivní odpovídá <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="400bb-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="400bb-118">XAML analyzuje hodnoty pro `x:Boolean` jako malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="400bb-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="400bb-119">Všimněte si, že `x:Bool` není alternativu přijala.</span><span class="sxs-lookup"><span data-stu-id="400bb-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="400bb-120">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.17 a 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="400bb-121">x: Char</span><span class="sxs-lookup"><span data-stu-id="400bb-121">x:Char</span></span>  
 <span data-ttu-id="400bb-122">Pro zálohování CLR `x:Char` primitivní odpovídá <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="400bb-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="400bb-123">Typy řetězce a znak mají interakci s celkovou kódování souboru na úrovni XML.</span><span class="sxs-lookup"><span data-stu-id="400bb-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="400bb-124">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.7 a 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="400bb-125">x: řetězec</span><span class="sxs-lookup"><span data-stu-id="400bb-125">x:String</span></span>  
 <span data-ttu-id="400bb-126">Pro zálohování CLR `x:String` primitivní odpovídá <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="400bb-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="400bb-127">Typy řetězce a znak mají interakci s celkovou kódování souboru na úrovni XML.</span><span class="sxs-lookup"><span data-stu-id="400bb-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="400bb-128">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] části 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="400bb-129">x: Decimal</span><span class="sxs-lookup"><span data-stu-id="400bb-129">x:Decimal</span></span>  
 <span data-ttu-id="400bb-130">Pro zálohování CLR `x:Decimal` primitivní odpovídá <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="400bb-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="400bb-131">Všimněte si, že analýza XAML ze své podstaty probíhá v rámci `en-US` jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="400bb-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="400bb-132">V části `en-US` jazykové verzi, vždy období je správný oddělovač pro součásti desetinné číslo (`.`) bez ohledu na jazykové verzi nastavení vývojového prostředí nebo případné klienta cíle, kde je načtena XAML v době běhu.</span><span class="sxs-lookup"><span data-stu-id="400bb-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="400bb-133">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.14 a 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="400bb-134">x: jeden</span><span class="sxs-lookup"><span data-stu-id="400bb-134">x:Single</span></span>  
 <span data-ttu-id="400bb-135">Pro zálohování CLR `x:Single` primitivní odpovídá <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="400bb-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="400bb-136">Kromě číselné hodnoty textových syntaxi pro `x:Single` taky umožňuje tokeny `Infinity`, `-Infinity`, a `NaN`.</span><span class="sxs-lookup"><span data-stu-id="400bb-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="400bb-137">Tyto tokeny jsou zpracovány jako malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="400bb-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="400bb-138">`x:Single`ve formuláři exponenciální notace, může podporovat hodnoty, pokud je první znak v textových syntaxi `e` nebo `E`.</span><span class="sxs-lookup"><span data-stu-id="400bb-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="400bb-139">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.8 a 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="400bb-140">x: Double</span><span class="sxs-lookup"><span data-stu-id="400bb-140">x:Double</span></span>  
 <span data-ttu-id="400bb-141">Pro zálohování CLR `x:Double` primitivní odpovídá <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="400bb-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="400bb-142">Kromě číselné hodnoty textových syntaxi pro `x:Double` umožňuje tokeny `Infinity`, `-Infinity`, a `NaN`.</span><span class="sxs-lookup"><span data-stu-id="400bb-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="400bb-143">Tyto tokeny jsou zpracovány jako malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="400bb-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="400bb-144">`x:Double`ve formuláři vědecká notace může podporovat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="400bb-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="400bb-145">Použít znak `e` nebo `E` zavádět exponentu část.</span><span class="sxs-lookup"><span data-stu-id="400bb-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="400bb-146">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.9 a 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="400bb-147">x: Int16</span><span class="sxs-lookup"><span data-stu-id="400bb-147">x:Int16</span></span>  
 <span data-ttu-id="400bb-148">Pro zálohování CLR `x:Int16` primitivní odpovídá <xref:System.Int16> a `x:Int16` je zpracovaná jako podepsané.</span><span class="sxs-lookup"><span data-stu-id="400bb-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="400bb-149">V jazyce XAML, chybí znak plus (`+`) přihlášení syntaxe textu je implicitní jako podepsaný kladnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="400bb-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="400bb-150">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.11 a 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="400bb-151">x: Int32</span><span class="sxs-lookup"><span data-stu-id="400bb-151">x:Int32</span></span>  
 <span data-ttu-id="400bb-152">Pro zálohování CLR `x:Int32` primitivní odpovídá <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="400bb-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="400bb-153">`x:Int32`je zpracovaná jako podepsané.</span><span class="sxs-lookup"><span data-stu-id="400bb-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="400bb-154">V jazyce XAML, chybí znak plus (`+`) přihlášení syntaxe textu je implicitní jako podepsaný kladnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="400bb-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="400bb-155">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.12 a 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="400bb-156">x: Int64</span><span class="sxs-lookup"><span data-stu-id="400bb-156">x:Int64</span></span>  
 <span data-ttu-id="400bb-157">Pro zálohování CLR `x:Int64` primitivní odpovídá <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="400bb-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="400bb-158">`x:Int64`je zpracovaná jako podepsané.</span><span class="sxs-lookup"><span data-stu-id="400bb-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="400bb-159">V jazyce XAML, chybí znak plus (`+`) přihlášení syntaxe textu je implicitní jako podepsaný kladnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="400bb-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="400bb-160">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.13 a 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="400bb-161">x: časový interval</span><span class="sxs-lookup"><span data-stu-id="400bb-161">x:TimeSpan</span></span>  
 <span data-ttu-id="400bb-162">Pro zálohování CLR `x:TimeSpan` primitivní odpovídá <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="400bb-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="400bb-163">Upozorňujeme, že XAML analýza formátu čas datum je ze své podstaty pracujete v části `en-US` jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="400bb-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="400bb-164">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.16 a 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="400bb-165">x: identifikátor Uri</span><span class="sxs-lookup"><span data-stu-id="400bb-165">x:Uri</span></span>  
 <span data-ttu-id="400bb-166">Pro zálohování CLR `x:Uri` primitivní odpovídá <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="400bb-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="400bb-167">Kontrola protokolů není součástí definici XAML pro `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="400bb-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="400bb-168">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.15 a 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="400bb-169">x: bajtů</span><span class="sxs-lookup"><span data-stu-id="400bb-169">x:Byte</span></span>  
 <span data-ttu-id="400bb-170">Pro zálohování CLR `x:Byte` primitivní odpovídá <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="400bb-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="400bb-171">A <xref:System.Byte>  /  `x:Byte` považuje jako bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="400bb-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="400bb-172">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.10 a 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="400bb-173">x: Array</span><span class="sxs-lookup"><span data-stu-id="400bb-173">x:Array</span></span>  
 <span data-ttu-id="400bb-174">Pro zálohování CLR `x:Array` primitivní odpovídá <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="400bb-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="400bb-175">Pole v jazyce XAML 2006 můžete definovat pomocí syntaxi rozšíření značek; Syntaxe jazyka XAML 2009 je však definován jazyk Primitivum, které nevyžaduje přístup k rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="400bb-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="400bb-176">Další informace o podpoře XAML 2006 najdete v tématu [x: Array – rozšíření značek](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="400bb-176">For more information about XAML 2006 support, see [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="400bb-177">Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] části 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="400bb-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="400bb-178">Podpora WPF</span><span class="sxs-lookup"><span data-stu-id="400bb-178">WPF Support</span></span>  
 <span data-ttu-id="400bb-179">V grafickém subsystému WPF můžete použít funkce jazyka XAML 2009 ale jenom pro jazyk XAML, který zkompiluje značek není.</span><span class="sxs-lookup"><span data-stu-id="400bb-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="400bb-180">Zkompilovaný kód XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.</span><span class="sxs-lookup"><span data-stu-id="400bb-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="400bb-181">Scénář, kde můžete použít funkce jazyka XAML 2009 společně s WPF je-li vytvořit přijít XAML a pak načtení tohoto XAML do grafu WPF runtime a objekt s <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="400bb-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="400bb-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a jeho <xref:System.Windows.Markup.XamlReader.Load%2A> může zpracovat klíčová slova jazyka XAML 2009 a funkcí do znázornění platný objekt grafu.</span><span class="sxs-lookup"><span data-stu-id="400bb-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
