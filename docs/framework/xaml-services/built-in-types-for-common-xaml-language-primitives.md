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
ms.openlocfilehash: c6af46fe2ea21d081e693ee83949651bd388a045
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837269"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="84598-102">Předdefinované typy obecných primitiv jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="84598-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="84598-103">XAML 2009 zavádí podporu na úrovni jazyka XAML pro několik datových typů, které jsou často používány primitivními prvky v modulu CLR (Common Language Runtime) a v jiných programovacích jazycích.</span><span class="sxs-lookup"><span data-stu-id="84598-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="84598-104">XAML 2009 přidává podporu pro tyto primitivní prvky: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`a `x:Array`</span><span class="sxs-lookup"><span data-stu-id="84598-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="84598-105">Předchozí postupy pro primitivní prvky pro značky XAML</span><span class="sxs-lookup"><span data-stu-id="84598-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="84598-106">V jazyce XAML pro předchozí verze WPF může odkazovat základní prvky jazyka CLR mapováním sestavení a oboru názvů, který obsahuje třídy definice základních prvků CLR pro .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84598-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="84598-107">Většina z nich jsou v sestavení mscorlib a oboru názvů <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="84598-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="84598-108">Můžete například použít <xref:System.Int32>, můžete deklarovat následující mapování (s následně zobrazeným příkladem použití):</span><span class="sxs-lookup"><span data-stu-id="84598-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
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
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="84598-109">XAML 2009 Language Primitives</span><span class="sxs-lookup"><span data-stu-id="84598-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="84598-110">Podle konvence jsou zobrazeny základy jazyka XAML a všechny ostatní prvky jazyka XAML, včetně předpony `x:`.</span><span class="sxs-lookup"><span data-stu-id="84598-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="84598-111">Tímto způsobem se běžně používají elementy jazyka XAML ve značkách reálného světa.</span><span class="sxs-lookup"><span data-stu-id="84598-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="84598-112">Tato konvence je uvedena v rámcové dokumentaci pro XAML ve WPF a také ve specifikaci jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="84598-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="84598-113">x:Objekt</span><span class="sxs-lookup"><span data-stu-id="84598-113">x:Object</span></span>  
 <span data-ttu-id="84598-114">Pro CLR zálohování primitiva `x:Object` odpovídá <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="84598-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="84598-115">Tato primitiva se obvykle nepoužívá ve značce aplikace, ale může být užitečná pro některé scénáře, jako je například kontrola přiřaditelnosti v typu systému XAML.</span><span class="sxs-lookup"><span data-stu-id="84598-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="84598-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="84598-116">x:Boolean</span></span>  
 <span data-ttu-id="84598-117">Pro CLR zálohování primitiva `x:Boolean` odpovídá <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="84598-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="84598-118">XAML analyzuje hodnoty pro `x:Boolean` bez rozlišení písma.</span><span class="sxs-lookup"><span data-stu-id="84598-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="84598-119">Všimněte si, že `x:Bool` není přijatou alternativu.</span><span class="sxs-lookup"><span data-stu-id="84598-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="84598-120">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.17 a 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="84598-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="84598-121">x:Char</span></span>  
 <span data-ttu-id="84598-122">Pro CLR zálohování primitiva `x:Char` odpovídá <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="84598-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="84598-123">Typy řetězce a znaku provádí interakci s celkovým kódováním souboru na úrovni XML.</span><span class="sxs-lookup"><span data-stu-id="84598-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="84598-124">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.7 a 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="84598-125">x:Řetězec</span><span class="sxs-lookup"><span data-stu-id="84598-125">x:String</span></span>  
 <span data-ttu-id="84598-126">Pro CLR zálohování primitiva `x:String` odpovídá <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="84598-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="84598-127">Typy řetězce a znaku provádí interakci s celkovým kódováním souboru na úrovni XML.</span><span class="sxs-lookup"><span data-stu-id="84598-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="84598-128">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="84598-129">x:Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="84598-129">x:Decimal</span></span>  
 <span data-ttu-id="84598-130">Pro CLR zálohování primitiva `x:Decimal` odpovídá <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="84598-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="84598-131">Všimněte si, že analýza XAML je ze své podstaty provedená v jazykové kultuře `en-US`.</span><span class="sxs-lookup"><span data-stu-id="84598-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="84598-132">V části jazyková verze `en-US` je správný oddělovač pro součásti desetinného čísla vždy tečka (`.`) bez ohledu na nastavení jazykové verze vývojového prostředí nebo případného cíle klienta, kde XAML je načten v době běhu.</span><span class="sxs-lookup"><span data-stu-id="84598-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="84598-133">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.14 a 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="84598-134">x:Jednoduché</span><span class="sxs-lookup"><span data-stu-id="84598-134">x:Single</span></span>  
 <span data-ttu-id="84598-135">Pro CLR zálohování primitiva `x:Single` odpovídá <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="84598-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="84598-136">Kromě číselných hodnot, textová syntaxe pro `x:Single` také umožňuje tokeny `Infinity`, `-Infinity` a `NaN`.</span><span class="sxs-lookup"><span data-stu-id="84598-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="84598-137">Tyto tokeny jsou zpracovány s rozlišováním malých a velkých písmen.</span><span class="sxs-lookup"><span data-stu-id="84598-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="84598-138">`x:Single` podporuje hodnoty ve formátu matematického zápisu, pokud je první znak v textu syntaxe `e` nebo `E`.</span><span class="sxs-lookup"><span data-stu-id="84598-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="84598-139">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.8 a 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="84598-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="84598-140">x:Double</span></span>  
 <span data-ttu-id="84598-141">Pro CLR zálohování primitiva `x:Double` odpovídá <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="84598-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="84598-142">Kromě číselných hodnot, textová syntaxe pro `x:Double` umožňuje tokeny `Infinity`, `-Infinity` a `NaN`.</span><span class="sxs-lookup"><span data-stu-id="84598-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="84598-143">Tyto tokeny jsou zpracovány s rozlišováním malých a velkých písmen.</span><span class="sxs-lookup"><span data-stu-id="84598-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="84598-144">`x:Double` může podporovat hodnoty ve formuláři pro matematický zápis.</span><span class="sxs-lookup"><span data-stu-id="84598-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="84598-145">Znak `e` nebo `E` použijte k zavedení části exponentu.</span><span class="sxs-lookup"><span data-stu-id="84598-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="84598-146">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.9 a 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="84598-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="84598-147">x:Int16</span></span>  
 <span data-ttu-id="84598-148">Pro zálohování CLR základ `x:Int16` odpovídající <xref:System.Int16> a `x:Int16` je považován za podepsaný.</span><span class="sxs-lookup"><span data-stu-id="84598-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="84598-149">V jazyce XAML, neexistence znaku plus (`+`) v syntaxi textu je vyjádřena jako kladná hodnota se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="84598-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="84598-150">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.11 a 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="84598-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="84598-151">x:Int32</span></span>  
 <span data-ttu-id="84598-152">Pro CLR zálohování primitiva `x:Int32` odpovídá <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="84598-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="84598-153">`x:Int32` je považován za se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="84598-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="84598-154">V jazyce XAML, neexistence znaku plus (`+`) v syntaxi textu je vyjádřena jako kladná hodnota se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="84598-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="84598-155">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.12 a 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="84598-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="84598-156">x:Int64</span></span>  
 <span data-ttu-id="84598-157">Pro CLR zálohování primitiva `x:Int64` odpovídá <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="84598-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="84598-158">`x:Int64` je považován za se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="84598-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="84598-159">V jazyce XAML, neexistence znaku plus (`+`) v syntaxi textu je vyjádřena jako kladná hodnota se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="84598-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="84598-160">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.13 a 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="84598-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="84598-161">x:TimeSpan</span></span>  
 <span data-ttu-id="84598-162">Pro CLR zálohování primitiva `x:TimeSpan` odpovídá <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="84598-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="84598-163">Všimněte si, že analýza XAML pro formát data a času je ze své podstaty provedená v jazykové kultuře `en-US`.</span><span class="sxs-lookup"><span data-stu-id="84598-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="84598-164">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.16 a 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="84598-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="84598-165">x:Uri</span></span>  
 <span data-ttu-id="84598-166">Pro CLR zálohování primitiva `x:Uri` odpovídá <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="84598-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="84598-167">Kontrola protokolů není součástí definice XAML pro `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="84598-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="84598-168">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.15 a 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="84598-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="84598-169">x:Byte</span></span>  
 <span data-ttu-id="84598-170">Pro CLR zálohování primitiva `x:Byte` odpovídá <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="84598-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="84598-171"><xref:System.Byte> / `x:Byte` se považuje za nepodepsaný.</span><span class="sxs-lookup"><span data-stu-id="84598-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="84598-172">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.10 a 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="84598-173">x:Pole</span><span class="sxs-lookup"><span data-stu-id="84598-173">x:Array</span></span>  
 <span data-ttu-id="84598-174">Pro CLR zálohování primitiva `x:Array` odpovídá <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="84598-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="84598-175">Pole v jazyce XAML 2006 můžete definovat pomocí syntaxe rozšíření značek; Syntaxe XAML 2009 však je jazykově definovaná primitiva, která nevyžaduje přístup k rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="84598-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="84598-176">Další informace o podpoře XAML 2006 naleznete v tématu [X:Array Markup Extension](x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="84598-176">For more information about XAML 2006 support, see [x:Array Markup Extension](x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="84598-177">Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="84598-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="84598-178">Podpora WPF</span><span class="sxs-lookup"><span data-stu-id="84598-178">WPF Support</span></span>  
 <span data-ttu-id="84598-179">V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, které nejsou kompilovány pomocí značek.</span><span class="sxs-lookup"><span data-stu-id="84598-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="84598-180">XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="84598-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="84598-181">Scénář, ve kterém můžete použít funkce XAML 2009 společně s WPF, je, pokud vytvoříte volný kód XAML a potom tento XAML navedete do modulu runtime WPF a grafu objektů pomocí <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84598-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="84598-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a její <xref:System.Windows.Markup.XamlReader.Load%2A> mohou zpracovat klíčová slova a funkce jazyka XAML 2009 do platného reprezentace grafu objektu.</span><span class="sxs-lookup"><span data-stu-id="84598-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
