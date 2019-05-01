---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: a6a7d615a3a54fbc75bb86b295fdf80433a31dc5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053493"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

Určuje vlastnosti <xref:System.Windows.Data.RelativeSource> zdroj vazby pro použití v rámci [Binding Markup Extension](binding-markup-extension.md), nebo při nastavení <xref:System.Windows.Data.Binding.RelativeSource%2A> vlastnost <xref:System.Windows.Data.Binding> prvku v XAML.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>Použití atributu XAML (vnořeného do rozšíření Binding)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

-nebo-

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

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`modeEnumValue`|Jeden z následujících postupů:<br /><br /> -Řetězec s tokenem `Self`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />-Řetězec s tokenem `TemplatedParent`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />-Řetězec s tokenem `PreviousData`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />-Níže najdete informace o `FindAncestor` režimu.|
|`FindAncestor`|Řetězec s tokenem `FindAncestor`. Pomocí tohoto tokenu přejde do režimu, kterým `RelativeSource` Určuje typ předchůdce a volitelně také úroveň předchůdce. To odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|
|`typeName`|Vyžaduje se pro `FindAncestor` režimu. Název typu, který vyplní <xref:System.Windows.Data.RelativeSource.AncestorType%2A> vlastnost.|
|`intLevel`|Volitelné pro `FindAncestor` režimu. Úroveň předchůdce (vyhodnocována ve směru nadřazeného uzlu v logickém stromu)|

## <a name="remarks"></a>Poznámky

`{RelativeSource TemplatedParent}` vazba je klíčovou techniku, která řeší rozsáhlejší koncept oddělení uživatelského ovládacího prvku rozhraní a logiky ovládacího prvku. To umožňuje vytvořit vazbu z definice šablony na nadřazený objekt vytvořený pomocí šablony (instanci objektu vytvořenou za běhu, pro niž je šablona použita). Pro tento případ [– rozšíření značek TemplateBinding](templatebinding-markup-extension.md) vlastně zjednodušením následujícího výrazu vazby: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding` nebo `{RelativeSource TemplatedParent}` je relevantní pouze v XAML, který definuje šablonu. Další informace najdete v tématu [TemplateBinding – rozšíření značek](templatebinding-markup-extension.md)

`{RelativeSource FindAncestor}` používá se hlavně v šablonách ovládacích prvků nebo předvídatelný kompozici uživatelského rozhraní, pro případy, ve kterém ovládací prvek se vždy očekává ve vizuálním stromu určitého typu předchůdce. Například může použít položky ovládacího prvku položek `FindAncestor` předchůdce nadřazeného ovládacího vytvořit vazby na vlastnosti prvku položek. Nebo můžete použít prvky, které jsou součástí kompozice ovládacích prvků v šabloně `FindAncestor` vazby na nadřazené elementy ve stejné struktuře kompozice.

V syntaxi elementu objektu pro `FindAncestor` uvedené v oddílech syntaxe XAML, slouží druhá syntaxe elementu objektu speciálně pro režim `FindAncestor` režimu. `FindAncestor` režim vyžaduje <xref:System.Windows.Data.RelativeSource.AncestorType%2A> hodnotu. Je nutné nastavit <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atribut s použitím [x: Type – rozšíření značek](../../xaml-services/x-type-markup-extension.md) odkaz na typ hledaného předchůdce. <xref:System.Windows.Data.RelativeSource.AncestorType%2A> Hodnota se používá, když požadavek na vytvoření vazby zpracován za běhu.

Pro `FindAncestor` režim, vlastnost nepovinný <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> může pomoci rozlišit vyhledávání v případech, kde je pravděpodobně více než jeden předchůdce tohoto typu existující ve stromu elementů.

Další informace o tom, jak používat `FindAncestor` režimu, najdete v článku <xref:System.Windows.Data.RelativeSource>.

`{RelativeSource Self}` je užitečné pro scénáře, kde jedna vlastnost instance měla záviset na hodnotě jiné vlastnosti stejné instance a žádný obecný vztah závislosti vlastností (například převod) již existuje mezi těmito dvěma vlastnostmi. I když je vzácné, že existují dvě vlastnosti v objektu tak, aby hodnoty jsou vyhledána stejné (a jsou stejně jako typu), můžete také použít `Converter` parametr, který má vazbu `{RelativeSource Self}`a pomocí tohoto převaděče převádět zdroje a cílové typy. Další možností pro `{RelativeSource Self}` je jako součást <xref:System.Windows.MultiDataTrigger>.

Například následující XAML definuje <xref:System.Windows.Shapes.Rectangle> element takový, který bez ohledu na to, jaká hodnota je zadána pro <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> je vždy čtverec: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}` je užitečná v šablonách dat nebo v případech, kdy vazby používají kolekce jako zdroj dat. Můžete použít `{RelativeSource PreviousData}` můžete zdůraznit vztahy mezi sousedními datovými položkami v kolekci. Související technikou je vytvořit <xref:System.Windows.Data.MultiBinding> mezi aktuální a předchozí položky ve zdroji dat a použití převaděče pro tuto vazbu určit rozdíl mezi těmito dvěma položkami a jejich vlastnosti.

V následujícím příkladu první <xref:System.Windows.Controls.TextBlock> v položkách šablona zobrazuje aktuální počet. Druhá <xref:System.Windows.Controls.TextBlock> vazba je <xref:System.Windows.Data.MultiBinding> , která má formálně dvě součásti <xref:System.Windows.Data.Binding> složek: aktuální záznam a vazbu, která záměrně používá předchozí záznam dat s využitím `{RelativeSource PreviousData}`. Potom převaděč pro <xref:System.Windows.Data.MultiBinding> vypočítá rozdíl a vrátí ji do vazby.

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

Popis vytváření datových vazeb koncept není součástí tohoto, naleznete v tématu [Data Binding Overview](../data/data-binding-overview.md).

V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementaci procesoru XAML je zpracování tohoto rozšíření značek je určené <xref:System.Windows.Data.RelativeSource> třídy.

`RelativeSource` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek XAML používá `{` a `}` znaků v syntaxi atributu, což je konvence, podle kterého na procesor XAML rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.Binding>
- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Přehled deklarací vazeb](../data/binding-declarations-overview.md)
- [x:Type – rozšíření značek](../../xaml-services/x-type-markup-extension.md)
