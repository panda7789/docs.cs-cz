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
ms.openlocfilehash: 8acb732841aa7aaaad3e8fdd2cf2962ff44dd60b
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506069"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="fdc1b-102">x:Array – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="fdc1b-102">x:Array Markup Extension</span></span>
<span data-ttu-id="fdc1b-103">Poskytuje obecné podporu pro pole objektů v XAML pomocí rozšíření kódu.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="fdc1b-104">To odpovídá `x:ArrayExtension` typ XAML v [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="fdc1b-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="fdc1b-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="fdc1b-105">XAML Object Element Usage</span></span>  
  
```xaml
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="fdc1b-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="fdc1b-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="fdc1b-107">Název typu, který vaše `x:Array` bude obsahovat.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="fdc1b-108">`typeName` může být (a často je) předponu pro XAML, obor názvů, který obsahuje XAML definice typů.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="fdc1b-109">Obsah položky, která je přiřazena vnitřní `ArrayExtension.Items` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="fdc1b-110">Obvykle tyto položky jsou specifikovány jako jeden nebo více elementů objektu, které jsou obsažené v `x:Array` počátečních a koncových značek.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="fdc1b-111">Objekty zadané tady se má být přiřaditelný k typu XAML určeného v `typeName`.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdc1b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdc1b-112">Remarks</span></span>  
 <span data-ttu-id="fdc1b-113">`Type` je povinný atribut pro všechny `x:Array` objektu elementy.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="fdc1b-114">A `Type` hodnota parametru není nutné používat `x:Type` – rozšíření značek; krátký název typu je typ, XAML, který lze zadat jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="fdc1b-115">V implementaci rozhraní .NET Framework XAML Services, vztah mezi XAML typ vstupu a výstupu CLR <xref:System.Type> vytvořené pole je ovlivněno kontext služby pro rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="fdc1b-116">Výstup <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupní typ XAML po vyhledání nezbytné <xref:System.Xaml.XamlType> založené na kontext schématu XAML a <xref:System.Windows.Markup.IXamlTypeResolver> service poskytuje kontext.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="fdc1b-117">Při zpracování, že je obsah pole jsou přiřazeny k `ArrayExtension.Items` vnitřní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="fdc1b-118">V <xref:System.Windows.Markup.ArrayExtension> implementace, to je reprezentována <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="fdc1b-119">V implementaci rozhraní .NET Framework XAML Services zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.ArrayExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="fdc1b-120"><xref:System.Windows.Markup.ArrayExtension> není zapečetěná a může použít jako základ pro implementaci rozšíření značek pro typ vlastního pole.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="fdc1b-121">`x:Array` je, že informace určené pro běžné rozšiřitelnost jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="fdc1b-122">Ale `x:Array` může také být vhodné při zadání hodnoty XAML určitých vlastností, které trvat XAML nepodporuje kolekce jako strukturované vlastnost obsah.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="fdc1b-123">Můžete například zadat obsah <xref:System.Collections.IEnumerable> vlastnost s `x:Array` využití.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="fdc1b-124">`x:Array` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="fdc1b-125">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="fdc1b-126">`x:Array` výjimkou z tohoto pravidla je částečně, protože namísto zadávání alternativní atribut hodnotu zpracování, `x:Array` poskytuje alternativní zpracování její obsah vnitřní text.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="fdc1b-127">Díky tomuto chování může typy, které nemusí být podporovány existujícího obsahu modelu seskupeny do pole a odkazuje později v modelu code-behind díky přístupu do pojmenované pole. můžete volat <xref:System.Array> metody k získání položek jednotlivá pole.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="fdc1b-128">Všechna rozšíření značek v XAML použít složené závorky ({,} `)` v syntaxi atributu, což je konvence, podle kterého na procesor XAML rozpozná, že rozšíření značek musí zpracovat hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="fdc1b-129">Další informace o rozšíření značek v obecné najdete v tématu [převaděče typů a rozšíření značek pro XAML](type-converters-and-markup-extensions-for-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="fdc1b-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="fdc1b-130">V XAML 2009 `x:Array` je definován jako primitivní místo rozšíření značek jazyka.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="fdc1b-131">Další informace najdete v tématu [předdefinované typy obecných primitiv jazyka XAML](built-in-types-for-common-xaml-language-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="fdc1b-131">For more information, see [Built-in Types for Common XAML Language Primitives](built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="fdc1b-132">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="fdc1b-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="fdc1b-133">Obvykle elementů objektu, která naplní `x:Array` nejsou prvky, které existují v [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] oboru názvů XAML a vyžadují mapování předpony oboru názvů XAML jiné než výchozí.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="fdc1b-134">Například tady je jednoduchý pole dvou řetězců s `sys` předpony (a také `x`) definované na úrovni pole.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
```xaml
<x:Array Type="sys:String"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:sys="clr-namespace:System;assembly=mscorlib">
    <sys:String>Hello</sys:String>
    <sys:String>World</sys:String>
</x:Array>
```
  
 <span data-ttu-id="fdc1b-135">Pro vlastní typy, které se používají jako prvky pole musí podporovat třídu také požadavky pro instance v XAML jako elementů objektu.</span><span class="sxs-lookup"><span data-stu-id="fdc1b-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="fdc1b-136">Další informace najdete v tématu [XAML a vlastní třídy pro WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="fdc1b-136">For more information, see [XAML and Custom Classes for WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc1b-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdc1b-137">See also</span></span>

- [<span data-ttu-id="fdc1b-138">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="fdc1b-138">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="fdc1b-139">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="fdc1b-139">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
