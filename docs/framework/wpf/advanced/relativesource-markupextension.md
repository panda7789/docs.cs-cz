---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 6301299da966ade9b5cc7ccd105c8269a486744e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646229"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="81b4d-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="81b4d-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="81b4d-103">Určuje vlastnosti <xref:System.Windows.Data.RelativeSource> zdroje vazby, které mají být použity v <xref:System.Windows.Data.Binding.RelativeSource%2A> rámci rozšíření <xref:System.Windows.Data.Binding> [značky vazby](binding-markup-extension.md)nebo při nastavování vlastnosti prvku vytvořeného v XAML.</span><span class="sxs-lookup"><span data-stu-id="81b4d-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="81b4d-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="81b4d-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="81b4d-105">Použití atributu XAML (vnořeného do rozšíření Binding)</span><span class="sxs-lookup"><span data-stu-id="81b4d-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="81b4d-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="81b4d-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="81b4d-107">-nebo-</span><span class="sxs-lookup"><span data-stu-id="81b4d-107">-or-</span></span>

```xml
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

## <a name="xaml-values"></a><span data-ttu-id="81b4d-108">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="81b4d-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="81b4d-109">Jeden z následujících produktů:</span><span class="sxs-lookup"><span data-stu-id="81b4d-109">One of the following:</span></span><br /><br /> <span data-ttu-id="81b4d-110">- Token `Self`řetězce ; odpovídá tak, <xref:System.Windows.Data.RelativeSource> jak bylo <xref:System.Windows.Data.RelativeSource.Mode%2A> vytvořeno <xref:System.Windows.Data.RelativeSourceMode.Self>s vlastností nastavenou na .</span><span class="sxs-lookup"><span data-stu-id="81b4d-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="81b4d-111">- Token `TemplatedParent`řetězce ; odpovídá tak, <xref:System.Windows.Data.RelativeSource> jak bylo <xref:System.Windows.Data.RelativeSource.Mode%2A> vytvořeno <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>s vlastností nastavenou na .</span><span class="sxs-lookup"><span data-stu-id="81b4d-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="81b4d-112">- Token `PreviousData`řetězce ; odpovídá tak, <xref:System.Windows.Data.RelativeSource> jak bylo <xref:System.Windows.Data.RelativeSource.Mode%2A> vytvořeno <xref:System.Windows.Data.RelativeSourceMode.PreviousData>s vlastností nastavenou na .</span><span class="sxs-lookup"><span data-stu-id="81b4d-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="81b4d-113">- Informace o `FindAncestor` režimu naleznete níže.</span><span class="sxs-lookup"><span data-stu-id="81b4d-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="81b4d-114">Token `FindAncestor`řetězce .</span><span class="sxs-lookup"><span data-stu-id="81b4d-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="81b4d-115">Pomocí tohoto tokenu přejde `RelativeSource` režim, ve kterém určuje typ předchůdce a volitelně úroveň předchůdce.</span><span class="sxs-lookup"><span data-stu-id="81b4d-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="81b4d-116">To odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořené s <xref:System.Windows.Data.RelativeSource.Mode%2A> jeho <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>vlastnost nastavena na .</span><span class="sxs-lookup"><span data-stu-id="81b4d-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="81b4d-117">Vyžadováno `FindAncestor` pro režim.</span><span class="sxs-lookup"><span data-stu-id="81b4d-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="81b4d-118">Název typu, který vyplní <xref:System.Windows.Data.RelativeSource.AncestorType%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81b4d-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="81b4d-119">Volitelné `FindAncestor` pro režim.</span><span class="sxs-lookup"><span data-stu-id="81b4d-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="81b4d-120">Úroveň předchůdce (vyhodnocována ve směru nadřazeného uzlu v logickém stromu)</span><span class="sxs-lookup"><span data-stu-id="81b4d-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="81b4d-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81b4d-121">Remarks</span></span>

<span data-ttu-id="81b4d-122">`{RelativeSource TemplatedParent}`použití vazby jsou klíčovou technikou, která řeší větší koncept oddělení hlavního použití ovládacího prvku a logiku ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="81b4d-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="81b4d-123">To umožňuje vytvořit vazbu z definice šablony na nadřazený objekt vytvořený pomocí šablony (instanci objektu vytvořenou za běhu, pro niž je šablona použita).</span><span class="sxs-lookup"><span data-stu-id="81b4d-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="81b4d-124">V tomto případě [TemplateBinding Markup Extension](templatebinding-markup-extension.md) je ve skutečnosti zkratka `{Binding RelativeSource={RelativeSource TemplatedParent}}`pro následující výraz vazby: .</span><span class="sxs-lookup"><span data-stu-id="81b4d-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="81b4d-125">`TemplateBinding`nebo `{RelativeSource TemplatedParent}` použití jsou relevantní pouze v rámci XAML, který definuje šablonu.</span><span class="sxs-lookup"><span data-stu-id="81b4d-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="81b4d-126">Další informace naleznete v [tématu TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="81b4d-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="81b4d-127">`{RelativeSource FindAncestor}`používá se hlavně v šablonách ovládacího prvku nebo předvídatelné samostatné kompozice uživatelského prvku, pro případy, kdy je vždy očekáváno, že ovládací prvek bude ve vizuálním stromu určitého typu předchůdce.</span><span class="sxs-lookup"><span data-stu-id="81b4d-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="81b4d-128">Například položky ovládacího prvku `FindAncestor` položky může použít použití svázat s vlastnostmi jejich položky řídit nadřazený předchůdce.</span><span class="sxs-lookup"><span data-stu-id="81b4d-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="81b4d-129">Nebo prvky, které jsou součástí složení `FindAncestor` ovládacího prvku v šabloně můžete použít vazby na nadřazené prvky ve stejné struktuře složení.</span><span class="sxs-lookup"><span data-stu-id="81b4d-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="81b4d-130">V syntaxi prvku `FindAncestor` objektu pro režim zobrazený v částech Syntaxe XAML se syntaxe druhého prvku objektu používá speciálně pro `FindAncestor` režim.</span><span class="sxs-lookup"><span data-stu-id="81b4d-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="81b4d-131">`FindAncestor`režim vyžaduje <xref:System.Windows.Data.RelativeSource.AncestorType%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="81b4d-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="81b4d-132">Je nutné <xref:System.Windows.Data.RelativeSource.AncestorType%2A> nastavit jako atribut pomocí [x:Typ Značkovací rozšíření](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) odkaz na typ předchůdce hledat.</span><span class="sxs-lookup"><span data-stu-id="81b4d-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="81b4d-133">Hodnota <xref:System.Windows.Data.RelativeSource.AncestorType%2A> se používá při zpracování požadavku na vazbu za běhu.</span><span class="sxs-lookup"><span data-stu-id="81b4d-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="81b4d-134">Pro `FindAncestor` režim může <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> volitelná vlastnost pomoci rozptýlit vyhledávání předchůdce v případech, kdy ve stromu prvků existuje více než jeden předchůdce tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="81b4d-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="81b4d-135">Další informace o použití `FindAncestor` režimu <xref:System.Windows.Data.RelativeSource>naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="81b4d-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="81b4d-136">`{RelativeSource Self}`je užitečné pro scénáře, kde jedna vlastnost instance by měla záviset na hodnotě jiné vlastnosti stejné instance a žádný obecný vztah vlastnosti závislosti (například nátlak) již existuje mezi těmito dvěma vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="81b4d-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="81b4d-137">I když je vzácné, že existují dvě vlastnosti na objekt tak, že hodnoty jsou doslova `Converter` identické (a `{RelativeSource Self}`jsou identicky zadány), můžete také použít parametr vazby, která má , a použít převaděč převést mezi zdrojové a cílové typy.</span><span class="sxs-lookup"><span data-stu-id="81b4d-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="81b4d-138">Další scénář `{RelativeSource Self}` pro je <xref:System.Windows.MultiDataTrigger>jako součást .</span><span class="sxs-lookup"><span data-stu-id="81b4d-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="81b4d-139">Například následující XAML definuje <xref:System.Windows.Shapes.Rectangle> prvek tak, že bez ohledu <xref:System.Windows.FrameworkElement.Width%2A>na <xref:System.Windows.Shapes.Rectangle> to, jaká hodnota je zadána , je vždy čtverec:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="81b4d-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="81b4d-140">`{RelativeSource PreviousData}`je užitečné buď v šablonách dat nebo v případech, kdy vazby používají kolekci jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="81b4d-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="81b4d-141">Můžete zvýraznit `{RelativeSource PreviousData}` vztahy mezi sousedními datovými položkami v kolekci.</span><span class="sxs-lookup"><span data-stu-id="81b4d-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="81b4d-142">Související technika je vytvořit <xref:System.Windows.Data.MultiBinding> mezi aktuální a předchozí položky ve zdroji dat a použít převaděč na tuto vazbu k určení rozdílu mezi dvě položky a jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81b4d-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="81b4d-143">V následujícím příkladu <xref:System.Windows.Controls.TextBlock> se zobrazí první v šabloně položek aktuální číslo.</span><span class="sxs-lookup"><span data-stu-id="81b4d-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="81b4d-144">Druhá <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Data.MultiBinding> vazba je, že <xref:System.Windows.Data.Binding> nominálně má dva složky: aktuální záznam a vazba, která záměrně používá předchozí záznam dat pomocí `{RelativeSource PreviousData}`.</span><span class="sxs-lookup"><span data-stu-id="81b4d-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="81b4d-145">Poté převaděč <xref:System.Windows.Data.MultiBinding> na vypočítá rozdíl a vrátí jej do vazby.</span><span class="sxs-lookup"><span data-stu-id="81b4d-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

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

<span data-ttu-id="81b4d-146">Popis datové vazby jako koncept zde není popsán, viz [Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="81b4d-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="81b4d-147">V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementaci procesoru XAML zpracování pro toto rozšíření <xref:System.Windows.Data.RelativeSource> značky je definováno třídou.</span><span class="sxs-lookup"><span data-stu-id="81b4d-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="81b4d-148">`RelativeSource`je rozšíření značky.</span><span class="sxs-lookup"><span data-stu-id="81b4d-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="81b4d-149">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81b4d-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="81b4d-150">Všechna rozšíření značek v XAML `{` `}` používají znaky a v syntaxi jejich atributu, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí atribut zpracovat.</span><span class="sxs-lookup"><span data-stu-id="81b4d-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="81b4d-151">Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="81b4d-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81b4d-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="81b4d-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="81b4d-153">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="81b4d-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="81b4d-154">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="81b4d-154">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="81b4d-155">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="81b4d-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="81b4d-156">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="81b4d-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="81b4d-157">Přehled deklarací připojení</span><span class="sxs-lookup"><span data-stu-id="81b4d-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="81b4d-158">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="81b4d-158">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
