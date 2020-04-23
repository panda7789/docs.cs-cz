---
title: Vytvoření šablony v aplikaci WPF - .NET Desktop
description: Zjistěte, jak vytvořit a odkazovat na šablonu ovládacího prvku v systému Windows Presentation Foundation a .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071246"
---
# <a name="create-a-template-for-a-control"></a>Vytvoření šablony pro ovládací prvek

Pomocí windows presentation foundation (WPF) můžete přizpůsobit vizuální strukturu a chování existujícího ovládacího prvku pomocí vlastní opakovaně použitelné šablony. Šablony lze použít globálně na vaši aplikaci, okna a stránky nebo přímo na ovládací prvky. Většina scénářů, které vyžadují vytvoření nového ovládacího prvku, může být pokryta místo toho vytvoření množení nové šablony pro existující ovládací prvek.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

V tomto článku se budete zabývat vytvořením nového <xref:System.Windows.Controls.ControlTemplate> ovládacího <xref:System.Windows.Controls.Button> prvku.

## <a name="when-to-create-a-controltemplate"></a>Kdy vytvořit šablonu ovládacího prvku

Ovládací prvky mají <xref:System.Windows.Controls.Border.Background%2A>mnoho <xref:System.Windows.Controls.Control.Foreground%2A>vlastností, například , a <xref:System.Windows.Controls.Control.FontFamily%2A>. Tyto vlastnosti řídí různé aspekty vzhledu ovládacího prvku, ale změny, které můžete provést nastavením těchto vlastností, jsou omezené. Můžete například nastavit <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost na <xref:System.Windows.Controls.Control.FontStyle%2A> modrou a kurzívu <xref:System.Windows.Controls.CheckBox>na . Pokud chcete přizpůsobit vzhled ovládacího prvku nad rámec toho, co může nastavení <xref:System.Windows.Controls.ControlTemplate>ostatních vlastností v ovládacím prvku provést, vytvořte .

Ve většině uživatelských rozhraní má tlačítko stejný celkový vzhled: obdélník s určitým textem. Pokud chcete vytvořit zaoblené tlačítko, můžete vytvořit nový ovládací prvek, který dědí z tlačítka nebo znovu vytvoří funkce tlačítka. Kromě toho nový uživatelský ovládací prvek by poskytnout kruhový vizuál.

Můžete se vyhnout vytváření nových ovládacích prvků přizpůsobením vizuální rozložení existujícího ovládacího prvku. Se zaobleným tlačítkem vytvoříte a <xref:System.Windows.Controls.ControlTemplate> s požadovaným vizuálním rozložením.

Na druhou stranu, pokud potřebujete ovládací prvek s novými funkcemi, různými vlastnostmi a novýmnastavením, vytvoříte nový <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Požadované součásti

Vytvořte novou aplikaci WPF a v *mainwindow.xaml* (nebo jiné okno podle vašeho výběru) nastavit následující vlastnosti na ** \<Element Okna>:**

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

Nastavte obsah elementu ** \<Window>** na následující XAML:

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Nakonec *mainwindow.xaml* soubor by měl vypadat podobně jako následující:

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

Pokud spustíte aplikaci, vypadá to takto:

