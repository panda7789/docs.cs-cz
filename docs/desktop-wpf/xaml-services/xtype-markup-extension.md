---
title: x:Type – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071358"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="9e40f-102">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="9e40f-102">x:Type Markup Extension</span></span>

<span data-ttu-id="9e40f-103">Dodává objekt CLR, <xref:System.Type> který je základním typem pro zadaný typ XAML.</span><span class="sxs-lookup"><span data-stu-id="9e40f-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="9e40f-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="9e40f-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="9e40f-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="9e40f-105">XAML Object Element Usage</span></span>

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a><span data-ttu-id="9e40f-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="9e40f-106">XAML Values</span></span>

|||
|-|-|
|`prefix`|<span data-ttu-id="9e40f-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9e40f-107">Optional.</span></span> <span data-ttu-id="9e40f-108">Předpona, která mapuje nevýchozí obor názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="9e40f-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="9e40f-109">Zadání předpony často není nutné.</span><span class="sxs-lookup"><span data-stu-id="9e40f-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="9e40f-110">Viz Poznámky.</span><span class="sxs-lookup"><span data-stu-id="9e40f-110">See Remarks.</span></span>|
|`typeNameValue`|<span data-ttu-id="9e40f-111">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="9e40f-111">Required.</span></span> <span data-ttu-id="9e40f-112">Název typu, který lze řešit na aktuální výchozí obor názvů XAML; nebo zadanou mapovanou `prefix` předponu, pokud je zadána.</span><span class="sxs-lookup"><span data-stu-id="9e40f-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9e40f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e40f-113">Remarks</span></span>

<span data-ttu-id="9e40f-114">Rozšíření `x:Type` značek má podobnou funkci `typeof()` jako operátor v `GetType` jazyce C# nebo operátor v jazyce Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e40f-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>

<span data-ttu-id="9e40f-115">Rozšíření `x:Type` značek poskytuje chování převodu od řetězce pro vlastnosti, které berou typ <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="9e40f-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="9e40f-116">Vstup je typ XAML.</span><span class="sxs-lookup"><span data-stu-id="9e40f-116">The input is a XAML type.</span></span> <span data-ttu-id="9e40f-117">Vztah mezi vstupní maml typu a <xref:System.Type> výstup CLR <xref:System.Type> je, že výstup <xref:System.Xaml.XamlType.UnderlyingType%2A> je vstup <xref:System.Xaml.XamlType>, po vyhledání nezbytné <xref:System.Xaml.XamlType> na <xref:System.Windows.Markup.IXamlTypeResolver> základě kontextu schématu XAML a služby, které poskytuje kontext.</span><span class="sxs-lookup"><span data-stu-id="9e40f-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="9e40f-118">Ve službě .NET XAML Services je zpracování pro <xref:System.Windows.Markup.TypeExtension> toto rozšíření značek definováno třídou.</span><span class="sxs-lookup"><span data-stu-id="9e40f-118">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>

<span data-ttu-id="9e40f-119">V implementacich konkrétní architektury některé <xref:System.Type> vlastnosti, které berou jako hodnotu můžete přijmout `Name`název typu přímo (hodnota řetězce typu ).</span><span class="sxs-lookup"><span data-stu-id="9e40f-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="9e40f-120">Implementace tohoto chování je však složitý scénář.</span><span class="sxs-lookup"><span data-stu-id="9e40f-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="9e40f-121">Příklady naleznete v části "WPF Poznámky k použití", která následuje.</span><span class="sxs-lookup"><span data-stu-id="9e40f-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>

<span data-ttu-id="9e40f-122">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="9e40f-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="9e40f-123">Token řetězce zadaný `x:Type` po přidělení řetězce <xref:System.Windows.Markup.TypeExtension.TypeName%2A> identifikátoru jako <xref:System.Windows.Markup.TypeExtension> hodnota základní třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="9e40f-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="9e40f-124">Ve výchozím kontextu schématu XAML pro služby .NET XAML Services, který je založen na <xref:System.Reflection.MemberInfo.Name%2A> typech CLR, <xref:System.Reflection.MemberInfo.Name%2A> je hodnota tohoto atributu buď požadovaného typu, nebo obsahuje předponu pro mapování oboru názvů XAML, které není výchozí.</span><span class="sxs-lookup"><span data-stu-id="9e40f-124">Under the default XAML schema context for .NET XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>

<span data-ttu-id="9e40f-125">Rozšíření `x:Type` značek lze použít v syntaxi prvku objektu.</span><span class="sxs-lookup"><span data-stu-id="9e40f-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="9e40f-126">V tomto případě je nutné <xref:System.Windows.Markup.TypeExtension.TypeName%2A> zadat hodnotu vlastnosti správně inicializovat rozšíření.</span><span class="sxs-lookup"><span data-stu-id="9e40f-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>

