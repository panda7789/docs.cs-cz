---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 28f3aa500014b768bd07723511613a42df8689aa
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458771"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="301d5-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="301d5-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="301d5-103">Určuje vlastnosti zdroje vazby <xref:System.Windows.Data.RelativeSource>, který se má použít v rámci [rozšíření značek vazby](binding-markup-extension.md), nebo při nastavení vlastnosti <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding> elementu vytvořeného v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="301d5-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="301d5-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="301d5-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="301d5-105">Použití atributu XAML (vnořeného do rozšíření Binding)</span><span class="sxs-lookup"><span data-stu-id="301d5-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="301d5-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="301d5-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="301d5-107">-nebo-</span><span class="sxs-lookup"><span data-stu-id="301d5-107">-or-</span></span>

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

## <a name="xaml-values"></a><span data-ttu-id="301d5-108">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="301d5-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="301d5-109">Jeden z následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="301d5-109">One of the following:</span></span><br /><br /> <span data-ttu-id="301d5-110">– Řetězcový token `Self`; odpovídá <xref:System.Windows.Data.RelativeSource> vytvořenému s vlastností <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="301d5-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="301d5-111">– Řetězcový token `TemplatedParent`; odpovídá <xref:System.Windows.Data.RelativeSource> vytvořenému s vlastností <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="301d5-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="301d5-112">– Řetězcový token `PreviousData`; odpovídá <xref:System.Windows.Data.RelativeSource> vytvořenému s vlastností <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="301d5-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="301d5-113">– Viz níže pro informace o režimu `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="301d5-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="301d5-114">`FindAncestor`řetězcového tokenu.</span><span class="sxs-lookup"><span data-stu-id="301d5-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="301d5-115">Pomocí tohoto tokenu přejdete do režimu, kdy `RelativeSource` určuje typ předchůdce a volitelně i úroveň předchůdce.</span><span class="sxs-lookup"><span data-stu-id="301d5-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="301d5-116">To odpovídá <xref:System.Windows.Data.RelativeSource> vytvořenému s vlastností <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="301d5-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="301d5-117">Vyžaduje se pro režim `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="301d5-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="301d5-118">Název typu, který vyplní vlastnost <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="301d5-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="301d5-119">Volitelné pro režim `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="301d5-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="301d5-120">Úroveň předchůdce (vyhodnocována ve směru nadřazeného uzlu v logickém stromu)</span><span class="sxs-lookup"><span data-stu-id="301d5-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="301d5-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="301d5-121">Remarks</span></span>

