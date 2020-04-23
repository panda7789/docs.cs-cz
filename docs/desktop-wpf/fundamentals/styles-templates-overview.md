---
title: Styly a šablony
description: Další informace o prostředcích XAML v systému Windows Presentation Foundation (WPF) pro .NET Core. Seznamte se s typy prostředků XAML souvisejících se styly a motivy.
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
# <a name="styles-and-templates-in-wpf"></a>Styly a šablony ve WPF

Windows Presentation Foundation (WPF) styling a šablonování odkazují na sadu funkcí, které umožňují vývojářům a návrhářům vytvářet vizuálně přesvědčivé efekty a konzistentní vzhled pro jejich produkt. Při přizpůsobení vzhledu aplikace chcete silný styl a šablonovací model, který umožňuje údržbu a sdílení vzhledu v aplikacích i mezi nimi. WPF poskytuje tento model.

Dalším rysem modelu wpf styling je oddělení prezentace a logiky. Návrháři mohou pracovat na vzhledu aplikace pomocí pouze XAML ve stejnou dobu, že vývojáři pracují na programovací logiku pomocí Jazyka C# nebo Visual Basic.

Tento přehled se zaměřuje na stylování a šablonování aspekty aplikace a nepopisuje žádné koncepty vazby dat. Informace o datové vazbě naleznete v [tématu Přehled datové vazby](../data/data-binding-overview.md).

