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
ms.openlocfilehash: f86b7000b97bbc1287347947a9244c24a7de74c2
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141127"
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="915d0-102">ComponentResourceKey – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="915d0-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="915d0-103">Definuje a odkazuje na klíče pro prostředky, které jsou načteny z externích sestavení.</span><span class="sxs-lookup"><span data-stu-id="915d0-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="915d0-104">Díky tomu může vyhledávání prostředků určovat cílový typ v sestavení, nikoli explicitní slovník prostředků v sestavení nebo třídě.</span><span class="sxs-lookup"><span data-stu-id="915d0-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="915d0-105">Použití atributu XAML (nastavení klíče, komprimace)</span><span class="sxs-lookup"><span data-stu-id="915d0-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" ... />  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="915d0-106">Použití atributu XAML (nastavení klíče, verbose)</span><span class="sxs-lookup"><span data-stu-id="915d0-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" ... />  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="915d0-107">Použití atributu XAML (vyžádání prostředku, kompaktní)</span><span class="sxs-lookup"><span data-stu-id="915d0-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" ... />  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="915d0-108">Použití atributu XAML (vyžádání prostředku, verbose)</span><span class="sxs-lookup"><span data-stu-id="915d0-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" ... />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="915d0-109">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="915d0-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="915d0-110">Název veřejného typu modulu CLR (Common Language Runtime), který je definován v sestavení prostředků.</span><span class="sxs-lookup"><span data-stu-id="915d0-110">The name of the public common language runtime (CLR) type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="915d0-111">Klíč pro prostředek</span><span class="sxs-lookup"><span data-stu-id="915d0-111">The key for the resource.</span></span> <span data-ttu-id="915d0-112">Při vyhledání prostředků `targetID` se bude považovat za analogku s [direktivou x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) prostředku.</span><span class="sxs-lookup"><span data-stu-id="915d0-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="915d0-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="915d0-113">Remarks</span></span>  
 <span data-ttu-id="915d0-114">Jak je vidět výše, použití rozšíření značek {`ComponentResourceKey`} se nachází na dvou místech:</span><span class="sxs-lookup"><span data-stu-id="915d0-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
- <span data-ttu-id="915d0-115">Definice klíče v rámci slovníku prostředků motivu, jak poskytuje autor ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="915d0-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
- <span data-ttu-id="915d0-116">Přístup k prostředku motivu ze sestavení, když jste retemplating ovládací prvek, ale chcete použít hodnoty vlastností, které pocházejí z prostředků poskytovaných motivy ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="915d0-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="915d0-117">Pro odkazování na prostředky komponent, které pocházejí z motivů, se obecně doporučuje použít `{DynamicResource}` místo `{StaticResource}`.</span><span class="sxs-lookup"><span data-stu-id="915d0-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="915d0-118">To se zobrazuje v části použití.</span><span class="sxs-lookup"><span data-stu-id="915d0-118">This is shown in the usages.</span></span> <span data-ttu-id="915d0-119">`{DynamicResource}`se doporučuje, protože daný motiv může změnit uživatel.</span><span class="sxs-lookup"><span data-stu-id="915d0-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="915d0-120">Chcete-li, aby prostředek součásti, který nejlépe odpovídá záměru autora ovládacího prvku, podporoval motiv, měli byste povolit, aby byl odkaz na prostředek komponenty také dynamický.</span><span class="sxs-lookup"><span data-stu-id="915d0-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="915d0-121"><xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Identifikuje typ, který existuje v cílovém sestavení, kde je prostředek skutečně definován.</span><span class="sxs-lookup"><span data-stu-id="915d0-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="915d0-122">`ComponentResourceKey` Lze definovat a použít nezávisle na tom, kde <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> je definována, ale nakonec musí vyřešit typ prostřednictvím odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="915d0-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="915d0-123">Běžné použití pro <xref:System.Windows.ComponentResourceKey> je definování klíčů, které jsou pak zveřejněny jako členové třídy.</span><span class="sxs-lookup"><span data-stu-id="915d0-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="915d0-124">Pro toto použití použijte konstruktor <xref:System.Windows.ComponentResourceKey> třídy, nikoli rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="915d0-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="915d0-125">Další informace najdete v <xref:System.Windows.ComponentResourceKey>části nebo v části Definování a odkazování klíčů pro prostředky motivů v tématu [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="915d0-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="915d0-126">Pro vytváření klíčů a odkazujících se na prostředky s klíčem se běžně používá syntaxe atributu pro `ComponentResourceKey` rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="915d0-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="915d0-127">Uvedená syntaxe komprimace spoléhá na signaturu <xref:System.Windows.ComponentResourceKey.%23ctor%2A> konstruktoru a použití pozičního parametru rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="915d0-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="915d0-128">Pořadí, ve kterém jsou `targetTypeName` uvedeny `targetID` a jsou důležité.</span><span class="sxs-lookup"><span data-stu-id="915d0-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="915d0-129">Podrobná syntaxe se spoléhá na konstruktor <xref:System.Windows.ComponentResourceKey.%23ctor%2A> bez parametrů a pak nastaví <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> a <xref:System.Windows.ComponentResourceKey.ResourceId%2A> způsobem, který je podobný syntaxi true atributu v elementu Object.</span><span class="sxs-lookup"><span data-stu-id="915d0-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> parameterless constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="915d0-130">V podrobné syntaxi není pořadí, ve kterém jsou vlastnosti nastaveny, důležité.</span><span class="sxs-lookup"><span data-stu-id="915d0-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="915d0-131">Vztah a mechanismy těchto dvou alternativ (Compact a verbose) jsou podrobněji popsány v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="915d0-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="915d0-132">Technicky, hodnota pro `targetID` může být libovolný objekt, nemusí se jednat o řetězec.</span><span class="sxs-lookup"><span data-stu-id="915d0-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="915d0-133">Nejběžnějším využitím v subsystému WPF je však zarovnání `targetID` hodnoty pomocí formulářů, které jsou řetězce a kde jsou tyto řetězce platné v gramatice v kódu [XAML](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="915d0-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="915d0-134">`ComponentResourceKey`lze použít v syntaxi elementu Object.</span><span class="sxs-lookup"><span data-stu-id="915d0-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="915d0-135">V takovém případě je nutné zadat hodnotu vlastností <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> a <xref:System.Windows.ComponentResourceKey.ResourceId%2A> , aby bylo rozšíření správně inicializováno.</span><span class="sxs-lookup"><span data-stu-id="915d0-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="915d0-136">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] V implementaci čtecího modulu je zpracování tohoto rozšíření značek definováno <xref:System.Windows.ComponentResourceKey> třídou.</span><span class="sxs-lookup"><span data-stu-id="915d0-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="915d0-137">`ComponentResourceKey`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="915d0-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="915d0-138">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="915d0-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="915d0-139">Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že je nutné zpracovat atribut v rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="915d0-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="915d0-140">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="915d0-140">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915d0-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="915d0-141">See also</span></span>

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="915d0-142">Přehled řízeného vytváření</span><span class="sxs-lookup"><span data-stu-id="915d0-142">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
- [<span data-ttu-id="915d0-143">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="915d0-143">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="915d0-144">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="915d0-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
