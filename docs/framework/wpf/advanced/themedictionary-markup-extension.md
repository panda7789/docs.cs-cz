---
title: "ThemeDictionary – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f878ce89dcf76ae800ade10a0e67f019741f65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="d80ad-102">ThemeDictionary – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="d80ad-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="d80ad-103">Umožňuje autorům vlastní ovládací prvek nebo aplikací, které se integrují ovládací prvky třetích stran načíst slovnících prostředků motiv specifické pro použití v styly ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d80ad-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="d80ad-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="d80ad-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="d80ad-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="d80ad-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="d80ad-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="d80ad-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="d80ad-107">[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Sestavení, který obsahuje informace o motivu.</span><span class="sxs-lookup"><span data-stu-id="d80ad-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="d80ad-108">Obvykle je to identifikátor URI, který odkazuje na sestavení v větší balíčku aktualizací Service pack.</span><span class="sxs-lookup"><span data-stu-id="d80ad-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="d80ad-109">Prostředky sestavení a pack identifikátory URI zjednodušit problémy při nasazení.</span><span class="sxs-lookup"><span data-stu-id="d80ad-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="d80ad-110">Další informace najdete v části [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="d80ad-110">For more information see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d80ad-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d80ad-111">Remarks</span></span>  
 <span data-ttu-id="d80ad-112">Toto rozšíření je určený k vyplnění pouze jednu hodnotu určitou vlastnost: hodnotu <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d80ad-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="d80ad-113">Když použijete toto rozšíření, můžete zadat jednoho pouze prostředky sestavení, který obsahuje některé styly používat pouze tehdy, když [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] motivu uživatele systému, jiné styly po vzhled Luna motiv aktivní a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d80ad-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] theme is applied to the user's system, other styles when Luna theme is active, and so on.</span></span> <span data-ttu-id="d80ad-114">Pomocí tohoto rozšíření obsah slovník prostředků specifické pro ovládací prvek může být automaticky zrušena znovu načíst a specifické pro jiný motiv vyžádání.</span><span class="sxs-lookup"><span data-stu-id="d80ad-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="d80ad-115">`assemblyUri` Řetězec (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnotu vlastnosti) je základem zásady vytváření názvů, který identifikuje, který slovník platí pro konkrétní motiv.</span><span class="sxs-lookup"><span data-stu-id="d80ad-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="d80ad-116"><xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Logiku pro `ThemeDictionary` dokončení konvence vygenerováním [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] který odkazuje na hodnotu typu variant slovník konkrétní motiv jako obsažené v sestavení předkompilovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="d80ad-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="d80ad-117">Popisující tento convention nebo motivu interakce s obecné řízení styly a úrovně stylů stránky nebo aplikace jako koncept a nepopisuje plně sem.</span><span class="sxs-lookup"><span data-stu-id="d80ad-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="d80ad-118">Základní scénáře použití `ThemeDictionary` slouží k zadání <xref:System.Windows.ResourceDictionary.Source%2A> vlastnost `ResourceDictionary` deklarovat na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="d80ad-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="d80ad-119">Když zadáte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro sestavení prostřednictvím `ThemeDictionary` rozšíření a nikoli jako přímou [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], logiku rozšíření zajistí zneplatnění logiku, která se použije při každé změně motiv systému.</span><span class="sxs-lookup"><span data-stu-id="d80ad-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="d80ad-120">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="d80ad-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="d80ad-121">Token řetězec zadaný po `ThemeDictionary` řetězec identifikátoru je přiřazen jako <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnotu základní <xref:System.Windows.ThemeDictionaryExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="d80ad-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="d80ad-122">`ThemeDictionary`také je možné použít objekt elementu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="d80ad-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="d80ad-123">V takovém případě určující hodnotu <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> vlastnost je povinná.</span><span class="sxs-lookup"><span data-stu-id="d80ad-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="d80ad-124">`ThemeDictionary`Můžete také použít využití podrobné atribut, který určuje <xref:System.Windows.Markup.StaticExtension.Member%2A> vlastnost jako vlastnost = dvojice hodnota:</span><span class="sxs-lookup"><span data-stu-id="d80ad-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="d80ad-125">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="d80ad-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="d80ad-126">Protože `ThemeDictionary` má jenom jednu nastavit vlastnost, který je vyžadován, toto podrobné použití není Typická.</span><span class="sxs-lookup"><span data-stu-id="d80ad-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="d80ad-127">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.ThemeDictionaryExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="d80ad-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="d80ad-128">`ThemeDictionary`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="d80ad-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="d80ad-129">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d80ad-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="d80ad-130">Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v jejich syntaxi atributů, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="d80ad-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="d80ad-131">Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="d80ad-131">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d80ad-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="d80ad-132">See Also</span></span>  
 [<span data-ttu-id="d80ad-133">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="d80ad-133">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d80ad-134">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="d80ad-134">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="d80ad-135">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="d80ad-135">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="d80ad-136">Prostředek aplikace WPF, obsahu a datových souborů</span><span class="sxs-lookup"><span data-stu-id="d80ad-136">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
