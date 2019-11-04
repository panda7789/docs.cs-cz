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
ms.openlocfilehash: 399e4ac223d2fcb728ece2c92d25a087990992f2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458667"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="23bc4-102">TemplateBinding – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="23bc4-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="23bc4-103">Propojuje hodnotu vlastnosti v šabloně ovládacího prvku s hodnotou jiné vlastnosti ovládacího prvku bez vizuálního vzhledu.</span><span class="sxs-lookup"><span data-stu-id="23bc4-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="23bc4-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="23bc4-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="23bc4-105">Použití atributu XAML (pro vlastnost Setter v šabloně nebo stylu)</span><span class="sxs-lookup"><span data-stu-id="23bc4-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="23bc4-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="23bc4-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="23bc4-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> vlastnosti nastavené v syntaxi setter.</span><span class="sxs-lookup"><span data-stu-id="23bc4-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="23bc4-108">Další vlastnost závislosti, která existuje pro typ se šablonou, určená jeho <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="23bc4-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="23bc4-109">ani</span><span class="sxs-lookup"><span data-stu-id="23bc4-109">- or -</span></span><br /><br /> <span data-ttu-id="23bc4-110">Název vlastnosti specifikovaný s použitím teček, který je definován jiným typem než cílovým typem bez vizuálního vzhledu.</span><span class="sxs-lookup"><span data-stu-id="23bc4-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="23bc4-111">Toto je ve skutečnosti <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="23bc4-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="23bc4-112">Viz [syntaxe jazyka XAML pro PropertyPath](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="23bc4-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23bc4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23bc4-113">Remarks</span></span>  
 <span data-ttu-id="23bc4-114">`TemplateBinding` je optimalizovaná forma [vazby](binding-markup-extension.md) pro scénáře šablon, která je podobná `Binding` vytvořená pomocí `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="23bc4-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="23bc4-115">`TemplateBinding` je vždy jednosměrná vazba, a to i v případě, že vlastnosti použité jako výchozí jsou obousměrné vazby.</span><span class="sxs-lookup"><span data-stu-id="23bc4-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="23bc4-116">Obě vlastnosti musejí být vlastnosti závislostí.</span><span class="sxs-lookup"><span data-stu-id="23bc4-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="23bc4-117">Aby bylo možné dosáhnout obousměrné vazby k nadřazenému objektu, použijte následující příkaz vazby místo `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span><span class="sxs-lookup"><span data-stu-id="23bc4-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span> 
  
 <span data-ttu-id="23bc4-118">[RelativeSource](relativesource-markupextension.md) je další rozšíření značek, které se někdy používá ve spojení s nebo místo `TemplateBinding`, aby bylo možné provést relativní vazbu vlastnosti v rámci šablony.</span><span class="sxs-lookup"><span data-stu-id="23bc4-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="23bc4-119">Popis šablon ovládacích prvků v rámci konceptu se zde nezabývá; Další informace najdete v tématu [styly a šablony ovládacích prvků](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="23bc4-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="23bc4-120">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="23bc4-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="23bc4-121">Token řetězce poskytnutý po řetězci `TemplateBinding` identifikátoru je přiřazen jako hodnota <xref:System.Windows.TemplateBindingExtension.Property%2A> základní třídy rozšíření <xref:System.Windows.TemplateBindingExtension>.</span><span class="sxs-lookup"><span data-stu-id="23bc4-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="23bc4-122">Je možné použít syntaxi elementu objektu, kterou ale neuvádíme, protože nemá žádné reálné použití.</span><span class="sxs-lookup"><span data-stu-id="23bc4-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="23bc4-123">`TemplateBinding` slouží k vyplňování hodnot v rámci setter, pomocí vyhodnocených výrazů a použití syntaxe elementů objektu pro `TemplateBinding` k vyplnění `<Setter.Property>` syntaxe elementu vlastnosti není nutně podrobná.</span><span class="sxs-lookup"><span data-stu-id="23bc4-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="23bc4-124">`TemplateBinding` lze také použít v podrobném použití atributu, které určuje vlastnost <xref:System.Windows.TemplateBindingExtension.Property%2A> jako dvojici vlastnost = hodnota:</span><span class="sxs-lookup"><span data-stu-id="23bc4-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="23bc4-125">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="23bc4-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="23bc4-126">Protože `TemplateBinding` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.</span><span class="sxs-lookup"><span data-stu-id="23bc4-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="23bc4-127">V implementaci procesoru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.TemplateBindingExtension>.</span><span class="sxs-lookup"><span data-stu-id="23bc4-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="23bc4-128">`TemplateBinding` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="23bc4-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="23bc4-129">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="23bc4-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="23bc4-130">Všechna rozšíření značek v jazyce XAML používají ve své syntaxi atributu `{` a `}` znaky, což je konvence, pomocí níž procesor XAML rozpozná, že musí zpracovat atribut rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="23bc4-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="23bc4-131">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="23bc4-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23bc4-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23bc4-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="23bc4-133">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="23bc4-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="23bc4-134">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="23bc4-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="23bc4-135">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="23bc4-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="23bc4-136">Rozšíření značek RelativeSource</span><span class="sxs-lookup"><span data-stu-id="23bc4-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="23bc4-137">Rozšíření značek datové vazby</span><span class="sxs-lookup"><span data-stu-id="23bc4-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
