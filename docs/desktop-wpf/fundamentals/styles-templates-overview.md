---
title: Styly a šablony
description: Přečtěte si o prostředcích XAML v Windows Presentation Foundation (WPF) pro .NET Core. Seznamte se s typy prostředků XAML, které se týkají stylů a motivů.
author: thraka
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f845e739ec3cae502d1e4fd6631f987c5364a42e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071883"
---
# <a name="styles-and-templates-in-wpf"></a>Styly a šablony v subsystému WPF

Windows Presentation Foundation (WPF) – stylování a šablonování odkazují na sadu funkcí, které vývojářům a návrhářům umožní vytvářet vizuálně působivé efekty a konzistentní vzhled pro jejich produkt. Při přizpůsobování vzhledu aplikace chcete mít silný styl stylů a šablonování, který umožňuje údržbu a sdílení vzhledu v rámci aplikací i mezi nimi. WPF poskytuje tento model.

Další funkcí modelu stylu WPF je oddělení prezentace a logiky. Návrháři mohou pracovat s vzhledem aplikace pomocí pouze XAML v současné době, kdy vývojáři pracují s logikou programování pomocí jazyka C# nebo Visual Basic.

Tento přehled se zaměřuje na styly a šablonování aspekty aplikace a nezabývá se žádnými koncepty datových vazeb. Informace o datové vazbě najdete v tématu [Přehled datových vazeb](../data/data-binding-overview.md).

