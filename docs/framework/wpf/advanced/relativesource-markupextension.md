---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 47117d684a981f31e22cf513fc78e1e2dda73f8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141266"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

Určuje vlastnosti zdroje <xref:System.Windows.Data.RelativeSource> vazby, které mají být použity v [rozšíření značek vazby](binding-markup-extension.md), nebo při nastavení <xref:System.Windows.Data.Binding.RelativeSource%2A> vlastnosti <xref:System.Windows.Data.Binding> prvku vytvořeného v jazyce XAML.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>Použití atributu XAML (vnořeného do rozšíření Binding)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
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
|`modeEnumValue`|Jeden z následujících produktů:<br /><br /> – Řetězcový token `Self`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořený s <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastností nastavenou na. <xref:System.Windows.Data.RelativeSourceMode.Self><br />– Řetězcový token `TemplatedParent`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořený s <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastností nastavenou na. <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent><br />– Řetězcový token `PreviousData`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořený s <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastností nastavenou na. <xref:System.Windows.Data.RelativeSourceMode.PreviousData><br />– Viz níže pro informace o `FindAncestor` režimu.|
|`FindAncestor`|Řetězcový token `FindAncestor`. Pomocí tohoto tokenu přejdete do režimu `RelativeSource` , který určuje typ předchůdce a volitelně i úroveň předchůdce. To odpovídá typu <xref:System.Windows.Data.RelativeSource> , který byl vytvořen s <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastností nastavenou na <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|
|`typeName`|Vyžaduje se `FindAncestor` pro režim. Název typu, který vyplní <xref:System.Windows.Data.RelativeSource.AncestorType%2A> vlastnost.|
|`intLevel`|Volitelné pro `FindAncestor` režim. Úroveň předchůdce (vyhodnocována ve směru nadřazeného uzlu v logickém stromu)|

## <a name="remarks"></a>Poznámky

`{RelativeSource TemplatedParent}`použití vazby představují klíčovou techniku, která řeší větší pojem oddělení uživatelského rozhraní ovládacího prvku a logiky ovládacího prvku. To umožňuje vytvořit vazbu z definice šablony na nadřazený objekt vytvořený pomocí šablony (instanci objektu vytvořenou za běhu, pro niž je šablona použita). V tomto případě je [rozšíření značek TemplateBinding](templatebinding-markup-extension.md) ve skutečnosti zkrácený pro následující výraz vazby: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding`nebo `{RelativeSource TemplatedParent}` použití jsou relevantní pouze v rámci jazyka XAML, který definuje šablonu. Další informace najdete v tématu [rozšíření značek TemplateBinding](templatebinding-markup-extension.md).

`{RelativeSource FindAncestor}`se primárně používá v šablonách ovládacích prvků nebo předvídatelných sestavách uživatelského rozhraní, v případech, kdy se ovládací prvek vždy očekává ve vizuálním stromu určitého typu předchůdce. Například položky ovládacího prvku položky mohou použít `FindAncestor` použití k vytvoření vazby na vlastnosti svých položek nadřízený nadřazený prvek. Nebo elementy, které jsou součástí kompozice ovládacích prvků v šabloně, mohou `FindAncestor` použít vazby na nadřazené prvky ve stejné struktuře kompozice.

V syntaxi elementu objektu pro `FindAncestor` režim zobrazený v sekcích Syntaxe XAML se druhá syntaxe elementu Object používá konkrétně pro `FindAncestor` režim. `FindAncestor`režim vyžaduje <xref:System.Windows.Data.RelativeSource.AncestorType%2A> hodnotu. Musíte nastavit <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atribut pomocí odkazu [rozšíření značek x:Type](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) na typ předchůdce, který se má hledat. <xref:System.Windows.Data.RelativeSource.AncestorType%2A> Hodnota se používá v případě, že je požadavek na vazbu zpracován v době běhu.

V `FindAncestor` případě režimu volitelná vlastnost <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> může podobu nejednoznačnosti vyhledávání předchůdce v případech, kdy je ve stromové struktuře elementu možná více než jeden nadřazený prvek daného typu.

Další informace o použití `FindAncestor` režimu naleznete v tématu. <xref:System.Windows.Data.RelativeSource>

`{RelativeSource Self}`je vhodný pro scénáře, kdy by jedna vlastnost instance měla záviset na hodnotě jiné vlastnosti stejné instance a žádný obecný vztah vlastnosti závislosti (jako je například konverze) již mezi těmito dvěma vlastnostmi existuje. I když je pravděpodobné, že v objektu existují dvě vlastnosti, například hodnoty jsou doslova identické (a jsou identicky), můžete také použít `Converter` parametr na vazbu, která má `{RelativeSource Self}`, a použít konvertor k převodu mezi zdrojovým a cílovým typem. Další situací pro `{RelativeSource Self}` je jako součást <xref:System.Windows.MultiDataTrigger>.

Například následující kód XAML definuje <xref:System.Windows.Shapes.Rectangle> prvek tak, aby bez ohledu na <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> to, jaká hodnota je zadána pro, je vždy čtvercový:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`je užitečné buď v datových šablonách, nebo v případech, kdy vazby používají kolekci jako zdroj dat. Můžete použít `{RelativeSource PreviousData}` k zvýraznění vztahů mezi sousedními datovými položkami v kolekci. Související technikou je vytvořit <xref:System.Windows.Data.MultiBinding> mezi aktuálními a předchozími položkami ve zdroji dat a pomocí převaděče na této vazbě určit rozdíl mezi dvěma položkami a jejich vlastnostmi.

V následujícím příkladu první <xref:System.Windows.Controls.TextBlock> v šabloně Items zobrazí aktuální číslo. Druhá <xref:System.Windows.Controls.TextBlock> vazba je, která <xref:System.Windows.Data.MultiBinding> má nominální hodnotu dvou <xref:System.Windows.Data.Binding> prvků: aktuální záznam a vazba, která záměrně používá předchozí datový záznam pomocí. `{RelativeSource PreviousData}` Pak konvertor na základě <xref:System.Windows.Data.MultiBinding> vypočítá rozdíl a vrátí ho do vazby.

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
</ListBox>
```

Popis datové vazby jako koncept se tady nezabývá, najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).

V implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesoru XAML je zpracování tohoto rozšíření značek definováno <xref:System.Windows.Data.RelativeSource> třídou.

`RelativeSource`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v jazyce XAML používají `{` ve `}` svých syntaxech atributů znaky a, což je konvence, pomocí níž procesor XAML rozpozná, že je nutné zpracovat atribut rozšířením značek. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Data.Binding>
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled deklarací připojení](../data/binding-declarations-overview.md)
- [x:Type – rozšíření značek](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
