---
title: RelativeSource MarkupExtension
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ea5d269c3d455a4fbe3a34dca4335e0d8999d80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="4aa9c-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="4aa9c-102">RelativeSource MarkupExtension</span></span>
<span data-ttu-id="4aa9c-103">Určuje vlastnosti <xref:System.Windows.Data.RelativeSource> vazby zdroj, který se má použít v rámci [vazba – rozšíření značek](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), nebo při nastavení <xref:System.Windows.Data.Binding.RelativeSource%2A> vlastnost <xref:System.Windows.Data.Binding> element navázat v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4aa9c-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="4aa9c-104">XAML Attribute Usage</span></span>  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="4aa9c-105">Použití atributu XAML (vnořeného do rozšíření Binding)</span><span class="sxs-lookup"><span data-stu-id="4aa9c-105">XAML Attribute Usage (nested within Binding extension)</span></span>  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="4aa9c-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="4aa9c-106">XAML Object Element Usage</span></span>  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4aa9c-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="4aa9c-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`modeEnumValue`|<span data-ttu-id="4aa9c-108">Jeden z následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="4aa9c-108">One of the following:</span></span><br /><br /> <span data-ttu-id="4aa9c-109">-Token řetězec `Self`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-109">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="4aa9c-110">-Token řetězec `TemplatedParent`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-110">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="4aa9c-111">-Token řetězec `PreviousData`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-111">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="4aa9c-112">-Níže najdete informace v `FindAncestor` režimu.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-112">-   See below for information on `FindAncestor` mode.</span></span>|  
|`FindAncestor`|<span data-ttu-id="4aa9c-113">Token řetězec `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-113">The string token `FindAncestor`.</span></span> <span data-ttu-id="4aa9c-114">Pomocí tohoto tokenu přejde do režimu které `RelativeSource` Určuje typ nadřazené a volitelně nadřazené úrovni.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-114">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="4aa9c-115">To odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-115">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|  
|`typeName`|<span data-ttu-id="4aa9c-116">Vyžaduje se pro `FindAncestor` režimu.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-116">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="4aa9c-117">Název typu, který vyplní celé <xref:System.Windows.Data.RelativeSource.AncestorType%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-117">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|  
|`intLevel`|<span data-ttu-id="4aa9c-118">Volitelné pro `FindAncestor` režimu.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-118">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="4aa9c-119">Úroveň předchůdce (vyhodnocována ve směru nadřazeného uzlu v logickém stromu)</span><span class="sxs-lookup"><span data-stu-id="4aa9c-119">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aa9c-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4aa9c-120">Remarks</span></span>  
 <span data-ttu-id="4aa9c-121">`{RelativeSource TemplatedParent}`použití vazby jsou klíče technik, které řeší větší koncept oddělení ovládacího prvku uživatelského rozhraní a logiku ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-121">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="4aa9c-122">To umožňuje vytvořit vazbu z definice šablony na nadřazený objekt vytvořený pomocí šablony (instanci objektu vytvořenou za běhu, pro niž je šablona použita).</span><span class="sxs-lookup"><span data-stu-id="4aa9c-122">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="4aa9c-123">Pro tento případ [TemplateBinding – rozšíření značek](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) ve skutečnosti je sdružená vlastnost pro následující výraz vazby: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-123">For this case, the [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="4aa9c-124">`TemplateBinding`nebo `{RelativeSource TemplatedParent}` použití jsou obě pouze relevantní v jazyce XAML, který definuje šablonu.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-124">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="4aa9c-125">Další informace najdete v tématu [TemplateBinding – rozšíření značek](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="4aa9c-125">For more information, see [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span></span>  
  
 <span data-ttu-id="4aa9c-126">`{RelativeSource FindAncestor}`používá se především ve řízení šablony nebo předvídatelný nezávislý složení uživatelského rozhraní pro případy, kde je vždy očekávána ovládacího prvku ve vizuálním stromu určitého nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-126">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="4aa9c-127">Například může použít položky ovládacího prvku položky `FindAncestor` použití k vytvoření vazby vlastnosti jejich položek řízení nadřazené nadřazený.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-127">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="4aa9c-128">Nebo můžete použít prvky, které jsou součástí sestavení ovládacího prvku v šabloně `FindAncestor` vazby na nadřazené elementy v této stejné struktury složení.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-128">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>  
  
 <span data-ttu-id="4aa9c-129">V elementu syntaxe objekt `FindAncestor` režimu uvedené v částech syntaxe jazyka XAML, druhý element syntaxe objekt je používán speciálně pro `FindAncestor` režimu.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-129">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="4aa9c-130">`FindAncestor`režim vyžaduje, aby <xref:System.Windows.Data.RelativeSource.AncestorType%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-130">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="4aa9c-131">Je nutné nastavit <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako použití atributu [x: Type – rozšíření značek](../../../../docs/framework/xaml-services/x-type-markup-extension.md) odkaz na typ nadřazené má být vyhledán.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-131">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../../docs/framework/xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="4aa9c-132"><xref:System.Windows.Data.RelativeSource.AncestorType%2A> Hodnota se používá při zpracování požadavku vazba za běhu.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-132">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>  
  
 <span data-ttu-id="4aa9c-133">Pro `FindAncestor` režim, vlastnost volitelné <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> může pomoci odstranit nejednoznačnost předchůdce vyhledávání v případech, kde může být více než jeden předchůdce tohoto typu existující ve stromové struktuře elementu.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-133">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>  
  
 <span data-ttu-id="4aa9c-134">Další informace o tom, jak používat `FindAncestor` režimu, najdete v části <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-134">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>  
  
 <span data-ttu-id="4aa9c-135">`{RelativeSource Self}`je užitečné pro scénáře, kde jednu vlastnost instance by měl záviset na hodnotu jiné vlastnosti na stejnou instanci a neexistuje žádný vztah vlastnost obecné závislosti (například převod) již existuje mezi tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-135">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="4aa9c-136">I když je taková situace vzácná, že existují dvě vlastnosti objektu tak, aby hodnoty oznámena identické (a jsou stejně jako typu), můžete taky použít `Converter` parametru vazby, která má `{RelativeSource Self}`a použijte převaděč pro převod mezi zdrojem a typy cíle.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-136">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="4aa9c-137">Jiné scénáře `{RelativeSource Self}` je jako součást <xref:System.Windows.MultiDataTrigger>.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-137">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>  
  
 <span data-ttu-id="4aa9c-138">Například následující XAML definuje <xref:System.Windows.Shapes.Rectangle> element takové bez ohledu na to, jaká hodnota zadaná pro <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> je vždy čtverce:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="4aa9c-138">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>  
  
 <span data-ttu-id="4aa9c-139">`{RelativeSource PreviousData}`je užitečná v šablonách dat, nebo v případech, kde jsou vazby pomocí kolekce jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-139">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="4aa9c-140">Můžete použít `{RelativeSource PreviousData}` zvýrazněte vztahy mezi přiléhající datových položek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-140">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="4aa9c-141">Související technika je k vytvoření <xref:System.Windows.Data.MultiBinding> mezi aktuální a předchozí položky zdroj dat a použít převaděč na této vazby k určení rozdílu mezi dvě položky a jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-141">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>  
  
 <span data-ttu-id="4aa9c-142">V následujícím příkladu první <xref:System.Windows.Controls.TextBlock> v položkách šablona zobrazuje aktuální číslo.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-142">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="4aa9c-143">Druhý <xref:System.Windows.Controls.TextBlock> vazba je <xref:System.Windows.Data.MultiBinding> , jmenovitě má dva <xref:System.Windows.Data.Binding> consistuents: záznam na aktuální záznam a vazbu, která používá úmyslně předchozího záznamu dat pomocí `{RelativeSource PreviousData}`.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-143">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> consistuents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="4aa9c-144">Potom převaděč na <xref:System.Windows.Data.MultiBinding> vypočítá rozdíl a vrátí ji do vazby.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-144">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>  
  
```xml  
<ListBox Name="fibolist">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding}"/>  
            <TextBlock>, difference = </TextBlock>  
                <TextBlock>  
                    <TextBlock.Text>  
                        <MultiBinding Converter="{StaticResource DiffConverter}">  
                            <Binding/>  
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>  
                        </MultiBinding>  
                    </TextBlock.Text>  
                </TextBlock>  
            </StackPanel>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
```  
  
 <span data-ttu-id="4aa9c-145">Datová vazba popisující, jak koncept neplatí zde najdete v části [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4aa9c-145">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="4aa9c-146">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace XAML procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.Data.RelativeSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-146">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>  
  
 <span data-ttu-id="4aa9c-147">`RelativeSource`je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-147">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="4aa9c-148">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-148">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="4aa9c-149">Všechna rozšíření značek v XAML použití `{` a `}` znaků v jejich syntaxi atributů, což je konvence, podle kterého XAML procesor rozpozná, že rozšíření značek musí zpracovat atribut.</span><span class="sxs-lookup"><span data-stu-id="4aa9c-149">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="4aa9c-150">Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="4aa9c-150">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa9c-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="4aa9c-151">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="4aa9c-152">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="4aa9c-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="4aa9c-153">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="4aa9c-153">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="4aa9c-154">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="4aa9c-154">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="4aa9c-155">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="4aa9c-155">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="4aa9c-156">Přehled deklarací vazeb</span><span class="sxs-lookup"><span data-stu-id="4aa9c-156">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="4aa9c-157">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="4aa9c-157">x:Type Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
