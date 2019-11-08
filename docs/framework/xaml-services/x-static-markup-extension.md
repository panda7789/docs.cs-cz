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
ms.openlocfilehash: bf94f1d61ee3080c9d3582e55e0695b269801c80
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733356"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="887bd-102">x:Static – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="887bd-102">x:Static Markup Extension</span></span>
<span data-ttu-id="887bd-103">Odkazuje na libovolnou entitu kódu static podle hodnoty, která je definována v jazyce CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="887bd-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="887bd-104">Odkazovaná statická vlastnost může být použita k poskytnutí hodnoty vlastnosti v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="887bd-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="887bd-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="887bd-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="887bd-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="887bd-106">XAML Values</span></span>  
  
| | |  
|-|-|  
|`prefix`|<span data-ttu-id="887bd-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="887bd-107">Optional.</span></span> <span data-ttu-id="887bd-108">Předpona, která odkazuje na namapovaný, nevýchozí obor názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="887bd-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="887bd-109">`prefix` se zobrazuje explicitně v použití, protože zřídka odkazujete na statické vlastnosti, které pocházejí z výchozího oboru názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="887bd-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="887bd-110">Viz poznámky.</span><span class="sxs-lookup"><span data-stu-id="887bd-110">See Remarks.</span></span>|  
|`typeName`|<span data-ttu-id="887bd-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="887bd-111">Required.</span></span> <span data-ttu-id="887bd-112">Název typu, který definuje požadovaného statického člena.</span><span class="sxs-lookup"><span data-stu-id="887bd-112">The name of the type that defines the desired static member.</span></span>|  
|`staticMemberName`|<span data-ttu-id="887bd-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="887bd-113">Required.</span></span> <span data-ttu-id="887bd-114">Název požadovaného člena statické hodnoty (konstanta, statická vlastnost, pole nebo hodnota výčtu).</span><span class="sxs-lookup"><span data-stu-id="887bd-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="887bd-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="887bd-115">Remarks</span></span>  

<span data-ttu-id="887bd-116">Odkazovaná entita kódu musí být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="887bd-116">The code entity that is referenced must be one of the following:</span></span>  
  
- <span data-ttu-id="887bd-117">Konstanta</span><span class="sxs-lookup"><span data-stu-id="887bd-117">A constant</span></span>  
- <span data-ttu-id="887bd-118">Statická vlastnost</span><span class="sxs-lookup"><span data-stu-id="887bd-118">A static property</span></span>  
- <span data-ttu-id="887bd-119">Pole</span><span class="sxs-lookup"><span data-stu-id="887bd-119">A field</span></span>  
- <span data-ttu-id="887bd-120">Hodnota výčtu</span><span class="sxs-lookup"><span data-stu-id="887bd-120">An enumeration value</span></span>

<span data-ttu-id="887bd-121">Určení jakékoli jiné entity kódu, jako je například nestatická vlastnost, způsobí chybu při kompilaci, je-li kód XAML zkompilován, nebo výjimka při analýze při načítání jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="887bd-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>  

<span data-ttu-id="887bd-122">Můžete nastavit `x:Static` odkazy na statická pole nebo vlastnosti, které nejsou ve výchozím oboru názvů XAML pro aktuální dokument XAML. to však vyžaduje mapování předpony.</span><span class="sxs-lookup"><span data-stu-id="887bd-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="887bd-123">Obory názvů XAML jsou téměř vždy definovány u kořenového prvku dokumentu XAML.</span><span class="sxs-lookup"><span data-stu-id="887bd-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>  

<span data-ttu-id="887bd-124">Operace vyhledávání statických vlastností lze provádět pomocí .NET Framework služby XAML a jejich čteček XAML a zapisovače XAML, pokud jsou spuštěny s výchozím kontextem schématu XAML.</span><span class="sxs-lookup"><span data-stu-id="887bd-124">The lookup operations for static properties can be performed by .NET Framework XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="887bd-125">Tento kontext schématu XAML může použít reflexi CLR k poskytnutí nezbytných statických hodnot pro vytváření grafů objektů.</span><span class="sxs-lookup"><span data-stu-id="887bd-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="887bd-126">`typeName`, které zadáte, je jako název typu XAML, nikoli název typu CLR, i když jsou v podstatě stejný název při použití výchozího kontextu schématu XAML nebo při použití všech stávajících rozhraní implementací XAML založených na CLR.</span><span class="sxs-lookup"><span data-stu-id="887bd-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>  

<span data-ttu-id="887bd-127">Při provádění `x:Static` odkazů, které nejsou přímo typu hodnoty vlastnosti, buďte opatrní.</span><span class="sxs-lookup"><span data-stu-id="887bd-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="887bd-128">V sekvenci zpracování XAML poskytují hodnoty z rozšíření značek nevyvolávají další převod hodnoty.</span><span class="sxs-lookup"><span data-stu-id="887bd-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="887bd-129">To platí i v případě, že `x:Static` odkaz vytvoří textový řetězec a převod hodnoty atributů na základě textového řetězce obvykle probíhá buď pro tento konkrétní člen, nebo pro jakékoli členské hodnoty návratového typu.</span><span class="sxs-lookup"><span data-stu-id="887bd-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>  

