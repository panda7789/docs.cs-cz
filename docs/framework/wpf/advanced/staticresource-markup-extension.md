---
title: StaticResource – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 5c0bb247bae525658d89d53f1672e57b87aba7bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646216"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="86e55-102">StaticResource – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="86e55-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="86e55-103">Poskytuje hodnotu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro všechny atributy vlastnosti vyhledáním odkaz na již definovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="86e55-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="86e55-104">Chování vyhledávání pro tento prostředek je analogické vyhledávání v době načítání, které bude hledat prostředky, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které byly dříve načteny ze značek aktuální stránky a jiných zdrojů aplikace, a vygeneruje tuto hodnotu prostředku jako hodnotu vlastnosti v objektech za běhu.</span><span class="sxs-lookup"><span data-stu-id="86e55-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="86e55-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="86e55-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="86e55-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="86e55-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="86e55-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="86e55-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="86e55-108">Klíč pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="86e55-108">The key for the requested resource.</span></span> <span data-ttu-id="86e55-109">Tento klíč byl původně přiřazen [x:Key směrnice,](../../../desktop-wpf/xaml-services/xkey-directive.md) pokud prostředek byl vytvořen `key` ve značkách nebo byl poskytnut jako parametr při volání, <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> pokud prostředek byl vytvořen v kódu.</span><span class="sxs-lookup"><span data-stu-id="86e55-109">This key was initially assigned by the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86e55-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86e55-110">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="86e55-111">Nesmí `StaticResource` se pokoušet o odkaz dopředné na prostředek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] který je definován lexikálně dále v souboru.</span><span class="sxs-lookup"><span data-stu-id="86e55-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="86e55-112">Pokus o to není podporována a i v případě, že takový odkaz neselže, pokus o odkaz dopředné bude <xref:System.Windows.ResourceDictionary> mít za následek snížení výkonu doby načítání při prohledávání vnitřních tabulek hash představujících a.</span><span class="sxs-lookup"><span data-stu-id="86e55-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="86e55-113">Nejlepších výsledků dosáhnete, když upravíte složení slovníků prostředků tak, aby se předkládaly odkazy dopředu.</span><span class="sxs-lookup"><span data-stu-id="86e55-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="86e55-114">Pokud se nemůžete vyhnout dopředný odkaz, použijte [dynamicResource Markup Extension](dynamicresource-markup-extension.md) místo.</span><span class="sxs-lookup"><span data-stu-id="86e55-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="86e55-115">Zadaný <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měl odpovídat existujícímu prostředku označenému [direktivou x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) na určité úrovni na stránce, aplikaci, dostupných tématech ovládacích prvku a externích prostředcích nebo systémových prostředcích.</span><span class="sxs-lookup"><span data-stu-id="86e55-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="86e55-116">Vyhledávání prostředků probíhá v tomto pořadí.</span><span class="sxs-lookup"><span data-stu-id="86e55-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="86e55-117">Další informace o chování vyhledávání prostředků pro statické a dynamické prostředky naleznete v [tématu XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="86e55-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="86e55-118">Klíč prostředku může být libovolný řetězec definovaný v [gramatice XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="86e55-118">A resource key can be any string defined in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="86e55-119">Klíč prostředku může být také jiné typy <xref:System.Type>objektů, například .</span><span class="sxs-lookup"><span data-stu-id="86e55-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="86e55-120">Klíč <xref:System.Type> je zásadní pro to, jak lze ovládací prvky stylovat podle motivů, prostřednictvím implicitního klíče stylu.</span><span class="sxs-lookup"><span data-stu-id="86e55-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="86e55-121">Další informace naleznete [v tématu Přehled vytváření ovládacích prvku](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="86e55-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="86e55-122">Alternativní deklarativní prostředky odkazování na prostředek je jako [dynamicResource Markup Extension](dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="86e55-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="86e55-123">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="86e55-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="86e55-124">Token řetězce zadaný `StaticResource` po přidělení řetězce <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> identifikátoru jako <xref:System.Windows.StaticResourceExtension> hodnota základní třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="86e55-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="86e55-125">`StaticResource`lze použít v syntaxi prvku objektu.</span><span class="sxs-lookup"><span data-stu-id="86e55-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="86e55-126">V tomto případě je vyžadováno <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> zadání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="86e55-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="86e55-127">`StaticResource`lze také použít v podrobném použití atributu, který určuje <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost jako dvojici vlastností=hodnota:</span><span class="sxs-lookup"><span data-stu-id="86e55-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="86e55-128">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="86e55-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="86e55-129">Protože `StaticResource` má pouze jednu vlastnost settable, která je vyžadována, toto podrobné použití není typické.</span><span class="sxs-lookup"><span data-stu-id="86e55-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="86e55-130">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] V implementaci procesoru zpracování pro toto rozšíření <xref:System.Windows.StaticResourceExtension> značky je definována třídy.</span><span class="sxs-lookup"><span data-stu-id="86e55-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="86e55-131">`StaticResource`je rozšíření značky.</span><span class="sxs-lookup"><span data-stu-id="86e55-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="86e55-132">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="86e55-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="86e55-133">Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky { a } v syntaxi atributu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] což je konvence, podle které procesor rozpozná, že rozšíření značek musí atribut zpracovat.</span><span class="sxs-lookup"><span data-stu-id="86e55-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="86e55-134">Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="86e55-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e55-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="86e55-135">See also</span></span>

- [<span data-ttu-id="86e55-136">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="86e55-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="86e55-137">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="86e55-137">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="86e55-138">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="86e55-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="86e55-139">Zdroje XAML</span><span class="sxs-lookup"><span data-stu-id="86e55-139">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="86e55-140">Zdroje a kód</span><span class="sxs-lookup"><span data-stu-id="86e55-140">Resources and Code</span></span>](resources-and-code.md)
