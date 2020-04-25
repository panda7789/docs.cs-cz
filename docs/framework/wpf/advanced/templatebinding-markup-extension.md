---
title: TemplateBinding – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 69698db8b51e3872d5941d4fba67271b1e61226e
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140463"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="2863e-102">TemplateBinding – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="2863e-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="2863e-103">Propojuje hodnotu vlastnosti v šabloně ovládacího prvku s hodnotou jiné vlastnosti ovládacího prvku bez vizuálního vzhledu.</span><span class="sxs-lookup"><span data-stu-id="2863e-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="2863e-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="2863e-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" ... />
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="2863e-105">Použití atributu XAML (pro vlastnost Setter v šabloně nebo stylu)</span><span class="sxs-lookup"><span data-stu-id="2863e-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" ... />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="2863e-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="2863e-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="2863e-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>vlastnosti nastavené v syntaxi setter.</span><span class="sxs-lookup"><span data-stu-id="2863e-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="2863e-108">Další vlastnost závislosti, která existuje pro typ, který je vytvářen šablonou, <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>kterou určuje.</span><span class="sxs-lookup"><span data-stu-id="2863e-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="2863e-109">- nebo -</span><span class="sxs-lookup"><span data-stu-id="2863e-109">- or -</span></span><br /><br /> <span data-ttu-id="2863e-110">Název vlastnosti specifikovaný s použitím teček, který je definován jiným typem než cílovým typem bez vizuálního vzhledu.</span><span class="sxs-lookup"><span data-stu-id="2863e-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="2863e-111">To je ve skutečnosti <xref:System.Windows.PropertyPath>a.</span><span class="sxs-lookup"><span data-stu-id="2863e-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="2863e-112">Viz [syntaxe jazyka XAML pro PropertyPath](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="2863e-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2863e-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2863e-113">Remarks</span></span>  
 <span data-ttu-id="2863e-114">Je optimalizovaná forma [vazby](binding-markup-extension.md) pro scénáře šablon, která je analogická s `Binding` `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`vytvořenou. `TemplateBinding`</span><span class="sxs-lookup"><span data-stu-id="2863e-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`.</span></span> <span data-ttu-id="2863e-115">`TemplateBinding` Je vždy jednosměrná vazba, a to i v případě, že vlastnosti použité jako výchozí jsou obousměrné vazby.</span><span class="sxs-lookup"><span data-stu-id="2863e-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="2863e-116">Obě vlastnosti musejí být vlastnosti závislostí.</span><span class="sxs-lookup"><span data-stu-id="2863e-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="2863e-117">Aby bylo možné dosáhnout obousměrné vazby k nadřazenému objektu, použijte místo něj `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`následující příkaz vazby.</span><span class="sxs-lookup"><span data-stu-id="2863e-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span>
  
 <span data-ttu-id="2863e-118">[RelativeSource](relativesource-markupextension.md) je další rozšíření značek, které se někdy používá ve spojení s nebo namísto `TemplateBinding` , aby bylo možné provést relativní vazbu vlastnosti v rámci šablony.</span><span class="sxs-lookup"><span data-stu-id="2863e-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="2863e-119">Popis šablon ovládacích prvků v rámci konceptu se zde nezabývá; Další informace najdete v tématu [styly a šablony ovládacích prvků](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="2863e-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="2863e-120">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="2863e-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="2863e-121">Token řetězce poskytnutý po řetězci `TemplateBinding` identifikátoru je přiřazen jako <xref:System.Windows.TemplateBindingExtension.Property%2A> hodnota základní <xref:System.Windows.TemplateBindingExtension> třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2863e-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="2863e-122">Je možné použít syntaxi elementu objektu, kterou ale neuvádíme, protože nemá žádné reálné použití.</span><span class="sxs-lookup"><span data-stu-id="2863e-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="2863e-123">`TemplateBinding`slouží k vyplňování hodnot v rámci setter, pomocí vyhodnocených výrazů a použití syntaxe elementů `TemplateBinding` objektu pro `<Setter.Property>` k vyplnění syntaxe elementu Property je zbytečně podrobné.</span><span class="sxs-lookup"><span data-stu-id="2863e-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="2863e-124">`TemplateBinding`lze také použít v podrobném použití atributu, které určuje <xref:System.Windows.TemplateBindingExtension.Property%2A> vlastnost jako dvojici vlastnost = hodnota:</span><span class="sxs-lookup"><span data-stu-id="2863e-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" ... />
```  
  
 <span data-ttu-id="2863e-125">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="2863e-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="2863e-126">Protože `TemplateBinding` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.</span><span class="sxs-lookup"><span data-stu-id="2863e-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="2863e-127">V implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesoru XAML je zpracování tohoto rozšíření značek definováno <xref:System.Windows.TemplateBindingExtension> třídou.</span><span class="sxs-lookup"><span data-stu-id="2863e-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="2863e-128">`TemplateBinding`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="2863e-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="2863e-129">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2863e-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="2863e-130">Všechna rozšíření značek v jazyce XAML používají `{` ve `}` svých syntaxech atributů znaky a, což je konvence, pomocí níž procesor XAML rozpozná, že je nutné zpracovat atribut rozšířením značek.</span><span class="sxs-lookup"><span data-stu-id="2863e-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="2863e-131">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="2863e-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2863e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2863e-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2863e-133">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="2863e-133">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="2863e-134">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="2863e-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="2863e-135">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="2863e-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="2863e-136">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="2863e-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="2863e-137">Rozšíření značek připojení</span><span class="sxs-lookup"><span data-stu-id="2863e-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
