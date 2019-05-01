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
ms.openlocfilehash: 1d1b10b4da1263843bdce5447f0716569c7700e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982589"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="a4cb8-102">x:TypeArguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="a4cb8-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="a4cb8-103">Předá omezení argumentů obecného konstruktoru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="a4cb8-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="a4cb8-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="a4cb8-105">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="a4cb8-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="a4cb8-106">Deklarace elementu objektu XAML typu, který se zálohuje pomocí obecného typu CLR.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="a4cb8-107">Pokud `object` odkazuje na typ XAML, který nepochází od výchozí obor názvů XAML, `object` vyžaduje předpona k označení oboru názvů XAML kde `object` existuje.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="a4cb8-108">Řetězec, který deklaruje nejmíň jeden XAML zadejte názvy jako řetězce, který poskytuje argumentů typu pro obecný typ CLR.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="a4cb8-109">Viz poznámky pro další syntaxe poznámky.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4cb8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4cb8-110">Remarks</span></span>  
 <span data-ttu-id="a4cb8-111">Ve většině případů XAML typy, které se používají jako položka informace `typeString` mají předponu řetězec.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="a4cb8-112">Obvyklé typy CLR obecná omezení (například <xref:System.Int32> a <xref:System.String>) pocházejí z knihovny základních tříd CLR.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="a4cb8-113">Tyto knihovny nejsou namapované na typické výchozí specifické pro architekturu obory názvů XAML a proto vyžadovat mapování předpony pro využití XAML.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="a4cb8-114">S použitím oddělovače čárky můžete zadat více než jeden název typu XAML.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="a4cb8-115">Obecná omezení sami použití obecných typů, typů argumentů vnořené omezení může být obsažený ve závorky ().</span><span class="sxs-lookup"><span data-stu-id="a4cb8-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="a4cb8-116">Všimněte si, že tato definice `x:TypeArguments` je specifická pro rozhraní .NET Framework XAML Services a pomocí CLR zálohování.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="a4cb8-117">Definice úrovni jazyka najdete v [ \[MS-XAML\] části 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="a4cb8-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="a4cb8-118">Příklady použití</span><span class="sxs-lookup"><span data-stu-id="a4cb8-118">Usage Examples</span></span>  
 <span data-ttu-id="a4cb8-119">Tyto příklady předpokládají, že jsou deklarovány následující definice oboru názvů XAML:</span><span class="sxs-lookup"><span data-stu-id="a4cb8-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="a4cb8-120">Seznam\<řetězec ></span><span class="sxs-lookup"><span data-stu-id="a4cb8-120">List\<String></span></span>  
 <span data-ttu-id="a4cb8-121">`<scg:List x:TypeArguments="sys:String" ...>` Vytvoří novou instanci <xref:System.Collections.Generic.List%601> s <xref:System.String> argument typu.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="a4cb8-122">Slovník\<String, String ></span><span class="sxs-lookup"><span data-stu-id="a4cb8-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="a4cb8-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` Vytvoří novou instanci <xref:System.Collections.Generic.Dictionary%602> se dvěma <xref:System.String> argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="a4cb8-124">Fronty < nenašla\<String, String >></span><span class="sxs-lookup"><span data-stu-id="a4cb8-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="a4cb8-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` Vytvoří novou instanci <xref:System.Collections.Generic.Queue%601> , který má omezení <xref:System.Collections.Generic.KeyValuePair%602> s argumenty typu vnitřní omezení, které <xref:System.String> a <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="a4cb8-126">XAML 2006 a WPF XAML obecné použití</span><span class="sxs-lookup"><span data-stu-id="a4cb8-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="a4cb8-127">Pro použití XAML 2006 a XAML, který se používá pro aplikace WPF, existují následující omezení pro `x:TypeArguments` a použití obecného typu z XAML v obecné:</span><span class="sxs-lookup"><span data-stu-id="a4cb8-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
- <span data-ttu-id="a4cb8-128">Kořenový element souboru XAML může podporovat obecný využití XAML, který odkazuje na obecném typu.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
- <span data-ttu-id="a4cb8-129">Kořenový element musí být namapovaný na obecný typ s alespoň jeden argument typu.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="a4cb8-130">Příklad: <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="a4cb8-131">Funkce stránky jsou primární scénáře pro podporu obecných využití XAML v subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
- <span data-ttu-id="a4cb8-132">Kořenový prvek XAML objekt elementu obecné musí také deklarovat částečné třídy pomocí `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="a4cb8-133">To platí i v případě, že definice WPF akci sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-133">This is true even if defining a WPF build action.</span></span>  
  
- <span data-ttu-id="a4cb8-134">`x:TypeArguments` nemůže odkazovat na vnořených obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="a4cb8-135">XAML 2009 nebo XAML 2006 bez WPF 3.0 nebo WPF 3.5 závislostí</span><span class="sxs-lookup"><span data-stu-id="a4cb8-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="a4cb8-136">V rozhraní .NET Framework XAML Services pro XAML 2006 nebo XAML 2009 jsou mírnější omezení související s WPF v použití obecného XAML.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="a4cb8-137">Generický objekt elementu v jakékoliv pozici v kódu XAML, které podporují základní typ systému a objekt modelu lze vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="a4cb8-138">Pokud používáte XAML 2009 místo mapování CLR základní typy získat primitiv jazyka XAML typy, můžete použít [předdefinované typy obecných primitiv jazyka XAML](built-in-types-for-common-xaml-language-primitives.md) jako informačních položek v `typeString`.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="a4cb8-139">Například můžete deklarovat následující (mapování předpon, které nejsou uvedené, ale x je obor názvů jazyka XAML XAML pro XAML 2009):</span><span class="sxs-lookup"><span data-stu-id="a4cb8-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="a4cb8-140">V grafickém subsystému WPF a při cílení na [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], je možné použít funkce XAML 2009 spolu s `x:TypeArguments` , ale pouze pro volný XAML (XAML, který není kompilována značka).</span><span class="sxs-lookup"><span data-stu-id="a4cb8-140">In WPF and when targeting [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="a4cb8-141">Kompilována značka XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova XAML 2009 a funkce.</span><span class="sxs-lookup"><span data-stu-id="a4cb8-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="a4cb8-142">Pokud třeba do kódu kompilaci XAML, musí pracovat v rámci omezení, které jste si poznamenali v části "XAML 2006 a WPF obecný XAML použití".</span><span class="sxs-lookup"><span data-stu-id="a4cb8-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4cb8-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4cb8-143">See also</span></span>

- [<span data-ttu-id="a4cb8-144">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="a4cb8-144">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="a4cb8-145">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="a4cb8-145">x:Type Markup Extension</span></span>](x-type-markup-extension.md)
- [<span data-ttu-id="a4cb8-146">Předdefinované typy obecných primitiv jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="a4cb8-146">Built-in Types for Common XAML Language Primitives</span></span>](built-in-types-for-common-xaml-language-primitives.md)
- [<span data-ttu-id="a4cb8-147">Obecné typy v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="a4cb8-147">Generics in XAML</span></span>](generics-in-xaml.md)
