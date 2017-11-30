---
title: "TemplateBinding – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ab8645de78a79f4bd47fa436699af002db99b9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="3596c-102">TemplateBinding – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="3596c-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="3596c-103">Propojuje hodnotu vlastnosti v šabloně ovládacího prvku s hodnotou jiné vlastnosti ovládacího prvku bez vizuálního vzhledu.</span><span class="sxs-lookup"><span data-stu-id="3596c-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3596c-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="3596c-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="3596c-105">Použití atributu XAML (pro vlastnost Setter v šabloně nebo stylu)</span><span class="sxs-lookup"><span data-stu-id="3596c-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3596c-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="3596c-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="3596c-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>vlastnosti se nastavuje v syntaxi setter.</span><span class="sxs-lookup"><span data-stu-id="3596c-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="3596c-108">Další závislosti vlastnost, která existuje v typu probíhá podle šablony, určeného jeho <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3596c-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="3596c-109">- nebo -</span><span class="sxs-lookup"><span data-stu-id="3596c-109">- or -</span></span><br /><br /> <span data-ttu-id="3596c-110">Název vlastnosti specifikovaný s použitím teček, který je definován jiným typem než cílovým typem bez vizuálního vzhledu.</span><span class="sxs-lookup"><span data-stu-id="3596c-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="3596c-111">Toto je ve skutečnosti <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="3596c-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="3596c-112">V tématu [syntaxe PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="3596c-112">See [PropertyPath XAML Syntax](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3596c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3596c-113">Remarks</span></span>  
 <span data-ttu-id="3596c-114">A `TemplateBinding` optimalizované formu [vazby](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) pro scénáře šablon, podobá `Binding` zkonstruovat s `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="3596c-114">A `TemplateBinding` is an optimized form of a [Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="3596c-115">A `TemplateBinding` je vždy jednosměrný vazbu, i v případě, že vlastnosti podílejí výchozí nastavení vazba obousměrná.</span><span class="sxs-lookup"><span data-stu-id="3596c-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="3596c-116">Obě vlastnosti musejí být vlastnosti závislostí.</span><span class="sxs-lookup"><span data-stu-id="3596c-116">Both properties involved must be dependency properties.</span></span>  
  
 <span data-ttu-id="3596c-117">[RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) je jiné rozšíření značek, které se někdy používá ve spojení s nebo místo `TemplateBinding` za účelem provedení relativní vlastnost vazbu v rámci šablony.</span><span class="sxs-lookup"><span data-stu-id="3596c-117">[RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="3596c-118">Popisující šablon ovládacích prvků jako koncept neplatí zde; Další informace najdete v tématu [– styly ovládacích prvků a šablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="3596c-118">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="3596c-119">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="3596c-119">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="3596c-120">Token řetězec zadaný po `TemplateBinding` řetězec identifikátoru je přiřazen jako <xref:System.Windows.TemplateBindingExtension.Property%2A> hodnotu základní <xref:System.Windows.TemplateBindingExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="3596c-120">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="3596c-121">Je možné použít syntaxi elementu objektu, kterou ale neuvádíme, protože nemá žádné reálné použití.</span><span class="sxs-lookup"><span data-stu-id="3596c-121">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="3596c-122">`TemplateBinding`slouží k vyplnění výrazy hodnot v rámci setter, pomocí vyhodnotit a pomocí syntaxe element objektu pro `TemplateBinding` k vyplnění `<Setter.Property>` vlastnost element syntaxe je zbytečně verbose.</span><span class="sxs-lookup"><span data-stu-id="3596c-122">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="3596c-123">`TemplateBinding`Můžete také použít využití podrobné atribut, který určuje <xref:System.Windows.TemplateBindingExtension.Property%2A> vlastnost jako vlastnost = dvojice hodnota:</span><span class="sxs-lookup"><span data-stu-id="3596c-123">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="3596c-124">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="3596c-124">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="3596c-125">Protože `TemplateBinding` má jenom jednu nastavit vlastnost, který je vyžadován, toto podrobné použití není Typická.</span><span class="sxs-lookup"><span data-stu-id="3596c-125">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="3596c-126">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace XAML procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.TemplateBindingExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="3596c-126">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="3596c-127">`TemplateBinding`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="3596c-127">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="3596c-128">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3596c-128">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="3596c-129">Všechna rozšíření značek v XAML použití `{` a `}` znaků v jejich syntaxi atributů, což je konvence, podle kterého XAML procesor rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="3596c-129">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="3596c-130">Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="3596c-130">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3596c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="3596c-131">See Also</span></span>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="3596c-132">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="3596c-132">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3596c-133">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="3596c-133">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="3596c-134">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="3596c-134">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="3596c-135">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="3596c-135">RelativeSource MarkupExtension</span></span>](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)  
 [<span data-ttu-id="3596c-136">Vazby – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="3596c-136">Binding Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
