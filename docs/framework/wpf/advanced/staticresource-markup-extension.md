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
ms.openlocfilehash: 8319e451268152e95326c02027157db72df631b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981900"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="8e41e-102">StaticResource – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="8e41e-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="8e41e-103">Poskytuje hodnotu pro všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnost atributu vyhledáním odkaz na prostředek už definované.</span><span class="sxs-lookup"><span data-stu-id="8e41e-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="8e41e-104">Chování při vyhledávání pro daný prostředek je obdobou během načítání vyhledávání, která bude hledat prostředky, které byly dříve načteny z kódu aktuálního [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránek a jiných zdrojů aplikace a vygeneruje tuto hodnotu prostředků jako Hodnota vlastnosti objektů za běhu.</span><span class="sxs-lookup"><span data-stu-id="8e41e-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8e41e-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="8e41e-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="8e41e-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="8e41e-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8e41e-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="8e41e-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="8e41e-108">Klíč pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="8e41e-108">The key for the requested resource.</span></span> <span data-ttu-id="8e41e-109">Tento klíč byl zpočátku přiřadil [x: Key – direktiva](../../xaml-services/x-key-directive.md) prostředek byl vytvořen v označení, zda byla poskytnuta jako `key` parametru při volání metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Pokud prostředek se vytvořil v kódu.</span><span class="sxs-lookup"><span data-stu-id="8e41e-109">This key was initially assigned by the [x:Key Directive](../../xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e41e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e41e-110">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e41e-111">A `StaticResource` nesmí se pokusit vytvořit dopředný odkaz na prostředek, který je definován v rámci lexikálně Další [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.</span><span class="sxs-lookup"><span data-stu-id="8e41e-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="8e41e-112">To pokusíte, není podporována, a i v případě selhání odkazu není pokusem dopředný odkaz se vám být naúčtovány snížení výkonu času zatížení při interní zatřiďovacích tabulek reprezentující <xref:System.Windows.ResourceDictionary> budou vyhledány.</span><span class="sxs-lookup"><span data-stu-id="8e41e-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="8e41e-113">Nejlepších výsledků dosáhnete upravte tak, aby dopředné odkazy se lze vyvarovat složení zdrojové slovníky.</span><span class="sxs-lookup"><span data-stu-id="8e41e-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="8e41e-114">Pokud se nelze vyhnout dopředný odkaz, použijte [– rozšíření značek DynamicResource](dynamicresource-markup-extension.md) místo.</span><span class="sxs-lookup"><span data-stu-id="8e41e-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="8e41e-115">Zadaný <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měl odpovídat existující prostředek, označena [x: Key – direktiva](../../xaml-services/x-key-directive.md) na určité úrovni v vaše stránka, aplikace, ovládací prvek k dispozici motivy a externí prostředky nebo systémové prostředky.</span><span class="sxs-lookup"><span data-stu-id="8e41e-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="8e41e-116">Vyvolá se v tomto pořadí vyhledávání prostředků.</span><span class="sxs-lookup"><span data-stu-id="8e41e-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="8e41e-117">Další informace o chování při vyhledávání prostředků pro statické a dynamické prostředky, najdete v části [prostředky XAML](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="8e41e-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
 <span data-ttu-id="8e41e-118">Klíč prostředku může obsahovat libovolný řetězec podle [xamlname – gramatika](../../xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="8e41e-118">A resource key can be any string defined in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="8e41e-119">Klíč prostředku může být také jinými typy objektů, například <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="8e41e-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="8e41e-120">A <xref:System.Type> klíč je nezbytné k tom, jak můžete styl ovládací prvky podle motivy, prostřednictvím klíče k implicitní styl.</span><span class="sxs-lookup"><span data-stu-id="8e41e-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="8e41e-121">Další informace najdete v tématu [Přehled vytváření ovládacího prvku](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8e41e-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="8e41e-122">Alternativní deklarativní způsob odkazuje na prostředek je jako [– rozšíření značek DynamicResource](dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="8e41e-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="8e41e-123">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="8e41e-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="8e41e-124">Řetězec s tokenem uvedený za `StaticResource` řetězec identifikátoru je přiřazen jako <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> hodnoty základního <xref:System.Windows.StaticResourceExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="8e41e-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="8e41e-125">`StaticResource` můžete použít v syntaxi elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="8e41e-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="8e41e-126">V takovém případě zadáte hodnotu <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost je povinná.</span><span class="sxs-lookup"><span data-stu-id="8e41e-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="8e41e-127">`StaticResource` je také možné využití podrobné atribut, který určuje <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost jako vlastnost = hodnota pár:</span><span class="sxs-lookup"><span data-stu-id="8e41e-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="8e41e-128">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="8e41e-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="8e41e-129">Protože `StaticResource` má jen jednu nastavitelnou vlastnost, která je požadována, toto použití podrobné syntaxe není typické.</span><span class="sxs-lookup"><span data-stu-id="8e41e-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="8e41e-130">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru, zpracování tohoto rozšíření značek definováno <xref:System.Windows.StaticResourceExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="8e41e-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="8e41e-131">`StaticResource` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="8e41e-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="8e41e-132">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8e41e-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="8e41e-133">Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v syntaxi atributu, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="8e41e-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="8e41e-134">Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="8e41e-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e41e-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e41e-135">See also</span></span>

- [<span data-ttu-id="8e41e-136">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="8e41e-136">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="8e41e-137">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="8e41e-137">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="8e41e-138">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="8e41e-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="8e41e-139">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="8e41e-139">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="8e41e-140">Prostředky a kód</span><span class="sxs-lookup"><span data-stu-id="8e41e-140">Resources and Code</span></span>](resources-and-code.md)
