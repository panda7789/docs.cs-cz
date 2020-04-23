---
title: x:TypeArguments – direktiva
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071351"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="809c2-102">x:TypeArguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="809c2-102">x:TypeArguments Directive</span></span>

<span data-ttu-id="809c2-103">Předá argumenty typu omezující typu obecného konstruktoru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="809c2-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="809c2-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="809c2-104">XAML Attribute Usage</span></span>

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="809c2-105">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="809c2-105">XAML Values</span></span>

|||
|-|-|
|`object`|<span data-ttu-id="809c2-106">Deklarace prvku objektu typu XAML, která je podpořena obecným typem CLR.</span><span class="sxs-lookup"><span data-stu-id="809c2-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="809c2-107">Pokud `object` odkazuje na typ XAML, který není z výchozího `object` oboru názvů XAML, vyžaduje předponu k označení oboru názvů XAML, kde `object` existuje.</span><span class="sxs-lookup"><span data-stu-id="809c2-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|
|`typeString`|<span data-ttu-id="809c2-108">Řetězec, který deklaruje jeden nebo více názvů typů XAML jako řetězce, který poskytuje argumenty typu pro obecný typ CLR.</span><span class="sxs-lookup"><span data-stu-id="809c2-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="809c2-109">Další poznámky k syntaxi naleznete v tématu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="809c2-109">See Remarks for additional syntax notes.</span></span>|

## <a name="remarks"></a><span data-ttu-id="809c2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="809c2-110">Remarks</span></span>

<span data-ttu-id="809c2-111">Ve většině případů jsou předponou typy XAML, `typeString` které se používají jako informační položka v řetězci.</span><span class="sxs-lookup"><span data-stu-id="809c2-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="809c2-112">Typické typy obecných omezení CLR <xref:System.Int32> (například a <xref:System.String>) pocházejí z knihoven základní třídy CLR.</span><span class="sxs-lookup"><span data-stu-id="809c2-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="809c2-113">Tyto knihovny nejsou mapovány na typické výchozí prostory názvů XAML specifické pro architekturu, a proto vyžadují mapování předpony pro použití XAML.</span><span class="sxs-lookup"><span data-stu-id="809c2-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>

<span data-ttu-id="809c2-114">Pomocí oddělovače čárky můžete zadat více než jeden název typu XAML.</span><span class="sxs-lookup"><span data-stu-id="809c2-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>

<span data-ttu-id="809c2-115">Pokud samotná obecná omezení používají obecné typy, mohou být vnořené argumenty typu omezení obsaženy v závorcích ().</span><span class="sxs-lookup"><span data-stu-id="809c2-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>

