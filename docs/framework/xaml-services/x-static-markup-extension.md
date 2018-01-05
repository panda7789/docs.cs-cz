---
title: "x:Static – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 647bfed7b321a949090f6da047f9b8105d335101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="031f6-102">x:Static – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="031f6-102">x:Static Markup Extension</span></span>
<span data-ttu-id="031f6-103">Každá entita kód statické podle hodnoty, která je definována v odkazuje [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– kompatibilní způsob.</span><span class="sxs-lookup"><span data-stu-id="031f6-103">References any static by-value code entity that is defined in a [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]–compliant way.</span></span> <span data-ttu-id="031f6-104">Statické vlastnosti, která se odkazuje slouží k poskytování hodnotou vlastnosti v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="031f6-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="031f6-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="031f6-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="031f6-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="031f6-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="031f6-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="031f6-107">Optional.</span></span> <span data-ttu-id="031f6-108">Předponu, která odkazuje na namapované, jiné než výchozí obor názvů jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="031f6-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="031f6-109">`prefix`ukazuje explicitně využití zřídka odkazovat statické vlastnosti, které pocházejí z oboru názvů jazyka XAML výchozí.</span><span class="sxs-lookup"><span data-stu-id="031f6-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="031f6-110">V části poznámky.</span><span class="sxs-lookup"><span data-stu-id="031f6-110">See Remarks.</span></span>|  
|`typeName`|<span data-ttu-id="031f6-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="031f6-111">Required.</span></span> <span data-ttu-id="031f6-112">Název typu, který definuje požadované statický člen.</span><span class="sxs-lookup"><span data-stu-id="031f6-112">The name of the type that defines the desired static member.</span></span>|  
|`staticMemberName`|<span data-ttu-id="031f6-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="031f6-113">Required.</span></span> <span data-ttu-id="031f6-114">Název člena požadovanou statickou hodnotu (konstanta, pomocí statické vlastnosti, pole nebo hodnotou výčtu).</span><span class="sxs-lookup"><span data-stu-id="031f6-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="031f6-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="031f6-115">Remarks</span></span>  
 <span data-ttu-id="031f6-116">Entity kód, který se odkazuje musí mít jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="031f6-116">The code entity that is referenced must be one of the following:</span></span>  
  
-   <span data-ttu-id="031f6-117">Konstanta</span><span class="sxs-lookup"><span data-stu-id="031f6-117">A constant</span></span>  
  
-   <span data-ttu-id="031f6-118">Statické vlastnosti</span><span class="sxs-lookup"><span data-stu-id="031f6-118">A static property</span></span>  
  
-   <span data-ttu-id="031f6-119">Pole</span><span class="sxs-lookup"><span data-stu-id="031f6-119">A field</span></span>  
  
-   <span data-ttu-id="031f6-120">Hodnota výčtu</span><span class="sxs-lookup"><span data-stu-id="031f6-120">An enumeration value</span></span>  
  
 <span data-ttu-id="031f6-121">Chyba kompilace zadání dalších kód entitu, jako je například nestatické vlastnost, dojde, pokud je XAML kompilaci kódu, nebo k výjimce při načtení analýzy XAML.</span><span class="sxs-lookup"><span data-stu-id="031f6-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>  
  
 <span data-ttu-id="031f6-122">Můžete provést `x:Static` odkazy na statických polí nebo vlastnosti, které nejsou ve výchozí obor názvů jazyka XAML pro aktuální dokument XAML; to však vyžaduje mapování předpony.</span><span class="sxs-lookup"><span data-stu-id="031f6-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="031f6-123">Obory názvů jazyka XAML jsou téměř vždy definována v kořenovém elementu dokumentu XAML.</span><span class="sxs-lookup"><span data-stu-id="031f6-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>  
  
 <span data-ttu-id="031f6-124">Operace vyhledávání pro statické vlastnosti můžete provést pomocí rozhraní .NET Framework XAML Services a jeho XAML čtení a zápis XAML, pokud jsou spuštěny s výchozí kontext schématu XAML.</span><span class="sxs-lookup"><span data-stu-id="031f6-124">The lookup operations for static properties can be performed by .NET Framework XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="031f6-125">Tento kontext schématu XAML zajistit potřebné statické hodnoty pro vytváření objektů grafu použít reflexe CLR.</span><span class="sxs-lookup"><span data-stu-id="031f6-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="031f6-126">`typeName` Zadejte je ve skutečnosti XAML název typu, nikoli název typu CLR, i když tyto jsou v podstatě stejný název, když používáte výchozí kontext schématu XAML nebo při použití architektury všechny existující implementace XAML na základě CLR.</span><span class="sxs-lookup"><span data-stu-id="031f6-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>  
  
 <span data-ttu-id="031f6-127">Buďte opatrní při provádění `x:Static` odkazy, které nejsou přímo typ vlastnosti na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="031f6-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="031f6-128">V XAML zpracování pořadí, zadat hodnoty z rozšíření značek Nevolejte převod další hodnoty.</span><span class="sxs-lookup"><span data-stu-id="031f6-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="031f6-129">To platí i v případě vaší `x:Static` odkaz vytvoří textový řetězec a převod hodnoty pro hodnoty atributů, které jsou založené na textový řetězec obvykle dochází pro konkrétní člena nebo všechny hodnoty členů návratového typu.</span><span class="sxs-lookup"><span data-stu-id="031f6-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>  
  
 <span data-ttu-id="031f6-130">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="031f6-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="031f6-131">Token řetězec zadaný po `x:Static` řetězec identifikátoru je přiřazen jako <xref:System.Windows.Markup.StaticExtension.Member%2A> hodnotu základní <xref:System.Windows.Markup.StaticExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="031f6-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>  
  
 <span data-ttu-id="031f6-132">Existují dva další XAML použití, které jsou technicky možné.</span><span class="sxs-lookup"><span data-stu-id="031f6-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="031f6-133">Tyto použití jsou však méně častých, protože je zbytečně podrobné:</span><span class="sxs-lookup"><span data-stu-id="031f6-133">However, these usages are less common because they are unnecessarily verbose:</span></span>  
  
 <span data-ttu-id="031f6-134">**Objekt elementu syntaxe:** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName``" .../>`</span><span class="sxs-lookup"><span data-stu-id="031f6-134">**Object element syntax:** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName` `" .../>`</span></span>  
  
 <span data-ttu-id="031f6-135">**Atribut syntaxi společně s explicitní vlastnost člena pro inicializačního řetězce:** `<` `object`  ``  `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName``}" .../>`</span><span class="sxs-lookup"><span data-stu-id="031f6-135">**Attribute syntax with explicit Member property for initialization string:** `<` `object` `` `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName` `}" .../>`</span></span>  
  
 <span data-ttu-id="031f6-136">Implementace rozhraní .NET Framework XAML Services je definované zpracování pro toto rozšíření značek <xref:System.Windows.Markup.StaticExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="031f6-136">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>  
  
 <span data-ttu-id="031f6-137">`x:Static`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="031f6-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="031f6-138">Všechna rozšíření značek v XAML použití `{` a `}` znaků v jejich syntaxi atributů, což je konvence, podle kterého XAML procesor rozpozná, že rozšíření značek musíte zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="031f6-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="031f6-139">Další informace o rozšíření značek najdete v tématu [XAML přehled rozšíření značek pro](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="031f6-140">Poznámky pro použití WPF</span><span class="sxs-lookup"><span data-stu-id="031f6-140">WPF Usage Notes</span></span>  
 <span data-ttu-id="031f6-141">Výchozí obor názvů jazyka XAML použijete pro programování WPF neobsahuje mnoho užitečné statické vlastnosti a většina užitečné statické vlastnosti má podpory, jako je například převaděče typů, které usnadňují použití bez nutnosti `{x:Static}` .</span><span class="sxs-lookup"><span data-stu-id="031f6-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="031f6-142">Statické vlastnosti je nutné mapovat předponu pro obor názvů jazyka XAML, pokud platí jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="031f6-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>  
  
-   <span data-ttu-id="031f6-143">Je odkazováno na typ, který existuje v grafickém subsystému WPF, ale není součástí výchozí obor názvů jazyka XAML pro grafický subsystém WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="031f6-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]).</span></span> <span data-ttu-id="031f6-144">Toto je celkem běžné scénáře použití `x:Static`.</span><span class="sxs-lookup"><span data-stu-id="031f6-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="031f6-145">Například můžete použít `x:Static` odkaz s mapování oboru názvů jazyka XAML do <xref:System> sestavení CLR obor názvů a mscorlib – Chcete-li odkazovat na statické vlastnosti <xref:System.Environment> třídy.</span><span class="sxs-lookup"><span data-stu-id="031f6-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>  
  
-   <span data-ttu-id="031f6-146">Typ odkazují z vlastního sestavení.</span><span class="sxs-lookup"><span data-stu-id="031f6-146">You are referencing a type from a custom assembly.</span></span>  
  
-   <span data-ttu-id="031f6-147">Je odkazováno na typ, který existuje v sestavení WPF, ale tento typ je v rámci oboru názvů CLR, který nebyl namapovaný jako součást WPF výchozí obor názvů jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="031f6-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="031f6-148">Mapování obory názvů CLR do výchozí obor názvů jazyka XAML pro grafický subsystém WPF provádí definice v různých sestavení grafického subsystému WPF (Další informace o tento koncept najdete v tématu [obory názvů jazyka XAML a mapování Namespace pro jazyk XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span><span class="sxs-lookup"><span data-stu-id="031f6-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="031f6-149">Mapované bez obory názvů CLR může existovat, pokud tento obor názvů CLR tvoří většinou definice tříd, které nejsou určeny obvykle pro jazyk XAML, jako například <xref:System.Windows.Threading>.</span><span class="sxs-lookup"><span data-stu-id="031f6-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>  
  
 <span data-ttu-id="031f6-150">Další informace o tom, jak používat předpony a obory názvů jazyka XAML pro grafický subsystém WPF najdete v tématu [obory názvů jazyka XAML a Namespace mapování pro jazyk XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="031f6-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="031f6-151">See Also</span></span>  
 [<span data-ttu-id="031f6-152">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="031f6-152">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="031f6-153">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="031f6-153">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
