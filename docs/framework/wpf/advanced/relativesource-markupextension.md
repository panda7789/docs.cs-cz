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
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

Určuje vlastnosti <xref:System.Windows.Data.RelativeSource> zdroje vazby, které mají být použity v <xref:System.Windows.Data.Binding.RelativeSource%2A> rámci rozšíření <xref:System.Windows.Data.Binding> [značky vazby](binding-markup-extension.md)nebo při nastavování vlastnosti prvku vytvořeného v XAML.

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
|`modeEnumValue`|Jeden z následujících produktů:<br /><br /> - Token `Self`řetězce ; odpovídá tak, <xref:System.Windows.Data.RelativeSource> jak bylo <xref:System.Windows.Data.RelativeSource.Mode%2A> vytvořeno <xref:System.Windows.Data.RelativeSourceMode.Self>s vlastností nastavenou na .<br />- Token `TemplatedParent`řetězce ; odpovídá tak, <xref:System.Windows.Data.RelativeSource> jak bylo <xref:System.Windows.Data.RelativeSource.Mode%2A> vytvořeno <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>s vlastností nastavenou na .<br />- Token `PreviousData`řetězce ; odpovídá tak, <xref:System.Windows.Data.RelativeSource> jak bylo <xref:System.Windows.Data.RelativeSource.Mode%2A> vytvořeno <xref:System.Windows.Data.RelativeSourceMode.PreviousData>s vlastností nastavenou na .<br />- Informace o `FindAncestor` režimu naleznete níže.|
|`FindAncestor`|Token `FindAncestor`řetězce . Pomocí tohoto tokenu přejde `RelativeSource` režim, ve kterém určuje typ předchůdce a volitelně úroveň předchůdce. To odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořené s <xref:System.Windows.Data.RelativeSource.Mode%2A> jeho <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>vlastnost nastavena na .|
|`typeName`|Vyžadováno `FindAncestor` pro režim. Název typu, který vyplní <xref:System.Windows.Data.RelativeSource.AncestorType%2A> vlastnost.|
|`intLevel`|Volitelné `FindAncestor` pro režim. Úroveň předchůdce (vyhodnocována ve směru nadřazeného uzlu v logickém stromu)|

## <a name="remarks"></a>Poznámky

`{RelativeSource TemplatedParent}`použití vazby jsou klíčovou technikou, která řeší větší koncept oddělení hlavního použití ovládacího prvku a logiku ovládacího prvku. To umožňuje vytvořit vazbu z definice šablony na nadřazený objekt vytvořený pomocí šablony (instanci objektu vytvořenou za běhu, pro niž je šablona použita). V tomto případě [TemplateBinding Markup Extension](templatebinding-markup-extension.md) je ve skutečnosti zkratka `{Binding RelativeSource={RelativeSource TemplatedParent}}`pro následující výraz vazby: . `TemplateBinding`nebo `{RelativeSource TemplatedParent}` použití jsou relevantní pouze v rámci XAML, který definuje šablonu. Další informace naleznete v [tématu TemplateBinding Markup Extension](templatebinding-markup-extension.md).

`{RelativeSource FindAncestor}`používá se hlavně v šablonách ovládacího prvku nebo předvídatelné samostatné kompozice uživatelského prvku, pro případy, kdy je vždy očekáváno, že ovládací prvek bude ve vizuálním stromu určitého typu předchůdce. Například položky ovládacího prvku `FindAncestor` položky může použít použití svázat s vlastnostmi jejich položky řídit nadřazený předchůdce. Nebo prvky, které jsou součástí složení `FindAncestor` ovládacího prvku v šabloně můžete použít vazby na nadřazené prvky ve stejné struktuře složení.

V syntaxi prvku `FindAncestor` objektu pro režim zobrazený v částech Syntaxe XAML se syntaxe druhého prvku objektu používá speciálně pro `FindAncestor` režim. `FindAncestor`režim vyžaduje <xref:System.Windows.Data.RelativeSource.AncestorType%2A> hodnotu. Je nutné <xref:System.Windows.Data.RelativeSource.AncestorType%2A> nastavit jako atribut pomocí [x:Typ Značkovací rozšíření](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) odkaz na typ předchůdce hledat. Hodnota <xref:System.Windows.Data.RelativeSource.AncestorType%2A> se používá při zpracování požadavku na vazbu za běhu.

Pro `FindAncestor` režim může <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> volitelná vlastnost pomoci rozptýlit vyhledávání předchůdce v případech, kdy ve stromu prvků existuje více než jeden předchůdce tohoto typu.

Další informace o použití `FindAncestor` režimu <xref:System.Windows.Data.RelativeSource>naleznete v tématu .

`{RelativeSource Self}`je užitečné pro scénáře, kde jedna vlastnost instance by měla záviset na hodnotě jiné vlastnosti stejné instance a žádný obecný vztah vlastnosti závislosti (například nátlak) již existuje mezi těmito dvěma vlastnostmi. I když je vzácné, že existují dvě vlastnosti na objekt tak, že hodnoty jsou doslova `Converter` identické (a `{RelativeSource Self}`jsou identicky zadány), můžete také použít parametr vazby, která má , a použít převaděč převést mezi zdrojové a cílové typy. Další scénář `{RelativeSource Self}` pro je <xref:System.Windows.MultiDataTrigger>jako součást .

Například následující XAML definuje <xref:System.Windows.Shapes.Rectangle> prvek tak, že bez ohledu <xref:System.Windows.FrameworkElement.Width%2A>na <xref:System.Windows.Shapes.Rectangle> to, jaká hodnota je zadána , je vždy čtverec:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`je užitečné buď v šablonách dat nebo v případech, kdy vazby používají kolekci jako zdroj dat. Můžete zvýraznit `{RelativeSource PreviousData}` vztahy mezi sousedními datovými položkami v kolekci. Související technika je vytvořit <xref:System.Windows.Data.MultiBinding> mezi aktuální a předchozí položky ve zdroji dat a použít převaděč na tuto vazbu k určení rozdílu mezi dvě položky a jejich vlastnosti.

V následujícím příkladu <xref:System.Windows.Controls.TextBlock> se zobrazí první v šabloně položek aktuální číslo. Druhá <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Data.MultiBinding> vazba je, že <xref:System.Windows.Data.Binding> nominálně má dva složky: aktuální záznam a vazba, která záměrně používá předchozí záznam dat pomocí `{RelativeSource PreviousData}`. Poté převaděč <xref:System.Windows.Data.MultiBinding> na vypočítá rozdíl a vrátí jej do vazby.

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

Popis datové vazby jako koncept zde není popsán, viz [Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md).

V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementaci procesoru XAML zpracování pro toto rozšíření <xref:System.Windows.Data.RelativeSource> značky je definováno třídou.

`RelativeSource`je rozšíření značky. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v XAML `{` `}` používají znaky a v syntaxi jejich atributu, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí atribut zpracovat. Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Data.Binding>
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled deklarací připojení](../data/binding-declarations-overview.md)
- [x:Type – rozšíření značek](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
