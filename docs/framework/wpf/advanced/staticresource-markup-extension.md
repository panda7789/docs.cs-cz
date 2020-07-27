---
title: StaticResource – rozšíření značek
description: Poskytuje hodnotu pro libovolný atribut vlastnosti XAML vyhledáním odkazu na již definovaný prostředek.
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 77396c1867dcbe279d7ba158ed9e6f5f833f17b5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164680"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="58064-103">StaticResource – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="58064-103">StaticResource Markup Extension</span></span>
<span data-ttu-id="58064-104">Poskytuje hodnotu pro libovolný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atribut vlastnosti vyhledáním odkazu na již definovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="58064-104">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="58064-105">Chování vyhledávání pro tento prostředek je obdobou vyhledávání při načítání, což bude hledat prostředky, které byly dříve načteny ze značky aktuální [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky a také z jiných zdrojů aplikací, a vygeneruje tuto hodnotu prostředku jako hodnotu vlastnosti v objektech modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="58064-105">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="58064-106">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="58064-106">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" ... />  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="58064-107">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="58064-107">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="58064-108">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="58064-108">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="58064-109">Klíč pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="58064-109">The key for the requested resource.</span></span> <span data-ttu-id="58064-110">Tento klíč byl původně přiřazen [direktivou x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) , pokud byl prostředek vytvořen v kódu, nebo byl zadán jako `key` parametr při volání, <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Pokud byl prostředek vytvořen v kódu.</span><span class="sxs-lookup"><span data-stu-id="58064-110">This key was initially assigned by the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58064-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58064-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="58064-112">`StaticResource`Nesmí se pokoušet o vytvoření dopředný odkaz na prostředek, který je v souboru definován lexikálním [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="58064-112">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="58064-113">Pokus o provedení této akce není podporován a i v případě, že takový odkaz neselže, bude při pokusu o dopředné odkazu účtována pokuta výkonu zatížení, když jsou prohledány vnitřní tabulky hash reprezentující <xref:System.Windows.ResourceDictionary> .</span><span class="sxs-lookup"><span data-stu-id="58064-113">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="58064-114">Pro dosažení nejlepších výsledků upravte složení svých slovníků prostředků tak, aby bylo možné vyhnout se odkazům na dopředné odkazy.</span><span class="sxs-lookup"><span data-stu-id="58064-114">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="58064-115">Pokud se vám nedaří dopředný odkaz, použijte místo toho [rozšíření značek DynamicResource](dynamicresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="58064-115">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="58064-116">Zadaný parametr <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měl odpovídat existujícímu prostředku, který je identifikovaný pomocí [direktivy x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) na určité úrovni stránky, aplikace, dostupných motivů ovládacích prvků a externích prostředků nebo systémových prostředků.</span><span class="sxs-lookup"><span data-stu-id="58064-116">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="58064-117">K vyhledávání prostředků dochází v tomto pořadí.</span><span class="sxs-lookup"><span data-stu-id="58064-117">The resource lookup occurs in that order.</span></span> <span data-ttu-id="58064-118">Další informace o chování vyhledávání prostředků pro statické a dynamické prostředky naleznete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="58064-118">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="58064-119">Klíč prostředků může být libovolný řetězec definovaný v gramatice v kódu [XAML](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="58064-119">A resource key can be any string defined in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="58064-120">Klíč prostředků může být také jiné typy objektů, jako je například <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="58064-120">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="58064-121"><xref:System.Type>Klíč je zásadní pro to, jak lze ovládací prvky stylovat pomocí motivů pomocí implicitního klíče stylu.</span><span class="sxs-lookup"><span data-stu-id="58064-121">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="58064-122">Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="58064-122">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="58064-123">Alternativním deklarativním způsobem, který odkazuje na prostředek, je [rozšíření značek DynamicResource](dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="58064-123">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="58064-124">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="58064-124">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="58064-125">Token řetězce poskytnutý po `StaticResource` řetězci identifikátoru je přiřazen jako <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> hodnota základní <xref:System.Windows.StaticResourceExtension> třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="58064-125">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="58064-126">`StaticResource`lze použít v syntaxi elementu Object.</span><span class="sxs-lookup"><span data-stu-id="58064-126">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="58064-127">V takovém případě <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> je nutné zadat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58064-127">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="58064-128">`StaticResource`lze také použít v podrobném použití atributu, které určuje <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost jako dvojici vlastnost = hodnota:</span><span class="sxs-lookup"><span data-stu-id="58064-128">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" ... />  
```  
  
 <span data-ttu-id="58064-129">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="58064-129">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="58064-130">Protože `StaticResource` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.</span><span class="sxs-lookup"><span data-stu-id="58064-130">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="58064-131">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementaci procesoru je zpracování tohoto rozšíření značek definováno <xref:System.Windows.StaticResourceExtension> třídou.</span><span class="sxs-lookup"><span data-stu-id="58064-131">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="58064-132">`StaticResource`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="58064-132">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="58064-133">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58064-133">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="58064-134">Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že je nutné zpracovat atribut v rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="58064-134">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="58064-135">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="58064-135">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58064-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="58064-136">See also</span></span>

- [<span data-ttu-id="58064-137">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="58064-137">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="58064-138">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="58064-138">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="58064-139">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="58064-139">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="58064-140">Zdroje XAML</span><span class="sxs-lookup"><span data-stu-id="58064-140">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="58064-141">Zdroje a kód</span><span class="sxs-lookup"><span data-stu-id="58064-141">Resources and Code</span></span>](resources-and-code.md)
