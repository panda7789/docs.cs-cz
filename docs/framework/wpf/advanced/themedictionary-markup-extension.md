---
title: ThemeDictionary – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: 450956de1c7498bf2b92096b38ad2f64745a0b2d
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141100"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="244de-102">ThemeDictionary – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="244de-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="244de-103">Poskytuje způsob, jak vlastní autoři ovládacích prvků nebo aplikace, které integrují ovládací prvky třetích stran pro načtení slovníků prostředků specifických pro motiv pro použití při stylování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="244de-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="244de-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="244de-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" ... />  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="244de-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="244de-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="244de-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="244de-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="244de-107">Identifikátor URI (Uniform Resource Identifier) sestavení, které obsahuje informace o motivu.</span><span class="sxs-lookup"><span data-stu-id="244de-107">The uniform resource identifier (URI) of the assembly that contains theme information.</span></span> <span data-ttu-id="244de-108">Obvykle se jedná o identifikátor URI balíčku, který odkazuje na sestavení ve větším balíčku.</span><span class="sxs-lookup"><span data-stu-id="244de-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="244de-109">Prostředky sestavení a identifikátory URI balíčku zjednodušují problémy s nasazením.</span><span class="sxs-lookup"><span data-stu-id="244de-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="244de-110">Další informace najdete v tématu [identifikátory URI Pack v](../app-development/pack-uris-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="244de-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="244de-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="244de-111">Remarks</span></span>  
 <span data-ttu-id="244de-112">Toto rozšíření má vyplnit jenom jednu konkrétní hodnotu vlastnosti: hodnota pro <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="244de-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="244de-113">Pomocí tohoto rozšíření můžete zadat jediné sestavení pouze pro prostředky, které obsahuje některé styly, které se použijí, když se v systému uživatele použije motiv Windows Aero, ostatní styly, jenom když je motiv Luna aktivní a tak dále.</span><span class="sxs-lookup"><span data-stu-id="244de-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="244de-114">Když použijete toto rozšíření, obsah slovníku prostředků specifický pro ovládací prvek se dá v případě potřeby automaticky zrušit a znovu načíst, aby byl pro jiný motiv specifický.</span><span class="sxs-lookup"><span data-stu-id="244de-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="244de-115">`assemblyUri` Řetězec (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnota vlastnosti) tvoří základ zásady vytváření názvů, která určuje, který slovník se použije pro konkrétní motiv.</span><span class="sxs-lookup"><span data-stu-id="244de-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="244de-116"><xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Logika pro `ThemeDictionary` dokončení konvence vygenerováním identifikátoru URI (Uniform Resource Identifier), který odkazuje na konkrétní variantu slovníku motivů, jak je obsaženo v předkompilovaném sestavení prostředků.</span><span class="sxs-lookup"><span data-stu-id="244de-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a uniform resource identifier (URI) that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="244de-117">Popis této konvence nebo interakce motivů s obecným stylem řízení a stylem stránky nebo aplikace jako konceptu se zde nepokrývá.</span><span class="sxs-lookup"><span data-stu-id="244de-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="244de-118">Základní scénář pro použití `ThemeDictionary` je zadání <xref:System.Windows.ResourceDictionary.Source%2A> vlastnosti `ResourceDictionary` deklarované na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="244de-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="244de-119">Pokud zadáte identifikátor URI pro sestavení prostřednictvím `ThemeDictionary` rozšíření, nikoli jako přímý identifikátor URI, logika rozšíření poskytne neplatnou logiku, která se použije vždy, když se změní motiv systému.</span><span class="sxs-lookup"><span data-stu-id="244de-119">When you provide a URI for the assembly through a `ThemeDictionary` extension rather than as a direct URI, the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="244de-120">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="244de-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="244de-121">Token řetězce poskytnutý po řetězci `ThemeDictionary` identifikátoru je přiřazen jako <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnota základní <xref:System.Windows.ThemeDictionaryExtension> třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="244de-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="244de-122">`ThemeDictionary`lze také použít v syntaxi elementu Object.</span><span class="sxs-lookup"><span data-stu-id="244de-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="244de-123">V takovém případě je nutné zadat hodnotu <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="244de-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="244de-124">`ThemeDictionary`lze také použít v podrobném použití atributu, které určuje <xref:System.Windows.Markup.StaticExtension.Member%2A> vlastnost jako dvojici vlastnost = hodnota:</span><span class="sxs-lookup"><span data-stu-id="244de-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" ... />  
```  
  
 <span data-ttu-id="244de-125">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="244de-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="244de-126">Protože `ThemeDictionary` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.</span><span class="sxs-lookup"><span data-stu-id="244de-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="244de-127">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] V implementaci procesoru je zpracování tohoto rozšíření značek definováno <xref:System.Windows.ThemeDictionaryExtension> třídou.</span><span class="sxs-lookup"><span data-stu-id="244de-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="244de-128">`ThemeDictionary`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="244de-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="244de-129">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="244de-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="244de-130">Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že je nutné zpracovat atribut v rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="244de-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="244de-131">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="244de-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244de-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="244de-132">See also</span></span>

- [<span data-ttu-id="244de-133">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="244de-133">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="244de-134">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="244de-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="244de-135">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="244de-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="244de-136">Prostředek, obsah a datové soubory aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="244de-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
