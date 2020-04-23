---
title: x:Array – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b332c43d7f9ffe2117c9afe1ed625c3e3c869813
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072044"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="3be5a-102">x:Array – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="3be5a-102">x:Array Markup Extension</span></span>

<span data-ttu-id="3be5a-103">Poskytuje obecnou podporu pro pole objektů v XAML prostřednictvím rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="3be5a-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="3be5a-104">To odpovídá typu `x:ArrayExtension` XAML v [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="3be5a-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="3be5a-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="3be5a-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="3be5a-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="3be5a-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="3be5a-107">Název typu, který `x:Array` bude obsahovat.</span><span class="sxs-lookup"><span data-stu-id="3be5a-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="3be5a-108">`typeName`může být (a často je) předponou pro obor názvů XAML, který obsahuje definice typu XAML.</span><span class="sxs-lookup"><span data-stu-id="3be5a-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="3be5a-109">Obsah položek, který je přiřazen k `ArrayExtension.Items` vnitřní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3be5a-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="3be5a-110">Tyto položky jsou obvykle určeny jako jeden nebo `x:Array` více prvků objektu obsažených v otevírací a uzavírací značky.</span><span class="sxs-lookup"><span data-stu-id="3be5a-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="3be5a-111">Očekává se, že zde zadané objekty budou přiřaditelné typu XAML určenému v . `typeName`</span><span class="sxs-lookup"><span data-stu-id="3be5a-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3be5a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3be5a-112">Remarks</span></span>

<span data-ttu-id="3be5a-113">`Type`je povinný atribut `x:Array` pro všechny prvky objektu.</span><span class="sxs-lookup"><span data-stu-id="3be5a-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="3be5a-114">Hodnota `Type` parametru nemusí používat `x:Type` rozšíření značek; krátký název typu je typ XAML, který lze zadat jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="3be5a-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="3be5a-115">V implementaci služby .NET XAML Services je vztah mezi vstupním typem XAML a výstupním CLR <xref:System.Type> vytvořeného pole ovlivněn kontextem služby pro rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="3be5a-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="3be5a-116">Výstup <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupní typ XAML, po vyhledání nezbytné <xref:System.Xaml.XamlType> na základě kontextu schématu <xref:System.Windows.Markup.IXamlTypeResolver> XAML a služby, které poskytuje kontext.</span><span class="sxs-lookup"><span data-stu-id="3be5a-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="3be5a-117">Při zpracování jsou obsah pole přiřazen `ArrayExtension.Items` y vnitřní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3be5a-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="3be5a-118">V <xref:System.Windows.Markup.ArrayExtension> implementaci je to <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>reprezentováno .</span><span class="sxs-lookup"><span data-stu-id="3be5a-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3be5a-119">V implementaci služby .NET XAML Services je zpracování <xref:System.Windows.Markup.ArrayExtension> pro toto rozšíření značek definováno třídou.</span><span class="sxs-lookup"><span data-stu-id="3be5a-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="3be5a-120"><xref:System.Windows.Markup.ArrayExtension>není zapečetěna a může být použita jako základ pro implementaci rozšíření značky pro vlastní typ pole.</span><span class="sxs-lookup"><span data-stu-id="3be5a-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="3be5a-121">`x:Array`je více určen pro obecné rozšiřitelnost jazyka v XAML.</span><span class="sxs-lookup"><span data-stu-id="3be5a-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="3be5a-122">Ale `x:Array` může být také užitečné pro určení hodnot XAML určité vlastnosti, které berou XAML podporované kolekce jako jejich obsah strukturované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3be5a-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="3be5a-123">Můžete například zadat obsah <xref:System.Collections.IEnumerable> vlastnosti s `x:Array` použitím.</span><span class="sxs-lookup"><span data-stu-id="3be5a-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="3be5a-124">`x:Array`je rozšíření značky.</span><span class="sxs-lookup"><span data-stu-id="3be5a-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="3be5a-125">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3be5a-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="3be5a-126">`x:Array`je částečně výjimkou z tohoto pravidla, protože místo `x:Array` poskytování alternativní zpracování hodnoty atributu poskytuje alternativní zpracování jeho vnitřní obsah textu.</span><span class="sxs-lookup"><span data-stu-id="3be5a-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="3be5a-127">Toto chování umožňuje typy, které nemusí být podporovány existující model obsahu, které mají být seskupeny do pole a odkazoval se později v kódu na pozadí přístupem pojmenované pole; můžete volat <xref:System.Array> metody získat jednotlivé položky pole.</span><span class="sxs-lookup"><span data-stu-id="3be5a-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="3be5a-128">Všechna rozšíření značek v XAML používají{,} `)` závorky ( v syntaxi jejich atributu, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí zpracovat hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="3be5a-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="3be5a-129">Další informace o rozšířeních značek obecně naleznete v [tématu Převaděče typů a Rozšíření značek pro XAML](type-converters-and-markup-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="3be5a-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="3be5a-130">V XAML 2009 `x:Array` je definovánjako jazyk primitivna namísto rozšíření značky.</span><span class="sxs-lookup"><span data-stu-id="3be5a-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="3be5a-131">Další informace naleznete [v tématu Předdefinované typy pro běžné jazyková primitiva XAML](types-for-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="3be5a-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="3be5a-132">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="3be5a-132">WPF Usage Notes</span></span>

<span data-ttu-id="3be5a-133">Prvky objektu, které `x:Array` nabývají, obvykle nejsou [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] prvky, které existují v oboru názvů XAML a vyžadují mapování předpony na obor názvů XAML, který není výchozí.</span><span class="sxs-lookup"><span data-stu-id="3be5a-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="3be5a-134">Například následující je jednoduché pole dvou řetězců s `sys` předponou `x`(a také ) definovanou na úrovni pole.</span><span class="sxs-lookup"><span data-stu-id="3be5a-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="3be5a-135">Pro vlastní typy, které se používají jako prvky pole, musí třída také podporovat požadavky na vytvoření instance v XAML jako objektové prvky.</span><span class="sxs-lookup"><span data-stu-id="3be5a-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="3be5a-136">Další informace naleznete v tématu [XAML a vlastní třídy pro WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="3be5a-136">For more information, see [XAML and Custom Classes for WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3be5a-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="3be5a-137">See also</span></span>

- [<span data-ttu-id="3be5a-138">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="3be5a-138">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="3be5a-139">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="3be5a-139">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