Je důležité porozumět prostředkům, které umožňují opakované použití stylů a šablon. Další informace o prostředcích naleznete v tématu [XAML Resources](xaml-resources-define.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Ukázka

Ukázkový kód uvedený v tomto přehledu je založen na [jednoduché aplikaci pro prohlížení fotografií](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) zobrazené na následujícím obrázku.

![Stylizované listview](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Tato jednoduchá ukázka fotografií využívá styling a šablonování k vytvoření vizuálně působivého uživatelského prostředí. Ukázka má <xref:System.Windows.Controls.TextBlock> dva <xref:System.Windows.Controls.ListBox> prvky a ovládací prvek, který je vázán na seznam obrázků.

Kompletní ukázku najdete [v tématu Úvod do stylingu a šablonování ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="styles"></a>Styly

Můžete si <xref:System.Windows.Style> myslet, že je pohodlný způsob, jak použít sadu hodnot vlastností na více prvků. Styl můžete použít na libovolný prvek, <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> který je <xref:System.Windows.Window> odvozen <xref:System.Windows.Controls.Button>od nebo například nebo .

Nejběžnější způsob deklarování stylu je jako `Resources` prostředek v části v souboru XAML. Vzhledem k tomu, že styly jsou prostředky, řídí se stejnými pravidly oboru, která platí pro všechny prostředky. Jednoduše řečeno, kde deklarujete styl ovlivňuje, kde lze použít styl. Pokud například deklarujete styl v kořenovém prvku souboru XAML definice aplikace, styl lze použít kdekoli ve vaší aplikaci.

Například následující kód XAML deklaruje dva styly pro `TextBlock`, jeden automaticky použita na všechny `TextBlock` prvky a další, které musí být explicitně odkazovány.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Zde je příklad výše uvedených stylů.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![Stylizované textové bloky](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Další informace naleznete [v tématu Vytvoření stylu ovládacího prvku](styles-templates-create-apply-style.md).

## <a name="controltemplates"></a>Řídicí šablony

V WPF <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku definuje vzhled ovládacího prvku. Strukturu a vzhled ovládacího prvku můžete změnit <xref:System.Windows.Controls.ControlTemplate> definováním nového ovládacího prvku a jeho přiřazením ovládacímu prvku. V mnoha případech šablony poskytují dostatečnou flexibilitu, takže není třeba psát vlastní ovládací prvky.

Každý ovládací prvek má výchozí šablonu přiřazenou vlastnosti [Control.Template.](xref:System.Windows.Controls.Control.Template) Šablona spojuje vizuální prezentaci ovládacího prvku s možnostmi ovládacího prvku. Vzhledem k tomu, že definujete šablonu v XAML, můžete změnit vzhled ovládacího prvku bez psaní kódu. Každá šablona je určena pro konkrétní <xref:System.Windows.Controls.Button>ovládací prvek, například .

Obvykle deklarujete šablonu `Resources` jako prostředek v části souboru XAML. Stejně jako u všech zdrojů platí pravidla oboru.

Šablony ovládacích prvku jsou mnohem více než styl. Důvodem je, že šablona ovládacího prvku přepíše vizuální vzhled celého ovládacího prvku, zatímco styl jednoduše použije změny vlastností na existující ovládací prvek. Protože je však šablona ovládacího prvku použita nastavením vlastnosti [Control.Template,](xref:System.Windows.Controls.Control.Template) můžete použít styl k definování nebo nastavení šablony.

Návrháři obvykle umožňují vytvořit kopii existující šablony a upravit ji. Například v návrháři WPF sady `CheckBox` Visual Studio vyberte ovládací prvek a potom klepněte pravým tlačítkem myši a vyberte **upravit šablonu** > **Vytvořit kopii**. Tento příkaz generuje *styl, který definuje šablonu*.

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

Úprava kopie šablony je skvělý způsob, jak zjistit, jak šablony fungují. Místo vytváření nové prázdné šablony je snazší upravit kopii a změnit několik aspektů vizuální prezentace.

Příklad najdete v [tématu Vytvoření šablony pro ovládací prvek](../themes/how-to-create-apply-template.md).

### <a name="templatebinding"></a>Šablona vazba

Možná jste si všimli, že prostředek šablony definovaný v předchozí části používá [rozšíření TemplateBinding Markup Extension](../../framework/wpf/advanced/templatebinding-markup-extension.md). A `TemplateBinding` je optimalizovaná forma vazby pro scénáře šablony, analogické s vazbou vyrobenou s `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding`je užitečné pro vazby části šablony na vlastnosti ovládacího prvku. Například každý ovládací <xref:System.Windows.Controls.Control.BorderThickness> prvek má vlastnost. Slouží `TemplateBinding` ke správě prvku v šabloně, který je tímto nastavením ovládacího prvku ovlivněn.

### <a name="contentcontrol-and-itemscontrol"></a>ContentControl a ItemsControl

Pokud <xref:System.Windows.Controls.ContentPresenter> a je <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ContentControl>deklarována v od , <xref:System.Windows.Controls.ContentPresenter> bude automaticky vázat na vlastnosti <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a. <xref:System.Windows.Controls.ContentControl.Content%2A> Podobně, <xref:System.Windows.Controls.ItemsPresenter> který je v <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ItemsControl> bude automaticky vázat <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> na <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnosti a.

## <a name="datatemplates"></a>Šablony dat

V této ukázkové aplikaci je <xref:System.Windows.Controls.ListBox> ovládací prvek, který je vázán na seznam fotografií.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

To <xref:System.Windows.Controls.ListBox> to v současné době vypadá takto.

![ListBox před použitím šablony](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

Většina ovládacích prvků má určitý typ obsahu a tento obsah často pochází z dat, ke kterým jste vazby. V této ukázce jsou data seznamem fotografií. V WPF, můžete <xref:System.Windows.DataTemplate> definovat vizuální reprezentaci dat. V podstatě to, <xref:System.Windows.DataTemplate> co vložíte do, určuje, jak data vypadají v vykreslené aplikaci.

V naší ukázkové `Photo` aplikaci `Source` má každý vlastní objekt vlastnost typu, která určuje cestu k souboru obrázku. V současné době se objekty fotografií zobrazují jako cesty k souborům.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Aby se fotografie zobrazovaly jako <xref:System.Windows.DataTemplate> obrázky, vytvoříte je jako zdroj.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

Všimněte <xref:System.Windows.DataTemplate.DataType%2A> si, že <xref:System.Windows.Style.TargetType%2A> vlastnost je <xref:System.Windows.Style>podobná vlastnost . Pokud <xref:System.Windows.DataTemplate> je v části zdroje, když <xref:System.Windows.DataTemplate.DataType%2A> zadáte vlastnost typu a `x:Key`vynesete , použije se <xref:System.Windows.DataTemplate> vždy, když se tento typ zobrazí. Vždy máte možnost přiřadit <xref:System.Windows.DataTemplate> s `x:Key` a pak jej `StaticResource` nastavit jako <xref:System.Windows.DataTemplate> pro vlastnosti, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> které <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> berou typy, jako je například vlastnost nebo vlastnost.

V podstatě ve výše <xref:System.Windows.DataTemplate> uvedeném příkladu `Photo` definuje, že vždy, když je objekt, by se měl zobrazit jako <xref:System.Windows.Controls.Image> v rámci . <xref:System.Windows.Controls.Border> S <xref:System.Windows.DataTemplate>tímto , naše aplikace nyní vypadá takto.

![Obrázek fotografie](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

Model templating dat poskytuje další funkce. Například pokud zobrazujete data kolekce, která obsahuje <xref:System.Windows.Controls.HeaderedItemsControl> jiné kolekce <xref:System.Windows.Controls.Menu> pomocí <xref:System.Windows.Controls.TreeView>typu, jako <xref:System.Windows.HierarchicalDataTemplate>je například nebo , je . Další funkcí templating <xref:System.Windows.Controls.DataTemplateSelector>dat je , která <xref:System.Windows.DataTemplate> umožňuje zvolit a použít na základě vlastní logiky. Další informace naleznete v [tématu Přehled šablon dat](../../framework/wpf/data/data-templating-overview.md), který poskytuje podrobnější diskusi o různých funkcích templating dat.

## <a name="triggers"></a>Aktivační události

Aktivační událost nastaví vlastnosti nebo spustí akce, například animace, když se změní hodnota vlastnosti nebo když je vyvolána událost. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>a <xref:System.Windows.DataTemplate> všechny `Triggers` mají vlastnost, která může obsahovat sadu aktivačních událostí. Existuje několik typů aktivačních událostí.

### <a name="propertytriggers"></a>PropertyTriggers

A, <xref:System.Windows.Trigger> který nastaví hodnoty vlastností nebo spustí akce na základě hodnoty vlastnosti se nazývá aktivační událost vlastnosti.

Chcete-li předvést, jak používat aktivační <xref:System.Windows.Controls.ListBoxItem> události vlastností, můžete provést každý částečně transparentní, pokud není vybrán. Následující styl nastaví <xref:System.Windows.UIElement.Opacity%2A> hodnotu a <xref:System.Windows.Controls.ListBoxItem> na `0.5`. Pokud <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> je `true`vlastnost , <xref:System.Windows.UIElement.Opacity%2A> je však nastavena na `1.0`.

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

Tento příklad <xref:System.Windows.Trigger> používá k nastavení hodnoty vlastnosti, ale všimněte si, že <xref:System.Windows.Trigger> třída má také <xref:System.Windows.TriggerBase.EnterActions%2A> vlastnosti a, <xref:System.Windows.TriggerBase.ExitActions%2A> které umožňují aktivační událost provádět akce.

Všimněte <xref:System.Windows.FrameworkElement.MaxHeight%2A> si, <xref:System.Windows.Controls.ListBoxItem> že vlastnost `75`je nastavena na . Na následujícím obrázku je vybrána třetí položka.

![Stylizované listview](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>Aktivační události a scénáře

Dalším typem <xref:System.Windows.EventTrigger>aktivační události je , který spustí sadu akcí na základě výskytu události. Například <xref:System.Windows.EventTrigger> následující objekty určují, že když <xref:System.Windows.Controls.ListBoxItem>ukazatel <xref:System.Windows.FrameworkElement.MaxHeight%2A> myši zadá , `90` vlastnost `0.2` animuje na hodnotu za druhé období. Když se myš přesune od položky, vlastnost se vrátí `1` na původní hodnotu po dobu sekundy. Všimněte si, jak není <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> nutné <xref:System.Windows.ContentElement.MouseLeave> zadat hodnotu animace. Důvodem je, že animace je schopen sledovat původní hodnotu.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Další informace naleznete v přehledu [scénářů](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

Na následujícím obrázku ukazuje myš na třetí položku.

![Ukázkový snímek obrazovky s stylingem](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers a MultiDataTriggers

Kromě <xref:System.Windows.Trigger> a <xref:System.Windows.EventTrigger>, existují i jiné typy aktivačních událostí. <xref:System.Windows.MultiTrigger>umožňuje nastavit hodnoty vlastností na základě více podmínek. Můžete <xref:System.Windows.DataTrigger> použít <xref:System.Windows.MultiDataTrigger> a když je vlastnost vašeho stavu vázána na data.

## <a name="visual-states"></a>Vizuální stavy

Ovládací prvky jsou vždy v určitém **stavu**. Například když se myš pohybuje po povrchu ovládacího prvku, ovládací `MouseOver`prvek je považován za ve společném stavu . Ovládací prvek bez určitého stavu se `Normal` považuje za ve společném stavu. Státy jsou rozděleny do skupin a výše uvedené státy `CommonStates`jsou součástí státní skupiny . Většina ovládacích prvků `CommonStates` `FocusStates`má dvě skupiny stavu: a . Z každé skupiny stavu aplikované na ovládací prvek je ovládací `CommonStates.MouseOver` `FocusStates.Unfocused`prvek vždy v jednom stavu každé skupiny, například a . Ovládací prvek však nemůže být ve dvou různých stavech `CommonStates.Normal` `CommonStates.Disabled`ve stejné skupině, například a . Zde je tabulka stavů, které většina ovládacích prvků rozpozná a používá.

| Název VisualState | Název visualstategroup | Popis |
| ---------------- | --------------------- | ----------- |
| Normální           | Běžné státy          | Výchozí stav. |
| Mouseover        | Běžné státy          | Ukazatel myši je umístěn nad ovládacím prvkem. |
| Pressed          | Běžné státy          | Ovládací prvek je stisknut. |
| Zakázáno         | Běžné státy          | Ovládací prvek je zakázán. |
| Focused          | FocusStates           | Ovládací prvek má fokus. |
| Rozostřený        | FocusStates           | Ovládací prvek nemá fokus. |

Definováním <xref:System.Windows.VisualStateManager?displayProperty=fullName> na kořenový prvek šablony ovládacího prvku, můžete aktivovat animace, když ovládací prvek vstoupí do určitého stavu. Deklaruje, `VisualStateManager` <xref:System.Windows.VisualStateGroup> které <xref:System.Windows.VisualState> kombinace a sledovat. Když ovládací prvek přejde do sledovaného `VisaulStateManager` stavu, spustí se animace definovaná ovládacím prvkem.

Například následující kód XAML `CommonStates.MouseOver` sleduje stav animovat barvu výplně prvku s názvem `backgroundElement`. Když se ovládací `CommonStates.Normal` prvek vrátí do stavu, `backgroundElement` obnoví se barva výplně pojmenovaného prvku.

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

Další informace o scénářích najdete v [tématu Přehled scénářů](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

## <a name="shared-resources-and-themes"></a>Sdílené zdroje a motivy

Typická aplikace WPF může mít více prostředků ui, které se používají v celé aplikaci. Společně lze tuto sadu prostředků považovat za motiv pro aplikaci. WPF poskytuje podporu pro balení prostředků uzly jako motiv pomocí slovníku prostředků, který je zapouzdřen jako <xref:System.Windows.ResourceDictionary> třída.

WPF motivy jsou definovány pomocí styling a šablonování mechanismus, který WPF zveřejňuje pro přizpůsobení vizuály libovolného prvku.

Prostředky motivu WPF jsou uloženy ve vložených slovníkech prostředků. Tyto slovníky prostředků musí být vloženy do podepsaného sestavení a mohou být vloženy do stejného sestavení jako samotný kód nebo do sestavení vedle sebe. Pro PresentationFramework.dll, sestavení, které obsahuje ovládací prvky WPF, jsou prostředky motivu v řadě souběžných sestavení.

Motiv se stane posledním místem, kde se bude hledat při hledání stylu prvku. Hledání obvykle začne tak, že se dostanete do stromu elementů a vyhledáte příslušný prostředek, pak se podívejte do kolekce prostředků aplikace a nakonec se dotazujte na systém. To dává vývojářům aplikací možnost předefinovat styl pro libovolný objekt na úrovni stromu nebo aplikace před dosažením motivu.

Slovníky prostředků můžete definovat jako jednotlivé soubory, které umožňují opakované použití motivu ve více aplikacích. Vyměnitelné motivy můžete také vytvořit definováním více slovníků prostředků, které poskytují stejné typy prostředků, ale s různými hodnotami. Předefinování těchto stylů nebo jiných prostředků na úrovni aplikace je doporučený přístup pro stahování aplikace z kůže.

Chcete-li sdílet sadu prostředků, včetně stylů a šablon, mezi aplikacemi, můžete <xref:System.Windows.ResourceDictionary> vytvořit soubor `shared.xaml` XAML a definovat soubor, který obsahuje odkaz na soubor.

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

Je sdílení `shared.xaml`, který sám <xref:System.Windows.ResourceDictionary> definuje, který obsahuje sadu prostředků stylu a stopy, který umožňuje ovládací prvky v aplikaci mít konzistentní vzhled.

Další informace naleznete [v tématu Merged resource dictionaries](../../framework/wpf/advanced/merged-resource-dictionaries.md).

Pokud vytváříte motiv pro vlastní ovládací prvek, přečtěte si **část Definování zdrojů na úrovni motivu** v [přehledu vytváření ovládacího prvku](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level).

## <a name="see-also"></a>Viz také

- [Sbalení URI v technologii WPF](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [Postupy: Vyhledávání elementů generovaných objektem ControlTemplate](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [Najít prvky generované šablonou dat](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
