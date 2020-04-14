---
title: ComponentResourceKey – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243359"
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="26bdc-102">ComponentResourceKey – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="26bdc-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="26bdc-103">Definuje a odkazuje na klíče pro prostředky, které jsou načteny z externích sestavení.</span><span class="sxs-lookup"><span data-stu-id="26bdc-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="26bdc-104">To umožňuje vyhledávání prostředků určit cílový typ v sestavení, nikoli explicitní slovník prostředků v sestavení nebo ve třídě.</span><span class="sxs-lookup"><span data-stu-id="26bdc-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="26bdc-105">Použití atributu XAML (klíč nastavení, kompaktní)</span><span class="sxs-lookup"><span data-stu-id="26bdc-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="26bdc-106">Použití atributu XAML (nastavení klíče, podrobné)</span><span class="sxs-lookup"><span data-stu-id="26bdc-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="26bdc-107">Využití atributů XAML (vyžádání prostředku, komprimace)</span><span class="sxs-lookup"><span data-stu-id="26bdc-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="26bdc-108">Využití atributů XAML (vyžádání prostředku, podrobné)</span><span class="sxs-lookup"><span data-stu-id="26bdc-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="26bdc-109">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="26bdc-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="26bdc-110">Název typu clr (public common language language) , který je definován v sestavení prostředku.</span><span class="sxs-lookup"><span data-stu-id="26bdc-110">The name of the public common language runtime (CLR) type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="26bdc-111">Klíč pro prostředek.</span><span class="sxs-lookup"><span data-stu-id="26bdc-111">The key for the resource.</span></span> <span data-ttu-id="26bdc-112">Při vyhlédnout zdroje, `targetID` bude obdobou [x:Key směrnice](../../../desktop-wpf/xaml-services/xkey-directive.md) prostředku.</span><span class="sxs-lookup"><span data-stu-id="26bdc-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26bdc-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26bdc-113">Remarks</span></span>  
 <span data-ttu-id="26bdc-114">Jak je vidět ve výše`ComponentResourceKey`uvedených použitích, použití rozšíření značek { } se nachází na dvou místech:</span><span class="sxs-lookup"><span data-stu-id="26bdc-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
- <span data-ttu-id="26bdc-115">Definice klíče v rámci slovníku prostředků motivu, jak je k dispozici autor ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="26bdc-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
- <span data-ttu-id="26bdc-116">Přístup k prostředku motivu ze sestavení, když retemplating ovládacího prvku, ale chcete použít hodnoty vlastností, které pocházejí z prostředků poskytovaných motivy ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="26bdc-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="26bdc-117">Pro odkazování na zdroje komponent, které pocházejí z `{DynamicResource}` motivů, se obecně doporučuje použít spíše než `{StaticResource}`.</span><span class="sxs-lookup"><span data-stu-id="26bdc-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="26bdc-118">To je zobrazeno v použití.</span><span class="sxs-lookup"><span data-stu-id="26bdc-118">This is shown in the usages.</span></span> <span data-ttu-id="26bdc-119">`{DynamicResource}`doporučuje, protože samotný motiv může být změněn uživatelem.</span><span class="sxs-lookup"><span data-stu-id="26bdc-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="26bdc-120">Pokud chcete, aby prostředek komponenty, který nejvíce odpovídá záměru autora ovládacího prvku pro podporu motivu, měli byste povolit, aby byl odkaz na prostředek komponenty také dynamický.</span><span class="sxs-lookup"><span data-stu-id="26bdc-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="26bdc-121">Identifikuje <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> typ, který existuje v cílovém sestavení, kde je prostředek skutečně definován.</span><span class="sxs-lookup"><span data-stu-id="26bdc-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="26bdc-122">A `ComponentResourceKey` lze definovat a použít nezávisle na <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tom, přesně vědět, kde je definován, ale nakonec musí vyřešit typ prostřednictvím odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="26bdc-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="26bdc-123">Běžné použití <xref:System.Windows.ComponentResourceKey> pro je definovat klíče, které jsou pak vystaveny jako členové třídy.</span><span class="sxs-lookup"><span data-stu-id="26bdc-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="26bdc-124">Pro toto použití <xref:System.Windows.ComponentResourceKey> použijete konstruktor třídy, nikoli rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="26bdc-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="26bdc-125">Další informace naleznete <xref:System.Windows.ComponentResourceKey>v tématu Definování a odkazování klíčů pro prostředky motivu v tématu [Přehled vytváření ovládacího prvku](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="26bdc-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="26bdc-126">Pro vytváření klíčů a odkazování na klíče prostředky, syntaxe `ComponentResourceKey` atributu se běžně používá pro rozšíření značky.</span><span class="sxs-lookup"><span data-stu-id="26bdc-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="26bdc-127">Zobrazená kompaktní syntaxe <xref:System.Windows.ComponentResourceKey.%23ctor%2A> závisí na podpisu konstruktoru a použití pozičního parametru rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="26bdc-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="26bdc-128">Pořadí, ve `targetTypeName` kterém `targetID` a jsou uvedeny, je důležité.</span><span class="sxs-lookup"><span data-stu-id="26bdc-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="26bdc-129">Podrobná syntaxe spoléhá na <xref:System.Windows.ComponentResourceKey.%23ctor%2A> konstruktor bez parametrů a <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> <xref:System.Windows.ComponentResourceKey.ResourceId%2A> pak nastaví a způsobem, který je obdobou syntaxe true atributu na elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="26bdc-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> parameterless constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="26bdc-130">V podrobné syntaxi není důležité pořadí, ve kterém jsou nastaveny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26bdc-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="26bdc-131">Vztah a mechanismy těchto dvou alternativ (kompaktní a podrobné) jsou podrobněji popsány v tématu [Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="26bdc-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="26bdc-132">Technicky hodnota pro `targetID` může být libovolný objekt, nemusí být řetězec.</span><span class="sxs-lookup"><span data-stu-id="26bdc-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="26bdc-133">Nejběžnější použití v WPF je však `targetID` zarovnat hodnotu s formuláři, které jsou řetězce a kde tyto řetězce jsou platné v [XamlName gramatiky](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="26bdc-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="26bdc-134">`ComponentResourceKey`lze použít v syntaxi prvku objektu.</span><span class="sxs-lookup"><span data-stu-id="26bdc-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="26bdc-135">V tomto případě je nutné zadat <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> <xref:System.Windows.ComponentResourceKey.ResourceId%2A> hodnotu vlastnosti a správně inicializovat rozšíření.</span><span class="sxs-lookup"><span data-stu-id="26bdc-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="26bdc-136">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] V implementaci čtečky zpracování pro toto rozšíření <xref:System.Windows.ComponentResourceKey> značky je definována třídy.</span><span class="sxs-lookup"><span data-stu-id="26bdc-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="26bdc-137">`ComponentResourceKey`je rozšíření značky.</span><span class="sxs-lookup"><span data-stu-id="26bdc-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="26bdc-138">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26bdc-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="26bdc-139">Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky { a } v syntaxi atributu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] což je konvence, podle které procesor rozpozná, že rozšíření značek musí atribut zpracovat.</span><span class="sxs-lookup"><span data-stu-id="26bdc-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="26bdc-140">Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="26bdc-140">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bdc-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="26bdc-141">See also</span></span>

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="26bdc-142">Přehled vytváření ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="26bdc-142">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
- [<span data-ttu-id="26bdc-143">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="26bdc-143">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="26bdc-144">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="26bdc-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
