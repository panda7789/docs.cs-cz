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
ms.openlocfilehash: f6ba0fe45aa11063c79d673b26794072968f4200
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646190"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="395b5-102">ThemeDictionary – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="395b5-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="395b5-103">Poskytuje způsob, jak pro vlastní autoři ovládacích prvků nebo aplikace, které integrují ovládací prvky třetích stran k načtení slovníky prostředků specifické pro motiv pro použití v styling ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="395b5-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="395b5-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="395b5-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="395b5-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="395b5-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="395b5-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="395b5-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="395b5-107">Identifikátor jednotného prostředku (URI) sestavení, který obsahuje informace o motivu.</span><span class="sxs-lookup"><span data-stu-id="395b5-107">The uniform resource identifier (URI) of the assembly that contains theme information.</span></span> <span data-ttu-id="395b5-108">Obvykle se jedná o identifikátor URI balení, který odkazuje na sestavení ve větším balíčku.</span><span class="sxs-lookup"><span data-stu-id="395b5-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="395b5-109">Prostředky sestavení a balíčky identifikátorů URI zjednodušují problémy s nasazením.</span><span class="sxs-lookup"><span data-stu-id="395b5-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="395b5-110">Další informace naleznete [v tématu Pack URI v WPF](../app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="395b5-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="395b5-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="395b5-111">Remarks</span></span>  
 <span data-ttu-id="395b5-112">Toto rozšíření je určeno k vyplnění pouze <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>jedné konkrétní hodnoty vlastnosti: hodnota pro .</span><span class="sxs-lookup"><span data-stu-id="395b5-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="395b5-113">Pomocí tohoto rozšíření můžete určit jedno sestavení pouze pro prostředky, které obsahuje některé styly, které se použijí pouze v případě, že je motiv Prostředí Windows použit v systému uživatele, jiné styly pouze v případě, že je aktivní motiv Luna a tak dále.</span><span class="sxs-lookup"><span data-stu-id="395b5-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="395b5-114">Pomocí tohoto rozšíření obsah slovníku prostředků specifické pro ovládací prvek lze automaticky zneplatnit a znovu načíst být specifické pro jiný motiv v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="395b5-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="395b5-115">Řetězec `assemblyUri` (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnota vlastnosti) tvoří základ konvence pojmenování, která určuje, který slovník platí pro konkrétní motiv.</span><span class="sxs-lookup"><span data-stu-id="395b5-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="395b5-116">Logika <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> `ThemeDictionary` pro dokončení konvence generováním identifikátoru jednotného prostředku (URI), který odkazuje na konkrétní variantu slovníku motivu, jak je obsaženv rámci sestavení předkompilovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="395b5-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a uniform resource identifier (URI) that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="395b5-117">Popis této konvence nebo interakce motivu s obecným řídicím stylem a stylem na úrovni stránky/aplikace jako koncept emituje meze.</span><span class="sxs-lookup"><span data-stu-id="395b5-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="395b5-118">Základní scénář pro `ThemeDictionary` použití je <xref:System.Windows.ResourceDictionary.Source%2A> určit `ResourceDictionary` vlastnost deklarované na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="395b5-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="395b5-119">Pokud zadáte identifikátor URI pro `ThemeDictionary` sestavení prostřednictvím rozšíření, nikoli jako přímý identifikátor URI, logika rozšíření poskytne logiku zneplatnění, která se použije při každé změně motivu systému.</span><span class="sxs-lookup"><span data-stu-id="395b5-119">When you provide a URI for the assembly through a `ThemeDictionary` extension rather than as a direct URI, the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="395b5-120">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="395b5-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="395b5-121">Token řetězce zadaný `ThemeDictionary` po přidělení řetězce <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> identifikátoru jako <xref:System.Windows.ThemeDictionaryExtension> hodnota základní třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="395b5-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="395b5-122">`ThemeDictionary`lze také použít v syntaxi prvku objektu.</span><span class="sxs-lookup"><span data-stu-id="395b5-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="395b5-123">V tomto případě je vyžadováno <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> zadání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="395b5-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="395b5-124">`ThemeDictionary`lze také použít v podrobném použití atributu, který určuje <xref:System.Windows.Markup.StaticExtension.Member%2A> vlastnost jako dvojici vlastností=hodnota:</span><span class="sxs-lookup"><span data-stu-id="395b5-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="395b5-125">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="395b5-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="395b5-126">Protože `ThemeDictionary` má pouze jednu vlastnost settable, která je vyžadována, toto podrobné použití není typické.</span><span class="sxs-lookup"><span data-stu-id="395b5-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="395b5-127">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] V implementaci procesoru zpracování pro toto rozšíření <xref:System.Windows.ThemeDictionaryExtension> značky je definována třídy.</span><span class="sxs-lookup"><span data-stu-id="395b5-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="395b5-128">`ThemeDictionary`je rozšíření značky.</span><span class="sxs-lookup"><span data-stu-id="395b5-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="395b5-129">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="395b5-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="395b5-130">Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky { a } v syntaxi atributu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] což je konvence, podle které procesor rozpozná, že rozšíření značek musí atribut zpracovat.</span><span class="sxs-lookup"><span data-stu-id="395b5-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="395b5-131">Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="395b5-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395b5-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="395b5-132">See also</span></span>

- [<span data-ttu-id="395b5-133">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="395b5-133">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="395b5-134">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="395b5-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="395b5-135">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="395b5-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="395b5-136">Prostředek, obsah a datové soubory aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="395b5-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