<span data-ttu-id="887bd-130">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="887bd-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="887bd-131">Token řetězce poskytnutý po řetězci `x:Static` identifikátoru je přiřazen jako hodnota <xref:System.Windows.Markup.StaticExtension.Member%2A> základní třídy rozšíření <xref:System.Windows.Markup.StaticExtension>.</span><span class="sxs-lookup"><span data-stu-id="887bd-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>  

<span data-ttu-id="887bd-132">Existují dva další použití XAML, které jsou technicky možné.</span><span class="sxs-lookup"><span data-stu-id="887bd-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="887bd-133">Tato použití jsou ale méně společná, protože jsou zbytečně podrobná:</span><span class="sxs-lookup"><span data-stu-id="887bd-133">However, these usages are less common because they are unnecessarily verbose:</span></span>  

1. <span data-ttu-id="887bd-134">Syntaxe elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="887bd-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. <span data-ttu-id="887bd-135">Syntaxe atributu s explicitní vlastností member pro inicializační řetězec</span><span class="sxs-lookup"><span data-stu-id="887bd-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="887bd-136">V implementaci .NET Framework XAML Services je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.Markup.StaticExtension>.</span><span class="sxs-lookup"><span data-stu-id="887bd-136">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>  

<span data-ttu-id="887bd-137">`x:Static` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="887bd-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="887bd-138">Všechna rozšíření značek v jazyce XAML používají ve své syntaxi atributu `{` a `}` znaky, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí poskytovat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="887bd-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="887bd-139">Další informace o rozšíření značek naleznete v tématu [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="887bd-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="887bd-140">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="887bd-140">WPF Usage Notes</span></span>  
 <span data-ttu-id="887bd-141">Výchozí obor názvů jazyka XAML, který použijete pro programování WPF, neobsahuje mnoho užitečných statických vlastností a většina užitečných statických vlastností podporuje například převaděče typu, které umožňují použití bez nutnosti `{x:Static}`.</span><span class="sxs-lookup"><span data-stu-id="887bd-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="887bd-142">V případě statických vlastností je nutné namapovat předponu pro obor názvů XAML, pokud je splněna jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="887bd-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>  
  
- <span data-ttu-id="887bd-143">Odkazujete na typ, který existuje v WPF, ale není součástí výchozího oboru názvů XAML pro WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span><span class="sxs-lookup"><span data-stu-id="887bd-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="887bd-144">Toto je poměrně běžný scénář pro použití `x:Static`.</span><span class="sxs-lookup"><span data-stu-id="887bd-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="887bd-145">Například můžete použít `x:Static` odkaz s mapováním oboru názvů XAML na <xref:System> obor názvů CLR a sestavení mscorlib, aby odkazovaly na statické vlastnosti třídy <xref:System.Environment>.</span><span class="sxs-lookup"><span data-stu-id="887bd-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>  
  
- <span data-ttu-id="887bd-146">Odkazujete na typ z vlastního sestavení.</span><span class="sxs-lookup"><span data-stu-id="887bd-146">You are referencing a type from a custom assembly.</span></span>  
  
- <span data-ttu-id="887bd-147">Odkazujete na typ, který existuje v sestavení WPF, ale tento typ je v rámci oboru názvů CLR, který nebyl namapován, aby byl součástí výchozího oboru názvů jazyka XAML WPF.</span><span class="sxs-lookup"><span data-stu-id="887bd-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="887bd-148">Mapování oborů názvů CLR na výchozí obor názvů XAML pro WPF je prováděno definicemi v různých sestaveních WPF (Další informace o tomto konceptu naleznete v tématu [obory názvů XAML a mapování oboru názvů pro WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span><span class="sxs-lookup"><span data-stu-id="887bd-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="887bd-149">Nemapované obory názvů CLR mohou existovat, pokud je tento obor názvů CLR složen hlavně z definic třídy, které nejsou obvykle určeny pro jazyk XAML, například <xref:System.Windows.Threading>.</span><span class="sxs-lookup"><span data-stu-id="887bd-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>  
  
 <span data-ttu-id="887bd-150">Další informace o tom, jak používat předpony a obory názvů XAML pro WPF, naleznete v tématu [obory názvů XAML a mapování oboru názvů pro WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="887bd-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887bd-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="887bd-151">See also</span></span>

- [<span data-ttu-id="887bd-152">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="887bd-152">x:Type Markup Extension</span></span>](x-type-markup-extension.md)
- [<span data-ttu-id="887bd-153">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="887bd-153">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
