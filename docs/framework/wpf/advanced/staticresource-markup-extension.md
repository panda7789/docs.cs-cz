---
title: "StaticResource – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 821cd152ccb7a02dda5338d6a3ec44d6625c0097
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="12efd-102">StaticResource – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="12efd-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="12efd-103">Poskytuje hodnotu pro všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnost atribut vyhledáním odkaz na prostředek už definované.</span><span class="sxs-lookup"><span data-stu-id="12efd-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="12efd-104">Chování vyhledávání pro tento prostředek je obdobou čas načítání vyhledávání, který bude hledat prostředky, které byly dříve načteny z kódu aktuální [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky a také další aplikace zdroje a vygeneruje tuto hodnotu prostředků, jako Hodnota vlastnosti v objektech spuštění.</span><span class="sxs-lookup"><span data-stu-id="12efd-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="12efd-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="12efd-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="12efd-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="12efd-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="12efd-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="12efd-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="12efd-108">Klíč pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="12efd-108">The key for the requested resource.</span></span> <span data-ttu-id="12efd-109">Tento klíč původně přiřazený pomocí [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) prostředek byl vytvořen v značek, zda byla poskytnuta jako `key` parametr při volání metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Pokud prostředek se vytvořil v kódu.</span><span class="sxs-lookup"><span data-stu-id="12efd-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12efd-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12efd-110">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="12efd-111">A `StaticResource` nesmí pokus o spuštění dopředného odkazu na prostředek, který je definován v rámci lexikálně Další [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.</span><span class="sxs-lookup"><span data-stu-id="12efd-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="12efd-112">Pokusili, není podporován, a i v případě odkazu neselže, pokusu o odkaz na dopředného zpoplatněná snížení výkonu času zatížení při interní hodnota hash tabulky představující <xref:System.Windows.ResourceDictionary> vyhledávají.</span><span class="sxs-lookup"><span data-stu-id="12efd-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="12efd-113">Nejlepších výsledků dosáhnete upravte složení vaší slovnících prostředků tak, aby se vyhnout dopředného odkazy.</span><span class="sxs-lookup"><span data-stu-id="12efd-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="12efd-114">Pokud se nelze vyhnout dopředného odkaz, použijte [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) místo.</span><span class="sxs-lookup"><span data-stu-id="12efd-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="12efd-115">Zadaný <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měla odpovídat existující prostředek, označeny [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) na určité úrovni v stránku, aplikace, k dispozici řízení motivy a externím prostředkům nebo systémové prostředky.</span><span class="sxs-lookup"><span data-stu-id="12efd-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="12efd-116">K vyhledávání prostředků v tomto pořadí.</span><span class="sxs-lookup"><span data-stu-id="12efd-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="12efd-117">Další informace o chování vyhledávání prostředků pro statické a dynamické prostředky najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="12efd-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="12efd-118">Klíč prostředku může být libovolný řetězec definovaný v [XamlName – gramatika](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="12efd-118">A resource key can be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="12efd-119">Klíč prostředku může být také další typy objektů, jako například <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="12efd-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="12efd-120">A <xref:System.Type> klíč je nezbytné, aby jak můžete ve ovládací prvky podle motivy, prostřednictvím klíčem implicitní stylu.</span><span class="sxs-lookup"><span data-stu-id="12efd-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="12efd-121">Další informace najdete v tématu [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="12efd-121">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="12efd-122">Odkazování na prostředek alternativní deklarativní způsob je jako [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="12efd-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="12efd-123">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="12efd-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="12efd-124">Token řetězec zadaný po `StaticResource` řetězec identifikátoru je přiřazen jako <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> hodnotu základní <xref:System.Windows.StaticResourceExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="12efd-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="12efd-125">`StaticResource`lze použít v syntaxi objekt elementu.</span><span class="sxs-lookup"><span data-stu-id="12efd-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="12efd-126">V takovém případě určující hodnotu <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost je povinná.</span><span class="sxs-lookup"><span data-stu-id="12efd-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="12efd-127">`StaticResource`Můžete také použít využití podrobné atribut, který určuje <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost jako vlastnost = dvojice hodnota:</span><span class="sxs-lookup"><span data-stu-id="12efd-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="12efd-128">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="12efd-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="12efd-129">Protože `StaticResource` má jenom jednu nastavit vlastnost, který je vyžadován, toto podrobné použití není Typická.</span><span class="sxs-lookup"><span data-stu-id="12efd-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="12efd-130">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.StaticResourceExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="12efd-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="12efd-131">`StaticResource`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="12efd-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="12efd-132">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="12efd-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="12efd-133">Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v jejich syntaxi atributů, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="12efd-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="12efd-134">Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="12efd-134">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12efd-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="12efd-135">See Also</span></span>  
 [<span data-ttu-id="12efd-136">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="12efd-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="12efd-137">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="12efd-137">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="12efd-138">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="12efd-138">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="12efd-139">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="12efd-139">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="12efd-140">Prostředky a kódu</span><span class="sxs-lookup"><span data-stu-id="12efd-140">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)
