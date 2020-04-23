---
title: x:Static – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072023"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="5ef10-102">x:Static – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="5ef10-102">x:Static Markup Extension</span></span>

<span data-ttu-id="5ef10-103">Odkazuje na libovolnou statickou entitu kódu podle hodnoty, která je definována způsobem kompatibilním se specifikací common language (CLS).</span><span class="sxs-lookup"><span data-stu-id="5ef10-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="5ef10-104">Statickou vlastnost, na kterou se odkazuje, lze použít k poskytnutí hodnoty vlastnosti v xaml.</span><span class="sxs-lookup"><span data-stu-id="5ef10-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="5ef10-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="5ef10-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="5ef10-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="5ef10-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="5ef10-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5ef10-107">Optional.</span></span> <span data-ttu-id="5ef10-108">Předpona, která odkazuje na mapovaný, nevýchozí obor názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="5ef10-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="5ef10-109">`prefix`je v použití explicitně zobrazena, protože zřídka kdy odkazujete na statické vlastnosti, které pocházejí z výchozího oboru názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="5ef10-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="5ef10-110">Viz Poznámky.</span><span class="sxs-lookup"><span data-stu-id="5ef10-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="5ef10-111">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5ef10-111">Required.</span></span> <span data-ttu-id="5ef10-112">Název typu, který definuje požadovaný statický člen.</span><span class="sxs-lookup"><span data-stu-id="5ef10-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="5ef10-113">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5ef10-113">Required.</span></span> <span data-ttu-id="5ef10-114">Název členu požadované statické hodnoty (konstanta, statická vlastnost, pole nebo hodnota výčtu).</span><span class="sxs-lookup"><span data-stu-id="5ef10-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ef10-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ef10-115">Remarks</span></span>

<span data-ttu-id="5ef10-116">Entita kódu, na kterou se odkazuje, musí být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="5ef10-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="5ef10-117">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5ef10-117">A constant</span></span>
- <span data-ttu-id="5ef10-118">Statická vlastnost</span><span class="sxs-lookup"><span data-stu-id="5ef10-118">A static property</span></span>
- <span data-ttu-id="5ef10-119">Pole</span><span class="sxs-lookup"><span data-stu-id="5ef10-119">A field</span></span>
- <span data-ttu-id="5ef10-120">Hodnota výčtu</span><span class="sxs-lookup"><span data-stu-id="5ef10-120">An enumeration value</span></span>

