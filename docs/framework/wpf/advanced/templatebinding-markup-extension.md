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
ms.openlocfilehash: c004560a0b7ab367fbf4fbb48b0e8d8b63f3d8f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155997"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="1b04c-102">TemplateBinding – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="1b04c-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="1b04c-103">Propojuje hodnotu vlastnosti v šabloně ovládacího prvku s hodnotou jiné vlastnosti ovládacího prvku bez vizuálního vzhledu.</span><span class="sxs-lookup"><span data-stu-id="1b04c-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1b04c-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="1b04c-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="1b04c-105">Použití atributu XAML (pro vlastnost Setter v šabloně nebo stylu)</span><span class="sxs-lookup"><span data-stu-id="1b04c-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1b04c-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="1b04c-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> <span data-ttu-id="1b04c-107">vlastnosti, která je nastavena v syntaxi setter.</span><span class="sxs-lookup"><span data-stu-id="1b04c-107">of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="1b04c-108">Další vlastnost závislosti, která existuje pro typ bez vizuálního vzhledu, určená jeho <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b04c-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="1b04c-109">- nebo -</span><span class="sxs-lookup"><span data-stu-id="1b04c-109">- or -</span></span><br /><br /> <span data-ttu-id="1b04c-110">Název vlastnosti specifikovaný s použitím teček, který je definován jiným typem než cílovým typem bez vizuálního vzhledu.</span><span class="sxs-lookup"><span data-stu-id="1b04c-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="1b04c-111">Ve skutečnosti se jedná <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="1b04c-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="1b04c-112">Zobrazit [syntaxe PropertyPath XAML](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="1b04c-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b04c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b04c-113">Remarks</span></span>  
 <span data-ttu-id="1b04c-114">A `TemplateBinding` je optimalizovaná forma [vazby](binding-markup-extension.md) pro šablony je analogická `Binding` zkonstruován pomocí `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="1b04c-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="1b04c-115">A `TemplateBinding` je vždy jednosměrná vazba, i když příslušné vlastnosti ve výchozím nastavení používají obousměrné vazby.</span><span class="sxs-lookup"><span data-stu-id="1b04c-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="1b04c-116">Obě vlastnosti musejí být vlastnosti závislostí.</span><span class="sxs-lookup"><span data-stu-id="1b04c-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="1b04c-117">Abyste dosáhli Obousměrná vazba nadřazenému prvku bez vizuálního vzhledu použijte následující příkaz vazby `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span><span class="sxs-lookup"><span data-stu-id="1b04c-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span> 
  
 <span data-ttu-id="1b04c-118">[RelativeSource](relativesource-markupextension.md) je další rozšíření značek, které se někdy používá ve spojení s nebo namísto něj `TemplateBinding` účelem vytvoření relativní vazby vlastností v rámci šablony.</span><span class="sxs-lookup"><span data-stu-id="1b04c-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="1b04c-119">Popis šablon ovládacích prvků jako koncept není součástí tohoto Další informace najdete v tématu [– styly ovládacích prvků a šablon](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="1b04c-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="1b04c-120">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="1b04c-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="1b04c-121">Řetězec s tokenem uvedený za `TemplateBinding` řetězec identifikátoru je přiřazen jako <xref:System.Windows.TemplateBindingExtension.Property%2A> hodnoty základního <xref:System.Windows.TemplateBindingExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="1b04c-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="1b04c-122">Je možné použít syntaxi elementu objektu, kterou ale neuvádíme, protože nemá žádné reálné použití.</span><span class="sxs-lookup"><span data-stu-id="1b04c-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> `TemplateBinding` <span data-ttu-id="1b04c-123">slouží k naplnění hodnot v rámci elementů setter pomocí vyhodnocení výrazů a použití syntaxe elementu objektu pro `TemplateBinding` tak, aby vyplnil `<Setter.Property>` syntax prvku vlastnosti je zbytečné.</span><span class="sxs-lookup"><span data-stu-id="1b04c-123">is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 `TemplateBinding` <span data-ttu-id="1b04c-124">je také možné využití podrobné atribut, který určuje <xref:System.Windows.TemplateBindingExtension.Property%2A> vlastnost jako vlastnost = hodnota pár:</span><span class="sxs-lookup"><span data-stu-id="1b04c-124">can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="1b04c-125">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="1b04c-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="1b04c-126">Protože `TemplateBinding` má jen jednu nastavitelnou vlastnost, která je požadována, toto použití podrobné syntaxe není typické.</span><span class="sxs-lookup"><span data-stu-id="1b04c-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="1b04c-127">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementaci procesoru XAML je zpracování tohoto rozšíření značek je určené <xref:System.Windows.TemplateBindingExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="1b04c-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 `TemplateBinding` <span data-ttu-id="1b04c-128">je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="1b04c-128">is a markup extension.</span></span> <span data-ttu-id="1b04c-129">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1b04c-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="1b04c-130">Všechna rozšíření značek XAML používá `{` a `}` znaků v syntaxi atributu, což je konvence, podle kterého na procesor XAML rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="1b04c-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="1b04c-131">Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1b04c-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b04c-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b04c-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="1b04c-133">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="1b04c-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="1b04c-134">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="1b04c-134">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="1b04c-135">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="1b04c-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="1b04c-136">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="1b04c-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="1b04c-137">Rozšíření značek připojení</span><span class="sxs-lookup"><span data-stu-id="1b04c-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
