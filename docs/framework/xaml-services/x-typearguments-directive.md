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
ms.openlocfilehash: 2e64c716ee85934bf02c016ee408b8e5f612a819
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837191"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="45db6-102">x:TypeArguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="45db6-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="45db6-103">Předává omezující argumenty typu Obecné k konstruktoru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="45db6-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="45db6-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="45db6-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="45db6-105">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="45db6-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="45db6-106">Deklarace elementu objektu typu XAML, který je zálohovaný obecným typem CLR.</span><span class="sxs-lookup"><span data-stu-id="45db6-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="45db6-107">Pokud `object` odkazuje na typ XAML, který není z výchozího oboru názvů jazyka XAML, `object` vyžaduje předponu k označení oboru názvů XAML, kde `object` existuje.</span><span class="sxs-lookup"><span data-stu-id="45db6-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="45db6-108">Řetězec, který deklaruje jeden nebo více názvů typů XAML jako řetězců, které poskytuje argumenty typu pro obecný typ CLR.</span><span class="sxs-lookup"><span data-stu-id="45db6-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="45db6-109">Další poznámky k syntaxi najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="45db6-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45db6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45db6-110">Remarks</span></span>  
 <span data-ttu-id="45db6-111">Ve většině případů jsou typy XAML, které jsou používány jako informační položka v řetězci `typeString`, předem opraveny.</span><span class="sxs-lookup"><span data-stu-id="45db6-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="45db6-112">Typické typy obecných omezení CLR (například <xref:System.Int32> a <xref:System.String>) pocházejí z knihoven základních tříd CLR.</span><span class="sxs-lookup"><span data-stu-id="45db6-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="45db6-113">Tyto knihovny nejsou namapovány na typické standardní obory názvů jazyka XAML specifické pro rozhraní, a proto vyžadují mapování předpony pro použití XAML.</span><span class="sxs-lookup"><span data-stu-id="45db6-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="45db6-114">Pomocí oddělovače čárky lze zadat více než jeden název typu XAML.</span><span class="sxs-lookup"><span data-stu-id="45db6-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="45db6-115">Pokud obecná omezení samy používají obecné typy, vnořené argumenty typu omezení mohou být obsaženy v závorkách ().</span><span class="sxs-lookup"><span data-stu-id="45db6-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="45db6-116">Všimněte si, že tato definice `x:TypeArguments` je specifická pro .NET Framework služby XAML a pomocí zálohování CLR.</span><span class="sxs-lookup"><span data-stu-id="45db6-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="45db6-117">Definici na úrovni jazyka najdete v [\[MS-XAML\] oddílu 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="45db6-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="45db6-118">Příklady použití</span><span class="sxs-lookup"><span data-stu-id="45db6-118">Usage Examples</span></span>  
 <span data-ttu-id="45db6-119">Pro tyto příklady Předpokládejme, že jsou deklarovány následující definice oboru názvů XAML:</span><span class="sxs-lookup"><span data-stu-id="45db6-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="45db6-120">Seznam\<řetězců ></span><span class="sxs-lookup"><span data-stu-id="45db6-120">List\<String></span></span>  
 <span data-ttu-id="45db6-121">`<scg:List x:TypeArguments="sys:String" ...>` vytvoří instanci nového <xref:System.Collections.Generic.List%601> s argumentem <xref:System.String>ho typu.</span><span class="sxs-lookup"><span data-stu-id="45db6-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="45db6-122">Řetězec\<slovníku, řetězec ></span><span class="sxs-lookup"><span data-stu-id="45db6-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="45db6-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` vytvoří instanci nového <xref:System.Collections.Generic.Dictionary%602> se dvěma argumenty <xref:System.String>ho typu.</span><span class="sxs-lookup"><span data-stu-id="45db6-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="45db6-124">Queue < nenašla\<řetězec, řetězec > ></span><span class="sxs-lookup"><span data-stu-id="45db6-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="45db6-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` vytvoří instanci nového <xref:System.Collections.Generic.Queue%601>, která má omezení <xref:System.Collections.Generic.KeyValuePair%602> s argumenty typu vnitřního omezení <xref:System.String> a <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="45db6-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="45db6-126">Obecná použití XAML XAML 2006 a WPF</span><span class="sxs-lookup"><span data-stu-id="45db6-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="45db6-127">Pro použití XAML 2006 a XAML, které se používají pro aplikace WPF, existují následující omezení pro `x:TypeArguments` a obecné typy použití z XAML obecně:</span><span class="sxs-lookup"><span data-stu-id="45db6-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
- <span data-ttu-id="45db6-128">Pouze kořenový prvek souboru XAML může podporovat obecné použití XAML, které odkazuje na obecný typ.</span><span class="sxs-lookup"><span data-stu-id="45db6-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
- <span data-ttu-id="45db6-129">Kořenový element musí být namapován na obecný typ s alespoň jedním argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="45db6-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="45db6-130">Příklad: <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="45db6-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="45db6-131">Funkce stránky jsou primární scénář pro podporu obecného použití XAML v jazyce WPF.</span><span class="sxs-lookup"><span data-stu-id="45db6-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
- <span data-ttu-id="45db6-132">Element objektu XAML kořenového elementu pro obecný musí také deklarovat částečnou třídu pomocí `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="45db6-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="45db6-133">To platí i v případě, že definujete akci sestavení WPF.</span><span class="sxs-lookup"><span data-stu-id="45db6-133">This is true even if defining a WPF build action.</span></span>  
  
- <span data-ttu-id="45db6-134">`x:TypeArguments` nemůže odkazovat na vnořená obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="45db6-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="45db6-135">XAML 2009 nebo XAML 2006 bez závislosti WPF 3,0 nebo WPF 3,5</span><span class="sxs-lookup"><span data-stu-id="45db6-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="45db6-136">V jazyce .NET Framework XAML pro XAML 2006 nebo XAML 2009 jsou omezení související s WPF pro obecné použití XAML uvolněna.</span><span class="sxs-lookup"><span data-stu-id="45db6-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="45db6-137">Můžete vytvořit instanci obecného prvku objektu na libovolné pozici v kódu XAML, který může podporovat systém back-Type a objektový model.</span><span class="sxs-lookup"><span data-stu-id="45db6-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="45db6-138">Použijete-li XAML 2009 namísto mapování základních typů CLR pro získání typů XAML pro společné jazykové primitivy, můžete použít [vestavěné typy pro běžné primitivní prvky jazyka XAML](built-in-types-for-common-xaml-language-primitives.md) jako informační položky v `typeString`.</span><span class="sxs-lookup"><span data-stu-id="45db6-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="45db6-139">Například můžete deklarovat následující (mapování předpon není zobrazeno, ale x je obor názvů XAML jazyka XAML pro XAML 2009):</span><span class="sxs-lookup"><span data-stu-id="45db6-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="45db6-140">V jazyce WPF a při cílení na .NET Framework 4 můžete použít funkce XAML 2009 společně s `x:TypeArguments`, ale pouze pro volné XAML (XAML bez kódu kompilováno).</span><span class="sxs-lookup"><span data-stu-id="45db6-140">In WPF and when targeting .NET Framework 4, you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="45db6-141">XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="45db6-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="45db6-142">Pokud potřebujete kód zkompilovat do kódu XAML, je nutné pracovat s omezeními v části "XAML 2006 and WPF Generic XAML".</span><span class="sxs-lookup"><span data-stu-id="45db6-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45db6-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45db6-143">See also</span></span>

- [<span data-ttu-id="45db6-144">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="45db6-144">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="45db6-145">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="45db6-145">x:Type Markup Extension</span></span>](x-type-markup-extension.md)
- [<span data-ttu-id="45db6-146">Předdefinované typy obecných primitiv jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="45db6-146">Built-in Types for Common XAML Language Primitives</span></span>](built-in-types-for-common-xaml-language-primitives.md)
- [<span data-ttu-id="45db6-147">Obecné typy v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="45db6-147">Generics in XAML</span></span>](generics-in-xaml.md)
