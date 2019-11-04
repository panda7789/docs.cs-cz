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
ms.openlocfilehash: ab38c2c885e230183852fff895e0a8a8f1d7a666
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459485"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="e70ed-102">ThemeDictionary – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="e70ed-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="e70ed-103">Poskytuje způsob, jak vlastní autoři ovládacích prvků nebo aplikace, které integrují ovládací prvky třetích stran pro načtení slovníků prostředků specifických pro motiv pro použití při stylování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e70ed-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e70ed-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="e70ed-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="e70ed-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="e70ed-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e70ed-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="e70ed-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="e70ed-107">Identifikátor URI (Uniform Resource Identifier) sestavení, které obsahuje informace o motivu.</span><span class="sxs-lookup"><span data-stu-id="e70ed-107">The uniform resource identifier (URI) of the assembly that contains theme information.</span></span> <span data-ttu-id="e70ed-108">Obvykle se jedná o identifikátor URI balíčku, který odkazuje na sestavení ve větším balíčku.</span><span class="sxs-lookup"><span data-stu-id="e70ed-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="e70ed-109">Prostředky sestavení a identifikátory URI balíčku zjednodušují problémy s nasazením.</span><span class="sxs-lookup"><span data-stu-id="e70ed-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="e70ed-110">Další informace najdete v tématu [identifikátory URI Pack v](../app-development/pack-uris-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="e70ed-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e70ed-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e70ed-111">Remarks</span></span>  
 <span data-ttu-id="e70ed-112">Toto rozšíření má vyplnit jenom jednu konkrétní hodnotu vlastnosti: hodnotu pro <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e70ed-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e70ed-113">Pomocí tohoto rozšíření můžete zadat jediné sestavení pouze pro prostředky, které obsahuje některé styly, které se použijí, když se v systému uživatele použije motiv Windows Aero, ostatní styly, jenom když je motiv Luna aktivní a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e70ed-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="e70ed-114">Když použijete toto rozšíření, obsah slovníku prostředků specifický pro ovládací prvek se dá v případě potřeby automaticky zrušit a znovu načíst, aby byl pro jiný motiv specifický.</span><span class="sxs-lookup"><span data-stu-id="e70ed-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="e70ed-115">`assemblyUri` řetězec (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnota vlastnosti) tvoří základ konvence pojmenování, která určuje, který slovník se použije pro konkrétní motiv.</span><span class="sxs-lookup"><span data-stu-id="e70ed-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="e70ed-116">Logika <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> pro `ThemeDictionary` dokončí konvenci vygenerováním identifikátoru URI (Uniform Resource Identifier), který odkazuje na konkrétní variantu slovníku motivů, jak je obsaženo v předkompilovaném sestavení prostředků.</span><span class="sxs-lookup"><span data-stu-id="e70ed-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a uniform resource identifier (URI) that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="e70ed-117">Popis této konvence nebo interakce motivů s obecným stylem řízení a stylem stránky nebo aplikace jako konceptu se zde nepokrývá.</span><span class="sxs-lookup"><span data-stu-id="e70ed-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="e70ed-118">Základní scénář použití `ThemeDictionary` je zadání vlastnosti <xref:System.Windows.ResourceDictionary.Source%2A> `ResourceDictionary` deklarované na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="e70ed-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="e70ed-119">Pokud zadáte identifikátor URI pro sestavení prostřednictvím rozšíření `ThemeDictionary`, nikoli jako přímý identifikátor URI, logika rozšíření poskytne neplatnou logiku, která se použije vždy, když se změní motiv systému.</span><span class="sxs-lookup"><span data-stu-id="e70ed-119">When you provide a URI for the assembly through a `ThemeDictionary` extension rather than as a direct URI, the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="e70ed-120">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="e70ed-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="e70ed-121">Token řetězce poskytnutý po řetězci `ThemeDictionary` identifikátoru je přiřazen jako hodnota <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> základní třídy rozšíření <xref:System.Windows.ThemeDictionaryExtension>.</span><span class="sxs-lookup"><span data-stu-id="e70ed-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="e70ed-122">`ThemeDictionary` lze také použít v syntaxi elementu Object.</span><span class="sxs-lookup"><span data-stu-id="e70ed-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="e70ed-123">V takovém případě je nutné zadat hodnotu vlastnosti <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>.</span><span class="sxs-lookup"><span data-stu-id="e70ed-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="e70ed-124">`ThemeDictionary` lze také použít v podrobném použití atributu, které určuje vlastnost <xref:System.Windows.Markup.StaticExtension.Member%2A> jako dvojici vlastnost = hodnota:</span><span class="sxs-lookup"><span data-stu-id="e70ed-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="e70ed-125">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="e70ed-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="e70ed-126">Protože `ThemeDictionary` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.</span><span class="sxs-lookup"><span data-stu-id="e70ed-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="e70ed-127">V implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.ThemeDictionaryExtension>.</span><span class="sxs-lookup"><span data-stu-id="e70ed-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="e70ed-128">`ThemeDictionary` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="e70ed-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="e70ed-129">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e70ed-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="e70ed-130">Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznává, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="e70ed-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="e70ed-131">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="e70ed-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e70ed-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e70ed-132">See also</span></span>

- [<span data-ttu-id="e70ed-133">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e70ed-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="e70ed-134">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="e70ed-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="e70ed-135">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="e70ed-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="e70ed-136">Prostředek, obsah a datové soubory aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="e70ed-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