<span data-ttu-id="9e40f-127">Rozšíření `x:Type` značek lze také použít jako podrobný atribut; toto použití však není typické:`<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="9e40f-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="9e40f-128">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="9e40f-128">WPF Usage Notes</span></span>

### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="9e40f-129">Výchozí obor názvů XAML a mapování typů</span><span class="sxs-lookup"><span data-stu-id="9e40f-129">Default XAML Namespace and Type Mapping</span></span>

<span data-ttu-id="9e40f-130">Výchozí obor názvů XAML pro programování WPF obsahuje většinu typů XAML, které potřebujete pro typické scénáře XAML; proto se často můžete vyhnout předpony při odkazování na hodnoty typu XAML.</span><span class="sxs-lookup"><span data-stu-id="9e40f-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="9e40f-131">Možná budete muset mapovat předponu, pokud odkazujete na typ z vlastního sestavení nebo pro typy, které existují v sestavení WPF, ale pocházejí z oboru názvů CLR, který nebyl mapován na výchozí obor názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="9e40f-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="9e40f-132">Další informace o předponách, oborech názvů XAML a mapování oborů názvů CLR naleznete v [tématu XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="9e40f-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="9e40f-133">Vlastnosti typu, které podporují typename jako řetězec</span><span class="sxs-lookup"><span data-stu-id="9e40f-133">Type Properties That Support Typename-as-String</span></span>

<span data-ttu-id="9e40f-134">WPF podporuje techniky, které umožňují určení hodnoty <xref:System.Type> některých `x:Type` vlastností typu bez nutnosti použití rozšíření značky.</span><span class="sxs-lookup"><span data-stu-id="9e40f-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="9e40f-135">Místo toho můžete zadat hodnotu jako řetězec, který pojmenuje typ.</span><span class="sxs-lookup"><span data-stu-id="9e40f-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="9e40f-136">Příklady tohoto <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> jsou <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>a .</span><span class="sxs-lookup"><span data-stu-id="9e40f-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9e40f-137">Podpora pro toto chování není poskytována prostřednictvím převaděčů typu nebo rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="9e40f-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="9e40f-138">Místo toho se jedná o <xref:System.Windows.FrameworkElementFactory>chování časově rozlišené implementované prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="9e40f-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>

<span data-ttu-id="9e40f-139">Program Silverlight podporuje podobnou konvenci.</span><span class="sxs-lookup"><span data-stu-id="9e40f-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="9e40f-140">Ve skutečnosti program Silverlight aktuálně `{x:Type}` nepodporuje jazykovou podporu XAML `{x:Type}` a nepřijímá použití mimo několik okolností, které jsou určeny pro podporu migrace WPF-Silverlight XAML.</span><span class="sxs-lookup"><span data-stu-id="9e40f-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="9e40f-141">Proto typename-as-string chování je vestavěné pro všechny silverlight <xref:System.Type> nativní hodnocení vlastností, kde a je hodnota.</span><span class="sxs-lookup"><span data-stu-id="9e40f-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>

## <a name="xaml-2009"></a><span data-ttu-id="9e40f-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="9e40f-142">XAML 2009</span></span>

<span data-ttu-id="9e40f-143">XAML 2009 poskytuje další podporu pro obecné typy a `x:TypeArguments` `x:Type` upravuje chování funkcí a poskytovat tuto podporu.</span><span class="sxs-lookup"><span data-stu-id="9e40f-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>

- <span data-ttu-id="9e40f-144">`x:TypeArguments`a přidružený prvek objektu pro instanci obecného objektu může být na jiné prvky než kořen.</span><span class="sxs-lookup"><span data-stu-id="9e40f-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="9e40f-145">Další informace naleznete v části "XAML 2009" [x:TypeArguments směrnice](xtypearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="9e40f-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

- <span data-ttu-id="9e40f-146">XAML 2009 podporuje syntaxi pro určení omezení obecného typu ve značkách.</span><span class="sxs-lookup"><span data-stu-id="9e40f-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="9e40f-147">To může používat `x:TypeArguments`, `x:Type`, nebo dva prvky v kombinaci.</span><span class="sxs-lookup"><span data-stu-id="9e40f-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>

- <span data-ttu-id="9e40f-148">WPF XAML implementace při zpracování XAML 2009 pro zatížení také přidá tuto možnost <xref:System.Type>implicitní chování převodu typu pro určité vlastnosti rozhraní, které používají typ .</span><span class="sxs-lookup"><span data-stu-id="9e40f-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>

<span data-ttu-id="9e40f-149">V WPF můžete použít funkce XAML 2009, ale pouze pro volné XAML (XAML, který není zkompilován značky).</span><span class="sxs-lookup"><span data-stu-id="9e40f-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="9e40f-150">XAML kompilované značkami pro WPF a formu BAML XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="9e40f-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e40f-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e40f-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="9e40f-152">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9e40f-152">Styling and Templating</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="9e40f-153">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="9e40f-153">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="9e40f-154">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="9e40f-154">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
