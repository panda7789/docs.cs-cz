---
title: "DynamicResource – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c80d975e756fab449c254b9e1d8d1bc99a25652e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="c6770-102">DynamicResource – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="c6770-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="c6770-103">Poskytuje hodnotu pro všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnost atribut rozlišením tuto hodnotu jako odkaz na prostředek definované.</span><span class="sxs-lookup"><span data-stu-id="c6770-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="c6770-104">Chování vyhledávání pro tento prostředek je analogická spuštění vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="c6770-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c6770-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="c6770-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="c6770-106">Použití elementu vlastnosti XAML</span><span class="sxs-lookup"><span data-stu-id="c6770-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c6770-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="c6770-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="c6770-108">Klíč pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="c6770-108">The key for the requested resource.</span></span> <span data-ttu-id="c6770-109">Tento klíč původně přiřazený pomocí [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) prostředek byl vytvořen v značek, zda byla poskytnuta jako `key` parametr při volání metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Pokud prostředek se vytvořil v kódu.</span><span class="sxs-lookup"><span data-stu-id="c6770-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6770-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6770-110">Remarks</span></span>  
 <span data-ttu-id="c6770-111">A `DynamicResource` vytvoří dočasný výraz během počáteční kompilace a proto odložení vyhledávání pro prostředky, dokud hodnota požadovaný prostředek je ve skutečnosti vyžaduje, aby bylo možné vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="c6770-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="c6770-112">To může být potenciálně po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] načtení stránky.</span><span class="sxs-lookup"><span data-stu-id="c6770-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="c6770-113">Hodnota prostředků bude na základě nalezen klíč hledání u všech slovnících active prostředků od aktuální obor stránky a nahradí zástupný výraz ze kompilace.</span><span class="sxs-lookup"><span data-stu-id="c6770-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6770-114">Z hlediska přednost před vlastností závislostí `DynamicResource` výraz je ekvivalentní pozice, kdy se používá odkaz dynamické prostředků.</span><span class="sxs-lookup"><span data-stu-id="c6770-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="c6770-115">Pokud nastavíte místní hodnotu pro vlastnost, která dřív měla `DynamicResource` výraz jako místní hodnotu, `DynamicResource` je zcela odebrána.</span><span class="sxs-lookup"><span data-stu-id="c6770-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="c6770-116">Podrobnosti najdete v tématu [přednost hodnota vlastnosti závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="c6770-116">For details, see [Dependency Property Value Precedence](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="c6770-117">Některé scénáře přístupu prostředků jsou zvlášť vhodné pro `DynamicResource` naproti tomu [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="c6770-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span> <span data-ttu-id="c6770-118">V tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md) diskuzi o relativních výhodách a ovlivnit výkon systému `DynamicResource` a `StaticResource`.</span><span class="sxs-lookup"><span data-stu-id="c6770-118">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="c6770-119">Zadaný <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> by měla odpovídat existující prostředek dáno [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) na určité úrovni v stránku, aplikace, k dispozici řízení motivy a externím prostředkům nebo prostředky systému a vyhledávání prostředků proběhne v tomto pořadí.</span><span class="sxs-lookup"><span data-stu-id="c6770-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="c6770-120">Další informace o vyhledávání prostředků pro statické a dynamické prostředků najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="c6770-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="c6770-121">Klíč prostředku může být libovolný řetězec definovaný v [XamlName – gramatika](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="c6770-121">A resource key may be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="c6770-122">Klíč prostředku může také být jiné typy objektů, jako třeba <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="c6770-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="c6770-123">A <xref:System.Type> klíč je nezbytné, aby jak může být ve ovládací prvky podle motivů.</span><span class="sxs-lookup"><span data-stu-id="c6770-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="c6770-124">Další informace najdete v tématu [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c6770-124">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]<span data-ttu-id="c6770-125">pro vyhledávání prostředků hodnot jako například <xref:System.Windows.FrameworkElement.FindResource%2A>, postupujte podle stejné logiky vyhledávání prostředků jako použité ve `DynamicResource`.</span><span class="sxs-lookup"><span data-stu-id="c6770-125"> for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="c6770-126">Odkazování na prostředek alternativní deklarativní způsob je jako [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="c6770-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="c6770-127">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="c6770-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="c6770-128">Token řetězec zadaný po `DynamicResource` řetězec identifikátoru je přiřazen jako <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> hodnotu základní <xref:System.Windows.DynamicResourceExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="c6770-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="c6770-129">`DynamicResource`lze použít v syntaxi objekt elementu.</span><span class="sxs-lookup"><span data-stu-id="c6770-129">`DynamicResource` can be used in object element syntax.</span></span> <span data-ttu-id="c6770-130">V takovém případě určující hodnotu <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost je povinná.</span><span class="sxs-lookup"><span data-stu-id="c6770-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="c6770-131">`DynamicResource`Můžete také použít využití podrobné atribut, který určuje <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost jako vlastnost = dvojice hodnota:</span><span class="sxs-lookup"><span data-stu-id="c6770-131">`DynamicResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="c6770-132">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="c6770-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="c6770-133">Protože `DynamicResource` má jenom jednu nastavit vlastnost, který je vyžadován, toto podrobné použití není Typická.</span><span class="sxs-lookup"><span data-stu-id="c6770-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="c6770-134">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.DynamicResourceExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="c6770-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 <span data-ttu-id="c6770-135">`DynamicResource`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="c6770-135">`DynamicResource` is a markup extension.</span></span> <span data-ttu-id="c6770-136">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c6770-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="c6770-137">Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v jejich syntaxi atributů, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="c6770-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="c6770-138">Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c6770-138">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6770-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6770-139">See Also</span></span>  
 [<span data-ttu-id="c6770-140">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="c6770-140">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="c6770-141">Prostředky a kódu</span><span class="sxs-lookup"><span data-stu-id="c6770-141">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="c6770-142">x: Key – direktiva</span><span class="sxs-lookup"><span data-stu-id="c6770-142">x:Key Directive</span></span>](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [<span data-ttu-id="c6770-143">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c6770-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="c6770-144">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c6770-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="c6770-145">– Rozšíření značek StaticResource</span><span class="sxs-lookup"><span data-stu-id="c6770-145">StaticResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [<span data-ttu-id="c6770-146">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c6770-146">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
