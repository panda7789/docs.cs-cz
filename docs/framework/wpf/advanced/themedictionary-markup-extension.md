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
ms.openlocfilehash: ad2248c791fadc5363d90ff496d5e040f6036ab3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054221"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="395cc-102">ThemeDictionary – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="395cc-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="395cc-103">Poskytuje způsob, jak pro vlastní ovládací prvek autorů nebo aplikace, které se integrují ovládací prvky třetích stran pro načtení konkrétní motivu zdrojových slovnících pro použití v používání stylů pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="395cc-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="395cc-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="395cc-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="395cc-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="395cc-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="395cc-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="395cc-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="395cc-107">[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Sestavení, který obsahuje informace o motivech.</span><span class="sxs-lookup"><span data-stu-id="395cc-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="395cc-108">Obvykle je to identifikátor URI, který odkazuje na sestavení v balíčku větší sadu.</span><span class="sxs-lookup"><span data-stu-id="395cc-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="395cc-109">Prostředky sestavení a sady identifikátorů URI pro zjednodušení problémů s nasazením.</span><span class="sxs-lookup"><span data-stu-id="395cc-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="395cc-110">Další informace najdete v části [identifikátory Pack URI v subsystému WPF](../app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="395cc-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="395cc-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="395cc-111">Remarks</span></span>  
 <span data-ttu-id="395cc-112">Toto rozšíření je určený k vyplnění pouze jednu hodnotu určité vlastnosti: hodnota pro <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="395cc-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="395cc-113">Pomocí tohoto rozšíření, můžete určit jedno sestavení pouze pro prostředky, který obsahuje některé styly používat pouze tehdy, když [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] motivu systému uživatele, i jiné styly při Luna motivu je aktivní a tak dále.</span><span class="sxs-lookup"><span data-stu-id="395cc-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] theme is applied to the user's system, other styles when Luna theme is active, and so on.</span></span> <span data-ttu-id="395cc-114">Pomocí tohoto rozšíření obsah slovník prostředků specifických pro ovládací prvek může být automaticky zneplatněny a specifické pro jiný motiv v případě potřeby znovu načíst.</span><span class="sxs-lookup"><span data-stu-id="395cc-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="395cc-115">`assemblyUri` Řetězce (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnotu vlastnosti) tento balíček je základem zásady vytváření názvů identifikuje slovník, který se vztahuje na konkrétní motivu.</span><span class="sxs-lookup"><span data-stu-id="395cc-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="395cc-116"><xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Logiku pro `ThemeDictionary` dokončení úmluvy vygenerováním [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] , která odkazuje na hodnotu typu variant slovníku konkrétní motivu obsažené v rámci sestavení předkompilované prostředků.</span><span class="sxs-lookup"><span data-stu-id="395cc-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="395cc-117">Popisující vytváření názvů nebo motivu interakce s používání stylů pro ovládací prvek obecné a úrovni stylů stránky nebo aplikace jako koncept, není součástí tohoto plně.</span><span class="sxs-lookup"><span data-stu-id="395cc-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="395cc-118">Základní scénář pro použití `ThemeDictionary` je zadání <xref:System.Windows.ResourceDictionary.Source%2A> vlastnost `ResourceDictionary` deklarované na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="395cc-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="395cc-119">Když zadáte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro sestavení prostřednictvím `ThemeDictionary` rozšíření, nikoli jako přímou [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], logiku rozšíření poskytne zneplatnění logiku, která se použije při každé změně motiv systému.</span><span class="sxs-lookup"><span data-stu-id="395cc-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="395cc-120">Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="395cc-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="395cc-121">Řetězec s tokenem uvedený za `ThemeDictionary` řetězec identifikátoru je přiřazen jako <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnoty základního <xref:System.Windows.ThemeDictionaryExtension> rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="395cc-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="395cc-122">`ThemeDictionary` může také použít v syntaxi elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="395cc-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="395cc-123">V takovém případě zadáte hodnotu <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> vlastnost je povinná.</span><span class="sxs-lookup"><span data-stu-id="395cc-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="395cc-124">`ThemeDictionary` je také možné využití podrobné atribut, který určuje <xref:System.Windows.Markup.StaticExtension.Member%2A> vlastnost jako vlastnost = hodnota pár:</span><span class="sxs-lookup"><span data-stu-id="395cc-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="395cc-125">Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné.</span><span class="sxs-lookup"><span data-stu-id="395cc-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="395cc-126">Protože `ThemeDictionary` má jen jednu nastavitelnou vlastnost, která je požadována, toto použití podrobné syntaxe není typické.</span><span class="sxs-lookup"><span data-stu-id="395cc-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="395cc-127">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru, zpracování tohoto rozšíření značek definováno <xref:System.Windows.ThemeDictionaryExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="395cc-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="395cc-128">`ThemeDictionary` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="395cc-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="395cc-129">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="395cc-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="395cc-130">Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v syntaxi atributu, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="395cc-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="395cc-131">Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="395cc-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395cc-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="395cc-132">See also</span></span>

- [<span data-ttu-id="395cc-133">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="395cc-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="395cc-134">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="395cc-134">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="395cc-135">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="395cc-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="395cc-136">Prostředek, obsah a datové soubory aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="395cc-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