<span data-ttu-id="809c2-116">Všimněte si, `x:TypeArguments` že tato definice je specifická pro služby .NET XAML services a pomocí podpory CLR.</span><span class="sxs-lookup"><span data-stu-id="809c2-116">Note that this definition of `x:TypeArguments` is specific to .NET XAML Services and using CLR backing.</span></span> <span data-ttu-id="809c2-117">Definici na úrovni jazyka naleznete v [ \[oddíle\] 5.3.11 MS-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="809c2-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="usage-examples"></a><span data-ttu-id="809c2-118">Příklady použití</span><span class="sxs-lookup"><span data-stu-id="809c2-118">Usage Examples</span></span>

<span data-ttu-id="809c2-119">V těchto příkladech předpokládejme, že jsou deklarovány následující definice oboru názvů XAML:</span><span class="sxs-lookup"><span data-stu-id="809c2-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a><span data-ttu-id="809c2-120">>\<řetězce seznamu</span><span class="sxs-lookup"><span data-stu-id="809c2-120">List\<String></span></span>

<span data-ttu-id="809c2-121">`<scg:List x:TypeArguments="sys:String" ...>`kvituje <xref:System.Collections.Generic.List%601> nový <xref:System.String> s argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="809c2-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>

### <a name="dictionarystringstring"></a><span data-ttu-id="809c2-122">Řetězec\<slovníku,></span><span class="sxs-lookup"><span data-stu-id="809c2-122">Dictionary\<String,String></span></span>

<span data-ttu-id="809c2-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`kvituje <xref:System.Collections.Generic.Dictionary%602> nový <xref:System.String> se dvěma argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="809c2-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>

### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="809c2-124">Řetězec spáry\<KeyValue klíče fronty<,>> řetězce</span><span class="sxs-lookup"><span data-stu-id="809c2-124">Queue<KeyValuePair\<String,String>></span></span>

<span data-ttu-id="809c2-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`konkretizovat <xref:System.Collections.Generic.Queue%601> nový, který <xref:System.Collections.Generic.KeyValuePair%602> má omezení s <xref:System.String> argumenty vnitřní holužní typ a <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="809c2-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="809c2-126">Použití xaml 2006 a WPF obecné xaml</span><span class="sxs-lookup"><span data-stu-id="809c2-126">XAML 2006 and WPF Generic XAML Usages</span></span>

<span data-ttu-id="809c2-127">Pro použití XAML 2006 a XAML, který se používá pro `x:TypeArguments` aplikace WPF, existují následující omezení pro a obecné použití typu z XAML obecně:</span><span class="sxs-lookup"><span data-stu-id="809c2-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>

- <span data-ttu-id="809c2-128">Pouze kořenový prvek souboru XAML může podporovat obecné použití XAML, které odkazuje na obecný typ.</span><span class="sxs-lookup"><span data-stu-id="809c2-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>

- <span data-ttu-id="809c2-129">Kořenový prvek musí být mapován na obecný typ s alespoň jedním argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="809c2-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="809c2-130">Příklad: <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="809c2-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="809c2-131">Funkce stránky jsou primární scénář pro podporu obecného využití XAML v WPF.</span><span class="sxs-lookup"><span data-stu-id="809c2-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>

- <span data-ttu-id="809c2-132">Kořenový prvek XAML objektu element pro obecný `x:Class`musí také deklarovat částečné třídy pomocí .</span><span class="sxs-lookup"><span data-stu-id="809c2-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="809c2-133">To platí i v případě, že definování akce sestavení WPF.</span><span class="sxs-lookup"><span data-stu-id="809c2-133">This is true even if defining a WPF build action.</span></span>

- <span data-ttu-id="809c2-134">`x:TypeArguments`Nelze odkazovat na vnořená obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="809c2-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="809c2-135">XAML 2009 nebo XAML 2006 bez wpf 3.0 nebo WPF 3.5 závislost</span><span class="sxs-lookup"><span data-stu-id="809c2-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>

<span data-ttu-id="809c2-136">Ve službách .NET XAML pro XAML 2006 nebo XAML 2009 jsou uvolněná omezení týkající se WPF pro použití obecného xaml.</span><span class="sxs-lookup"><span data-stu-id="809c2-136">In .NET XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="809c2-137">Můžete vytvořit konstanci elementu obecného objektu na libovolné pozici ve značkách XAML, které může podporovat systém typu zálohování a objektový model.</span><span class="sxs-lookup"><span data-stu-id="809c2-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>

<span data-ttu-id="809c2-138">Pokud používáte XAML 2009 namísto mapování clr základní typy získat xaml typy pro základní jazyk běžné jazykové primitivy, `typeString`můžete použít [vestavěné typy pro běžné xaml jazyk primitiv](types-for-primitives.md) y jako informační položky v .</span><span class="sxs-lookup"><span data-stu-id="809c2-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](types-for-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="809c2-139">Můžete například deklarovat následující (mapování předpony nejsou zobrazena, ale x je jazyk XAML XAML pro XAML 2009):</span><span class="sxs-lookup"><span data-stu-id="809c2-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

<span data-ttu-id="809c2-140">V WPF a při cílení na rozhraní .NET Framework 4 nebo .NET Core 3.0 (nebo novější) můžete používat funkce XAML 2009 společně s, `x:TypeArguments` ale pouze pro volné XAML (XAML, který není kompilován se značkami).</span><span class="sxs-lookup"><span data-stu-id="809c2-140">In WPF and when targeting .NET Framework 4 or .NET Core 3.0 (or later), you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="809c2-141">XAML kompilované značkami pro WPF a formu BAML XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="809c2-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="809c2-142">Pokud potřebujete označit kompilovat XAML, musíte pracovat pod omezeními uvedenými v části [XAML 2006 a WPF Generic XAML Usages.](#xaml-2006-and-wpf-generic-xaml-usages)</span><span class="sxs-lookup"><span data-stu-id="809c2-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the [XAML 2006 and WPF Generic XAML Usages](#xaml-2006-and-wpf-generic-xaml-usages) section.</span></span> <span data-ttu-id="809c2-143">BAML je podporován a podporuje se pouze v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="809c2-143">BAML is only supported in .NET Framework.</span></span>

## <a name="see-also"></a><span data-ttu-id="809c2-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="809c2-144">See also</span></span>

- [<span data-ttu-id="809c2-145">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="809c2-145">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="809c2-146">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="809c2-146">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="809c2-147">Předdefinované typy obecných primitiv jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="809c2-147">Built-in Types for Common XAML Language Primitives</span></span>](types-for-primitives.md)
- [<span data-ttu-id="809c2-148">Obecné typy v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="809c2-148">Generics in XAML</span></span>](generics.md)
