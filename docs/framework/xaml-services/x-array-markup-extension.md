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
ms.openlocfilehash: 7c728b63c16d8f24c4ad68d07e6d174f510204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565010"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="96e76-102">x:Array – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="96e76-102">x:Array Markup Extension</span></span>
<span data-ttu-id="96e76-103">Poskytuje obecné podporu pro pole objektů v jazyce XAML prostřednictvím rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="96e76-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="96e76-104">To odpovídá `x:ArrayExtension` typ jazyka XAML v [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="96e76-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="96e76-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="96e76-105">XAML Object Element Usage</span></span>  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="96e76-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="96e76-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="96e76-107">Název typu, vaše `x:Array` bude obsahovat.</span><span class="sxs-lookup"><span data-stu-id="96e76-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="96e76-108">`typeName` může být (a často je) předponu pro jazyk XAML zadejte obor názvů, který obsahuje XAML definice.</span><span class="sxs-lookup"><span data-stu-id="96e76-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="96e76-109">Obsah položky, který je přiřazen k vnitřní `ArrayExtension.Items` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="96e76-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="96e76-110">Obvykle jsou tyto položky zadané jako jeden nebo více objektů elementů obsažených v rámci `x:Array` otvírání a zavírání značky.</span><span class="sxs-lookup"><span data-stu-id="96e76-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="96e76-111">Zadat objekty v tomto poli se měl přiřaditelné k typu XAML zadaný v `typeName`.</span><span class="sxs-lookup"><span data-stu-id="96e76-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96e76-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96e76-112">Remarks</span></span>  
 <span data-ttu-id="96e76-113">`Type` je povinný atribut pro všechny `x:Array` objektu elementy.</span><span class="sxs-lookup"><span data-stu-id="96e76-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="96e76-114">A `Type` hodnota parametru není nutné používat `x:Type` – rozšíření značek; krátké název typu je typ jazyka XAML, které lze zadat jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="96e76-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="96e76-115">V rozhraní .NET Framework XAML Services implementace, o vztah mezi vstupní typ jazyka XAML a výstup CLR <xref:System.Type> vytvořený pole je ovlivněno kontext služby pro rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="96e76-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="96e76-116">Výstup <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupní typu XAML, po vyhledávání nezbytné <xref:System.Xaml.XamlType> na základě kontextu schématu XAML a <xref:System.Windows.Markup.IXamlTypeResolver> service poskytuje kontext.</span><span class="sxs-lookup"><span data-stu-id="96e76-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="96e76-117">Při zpracování, že je obsah pole jsou přiřazeny `ArrayExtension.Items` vnitřní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="96e76-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="96e76-118">V <xref:System.Windows.Markup.ArrayExtension> implementace, to je reprezentována <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="96e76-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="96e76-119">Implementace rozhraní .NET Framework XAML Services je definované zpracování pro toto rozšíření značek <xref:System.Windows.Markup.ArrayExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="96e76-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="96e76-120"><xref:System.Windows.Markup.ArrayExtension> není zapečetěná a může jako základ pro implementaci rozšíření značek pro typ vlastní pole.</span><span class="sxs-lookup"><span data-stu-id="96e76-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="96e76-121">`x:Array` je že více určený pro obecné rozšiřitelnosti jazyka v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="96e76-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="96e76-122">Ale `x:Array` může být také užitečná pro zadání hodnoty XAML určité vlastnosti, které provést podporované XAML kolekce jako strukturovaný vlastnost obsah.</span><span class="sxs-lookup"><span data-stu-id="96e76-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="96e76-123">Například můžete zadat obsah <xref:System.Collections.IEnumerable> vlastnost s `x:Array` využití.</span><span class="sxs-lookup"><span data-stu-id="96e76-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="96e76-124">`x:Array` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="96e76-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="96e76-125">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="96e76-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="96e76-126">`x:Array` je částečně výjimkou tohoto pravidla, protože místo zpracování hodnota atributu alternativní, `x:Array` poskytuje alternativní zpracování část jeho obsahu vnitřní text.</span><span class="sxs-lookup"><span data-stu-id="96e76-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="96e76-127">Toto chování umožňuje typy, které nemusí být podporován pomocí existujícího modelu obsahu seskupeny do pole a odkazuje později v kódu přístup k poli s názvem; můžete volat <xref:System.Array> metody k načtení pole jednotlivých položek.</span><span class="sxs-lookup"><span data-stu-id="96e76-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="96e76-128">Všechna rozšíření značek v jazyce XAML použít složené závorky ({,} `)` v jejich syntaxi atribut, který je konvence, podle kterého XAML procesor rozpozná, že rozšíření značek musí zpracovat hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="96e76-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="96e76-129">Další informace o rozšíření značek v obecné najdete v tématu [převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="96e76-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="96e76-130">V jazyce XAML 2009 `x:Array` je definován jako jazyk primitivní místo rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="96e76-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="96e76-131">Další informace najdete v tématu [předdefinované typy obecných primitiv jazyka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="96e76-131">For more information, see [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="96e76-132">Poznámky pro použití WPF</span><span class="sxs-lookup"><span data-stu-id="96e76-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="96e76-133">Obvykle objekt prvky, které naplnit `x:Array` nejsou elementy, které existují v [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] oboru názvů jazyka XAML a vyžadovat předponu mapování do oboru názvů jazyka XAML, jiné než výchozí.</span><span class="sxs-lookup"><span data-stu-id="96e76-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="96e76-134">Například následující je jednoduché pole dva řetězce, pomocí `sys` předpony (a také `x`) definované na úrovni pole.</span><span class="sxs-lookup"><span data-stu-id="96e76-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
 <span data-ttu-id="96e76-135">[xaml]</span><span class="sxs-lookup"><span data-stu-id="96e76-135">[xaml]</span></span>  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 <span data-ttu-id="96e76-136">Pro vlastní typy, které se používají jako elementy pole musí podporovat třídu i požadavky na vytváření instancí v jazyce XAML jako elementy objektu.</span><span class="sxs-lookup"><span data-stu-id="96e76-136">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="96e76-137">Další informace najdete v tématu [XAML a vlastní třídy pro grafický subsystém WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="96e76-137">For more information, see [XAML and Custom Classes for WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e76-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="96e76-138">See Also</span></span>  
 [<span data-ttu-id="96e76-139">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="96e76-139">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="96e76-140">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="96e76-140">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