<span data-ttu-id="5ef10-121">Zadání jakékoli jiné entity kódu, jako je například nestatická vlastnost, způsobí chybu v době kompilace, pokud je zkompilován kód XAML nebo výjimka analýzy doby načítání XAML.</span><span class="sxs-lookup"><span data-stu-id="5ef10-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="5ef10-122">Můžete odkazovat `x:Static` na statická pole nebo vlastnosti, které nejsou ve výchozím oboru názvů XAML pro aktuální dokument XAML. to však vyžaduje mapování předpony.</span><span class="sxs-lookup"><span data-stu-id="5ef10-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="5ef10-123">Obory názvů XAML jsou téměř vždy definovány v kořenovém prvku dokumentu XAML.</span><span class="sxs-lookup"><span data-stu-id="5ef10-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="5ef10-124">Vyhledávací operace pro statické vlastnosti mohou být prováděny službou .NET XAML Services a jejími čtečkami XAML a zapisovači XAML, pokud jsou spuštěny s výchozím kontextem schématu XAML.</span><span class="sxs-lookup"><span data-stu-id="5ef10-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="5ef10-125">Tento kontext schématu XAML můžete použít odraz CLR poskytnout potřebné statické hodnoty pro konstrukci grafu objektu.</span><span class="sxs-lookup"><span data-stu-id="5ef10-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="5ef10-126">Vámi `typeName` zadaný je ve skutečnosti název typu XAML, nikoli název typu CLR, i když se jedná v podstatě o stejný název při použití výchozího kontextu schématu XAML nebo při použití všech existujících rozhraní pro implementaci XAML založených na CLR.</span><span class="sxs-lookup"><span data-stu-id="5ef10-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="5ef10-127">Buďte opatrní při `x:Static` odkazech, které nejsou přímo typu hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5ef10-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="5ef10-128">V posloupnosti zpracování XAML zadaných hodnot z rozšíření značek nevyvolávají převod další hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5ef10-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="5ef10-129">To platí i `x:Static` v případě, že váš odkaz vytvoří textový řetězec a převod hodnoty pro hodnoty atributů na základě textového řetězce obvykle dochází buď pro konkrétního člena, nebo pro všechny členské hodnoty návratového typu.</span><span class="sxs-lookup"><span data-stu-id="5ef10-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="5ef10-130">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="5ef10-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="5ef10-131">Token řetězce zadaný `x:Static` po přidělení řetězce <xref:System.Windows.Markup.StaticExtension.Member%2A> identifikátoru jako <xref:System.Windows.Markup.StaticExtension> hodnota základní třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5ef10-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="5ef10-132">Existují dvě další použití XAML, které jsou technicky možné.</span><span class="sxs-lookup"><span data-stu-id="5ef10-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="5ef10-133">Tato použití jsou však méně časté, protože jsou zbytečně podrobné:</span><span class="sxs-lookup"><span data-stu-id="5ef10-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="5ef10-134">Syntaxe prvku objektu.</span><span class="sxs-lookup"><span data-stu-id="5ef10-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="5ef10-135">Syntaxe atributu s explicitní vlastností Member pro inicializační řetězec.</span><span class="sxs-lookup"><span data-stu-id="5ef10-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="5ef10-136">V implementaci služby .NET XAML Services je zpracování <xref:System.Windows.Markup.StaticExtension> pro toto rozšíření značek definováno třídou.</span><span class="sxs-lookup"><span data-stu-id="5ef10-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="5ef10-137">`x:Static`je rozšíření značky.</span><span class="sxs-lookup"><span data-stu-id="5ef10-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="5ef10-138">Všechna rozšíření značek v XAML `{` `}` používají znaky a v syntaxi jejich atributu, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí poskytnout hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5ef10-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="5ef10-139">Další informace o rozšířeních značek naleznete v [tématu Markup Extensions for XAML Overview](markup-extensions-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5ef10-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="5ef10-140">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="5ef10-140">WPF Usage Notes</span></span>

<span data-ttu-id="5ef10-141">Výchozí obor názvů XAML, který používáte pro programování WPF, neobsahuje mnoho užitečných statických vlastností a většina `{x:Static}` užitečných statických vlastností má podporu, například převaděče typů, které usnadňují použití bez nutnosti .</span><span class="sxs-lookup"><span data-stu-id="5ef10-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="5ef10-142">Pro statické vlastnosti je nutné mapovat předponu pro obor názvů XAML, pokud je splněna jedna z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="5ef10-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="5ef10-143">Odkazujete na typ, který existuje v WPF, ale není součástí výchozího oboru`http://schemas.microsoft.com/winfx/2006/xaml/presentation`názvů XAML pro WPF ( ).</span><span class="sxs-lookup"><span data-stu-id="5ef10-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="5ef10-144">Toto je poměrně běžný `x:Static`scénář pro použití .</span><span class="sxs-lookup"><span data-stu-id="5ef10-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="5ef10-145">Můžete například použít `x:Static` odkaz s mapováním oboru názvů <xref:System> XAML na obor názvů CLR a sestavení mscorlib, abyste mohli odkazovat na statické vlastnosti <xref:System.Environment> třídy.</span><span class="sxs-lookup"><span data-stu-id="5ef10-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="5ef10-146">Odkazujete na typ z vlastního sestavení.</span><span class="sxs-lookup"><span data-stu-id="5ef10-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="5ef10-147">Odkazujete na typ, který existuje v sestavení WPF, ale tento typ je v oboru názvů CLR, který nebyl namapován jako součást výchozího oboru názvů WPF XAML.</span><span class="sxs-lookup"><span data-stu-id="5ef10-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="5ef10-148">Mapování oborů názvů CLR do výchozího oboru názvů XAML pro WPF se provádí podle definic v různých sestaveních WPF (další informace o tomto konceptu naleznete v [tématu XAML Namespaces a Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span><span class="sxs-lookup"><span data-stu-id="5ef10-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="5ef10-149">Nemapované obory názvů CLR mohou existovat, pokud se tento obor názvů CLR skládá převážně z <xref:System.Windows.Threading>definic tříd, které nejsou obvykle určeny pro XAML, například .</span><span class="sxs-lookup"><span data-stu-id="5ef10-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="5ef10-150">Další informace o použití předpon a oborů názvů XAML pro WPF naleznete v [tématu XAML Obory názvů a Mapování oboru názvů pro WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="5ef10-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ef10-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ef10-151">See also</span></span>

- [<span data-ttu-id="5ef10-152">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="5ef10-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="5ef10-153">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="5ef10-153">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