Je důležité pochopit prostředky, které umožňují znovu použít styly a šablony. Další informace o prostředcích najdete v tématu věnovaném [prostředkům XAML](xaml-resources-define.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Ukázka

Vzorový kód uvedený v tomto přehledu je založený na [jednoduché aplikaci pro procházení fotek](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) , která je znázorněna na následujícím obrázku.

![Zobrazení stylu ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Ukázka jednoduché fotky používá styly a šablonování k vytvoření vizuálně působivého uživatelského prostředí. Vzorek má dva <xref:System.Windows.Controls.TextBlock> prvky a <xref:System.Windows.Controls.ListBox> ovládací prvek, který je svázán se seznamem obrázků.

Úplnou ukázku najdete v tématu [Úvod do stylů a šablonování Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="styles"></a>Styly

Můžete si představit <xref:System.Windows.Style> jako pohodlný způsob, jak použít sadu hodnot vlastností na více prvků. Můžete použít styl na jakémkoli prvku, který je odvozen <xref:System.Windows.FrameworkElement> z nebo <xref:System.Windows.FrameworkContentElement> jako <xref:System.Windows.Window> nebo. <xref:System.Windows.Controls.Button>

Nejběžnější způsob, jak deklarovat styl, je jako prostředek v `Resources` oddílu v souboru XAML. Vzhledem k tomu, že styly jsou prostředky, řídí se stejnými pravidly oboru, která se vztahují na všechny prostředky. Put, kde deklarujete styl, ovlivňuje, kde lze použít styl. Například pokud deklarujete styl v kořenovém elementu souboru XAML definice aplikace, styl lze použít kdekoli v aplikaci.

Například následující kód XAML deklaruje dva styly pro `TextBlock`, jeden automaticky aplikovaný na všechny `TextBlock` prvky a druhý, který musí být explicitně odkazován.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Tady je příklad stylů deklarovaných výše.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![TextBlocks ve stylu](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Další informace naleznete v tématu [vytvoření stylu pro ovládací prvek](styles-templates-create-apply-style.md).

## <a name="controltemplates"></a>ControlTemplates

V WPF <xref:System.Windows.Controls.ControlTemplate> ovládací prvek definuje vzhled ovládacího prvku. Můžete změnit strukturu a vzhled ovládacího prvku definováním nového <xref:System.Windows.Controls.ControlTemplate> a přiřazením k ovládacímu prvku. V mnoha případech šablony poskytují dostatečnou flexibilitu, takže nemusíte psát vlastní ovládací prvky.

Každému ovládacímu prvku je přiřazena výchozí šablona vlastnosti [Control. template](xref:System.Windows.Controls.Control.Template) . Šablona spojuje vizuální prezentaci ovládacího prvku s možnostmi ovládacího prvku. Vzhledem k tomu, že v jazyce XAML definujete šablonu, můžete změnit její vzhled bez psaní kódu. Každá šablona je navržena pro konkrétní ovládací prvek, jako je <xref:System.Windows.Controls.Button>například.

Obvykle deklarujete šablonu jako prostředek v `Resources` oddílu souboru XAML. Stejně jako u všech prostředků platí pravidla oboru.

Šablony ovládacích prvků jsou mnohem větší, než styl. Důvodem je, že šablona ovládacího prvku přepíše vizuální vzhled celého ovládacího prvku, zatímco styl jednoduše aplikuje změny vlastností na existující ovládací prvek. Vzhledem k tomu, že šablona ovládacího prvku je použita nastavením vlastnosti [Control. template](xref:System.Windows.Controls.Control.Template) , můžete použít styl k definování nebo nastavení šablony.

Návrháři obecně umožňují vytvořit kopii existující šablony a upravit ji. Například v návrháři aplikace Visual Studio WPF `CheckBox` vyberte ovládací prvek a potom klikněte pravým tlačítkem a vyberte **Upravit šablonu** > **vytvořit kopii**. Tento příkaz vygeneruje *styl definující šablonu*.

```xaml
<Style x:Key="CheckBoxStyle1" TargetType="{x:Type CheckBox}">
    <Setter Property="FocusVisualStyle" Value="{StaticResource FocusVisual1}"/>
    <Setter Property="Background" Value="{StaticResource OptionMark.Static.Background1}"/>
    <Setter Property="BorderBrush" Value="{StaticResource OptionMark.Static.Border1}"/>
    <Setter Property="Foreground" Value="{DynamicResource {x:Static SystemColors.ControlTextBrushKey}}"/>
    <Setter Property="BorderThickness" Value="1"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type CheckBox}">
                <Grid x:Name="templateRoot" Background="Transparent" SnapsToDevicePixels="True">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition Width="*"/>
                    </Grid.ColumnDefinitions>
                    <Border x:Name="checkBoxBorder" Background="{TemplateBinding Background}" BorderThickness="{TemplateBinding BorderThickness}" BorderBrush="{TemplateBinding BorderBrush}" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="1" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
                        <Grid x:Name="markGrid">
                            <Path x:Name="optionMark" Data="F1 M 9.97498,1.22334L 4.6983,9.09834L 4.52164,9.09834L 0,5.19331L 1.27664,3.52165L 4.255,6.08833L 8.33331,1.52588e-005L 9.97498,1.22334 Z " Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="1" Opacity="0" Stretch="None"/>
                            <Rectangle x:Name="indeterminateMark" Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="2" Opacity="0"/>
                        </Grid>
                    </Border>
                    <ContentPresenter x:Name="contentPresenter" Grid.Column="1" Focusable="False" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" RecognizesAccessKey="True" SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}"/>
                </Grid>
                <ControlTemplate.Triggers>
                    <Trigger Property="HasContent" Value="true">
                        <Setter Property="FocusVisualStyle" Value="{StaticResource OptionMarkFocusVisual1}"/>
                        <Setter Property="Padding" Value="4,-1,0,0"/>

... content removed to save space ...
```

Úprava kopie šablony je skvělým způsobem, jak se naučit, jak šablony fungují. Místo vytvoření nové prázdné šablony je snazší upravit kopii a změnit několik aspektů vizuální prezentace.

Příklad naleznete v tématu [Vytvoření šablony pro ovládací prvek](../themes/how-to-create-apply-template.md).

### <a name="templatebinding"></a>TemplateBinding

Možná jste si všimli, že prostředek šablony definovaný v předchozí části používá [rozšíření značek TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md). `TemplateBinding` Je optimalizovaná forma vazby pro scénáře šablon, která je podobná vazbě vytvořené s `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding`je užitečné pro vázání částí šablony na vlastnosti ovládacího prvku. Každý ovládací prvek má například <xref:System.Windows.Controls.Control.BorderThickness> vlastnost. Použijte `TemplateBinding` ke správě, který prvek v šabloně je ovlivněn nastavením tohoto ovládacího prvku.

### <a name="contentcontrol-and-itemscontrol"></a>ContentControl a ItemsControl

Pokud <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.ControlTemplate> je deklarována v typu <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> bude automaticky vytvořena vazba na vlastnosti <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a. <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.ItemsPresenter> Podobně,,,, který je v <xref:System.Windows.Controls.ControlTemplate> z, <xref:System.Windows.Controls.ItemsControl> bude automaticky svázán s vlastnostmi <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A> .

## <a name="datatemplates"></a>Šablony DataTemplates

V této ukázkové aplikaci je k dispozici <xref:System.Windows.Controls.ListBox> ovládací prvek, který je svázán se seznamem fotek.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

V <xref:System.Windows.Controls.ListBox> současné době vypadá jako následující.

![Seznam před použitím šablony](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

Většina ovládacích prvků má nějaký typ obsahu a tento obsah často pochází z dat, ke kterým vytváříte vazbu. V této ukázce jsou data seznamem fotek. V rámci <xref:System.Windows.DataTemplate> WPF použijte k definování vizuální reprezentace dat. V podstatě to, co jste umístili <xref:System.Windows.DataTemplate> do, určí, co data ve vykreslené aplikaci vypadá jako.

V naší ukázkové aplikaci má každý vlastní `Photo` objekt `Source` vlastnost typu String, která určuje cestu k souboru obrázku. V současné době se objekty fotografie zobrazují jako cesty k souborům.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Aby se fotky zobrazovaly jako obrázky, vytvoříte prostředek <xref:System.Windows.DataTemplate> jako prostředek.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

Všimněte si, <xref:System.Windows.DataTemplate.DataType%2A> že vlastnost je podobná <xref:System.Windows.Style.TargetType%2A> vlastnosti třídy <xref:System.Windows.Style>. Pokud <xref:System.Windows.DataTemplate> je v části Resources (prostředky), když <xref:System.Windows.DataTemplate.DataType%2A> zadáte vlastnost na typ a `x:Key`vynecháte <xref:System.Windows.DataTemplate> , použije se při každém výskytu tohoto typu. Vždy máte možnost přiřadit <xref:System.Windows.DataTemplate> s `x:Key` a pak ji nastavit jako `StaticResource` pro vlastnosti, které přebírají <xref:System.Windows.DataTemplate> typy, jako je <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> například vlastnost nebo <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost.

<xref:System.Windows.DataTemplate> V podstatě v předchozím příkladu definuje, že pokaždé, když je `Photo` objekt, by měl být uveden jako <xref:System.Windows.Controls.Image> v rámci <xref:System.Windows.Controls.Border>. Tato <xref:System.Windows.DataTemplate>aplikace teď vypadá jako to.

![Obrázek fotografie](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

Model data šablonování poskytuje další funkce. Například pokud zobrazujete data kolekce obsahující další kolekce <xref:System.Windows.Controls.HeaderedItemsControl> pomocí typu <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.TreeView>, jako je například nebo, je k dispozici. <xref:System.Windows.HierarchicalDataTemplate> Další funkcí šablonování dat je <xref:System.Windows.Controls.DataTemplateSelector>, která umožňuje zvolit <xref:System.Windows.DataTemplate> použití v závislosti na vlastní logice. Další informace najdete v tématu [Přehled šablonování dat](../../framework/wpf/data/data-templating-overview.md), který poskytuje podrobnější diskuzi o různých funkcích šablonování dat.

## <a name="triggers"></a>Aktivační události

Trigger nastaví vlastnosti nebo spustí akce, jako je například animace, když se změní hodnota vlastnosti nebo dojde k vyvolání události. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>a <xref:System.Windows.DataTemplate> všechny mají `Triggers` vlastnost, která může obsahovat sadu triggerů. K dispozici je několik typů triggerů.

### <a name="propertytriggers"></a>PropertyTriggers

Sada <xref:System.Windows.Trigger> , která nastavuje hodnoty vlastností nebo spouští akce založené na hodnotě vlastnosti, se nazývá Trigger vlastnosti.

Chcete-li předvést, jak používat triggery vlastností, <xref:System.Windows.Controls.ListBoxItem> můžete provést všechny částečně transparentní, pokud není vybrán. Následující styl nastaví <xref:System.Windows.UIElement.Opacity%2A> hodnotu typu <xref:System.Windows.Controls.ListBoxItem> na. `0.5` Pokud je <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> `true`však <xref:System.Windows.UIElement.Opacity%2A> vlastnost nastavena na `1.0`.

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

Tento <xref:System.Windows.Trigger> příklad používá k nastavení hodnoty vlastnosti, ale Všimněte si, <xref:System.Windows.Trigger> že třída má také vlastnosti <xref:System.Windows.TriggerBase.EnterActions%2A> a <xref:System.Windows.TriggerBase.ExitActions%2A> , které umožňují triggeru provádět akce.

Všimněte si, <xref:System.Windows.FrameworkElement.MaxHeight%2A> že vlastnost třídy <xref:System.Windows.Controls.ListBoxItem> je nastavena na `75`hodnotu. Na následujícím obrázku je třetí položka vybraná položka.

![Zobrazení stylu ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTriggers a scénáře

Jiný typ triggeru je <xref:System.Windows.EventTrigger>, který spustí sadu akcí založenou na výskytu události. <xref:System.Windows.EventTrigger> Například následující objekty určují, že když ukazatel myši vstoupí do <xref:System.Windows.Controls.ListBoxItem>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> vlastnost se animuje na hodnotu `90` za `0.2` druhé období. Když se ukazatel myši přesune mimo položku, vrátí se vlastnost na původní hodnotu za tečku `1` sekundy. Všimněte si, že není nutné zadávat <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> hodnotu <xref:System.Windows.ContentElement.MouseLeave> animace. Je to proto, že animace může sledovat původní hodnotu.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Další informace najdete v [přehledu scénářů](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

Na následujícím obrázku je ukazatel myši ukazující na třetí položku.

![Ukázka stylu snímku obrazovky](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>Více triggerů, DataTriggers a MultiDataTriggers

Kromě <xref:System.Windows.Trigger> a existují i <xref:System.Windows.EventTrigger>další typy triggerů. <xref:System.Windows.MultiTrigger>umožňuje nastavit hodnoty vlastností na základě několika podmínek. Použijete <xref:System.Windows.DataTrigger> a <xref:System.Windows.MultiDataTrigger> , pokud je vlastnost vaší podmínky vázána na data.

## <a name="visual-states"></a>Vizuální stavy

Ovládací prvky jsou vždy v určitém **stavu**. Například pokud se ukazatel myši pohybuje na povrchu ovládacího prvku, je ovládací prvek považován za v běžném stavu `MouseOver`. Ovládací prvek bez konkrétního stavu je považován za v běžném `Normal` stavu. Stavy jsou rozdělené do skupin a výše uvedené stavy jsou součástí skupiny `CommonStates`stavů. Většina ovládacích prvků má dvě skupiny `CommonStates` stavů `FocusStates`: a. V každé skupině stavů použité pro ovládací prvek je ovládací prvek vždy v jednom stavu každé skupiny, například `CommonStates.MouseOver` a. `FocusStates.Unfocused` Nicméně ovládací prvek nemůže být ve dvou různých stavech v rámci stejné skupiny, například `CommonStates.Normal` a. `CommonStates.Disabled` Zde je tabulka stavů, které jsou rozpoznány a používány nejvíce ovládacími prvky.

| Název VisualState | Název VisualStateGroup | Popis |
| ---------------- | --------------------- | ----------- |
| Normální           | CommonStates          | Výchozí stav. |
| MouseOver        | CommonStates          | Ukazatel myši je umístěn nad ovládacím prvkem. |
| Pressed          | CommonStates          | Ovládací prvek se stiskne. |
| Zakázáno         | CommonStates          | Ovládací prvek je zakázán. |
| Focused          | FocusStates           | Ovládací prvek má fokus. |
| Bez fokusu        | FocusStates           | Ovládací prvek nemá fokus. |

Definováním elementu <xref:System.Windows.VisualStateManager?displayProperty=fullName> v kořenovém prvku šablony ovládacího prvku lze spustit animace, když ovládací prvek vstoupí do určitého stavu. `VisualStateManager` Deklaruje, které kombinace <xref:System.Windows.VisualStateGroup> a <xref:System.Windows.VisualState> ke sledování. Když ovládací prvek vstoupí do sledovaného stavu, `VisaulStateManager` je spuštěna animace definovaná pomocí.

Například následující kód XAML sleduje `CommonStates.MouseOver` stav pro animaci barvy výplně elementu s názvem. `backgroundElement` Když se ovládací prvek vrátí do `CommonStates.Normal` stavu, je obnovena Barva výplně elementu s `backgroundElement` názvem.

```xaml
<ControlTemplate x:Key="roundbutton" TargetType="Button">
    <Grid>
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup Name="CommonStates">
                <VisualState Name="Normal">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="{TemplateBinding Background}"
                                    Duration="0:0:0.3"/>
                </VisualState>
                <VisualState Name="MouseOver">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="Yellow"
                                    Duration="0:0:0.3"/>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        ...
```

Další informace o scénářích najdete v tématu [Přehled scénářů](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

## <a name="shared-resources-and-themes"></a>Sdílené prostředky a motivy

Typická aplikace WPF může mít více prostředků uživatelského rozhraní, které jsou v rámci aplikace aplikovány. Souhrnná Tato sada prostředků může být považována za motiv aplikace. WPF poskytuje podporu pro prostředky uživatelského rozhraní pro sbalení jako motiv pomocí slovníku prostředků, který je zapouzdřen jako <xref:System.Windows.ResourceDictionary> třída.

Motivy WPF jsou definovány pomocí mechanismu stylů a šablonování, který WPF zpřístupňuje pro přizpůsobení vizuálů všech prvků.

Prostředky motivu WPF se ukládají do integrovaných slovníků prostředků. Tyto slovníky prostředků musí být vloženy v rámci podepsaného sestavení a mohou být buď vloženy do stejného sestavení jako samotný kód nebo do souběžného sestavení. Pro PresentationFramework. dll, sestavení, které obsahuje ovládací prvky WPF, jsou prostředky motivů v sérii souběžných sestavení.

Motiv se bude zobrazovat jako poslední místo pro hledání stylu elementu. Hledání se obvykle začne prozkoumáním stromu elementu, který hledá příslušný prostředek, a pak se podívejte do kolekce prostředků aplikace a nakonec dotazovat systém. To dává vývojářům aplikací možnost předefinovat styl pro libovolný objekt na úrovni stromu nebo aplikace, než se přiblíží k motivu.

Slovníky prostředků můžete definovat jako samostatné soubory, které vám umožní opakovaně používat motiv napříč více aplikacemi. Můžete také vytvořit vyměnitelné motivy definováním několika slovníků prostředků, které poskytují stejné typy prostředků, ale s různými hodnotami. Předefinování těchto stylů nebo jiných prostředků na úrovni aplikace je doporučený postup pro změny vzhledu aplikace.

Chcete-li sdílet sadu prostředků, včetně stylů a šablon, v rámci aplikací, můžete vytvořit soubor XAML a definovat <xref:System.Windows.ResourceDictionary> , který obsahuje odkaz na `shared.xaml` soubor.

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

Je to sdílení `shared.xaml`, které sám definuje <xref:System.Windows.ResourceDictionary> sadu prostředků stylu a štětce, která umožňuje ovládacím prvkům v aplikaci konzistentní vzhled.

Další informace najdete v tématu [sloučené slovníky prostředků](../../framework/wpf/advanced/merged-resource-dictionaries.md).

Pokud vytváříte motiv pro vlastní ovládací prvek, přečtěte si část **Definování prostředků v části úroveň motivu** v tématu [Přehled vytváření ovládacích prvků](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level).

## <a name="see-also"></a>Viz také

- [Sbalení URI v technologii WPF](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [Postupy: Vyhledávání elementů generovaných objektem ControlTemplate](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [Hledání elementů generovaných šablonou DataTemplate](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