![Okno WPF se dvěma nestylovými tlačítky](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>Vytvoření šablony ovládacího prvku

Nejběžnější způsob deklarování <xref:System.Windows.Controls.ControlTemplate> a je `Resources` jako prostředek v části v souboru XAML. Vzhledem k tomu, že šablony jsou prostředky, řídí se stejnými pravidly oboru, která platí pro všechny prostředky. Jednoduše řečeno, kde deklarujete, že šablona ovlivňuje, kde lze šablonu použít. Pokud například deklarujete šablonu v kořenovém prvku souboru XAML definice aplikace, šablonu lze použít kdekoli v aplikaci. Pokud definujete šablonu v okně, mohou šablonu používat pouze ovládací prvky v tomto okně.

Chcete-li začít, `Window.Resources` přidejte prvek do souboru *MainWindow.xaml:*

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

Vytvořte novou ** \<>ControlTemplate** s následující sadou vlastností:

|     |     |
| --- | --- |
| **x:Klíč**         | `roundbutton` |
| **TargetType**    | `Button` |

Tato šablona ovládacího prvku bude jednoduchá:

- kořenový prvek ovládacího prvku,<xref:System.Windows.Controls.Grid>
- a <xref:System.Windows.Shapes.Ellipse> nakreslit zaoblený vzhled tlačítka
- a <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah tlačítka určeného uživatelem

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>Šablona vazba

Při vytváření nového <xref:System.Windows.Controls.ControlTemplate>ovládacího prvku můžete stále chtít použít veřejné vlastnosti ke změně vzhledu ovládacího prvku. Rozšíření značky [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) váže vlastnost prvku, který <xref:System.Windows.Controls.ControlTemplate> je ve veřejné vlastnosti, která je definována ovládacím prvkem. Při použití [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), povolíte vlastnosti ovládacího prvku působit jako parametry šablony. To znamená, že když je nastavena vlastnost na ovládací prvek, tato hodnota je předána na prvek, který má [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) na něm.

### <a name="ellipse"></a>Elipsa

Všimněte **:::no-loc text="Fill":::** si, že a **:::no-loc text="Stroke":::** vlastnosti ** \<elementu elipsy** <xref:System.Windows.Controls.Control.Background>>jsou vázány na vlastnosti ovládacího <xref:System.Windows.Controls.Control.Foreground> prvku a vlastnosti.

### <a name="contentpresenter"></a>Contentpresenter

Do šablony je také přidán prvek [ \<ContentPresenter>.](xref:System.Windows.Controls.ContentPresenter) Vzhledem k tomu, že tato šablona je určena <xref:System.Windows.Controls.ContentControl>pro tlačítko, vezměte v úvahu, že tlačítko dědí z . Tlačítko představuje obsah prvku. Uvnitř tlačítka můžete nastavit cokoli, například prostý text nebo dokonce jiný ovládací prvek. Obě následující tlačítka jsou platná:

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

V obou předchozích příkladech jsou text a zaškrtávací políčko nastaveny jako vlastnost [Button.Content.](xref:System.Windows.Controls.ContentControl.Content) Cokoliv je nastaveno jako obsah, může být prezentováno prostřednictvím ** \<>ContentPresenter **, což je to, co šablona dělá.

Pokud <xref:System.Windows.Controls.ControlTemplate> je použita <xref:System.Windows.Controls.ContentControl> pro typ, `Button`například , a <xref:System.Windows.Controls.ContentPresenter> je hledána ve stromu prvků. Pokud `ContentPresenter` je nalezen, šablona automaticky sváže <xref:System.Windows.Controls.ContentControl.Content> vlastnost `ContentPresenter`ovládacího prvku na .

## <a name="use-the-template"></a>Použití šablony

Najít tlačítka, které byly deklarovány na začátku tohoto článku.

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Nastavte <xref:System.Windows.Controls.Control.Template> vlastnost druhého tlačítka na `roundbutton` prostředek:

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

Pokud spustíte projekt a podíváte se na výsledek, uvidíte, že tlačítko má zaoblené pozadí.

![Okno WPF s jedním tlačítkem oválné šablony](media/create-apply-template/styled-button.png)

Možná jste si všimli, že tlačítko není kruh, ale je zkosené. Vzhledem ke způsobu, ** \<>** jakým prvek funguje, se vždy zvětšuje tak, aby vyplnil dostupné místo. Změníte tak, že **:::no-loc text="width":::** **:::no-loc text="height":::** kruh bude jednotný na stejnou hodnotu:

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Okno WPF s jedním cyklovým tlačítkem šablony](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>Přidání aktivační události

I když tlačítko s použitou šablonou vypadá jinak, chová se stejně jako jakékoli jiné tlačítko. Pokud stisknete <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tlačítko, událost se spustí. Možná jste si však všimli, že když přesunete ukazatel myši nad tlačítko, vizuály tlačítka se nezmění. Všechny tyto vizuální interakce jsou definovány šablonou.

S dynamické události a vlastnosti systémy, které poskytuje WPF, můžete sledovat konkrétní vlastnost pro hodnotu a potom změnit styl šablony v případě potřeby. V tomto příkladu budete sledovat <xref:System.Windows.UIElement.IsMouseOver> vlastnost tlačítka. Když je myš nad ovládacím prvkem, styl ** \<Elipsa>** s novou barvou. Tento typ aktivační události se označuje jako *PropertyTrigger*.

Aby to fungovalo, budete muset přidat název ** \<elipsy>,** na které můžete odkazovat. Dejte mu název **backgroundElement**.

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

Dále přidejte <xref:System.Windows.Trigger> nové [controlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) kolekce. Aktivační událost bude `IsMouseOver` sledovat událost `true`pro hodnotu .

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

Dále přidejte ** \<setter>** do ** \<>aktivační události,** která změní **Fill** vlastnost ** \<>elipsy** na novou barvu.

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

Spusťte projekt. Všimněte si, že při přesunutí myši nad tlačítko se změní barva ** \<elipsy>.**

![přejecími myšpřes tlačítko WPF změnit barvu výplně](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>Použití visualstate

Vizuální stavy jsou definovány a spuštěny ovládacím prvkem. Například při přesunutí myši nad ovládací prvek, `CommonStates.MouseOver` stav se aktivuje. Můžete animovat změny vlastností na základě aktuálního stavu ovládacího prvku. V předchozí části ** \<PropertyTrigger>** byl použit ke změně popředí `AliceBlue` tlačítka, `IsMouseOver` když `true`byla vlastnost . Místo toho vytvořte vizuální stav, který animuje změnu této barvy a poskytuje hladký přechod. Další informace o *VisualStates*naleznete [v tématu styly a šablony v WPF](../fundamentals/styles-templates-overview.md#visual-states).

Chcete-li převést ** \<>Vlastnost triggeru** do animovaného vizuálního stavu, nejprve odeberte prvek ** \<ControlTemplate.Triggers>** ze šablony.

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

Dále `CommonStates`v kořenovém ** \<** adresáři grid>šablony ovládacího prvku přidejte prvek ** \<VisualStateManager.VisualStateGroups>** s>** \<VisualStateGroup** pro . Definujte dva `Normal` `MouseOver`stavy a .

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

Všechny animace definované v ** \<visualstate>** jsou použity při aktivaci tohoto stavu. Vytvořte animace pro každý stav. Animace jsou umístěny uvnitř ** \<Storyboard>** element. Další informace o scénářích najdete v [tématu Přehled scénářů](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

- Normální

  Tento stav animuje výplň elipsy a `Background` obnovuje ji na barvu ovládacího prvku.

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- Mouseover

  Tento stav animuje `Background` barvu elipsy `Yellow`na novou barvu: .

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

** \<ControlTemplate>** by nyní měl vypadat takto.

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

Spusťte projekt. Všimněte si, že při pohybu myší nad tlačítkem>barva ** \<elipsy** animovat.

![přejecími myšpřes tlačítko WPF změnit barvu výplně](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>Další kroky

- [Vytvoření stylu ovládacího prvku ve WPF](../fundamentals/styles-templates-create-apply-style.md)
- [Styly a šablony ve WPF](../fundamentals/styles-templates-overview.md)
- [Přehled zdrojů XAML](../fundamentals/xaml-resources-define.md)