<span data-ttu-id="301d5-122">`{RelativeSource TemplatedParent}` používání vazeb je klíčovou technikou, která řeší větší pojem oddělení uživatelského rozhraní ovládacího prvku a logiky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="301d5-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="301d5-123">To umožňuje vytvořit vazbu z definice šablony na nadřazený objekt vytvořený pomocí šablony (instanci objektu vytvořenou za běhu, pro niž je šablona použita).</span><span class="sxs-lookup"><span data-stu-id="301d5-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="301d5-124">V tomto případě je [rozšíření značek TemplateBinding](templatebinding-markup-extension.md) ve skutečnosti zkrácený pro následující výraz vazby: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="301d5-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="301d5-125">použití `TemplateBinding` nebo `{RelativeSource TemplatedParent}` se týkají pouze v jazyce XAML, který definuje šablonu.</span><span class="sxs-lookup"><span data-stu-id="301d5-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="301d5-126">Další informace najdete v tématu [rozšíření značek TemplateBinding](templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="301d5-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="301d5-127">`{RelativeSource FindAncestor}` se převážně používá v šablonách ovládacích prvků nebo předvídatelných kompozicích uživatelského rozhraní, v případech, kdy je ovládací prvek vždy ve vizuálním stromu určitého typu předchůdce.</span><span class="sxs-lookup"><span data-stu-id="301d5-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="301d5-128">Například položky ovládacího prvku položky mohou použít `FindAncestor` použití pro svázání s vlastnostmi svých položek nadřízený nadřazený prvek.</span><span class="sxs-lookup"><span data-stu-id="301d5-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="301d5-129">Nebo elementy, které jsou součástí kompozice ovládacích prvků v šabloně, mohou použít `FindAncestor` vazby k nadřazeným prvkům ve stejné struktuře kompozice.</span><span class="sxs-lookup"><span data-stu-id="301d5-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="301d5-130">V syntaxi elementu Object pro `FindAncestor` režim zobrazený v oddílech Syntaxe XAML se druhá syntaxe elementu Object používá konkrétně pro `FindAncestor` režim.</span><span class="sxs-lookup"><span data-stu-id="301d5-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="301d5-131">`FindAncestor` režim vyžaduje hodnotu <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="301d5-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="301d5-132">Je nutné nastavit <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atribut pomocí odkazu [rozšíření značek x:Type](../../xaml-services/x-type-markup-extension.md) na typ předchůdce, který se má hledat.</span><span class="sxs-lookup"><span data-stu-id="301d5-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="301d5-133">Hodnota <xref:System.Windows.Data.RelativeSource.AncestorType%2A> se používá v případě, že je požadavek na vazbu zpracován v době běhu.</span><span class="sxs-lookup"><span data-stu-id="301d5-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="301d5-134">V případě `FindAncestor`ho režimu může <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> volitelná vlastnost omezit jednoznačnosti vyhledávání předchůdce v případech, kdy je ve stromové struktuře elementu pravděpodobně více než jeden nadřazený prvek daného typu.</span><span class="sxs-lookup"><span data-stu-id="301d5-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="301d5-135">Další informace o tom, jak používat režim `FindAncestor`, najdete v tématu <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="301d5-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="301d5-136">`{RelativeSource Self}` je užitečná v případech, kdy by jedna vlastnost instance měla záviset na hodnotě jiné vlastnosti stejné instance a žádný obecný vztah vlastnosti závislosti (například konverze) již mezi těmito dvěma vlastnostmi existuje.</span><span class="sxs-lookup"><span data-stu-id="301d5-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="301d5-137">I když je pravděpodobné, že v objektu existují dvě vlastnosti, například hodnoty jsou doslova identické (a jsou identicky), můžete také použít parametr `Converter` na vazbu, která má `{RelativeSource Self}`a použít konvertor k převodu mezi zdrojem a cílem. druhy.</span><span class="sxs-lookup"><span data-stu-id="301d5-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="301d5-138">Dalším scénářem `{RelativeSource Self}` je jako součást <xref:System.Windows.MultiDataTrigger>.</span><span class="sxs-lookup"><span data-stu-id="301d5-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="301d5-139">Například následující kód XAML definuje prvek <xref:System.Windows.Shapes.Rectangle> tak, že bez ohledu na to, jaká hodnota je zadána pro <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> je vždy čtvercový: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="301d5-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="301d5-140">`{RelativeSource PreviousData}` je užitečné buď v datových šablonách, nebo v případech, kdy vazby používají jako zdroj dat kolekci.</span><span class="sxs-lookup"><span data-stu-id="301d5-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="301d5-141">Můžete použít `{RelativeSource PreviousData}` k zdůraznění vztahů mezi sousedními datovými položkami v kolekci.</span><span class="sxs-lookup"><span data-stu-id="301d5-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="301d5-142">Související technikou je navázat <xref:System.Windows.Data.MultiBinding> mezi aktuálními a předchozími položkami ve zdroji dat a pomocí převaděče na této vazbě určit rozdíl mezi dvěma položkami a jejich vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="301d5-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="301d5-143">V následujícím příkladu první <xref:System.Windows.Controls.TextBlock> v šabloně Items zobrazuje aktuální číslo.</span><span class="sxs-lookup"><span data-stu-id="301d5-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="301d5-144">Druhá vazba <xref:System.Windows.Controls.TextBlock> je <xref:System.Windows.Data.MultiBinding>, která má nominální hodnotu dvou <xref:System.Windows.Data.Binding> prvků: aktuální záznam a vazba, která záměrně používá předchozí datový záznam pomocí `{RelativeSource PreviousData}`.</span><span class="sxs-lookup"><span data-stu-id="301d5-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="301d5-145">Pak převaděč na <xref:System.Windows.Data.MultiBinding> vypočítá rozdíl a vrátí ho do vazby.</span><span class="sxs-lookup"><span data-stu-id="301d5-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

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

<span data-ttu-id="301d5-146">Popis datové vazby jako koncept se tady nezabývá, najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="301d5-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="301d5-147">V implementaci procesoru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="301d5-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="301d5-148">`RelativeSource` je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="301d5-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="301d5-149">Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="301d5-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="301d5-150">Všechna rozšíření značek v jazyce XAML používají ve své syntaxi atributu `{` a `}` znaky, což je konvence, pomocí níž procesor XAML rozpozná, že musí zpracovat atribut rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="301d5-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="301d5-151">Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="301d5-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="301d5-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="301d5-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="301d5-153">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="301d5-153">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="301d5-154">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="301d5-154">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="301d5-155">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="301d5-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="301d5-156">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="301d5-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="301d5-157">Přehled deklarací vazeb</span><span class="sxs-lookup"><span data-stu-id="301d5-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="301d5-158">x:Type – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="301d5-158">x:Type Markup Extension</span></span>](../../xaml-services/x-type-markup-extension.md)
