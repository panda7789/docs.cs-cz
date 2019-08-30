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
ms.openlocfilehash: 7fa729d600f25b73028bae0dd6d9248b5839dd4c
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133862"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="3d54d-102">ThemeDictionary – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="3d54d-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="3d54d-103">Poskytuje způsob, jak vlastní autoři ovládacích prvků nebo aplikace, které integrují ovládací prvky třetích stran pro načtení slovníků prostředků specifických pro motiv pro použití při stylování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3d54d-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3d54d-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="3d54d-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="3d54d-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="3d54d-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3d54d-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="3d54d-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="3d54d-107">[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Sestavení, které obsahuje informace o motivu.</span><span class="sxs-lookup"><span data-stu-id="3d54d-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="3d54d-108">Obvykle se jedná o identifikátor URI balíčku, který odkazuje na sestavení ve větším balíčku.</span><span class="sxs-lookup"><span data-stu-id="3d54d-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="3d54d-109">Prostředky sestavení a identifikátory URI balíčku zjednodušují problémy s nasazením.</span><span class="sxs-lookup"><span data-stu-id="3d54d-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="3d54d-110">Další informace najdete v tématu [identifikátory URI Pack v](../app-development/pack-uris-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="3d54d-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d54d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d54d-111">Remarks</span></span>  
 <span data-ttu-id="3d54d-112">Toto rozšíření má vyplnit jenom jednu konkrétní hodnotu vlastnosti: hodnota pro <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d54d-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="3d54d-113">Pomocí tohoto rozšíření můžete zadat jediné sestavení pouze pro prostředky, které obsahuje některé styly, které se použijí, když se v systému uživatele použije motiv Windows Aero, ostatní styly, jenom když je motiv Luna aktivní a tak dále.</span><span class="sxs-lookup"><span data-stu-id="3d54d-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="3d54d-114">Když použijete toto rozšíření, obsah slovníku prostředků specifický pro ovládací prvek se dá v případě potřeby automaticky zrušit a znovu načíst, aby byl pro jiný motiv specifický.</span><span class="sxs-lookup"><span data-stu-id="3d54d-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="3d54d-115">`assemblyUri` Řetězec(<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnota vlastnosti) tvoří základ zásady vytváření názvů, která určuje, který slovník se použije pro konkrétní motiv.</span><span class="sxs-lookup"><span data-stu-id="3d54d-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="3d54d-116">Logika pro `ThemeDictionary` dokončení konvence tím, že generuje [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] objekt, který odkazuje na konkrétní variantu slovníku motivu, jak je obsažen v předkompilovaném sestavení prostředků. <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A></span><span class="sxs-lookup"><span data-stu-id="3d54d-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="3d54d-117">Popis této konvence nebo interakce motivů s obecným stylem řízení a stylem stránky nebo aplikace jako konceptu se zde nepokrývá.</span><span class="sxs-lookup"><span data-stu-id="3d54d-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="3d54d-118">Základní scénář pro použití `ThemeDictionary` je <xref:System.Windows.ResourceDictionary.Source%2A> zadání vlastnosti `ResourceDictionary` deklarované na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="3d54d-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="3d54d-119">Pokud poskytnete [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] sestavení pro sestavení `ThemeDictionary` pomocí rozšíření, nikoli jako přímé [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], logika rozšíření poskytne neplatnou logiku, která se použije vždy, když se změní motiv systému.</span><span class="sxs-lookup"><span data-stu-id="3d54d-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="3d54d-120">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="3d54d-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="3d54d-121">Token řetězce poskytnutý po `ThemeDictionary` řetězci identifikátoru je přiřazen <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> jako hodnota základní <xref:System.Windows.ThemeDictionaryExtension> třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3d54d-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="3d54d-122">`ThemeDictionary`lze také použít v syntaxi elementu Object.</span><span class="sxs-lookup"><span data-stu-id="3d54d-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="3d54d-123">V takovém případě je nutné zadat hodnotu <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3d54d-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="3d54d-124">`ThemeDictionary`lze také použít v podrobném použití atributu, které určuje <xref:System.Windows.Markup.StaticExtension.Member%2A> vlastnost jako dvojici vlastnost = hodnota:</span><span class="sxs-lookup"><span data-stu-id="3d54d-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="3d54d-125">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="3d54d-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="3d54d-126">Protože `ThemeDictionary` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.</span><span class="sxs-lookup"><span data-stu-id="3d54d-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="3d54d-127">V implementaci procesoru je zpracování tohoto <xref:System.Windows.ThemeDictionaryExtension> rozšíření značek definováno třídou. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d54d-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="3d54d-128">`ThemeDictionary`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="3d54d-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="3d54d-129">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3d54d-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="3d54d-130">Všechna rozšíření [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek používají znaky {a} v jejich syntaxi atributu, což je konvence, podle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které procesor rozpozná, že je nutné zpracovat atribut v rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="3d54d-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="3d54d-131">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="3d54d-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d54d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d54d-132">See also</span></span>

- [<span data-ttu-id="3d54d-133">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="3d54d-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="3d54d-134">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="3d54d-134">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="3d54d-135">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="3d54d-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="3d54d-136">Prostředek, obsah a datové soubory aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="3d54d-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
