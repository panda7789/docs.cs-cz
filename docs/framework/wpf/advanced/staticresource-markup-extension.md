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
ms.openlocfilehash: b15e2c0bac5610c6f1b10a640254236987c0bcf5
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458733"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="5d83f-102">StaticResource – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="5d83f-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="5d83f-103">Poskytuje hodnotu pro libovolný atribut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnosti vyhledáním odkazu na již definovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="5d83f-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="5d83f-104">Chování vyhledávání pro tento prostředek je obdobou vyhledávání při načítání, což bude hledat prostředky, které byly dříve načteny z kódu aktuální [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky a také do jiných zdrojů aplikací, a vygeneruje tuto hodnotu prostředku jako vlastnost. hodnota v objektech runtime.</span><span class="sxs-lookup"><span data-stu-id="5d83f-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="5d83f-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="5d83f-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="5d83f-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="5d83f-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5d83f-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="5d83f-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="5d83f-108">Klíč pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="5d83f-108">The key for the requested resource.</span></span> <span data-ttu-id="5d83f-109">Tento klíč byl původně přiřazen [direktivou x:Key –](../../xaml-services/x-key-directive.md) , pokud byl prostředek vytvořen v kódu, nebo byl zadán jako parametr `key` při volání <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>, pokud byl prostředek vytvořen v kódu.</span><span class="sxs-lookup"><span data-stu-id="5d83f-109">This key was initially assigned by the [x:Key Directive](../../xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d83f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d83f-110">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5d83f-111">`StaticResource` se nesmí pokusit vytvořit dopředný odkaz na prostředek, který je v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru definován lexikálním.</span><span class="sxs-lookup"><span data-stu-id="5d83f-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="5d83f-112">Pokus o provedení této akce není podporován a i v případě, že takový odkaz neselže, bude při pokusu o přemístění v případě, že se prohledávají vnitřní tabulky hash reprezentující <xref:System.Windows.ResourceDictionary>, vyhledána pokuta výkonu při načítání.</span><span class="sxs-lookup"><span data-stu-id="5d83f-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="5d83f-113">Pro dosažení nejlepších výsledků upravte složení svých slovníků prostředků tak, aby bylo možné vyhnout se odkazům na dopředné odkazy.</span><span class="sxs-lookup"><span data-stu-id="5d83f-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="5d83f-114">Pokud se vám nedaří dopředný odkaz, použijte místo toho [rozšíření značek DynamicResource](dynamicresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="5d83f-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="5d83f-115">Zadaný <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měl odpovídat existujícímu prostředku identifikovanému pomocí [direktivy x:Key –](../../xaml-services/x-key-directive.md) na některé úrovni stránky, aplikaci, dostupných motivech ovládacích prvků a externích prostředků nebo systémových prostředků.</span><span class="sxs-lookup"><span data-stu-id="5d83f-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="5d83f-116">K vyhledávání prostředků dochází v tomto pořadí.</span><span class="sxs-lookup"><span data-stu-id="5d83f-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="5d83f-117">Další informace o chování vyhledávání prostředků pro statické a dynamické prostředky naleznete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="5d83f-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="5d83f-118">Klíč prostředků může být libovolný řetězec definovaný v gramatice v kódu [XAML](../../xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="5d83f-118">A resource key can be any string defined in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="5d83f-119">Klíč prostředků může být také jiné typy objektů, například <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="5d83f-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="5d83f-120"><xref:System.Type> klíč je zásadní pro to, jak lze ovládací prvky stylovat pomocí motivů pomocí implicitního klíče stylu.</span><span class="sxs-lookup"><span data-stu-id="5d83f-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="5d83f-121">Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d83f-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="5d83f-122">Alternativním deklarativním způsobem, který odkazuje na prostředek, je [rozšíření značek DynamicResource](dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="5d83f-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="5d83f-123">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="5d83f-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="5d83f-124">Token řetězce poskytnutý po řetězci `StaticResource` identifikátoru je přiřazen jako hodnota <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> základní třídy rozšíření <xref:System.Windows.StaticResourceExtension>.</span><span class="sxs-lookup"><span data-stu-id="5d83f-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="5d83f-125">`StaticResource` lze použít v syntaxi elementu Object.</span><span class="sxs-lookup"><span data-stu-id="5d83f-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="5d83f-126">V takovém případě je nutné zadat hodnotu vlastnosti <xref:System.Windows.StaticResourceExtension.ResourceKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d83f-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="5d83f-127">`StaticResource` lze také použít v podrobném použití atributu, které určuje vlastnost <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> jako dvojici vlastnost = hodnota:</span><span class="sxs-lookup"><span data-stu-id="5d83f-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="5d83f-128">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="5d83f-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="5d83f-129">Protože `StaticResource` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.</span><span class="sxs-lookup"><span data-stu-id="5d83f-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="5d83f-130">V implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.StaticResourceExtension>.</span><span class="sxs-lookup"><span data-stu-id="5d83f-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="5d83f-131">`StaticResource` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="5d83f-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="5d83f-132">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5d83f-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="5d83f-133">Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznává, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="5d83f-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="5d83f-134">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="5d83f-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d83f-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d83f-135">See also</span></span>

- [<span data-ttu-id="5d83f-136">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="5d83f-136">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="5d83f-137">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="5d83f-137">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="5d83f-138">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="5d83f-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="5d83f-139">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="5d83f-139">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="5d83f-140">Prostředky a kód</span><span class="sxs-lookup"><span data-stu-id="5d83f-140">Resources and Code</span></span>](resources-and-code.md)
