---
title: DynamicResource – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: d07816718ebee2507f1888cffb70e6f8037bb996
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091405"
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="e0d45-102">DynamicResource – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="e0d45-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="e0d45-103">Poskytuje hodnotu pro všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnost atributu odložením tuto hodnotu jako odkaz na prostředek definovaný.</span><span class="sxs-lookup"><span data-stu-id="e0d45-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="e0d45-104">Chování při vyhledávání pro daný prostředek je obdobou vyhledávání za běhu.</span><span class="sxs-lookup"><span data-stu-id="e0d45-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e0d45-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="e0d45-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="e0d45-106">Použití elementu vlastnosti XAML</span><span class="sxs-lookup"><span data-stu-id="e0d45-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e0d45-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="e0d45-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="e0d45-108">Klíč pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="e0d45-108">The key for the requested resource.</span></span> <span data-ttu-id="e0d45-109">Tento klíč byl zpočátku přiřadil [x: Key – direktiva](../../xaml-services/x-key-directive.md) prostředek byl vytvořen v označení, zda byla poskytnuta jako `key` parametru při volání metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Pokud prostředek se vytvořil v kódu.</span><span class="sxs-lookup"><span data-stu-id="e0d45-109">This key was initially assigned by the [x:Key Directive](../../xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0d45-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0d45-110">Remarks</span></span>  
 <span data-ttu-id="e0d45-111">A `DynamicResource` vytvoří dočasné výraz během počáteční kompilace a vyhledávání prostředků tedy odložit, dokud hodnota požadovaný prostředek je skutečně potřeba, abyste mohli vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="e0d45-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="e0d45-112">To může být potenciálně po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] načtení stránky.</span><span class="sxs-lookup"><span data-stu-id="e0d45-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="e0d45-113">Hodnota prostředku se najít podle klíčových vyhledávání na všechny aktivní zdrojové slovníky od aktuální obor page a nahradí zástupný symbol výrazu z kompilace.</span><span class="sxs-lookup"><span data-stu-id="e0d45-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e0d45-114">Z hlediska Priorita vlastností závislosti `DynamicResource` výraz je ekvivalentní k umístění, kde použít odkaz na prostředek dynamické.</span><span class="sxs-lookup"><span data-stu-id="e0d45-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="e0d45-115">Pokud nastavíte hodnotu místní vlastnosti, které dříve měly `DynamicResource` výraz jako místní hodnota `DynamicResource` úplně Odebereme.</span><span class="sxs-lookup"><span data-stu-id="e0d45-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="e0d45-116">Podrobnosti najdete v tématu [Priorita hodnot závislých vlastností](dependency-property-value-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="e0d45-116">For details, see [Dependency Property Value Precedence](dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="e0d45-117">Jsou zvlášť vhodná pro určité scénáře přístupu prostředků `DynamicResource` nikoli [– rozšíření značek StaticResource](staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="e0d45-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](staticresource-markup-extension.md).</span></span> <span data-ttu-id="e0d45-118">Zobrazit [prostředky XAML](xaml-resources.md) diskuzi o relativní věci a rozbor aspektů výkonu `DynamicResource` a `StaticResource`.</span><span class="sxs-lookup"><span data-stu-id="e0d45-118">See [XAML Resources](xaml-resources.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="e0d45-119">Zadaný <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> určené existující prostředek, musí odpovídat [x: Key – direktiva](../../xaml-services/x-key-directive.md) na určité úrovni v vaše stránka, aplikace, ovládací prvek dostupné motivy a externí prostředky nebo systémové prostředky a vyhledání prostředku se stane v tomto pořadí.</span><span class="sxs-lookup"><span data-stu-id="e0d45-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="e0d45-120">Další informace o vyhledání prostředku pro statické a dynamické prostředky, najdete v části [prostředky XAML](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="e0d45-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
 <span data-ttu-id="e0d45-121">Klíč prostředku může být libovolný řetězec podle [xamlname – gramatika](../../xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="e0d45-121">A resource key may be any string defined in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="e0d45-122">Klíč prostředku může být také další typy objektů, například <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="e0d45-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="e0d45-123">A <xref:System.Type> klíč je základní jak může být ovládací prvky ve stylu podle motivů.</span><span class="sxs-lookup"><span data-stu-id="e0d45-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="e0d45-124">Další informace najdete v tématu [Přehled vytváření ovládacího prvku](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e0d45-124">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <span data-ttu-id="e0d45-125">pro vyhledávání hodnoty prostředků jako například <xref:System.Windows.FrameworkElement.FindResource%2A>, se řídí stejnou logikou vyhledávání prostředků jako používá `DynamicResource`.</span><span class="sxs-lookup"><span data-stu-id="e0d45-125">for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="e0d45-126">Alternativní deklarativní způsob odkazuje na prostředek je jako [– rozšíření značek StaticResource](staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="e0d45-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="e0d45-127">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="e0d45-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="e0d45-128">Řetězec s tokenem uvedený za `DynamicResource` řetězec identifikátoru je přiřazen jako <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> hodnoty základního <xref:System.Windows.DynamicResourceExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="e0d45-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 `DynamicResource` <span data-ttu-id="e0d45-129">můžete použít v syntaxi elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="e0d45-129">can be used in object element syntax.</span></span> <span data-ttu-id="e0d45-130">V takovém případě zadáte hodnotu <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost je povinná.</span><span class="sxs-lookup"><span data-stu-id="e0d45-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 `DynamicResource` <span data-ttu-id="e0d45-131">je také možné využití podrobné atribut, který určuje <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost jako vlastnost = hodnota pár:</span><span class="sxs-lookup"><span data-stu-id="e0d45-131">can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="e0d45-132">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="e0d45-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="e0d45-133">Protože `DynamicResource` má jen jednu nastavitelnou vlastnost, která je požadována, toto použití podrobné syntaxe není typické.</span><span class="sxs-lookup"><span data-stu-id="e0d45-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="e0d45-134">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru, zpracování tohoto rozšíření značek definováno <xref:System.Windows.DynamicResourceExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="e0d45-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 `DynamicResource` <span data-ttu-id="e0d45-135">je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="e0d45-135">is a markup extension.</span></span> <span data-ttu-id="e0d45-136">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e0d45-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="e0d45-137">Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v syntaxi atributu, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="e0d45-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="e0d45-138">Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="e0d45-138">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d45-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0d45-139">See also</span></span>

- [<span data-ttu-id="e0d45-140">Zdroje XAML</span><span class="sxs-lookup"><span data-stu-id="e0d45-140">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="e0d45-141">Zdroje a kód</span><span class="sxs-lookup"><span data-stu-id="e0d45-141">Resources and Code</span></span>](resources-and-code.md)
- [<span data-ttu-id="e0d45-142">x:Key – direktiva</span><span class="sxs-lookup"><span data-stu-id="e0d45-142">x:Key Directive</span></span>](../../xaml-services/x-key-directive.md)
- [<span data-ttu-id="e0d45-143">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="e0d45-143">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="e0d45-144">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="e0d45-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="e0d45-145">StaticResource – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="e0d45-145">StaticResource Markup Extension</span></span>](staticresource-markup-extension.md)
- [<span data-ttu-id="e0d45-146">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="e0d45-146">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
