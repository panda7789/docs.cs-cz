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
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

Určuje vlastnosti zdroje vazby <xref:System.Windows.Data.RelativeSource>, který se má použít v rámci [rozšíření značek vazby](binding-markup-extension.md), nebo při nastavení vlastnosti <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding> elementu vytvořeného v jazyce XAML.

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
|`modeEnumValue`|Jeden z následujících postupů:<br /><br /> – Řetězcový token `Self`; odpovídá <xref:System.Windows.Data.RelativeSource> vytvořenému s vlastností <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />– Řetězcový token `TemplatedParent`; odpovídá <xref:System.Windows.Data.RelativeSource> vytvořenému s vlastností <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />– Řetězcový token `PreviousData`; odpovídá <xref:System.Windows.Data.RelativeSource> vytvořenému s vlastností <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />– Viz níže pro informace o režimu `FindAncestor`.|
|`FindAncestor`|`FindAncestor`řetězcového tokenu. Pomocí tohoto tokenu přejdete do režimu, kdy `RelativeSource` určuje typ předchůdce a volitelně i úroveň předchůdce. To odpovídá <xref:System.Windows.Data.RelativeSource> vytvořenému s vlastností <xref:System.Windows.Data.RelativeSource.Mode%2A> nastavenou na <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|
|`typeName`|Vyžaduje se pro režim `FindAncestor`. Název typu, který vyplní vlastnost <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.|
|`intLevel`|Volitelné pro režim `FindAncestor`. Úroveň předchůdce (vyhodnocována ve směru nadřazeného uzlu v logickém stromu)|

## <a name="remarks"></a>Poznámky

`{RelativeSource TemplatedParent}` používání vazeb je klíčovou technikou, která řeší větší pojem oddělení uživatelského rozhraní ovládacího prvku a logiky ovládacího prvku. To umožňuje vytvořit vazbu z definice šablony na nadřazený objekt vytvořený pomocí šablony (instanci objektu vytvořenou za běhu, pro niž je šablona použita). V tomto případě je [rozšíření značek TemplateBinding](templatebinding-markup-extension.md) ve skutečnosti zkrácený pro následující výraz vazby: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. použití `TemplateBinding` nebo `{RelativeSource TemplatedParent}` se týkají pouze v jazyce XAML, který definuje šablonu. Další informace najdete v tématu [rozšíření značek TemplateBinding](templatebinding-markup-extension.md).

`{RelativeSource FindAncestor}` se převážně používá v šablonách ovládacích prvků nebo předvídatelných kompozicích uživatelského rozhraní, v případech, kdy je ovládací prvek vždy ve vizuálním stromu určitého typu předchůdce. Například položky ovládacího prvku položky mohou použít `FindAncestor` použití pro svázání s vlastnostmi svých položek nadřízený nadřazený prvek. Nebo elementy, které jsou součástí kompozice ovládacích prvků v šabloně, mohou použít `FindAncestor` vazby k nadřazeným prvkům ve stejné struktuře kompozice.

V syntaxi elementu Object pro `FindAncestor` režim zobrazený v oddílech Syntaxe XAML se druhá syntaxe elementu Object používá konkrétně pro `FindAncestor` režim. `FindAncestor` režim vyžaduje hodnotu <xref:System.Windows.Data.RelativeSource.AncestorType%2A>. Je nutné nastavit <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atribut pomocí odkazu [rozšíření značek x:Type](../../xaml-services/x-type-markup-extension.md) na typ předchůdce, který se má hledat. Hodnota <xref:System.Windows.Data.RelativeSource.AncestorType%2A> se používá v případě, že je požadavek na vazbu zpracován v době běhu.

V případě `FindAncestor`ho režimu může <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> volitelná vlastnost omezit jednoznačnosti vyhledávání předchůdce v případech, kdy je ve stromové struktuře elementu pravděpodobně více než jeden nadřazený prvek daného typu.

Další informace o tom, jak používat režim `FindAncestor`, najdete v tématu <xref:System.Windows.Data.RelativeSource>.

`{RelativeSource Self}` je užitečná v případech, kdy by jedna vlastnost instance měla záviset na hodnotě jiné vlastnosti stejné instance a žádný obecný vztah vlastnosti závislosti (například konverze) již mezi těmito dvěma vlastnostmi existuje. I když je pravděpodobné, že v objektu existují dvě vlastnosti, například hodnoty jsou doslova identické (a jsou identicky), můžete také použít parametr `Converter` na vazbu, která má `{RelativeSource Self}`a použít konvertor k převodu mezi zdrojem a cílem. druhy. Dalším scénářem `{RelativeSource Self}` je jako součást <xref:System.Windows.MultiDataTrigger>.

Například následující kód XAML definuje prvek <xref:System.Windows.Shapes.Rectangle> tak, že bez ohledu na to, jaká hodnota je zadána pro <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> je vždy čtvercový: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}` je užitečné buď v datových šablonách, nebo v případech, kdy vazby používají jako zdroj dat kolekci. Můžete použít `{RelativeSource PreviousData}` k zdůraznění vztahů mezi sousedními datovými položkami v kolekci. Související technikou je navázat <xref:System.Windows.Data.MultiBinding> mezi aktuálními a předchozími položkami ve zdroji dat a pomocí převaděče na této vazbě určit rozdíl mezi dvěma položkami a jejich vlastnostmi.

V následujícím příkladu první <xref:System.Windows.Controls.TextBlock> v šabloně Items zobrazuje aktuální číslo. Druhá vazba <xref:System.Windows.Controls.TextBlock> je <xref:System.Windows.Data.MultiBinding>, která má nominální hodnotu dvou <xref:System.Windows.Data.Binding> prvků: aktuální záznam a vazba, která záměrně používá předchozí datový záznam pomocí `{RelativeSource PreviousData}`. Pak převaděč na <xref:System.Windows.Data.MultiBinding> vypočítá rozdíl a vrátí ho do vazby.

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

Popis datové vazby jako koncept se tady nezabývá, najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).

V implementaci procesoru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.Data.RelativeSource>.

`RelativeSource` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v jazyce XAML používají ve své syntaxi atributu `{` a `}` znaky, což je konvence, pomocí níž procesor XAML rozpozná, že musí zpracovat atribut rozšíření značek. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.Binding>
- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled deklarací vazeb](../data/binding-declarations-overview.md)
- [x:Type – rozšíření značek](../../xaml-services/x-type-markup-extension.md)
