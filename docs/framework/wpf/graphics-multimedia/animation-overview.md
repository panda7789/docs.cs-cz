---
title: Přehled animace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
ms.openlocfilehash: 870fc1d1f02dca7d4488a27385fcfeaec8098ced
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039178"
---
# <a name="animation-overview"></a>Přehled animace

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje výkonnou sadu funkcí grafiky a rozložení, které umožňují vytvářet atraktivní uživatelská rozhraní a odvolat dokumenty. Animace může vytvořit poutavé uživatelské rozhraní ještě více Spectacular a používat. Pouhým animováním barvy pozadí nebo použitím animovaných <xref:System.Windows.Media.Transform>můžete vytvořit výrazné přechody obrazovky nebo poskytnout užitečné vizuální pomůcky.

Tento přehled poskytuje Úvod do animačního systému [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a časování. Zaměřuje se na animaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů pomocí scénářů.

<a name="introducinganimations"></a>

## <a name="introducing-animations"></a>Představení animací

Animace je iluze vytvořená rychlým procházením řady imagí, která se trochu liší od poslední. Mozek navnímanou skupinu obrázků jako jednu měnící scénu. V případě filmu se tato iluze vytváří pomocí kamer, které zaznamenávají mnoho fotografií nebo snímků za sekundu. Když se snímky přehrávají projektorem, zobrazí se v cílové skupině Pohyblivý obrázek.

Animace na počítači je podobná. Například program, který usnadňuje vykreslení obdélníku, může fungovat následovně.

- Program vytvoří časovač.

- Program zkontroluje časovač v nastavených intervalech, aby bylo možné zjistit, kolik času uplynulo.

- Pokaždé, když program zkontroluje časovač, vypočítá aktuální hodnotu neprůhlednosti pro obdélník na základě toho, kolik času uplynulo.

- Program následně aktualizuje obdélník o novou hodnotu a překreslí ho.

Před [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]museli vývojáři Microsoft Windows vytvářet a spravovat svoje vlastní systémy časování nebo používat speciální vlastní knihovny. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje efektivní systém časování, který je vystavený prostřednictvím spravovaného kódu a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a který je hluboko integrovaný do rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Framework. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace usnadňuje animaci ovládacích prvků a dalších grafických objektů.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpracovává veškerou práci na pozadí správy systému časování a efektivně si obrazovku sestavuje. Poskytuje třídy časování, které vám umožní zaměřit se na efekty, které chcete vytvořit, a ne na mechanismy jejich dosažení. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také usnadňuje vytváření vlastních animací tím, že vystaví animační základní třídy, ze kterých vaše třídy mohou dědit, a vytvoří přizpůsobené animace. Tyto vlastní animace získají mnoho výhod pro výkon standardních tříd animace.

<a name="thewpftimingsystem"></a>

## <a name="wpf-property-animation-system"></a>Animační systém vlastností WPF

Pokud pochopíte několik důležitých konceptů, které se týkají časových systémů, můžete je snadno použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animací. Nejdůležitější je, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]animujete objekty použitím animace na jejich jednotlivé vlastnosti. Například chcete-li zvětšit prvek architektury, animace jeho <xref:System.Windows.FrameworkElement.Width%2A> a vlastností <xref:System.Windows.FrameworkElement.Height%2A>. Chcete-li objekt vymizet zobrazením, animaci jeho vlastnosti <xref:System.Windows.UIElement.Opacity%2A>.

Aby vlastnost měla možnosti animace, musí splňovat následující tři požadavky:

- Musí se jednat o vlastnost závislosti.

- Musí patřit do třídy, která dědí z <xref:System.Windows.DependencyObject> a implementuje rozhraní <xref:System.Windows.Media.Animation.IAnimatable>.

- K dispozici musí být kompatibilní typ animace. (Pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] žádný neposkytuje, můžete si vytvořit svoje vlastní. Podívejte se na [Přehled vlastních animací](custom-animations-overview.md).)

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje mnoho objektů, které mají <xref:System.Windows.Media.Animation.IAnimatable> vlastností. Ovládací prvky, jako <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.TabControl>, a také objekty <xref:System.Windows.Controls.Panel> a <xref:System.Windows.Shapes.Shape> dědí z <xref:System.Windows.DependencyObject>. Většina jejich vlastností je vlastností závislosti.

Animace můžete použít skoro kdekoli, což zahrnuje i v šablonách stylů a ovládacích prvků. Animace nemusí být vizuální. můžete animovat objekty, které nejsou součástí uživatelského rozhraní, pokud splňují kritéria, která jsou popsána v této části.

<a name="storyboardwalkthrough"></a>

## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Příklad: Vytvoření prvku v zobrazení a mimo zobrazení

Tento příklad ukazuje, jak použít animaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k animaci hodnoty vlastnosti závislosti. Používá <xref:System.Windows.Media.Animation.DoubleAnimation>, což je typ animace, která generuje <xref:System.Double> hodnoty pro animaci vlastnosti <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Shapes.Rectangle>. V důsledku toho se <xref:System.Windows.Shapes.Rectangle> zesílí a zmizí z pohledu.

První část příkladu vytvoří prvek <xref:System.Windows.Shapes.Rectangle>. Následující postup ukazuje, jak vytvořit animaci a použít ji na vlastnost <xref:System.Windows.UIElement.Opacity%2A> obdélníku.

Následující příklad ukazuje, jak vytvořit prvek <xref:System.Windows.Shapes.Rectangle> v <xref:System.Windows.Controls.StackPanel> v jazyce XAML.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]

Následující příklad ukazuje, jak vytvořit prvek <xref:System.Windows.Shapes.Rectangle> v <xref:System.Windows.Controls.StackPanel> v kódu.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]

<a name="opacity_animation_step1"></a>

### <a name="part-1-create-a-doubleanimation"></a>Část 1: vytvoření DoubleAnimation

Jedním ze způsobů, jak objekt rozmizet a ze zobrazení, je animovat jeho vlastnost <xref:System.Windows.UIElement.Opacity%2A>. Vzhledem k tomu, že vlastnost <xref:System.Windows.UIElement.Opacity%2A> je typu <xref:System.Double>, budete potřebovat animaci, která vytváří dvojité hodnoty. Jedním z těchto animací je <xref:System.Windows.Media.Animation.DoubleAnimation>. <xref:System.Windows.Media.Animation.DoubleAnimation> vytvoří přechod mezi dvěma hodnotami typu Double. Chcete-li zadat počáteční hodnotu, nastavte její vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>. Chcete-li zadat koncovou hodnotu, nastavte její vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.

1. Hodnota neprůhlednosti `1.0` způsobí, že objekt je zcela neprůhledný a hodnota neprůhlednosti `0.0` je zcela neviditelná. Aby se přechod z `1.0` na `0.0` nastavil jeho vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> na `1.0` a vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> na `0.0`. Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.DoubleAnimation> v jazyce XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]

    Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.DoubleAnimation> v kódu.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]

2. Dále je nutné zadat <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animace určuje, jak dlouho trvá přechod od počáteční hodnoty k její cílové hodnotě. Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pět sekund v jazyce XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]

    Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pět sekund v kódu.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]

3. Předchozí kód ukázal animaci, která přechází z `1.0` na `0.0`, což způsobí, že se cílový element rozzvolna od zcela neprůhledný na zcela neviditelný. Chcete-li, aby se element po zobrazení zmizí, nastavte vlastnost <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> animace na hodnotu `true`. Pokud chcete, aby se animace opakovala bez omezení, nastavte její vlastnost <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> na hodnotu <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a vlastnosti <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> v jazyce XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]

    Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnosti v kódu.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]

<a name="opacity_animation_step2"></a>

### <a name="part-2-create-a-storyboard"></a>Část 2: vytvoření scénáře

Chcete-li použít animaci na objekt, vytvořte <xref:System.Windows.Media.Animation.Storyboard> a pomocí vlastností <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené určete objekt a vlastnost, které chcete animovat.

1. Vytvořte <xref:System.Windows.Media.Animation.Storyboard> a přidejte animaci jako podřízenou položku. Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.Storyboard> v jazyce XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]

    Chcete-li vytvořit <xref:System.Windows.Media.Animation.Storyboard> v kódu, deklarujte <xref:System.Windows.Media.Animation.Storyboard> proměnnou na úrovni třídy.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]

    Pak inicializujte <xref:System.Windows.Media.Animation.Storyboard> a přidejte animaci jako podřízenou položku.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]

2. <xref:System.Windows.Media.Animation.Storyboard> musí znát, kde má být animace použita. Pomocí vlastnosti <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> připojené určete objekt, který se má animovat. Následující příklad ukazuje, jak nastavit cílový název <xref:System.Windows.Media.Animation.DoubleAnimation> pro `MyRectangle` v jazyce XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]

    Následující příklad ukazuje, jak nastavit cílový název <xref:System.Windows.Media.Animation.DoubleAnimation>, aby `MyRectangle` v kódu.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]

3. Pomocí vlastnosti <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojeno Určete vlastnost, která se má animovat. Následující příklad ukazuje, jak je animace nakonfigurována pro cílení na vlastnost <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Shapes.Rectangle> v jazyce XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]

    Následující příklad ukazuje, jak je animace nakonfigurována pro cílení na vlastnost <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Shapes.Rectangle> v kódu.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]

Další informace o syntaxi <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> a další příklady najdete v [přehledu scénářů](storyboards-overview.md).

<a name="opacity_animation_step3"></a>

### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Část 3 (XAML): přidružení scénáře k triggeru

Nejjednodušší způsob, jak použít a spustit <xref:System.Windows.Media.Animation.Storyboard> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], je použití triggeru události. V této části se dozvíte, jak přidružit <xref:System.Windows.Media.Animation.Storyboard> k triggeru v jazyce XAML.

1. Vytvořte objekt <xref:System.Windows.Media.Animation.BeginStoryboard> a přidružte k němu scénář. <xref:System.Windows.Media.Animation.BeginStoryboard> je typ <xref:System.Windows.TriggerAction>, který se vztahuje a spustí <xref:System.Windows.Media.Animation.Storyboard>.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]

2. Vytvořte <xref:System.Windows.EventTrigger> a přidejte <xref:System.Windows.Media.Animation.BeginStoryboard> do kolekce <xref:System.Windows.EventTrigger.Actions%2A>. Nastavte vlastnost <xref:System.Windows.EventTrigger.RoutedEvent%2A> <xref:System.Windows.EventTrigger> na směrovanou událost, kterou chcete spustit <xref:System.Windows.Media.Animation.Storyboard>. (Další informace o směrovaných událostech najdete v tématu [Přehled směrovaných událostí](../advanced/routed-events-overview.md).)

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]

3. Přidejte <xref:System.Windows.EventTrigger> do kolekce <xref:System.Windows.FrameworkElement.Triggers%2A> obdélníku.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]

<a name="opacity_animation_step3code"></a>

### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Část 3 (kód): přidružení scénáře k obslužné rutině události

Nejjednodušší způsob, jak použít a spustit <xref:System.Windows.Media.Animation.Storyboard> v kódu, je použití obslužné rutiny události. V této části se dozvíte, jak přidružit <xref:System.Windows.Media.Animation.Storyboard> k obslužné rutině události v kódu.

1. Zaregistrujte se na událost <xref:System.Windows.FrameworkElement.Loaded> obdélníku.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]

2. Deklarujte obslužnou rutinu události. V obslužné rutině události použijte metodu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> pro použití scénáře.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]

### <a name="complete-example"></a>Kompletní příklad

Následující příklad ukazuje, jak vytvořit obdélník, který se v jazyce XAML zesílí a z něj zobrazuje.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]

Následující příklad ukazuje, jak vytvořit obdélník, který se v kódu zesílí a z něj zobrazuje.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]

<a name="animationtypes"></a>

## <a name="animation-types"></a>Typy animací

Vzhledem k tomu, že animace generují hodnoty vlastností, existují různé typy animací pro různé typy vlastností. Chcete-li animovat vlastnost, která přebírá <xref:System.Double>, jako je například vlastnost <xref:System.Windows.FrameworkElement.Width%2A> elementu, použijte animaci, která vytvoří <xref:System.Double> hodnoty. Chcete-li animovat vlastnost, která přebírá <xref:System.Windows.Point>, použijte animaci, která vytváří <xref:System.Windows.Point> hodnoty atd. Z důvodu počtu různých typů vlastností existuje v oboru názvů <xref:System.Windows.Media.Animation> několik tříd animace. Naštěstí se řídí striktní konvencí pojmenování, která usnadňuje rozlišení mezi nimi:

- Animace > *typu*\<

  Označuje se jako animace "od/do/" nebo "základní", tato animace mezi počáteční a cílovou hodnotou nebo přidáním hodnoty posunu k počáteční hodnotě.

  - Chcete-li zadat počáteční hodnotu, nastavte vlastnost from animace.

  - Chcete-li zadat koncovou hodnotu, nastavte vlastnost do vlastnosti animace.

  - Chcete-li zadat hodnotu posunu, nastavte vlastnost Property animace.

  Příklady v tomto přehledu používají animace, protože jsou nejjednodušší pro použití. Animace od/do/podle jsou podrobněji popsány v přehledu animací z/do/podle.

- *typ*\<> AnimationUsingKeyFrames

  Animace klíčových snímků jsou výkonnější než z/do/podle animací, protože můžete zadat libovolný počet cílových hodnot a dokonce řídit metodu interpolace. Některé typy lze animovat pouze pomocí animací klíčových snímků. Animace klíčových snímků jsou podrobně popsané v tématu [Přehled animací klíčových snímků](key-frame-animations-overview.md).

- *typ*\<> AnimationUsingPath

  Animace cest umožňují použít geometrickou cestu, aby bylo možné vytvořit animované hodnoty.

- *typ*\<> AnimationBase

  Abstraktní třída, která při implementaci animuje \<*typ*> Value. Tato třída slouží jako základní třída pro \<*typ*> animace a \<*typ*> třídy AnimationUsingKeyFrames. Musíte se přímo s těmito třídami zabývat pouze v případě, že chcete vytvořit vlastní animace. V opačném případě použijte \<*typ*> animaci nebo klíčového snímku\<*typ*> animace.

Ve většině případů budete chtít použít \<*typ*> třídy animace, jako je například <xref:System.Windows.Media.Animation.DoubleAnimation> a <xref:System.Windows.Media.Animation.ColorAnimation>.

Následující tabulka ukazuje několik běžných typů animací a některé vlastnosti, se kterými se používají.

|Typ vlastnosti|Odpovídající animace Basic (od/do/po)|Odpovídající animace klíčových snímků|Animace odpovídající cesty|Příklad použití|
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Žádné|Animace <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> nebo <xref:System.Windows.Media.GradientStop>.|
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animace <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.Button>.|
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animace <xref:System.Windows.Media.EllipseGeometry.Center%2A> pozice <xref:System.Windows.Media.EllipseGeometry>|
|<xref:System.String>|Žádné|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Žádné|Animace <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> nebo <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Button>.|

<a name="animationsaretimelines"></a>

### <a name="animations-are-timelines"></a>Animace jsou časové osy

Všechny typy animací dědí z třídy <xref:System.Windows.Media.Animation.Timeline>; všechny animace jsou proto specializované typy časových os. <xref:System.Windows.Media.Animation.Timeline> definuje segment času. Můžete určit *chování časování* časové osy: jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, kolikrát se opakuje, a dokonce jak rychle to bude postupovat podle času.

Vzhledem k tomu, že je animace <xref:System.Windows.Media.Animation.Timeline>, představuje také segment času. Animace také počítá výstupní hodnoty tak, jak postupuje podle zadaného segmentu času (nebo <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Jak animace postupuje, nebo "hraje", aktualizuje vlastnost, ke které je přidružena.

Tři často používané vlastnosti časování jsou <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.

#### <a name="the-duration-property"></a>Vlastnost Duration

Jak už jsme uvedli, časová osa představuje segment času. Délka tohoto segmentu je určena <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy, která je obvykle určena pomocí <xref:System.Windows.Duration.TimeSpan%2A> hodnoty. Když časová osa dosáhne konce své doby, dokončila se iterace.

Animace používá vlastnost <xref:System.Windows.Media.Animation.Timeline.Duration%2A> k určení její aktuální hodnoty. Pokud nezadáte hodnotu <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animace, použije se 1 sekunda, což je výchozí hodnota.

Následující syntaxe ukazuje zjednodušenou verzi syntaxe atributu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro vlastnost <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.

*hodiny* `:` *minuty* `:` *sekund*

Následující tabulka ukazuje několik nastavení <xref:System.Windows.Duration> a jejich výsledných hodnot.

|Nastavením|Výsledná hodnota|
|-------------|---------------------|
|0:0: 5.5|5,5 sekund.|
|0:30:5,5|30 minut a 5,5 sekund.|
|1:30:5.5|1 hodina, 30 minut a 5,5 sekund.|

Jedním ze způsobů, jak určit <xref:System.Windows.Duration> v kódu, je použít metodu <xref:System.TimeSpan.FromSeconds%2A> k vytvoření <xref:System.TimeSpan>a pak deklarovat novou <xref:System.Windows.Duration> strukturu pomocí tohoto <xref:System.TimeSpan>.

Další informace o hodnotách <xref:System.Windows.Duration> a úplné syntaxi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] najdete v tématu Struktura <xref:System.Windows.Duration>.

#### <a name="autoreverse"></a>AutoReverse

Vlastnost <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> určuje, zda se časová osa přehrává zpět po dosažení konce jejího <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Pokud nastavíte tuto vlastnost animace na `true`, animace se vrátí po dosažení konce jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>a přehráním z jeho koncové hodnoty zpět na počáteční hodnotu. Ve výchozím nastavení je tato vlastnost `false`.

#### <a name="repeatbehavior"></a>RepeatBehavior

Vlastnost <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> určuje, kolikrát se časová osa hraje. Ve výchozím nastavení mají časová osa počet iterací `1.0`, což znamená, že se pohrají jednou a vůbec se neopakují.

Další informace o těchto vlastnostech a dalších najdete v tématu [Přehled chování časování](timing-behaviors-overview.md).

<a name="applyanimationstoproperty"></a>

## <a name="applying-an-animation-to-a-property"></a>Použití animace na vlastnost

Předchozí části popisují různé typy animací a jejich vlastnosti časování. V této části se dozvíte, jak použít animaci na vlastnost, kterou chcete animovat. objekty <xref:System.Windows.Media.Animation.Storyboard> poskytují jeden způsob, jak použít animace pro vlastnosti. <xref:System.Windows.Media.Animation.Storyboard> je *Časová osa kontejneru* , která poskytuje informace o cílení na animace, které obsahuje.

### <a name="targeting-objects-and-properties"></a>Cílení objektů a vlastností

Třída <xref:System.Windows.Media.Animation.Storyboard> poskytuje <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené vlastnosti. Nastavením těchto vlastností na animaci dáte funkci animace, která se má animovat. Nicméně před tím, než může být animace cílena na objekt, objekt musí obvykle být uveden název.

Přiřazení názvu <xref:System.Windows.FrameworkElement> se liší od přiřazení názvu k objektu <xref:System.Windows.Freezable>. Většina ovládacích prvků a panelů je prvky architektury; avšak většina čistě grafických objektů, jako jsou štětce, transformes a geometrií, jsou objekty Freezable. Pokud si nejste jistí, jestli je typ <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.Freezable>, přečtěte si část **Hierarchie dědičnosti** v příslušné referenční dokumentaci.

- Chcete-li vytvořit <xref:System.Windows.FrameworkElement> cíli animace, přidělte mu název nastavením jeho vlastnosti <xref:System.Windows.FrameworkElement.Name%2A>. V kódu je také nutné použít metodu <xref:System.Windows.FrameworkElement.RegisterName%2A> k registraci názvu elementu se stránkou, do které patří.

- Chcete-li vytvořit objekt <xref:System.Windows.Freezable> cíli animace v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte [direktivu x:Name](../../xaml-services/x-name-directive.md) k přiřazení názvu. V kódu stačí použít metodu <xref:System.Windows.FrameworkElement.RegisterName%2A> k registraci objektu se stránkou, do které patří.

Následující části obsahují příklad pojmenování prvku v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a kódu. Podrobnější informace o pojmenování a cílení najdete v [přehledu scénářů](storyboards-overview.md).

### <a name="applying-and-starting-storyboards"></a>Použití a spouštění scénářů

Pokud chcete začít scénář v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], přidružíte ho k <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> je objekt, který popisuje akce, které se mají provést při výskytu zadané události. Jednou z těchto akcí může být <xref:System.Windows.Media.Animation.BeginStoryboard> akce, kterou použijete k zahájení scénáře. Triggery událostí jsou podobné v konceptu obslužných rutin událostí, protože umožňují určit, jak vaše aplikace reaguje na konkrétní událost. Na rozdíl od obslužných rutin událostí lze triggery událostí plně popsány v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; není vyžadován žádný jiný kód.

Chcete-li spustit <xref:System.Windows.Media.Animation.Storyboard> v kódu, můžete použít <xref:System.Windows.EventTrigger> nebo použít metodu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> třídy <xref:System.Windows.Media.Animation.Storyboard>.

<a name="controllingstoryboards"></a>

## <a name="interactively-control-a-storyboard"></a>Interaktivní řízení scénáře

Předchozí příklad ukázal, jak spustit <xref:System.Windows.Media.Animation.Storyboard>, když dojde k události. Můžete také interaktivně řídit <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění: můžete pozastavit, obnovit, zastavit, pokračovat v jeho období vyplňování, vyhledat a odebrat <xref:System.Windows.Media.Animation.Storyboard>. Další informace a příklad, který ukazuje, jak interaktivně řídit <xref:System.Windows.Media.Animation.Storyboard>, najdete v [přehledu scénářů](storyboards-overview.md).

<a name="fillbehaviorsection"></a>

## <a name="what-happens-after-an-animation-ends"></a>Co se stane po skončení animace?

Vlastnost <xref:System.Windows.Media.Animation.FillBehavior> určuje, jak se časová osa chová, když končí. Ve výchozím nastavení se časová osa spustí <xref:System.Windows.Media.Animation.ClockState.Filling>, když skončí. Animace, která je <xref:System.Windows.Media.Animation.ClockState.Filling> obsahuje konečnou výstupní hodnotu.

<xref:System.Windows.Media.Animation.DoubleAnimation> v předchozím příkladu nekončí, protože jeho vlastnost <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> je nastavena na <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Následující příklad animuje obdélník pomocí podobné animace. Na rozdíl od předchozího příkladu jsou vlastnosti <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> a <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> této animace ponechány na jejich výchozích hodnotách. Proto animace během pěti sekund pokračuje od 1 do 0 a pak se zastaví.

[!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]

[!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
[!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]

Vzhledem k tomu, že se jeho <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> nezměnila z výchozí hodnoty, která je <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, animace uchovává konečnou hodnotu 0, když skončí. Proto <xref:System.Windows.UIElement.Opacity%2A> obdélníku po ukončení animace zůstane na 0. Pokud nastavíte <xref:System.Windows.UIElement.Opacity%2A> obdélníku na jinou hodnotu, váš kód se zdá být neúčinný, protože animace stále ovlivňuje vlastnost <xref:System.Windows.UIElement.Opacity%2A>.

Jedním ze způsobů, jak znovu získat kontrolu nad animovanou vlastností v kódu, je použít metodu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> a zadat pro parametr <xref:System.Windows.Media.Animation.AnimationTimeline> hodnotu null. Další informace a příklad naleznete v tématu [nastavení vlastnosti po animaci pomocí scénáře](how-to-set-a-property-after-animating-it-with-a-storyboard.md).

Všimněte si, že přestože nastavení hodnoty vlastnosti, která má <xref:System.Windows.Media.Animation.ClockState.Active> nebo animace <xref:System.Windows.Media.Animation.ClockState.Filling>, nemá žádný vliv, hodnota vlastnosti se změní. Další informace najdete v [přehledu animace a časování systému](animation-and-timing-system-overview.md).

<a name="databindingAndAnimatingAnimationsSection"></a>

## <a name="data-binding-and-animating-animations"></a>Vytváření datových vazeb a animace animací

Většina vlastností animace může být vázaná na data nebo animována; Můžete například animovat vlastnost <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.DoubleAnimation>. Vzhledem k tomu, jak systém časování funguje, se datové nebo animované animace nechovají podobně jako jiné vázané nebo animované objekty. Pro pochopení jejich chování pomáhá pochopit, co znamená použít animaci na vlastnost.

Podívejte se na příklad v předchozí části, který ukázal, jak animovat <xref:System.Windows.UIElement.Opacity%2A> obdélníku. Když je načten obdélník v předchozím příkladu, použije jeho Trigger události <xref:System.Windows.Media.Animation.Storyboard>. Systém časování vytvoří kopii <xref:System.Windows.Media.Animation.Storyboard> a jeho animace. Tyto kopie jsou zmrazeny (jsou určeny jen pro čtení) a objekty <xref:System.Windows.Media.Animation.Clock> jsou z nich vytvářeny. Tyto hodiny dělají skutečnou práci animování cílových vlastností.

Systém časování vytvoří čas pro <xref:System.Windows.Media.Animation.DoubleAnimation> a použije ho pro objekt a vlastnost, které jsou určeny <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> <xref:System.Windows.Media.Animation.DoubleAnimation>. V tomto případě systém časování použije hodiny na vlastnost <xref:System.Windows.UIElement.Opacity%2A> objektu, který má název "MyRectangle".

I když se pro <xref:System.Windows.Media.Animation.Storyboard>vytvoří i hodiny, hodiny se neaplikují na žádné vlastnosti. Jeho účelem je řídit své podřízené hodiny, hodiny, které jsou vytvořeny pro <xref:System.Windows.Media.Animation.DoubleAnimation>.

Aby animace odrážela změny vazeb a dat animace, je nutné jejich hodiny znovu vygenerovat. Hodiny se negenerují automaticky. Chcete-li, aby animace odrážela změny, proveďte znovu použití scénáře pomocí <xref:System.Windows.Media.Animation.BeginStoryboard> nebo <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody. Když použijete některou z těchto metod, animace se restartuje. V kódu můžete pomocí metody <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> posunout scénář zpátky do jeho předchozí pozice.

Příklad animace vázané na data naleznete v tématu [Ukázka animace Key spline](https://go.microsoft.com/fwlink/?LinkID=160011). Další informace o tom, jak systém animace a časování funguje, najdete v tématu [Přehled systému pro animace a časování](animation-and-timing-system-overview.md).

<a name="otherWaysToAnimateSection"></a>

## <a name="other-ways-to-animate"></a>Další způsoby, jak animovat

Příklady v tomto přehledu ukazují, jak animovat pomocí scénářů. Při použití kódu můžete animovat několika různými způsoby. Další informace naleznete v tématu [Přehled technik animace vlastností](property-animation-techniques-overview.md).

<a name="animation_samples"></a>

## <a name="animation-samples"></a>Ukázky animací

Následující ukázky vám můžou pomáhat začít s přidáváním animací do vašich aplikací.

- [Ukázka cílových hodnot z, do a podle animace](https://go.microsoft.com/fwlink/?LinkID=159988)

  Ukazuje různé nastavení z/na/podle.

- [Ukázka chování časování animace](https://go.microsoft.com/fwlink/?LinkID=159970)

  Ukazuje různé způsoby, jak můžete řídit chování časování animace. Tato ukázka také ukazuje, jak vytvořit datovou cílovou hodnotu animace.

<a name="related_topics"></a>

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Přehled animace a systému časování](animation-and-timing-system-overview.md)|Popisuje, jak systém časování používá třídy <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Clock>, které umožňují vytvářet animace.|
|[Tipy a triky animace](animation-tips-and-tricks.md)|Obsahuje seznam užitečných tipů pro řešení problémů s animacemi, jako je například výkon.|
|[Přehled vlastních animací](custom-animations-overview.md)|Popisuje, jak roztáhnout systém animace pomocí klíčových snímků, tříd animace nebo zpětných volání pro jednotlivá rámce.|
|[Přehled animace od/komu/kým](from-to-by-animations-overview.md)|Popisuje, jak vytvořit animaci, která přechází mezi dvěma hodnotami.|
|[Přehled animací klíčových snímků](key-frame-animations-overview.md)|Popisuje postup vytvoření animace s více cílovými hodnotami, včetně možnosti řízení metody interpolace.|
|[Funkce uvolnění](easing-functions.md)|Vysvětluje, jak použít matematické vzorce pro animace k dosažení realistického chování, například skákající.|
|[Přehled animací cesty](path-animations-overview.md)|Popisuje, jak přesunout nebo otočit objekt podél složité cesty.|
|[Přehled způsobů animace vlastností](property-animation-techniques-overview.md)|Popisuje animace vlastností pomocí scénářů, místních animací, hodin a animací pro jednotlivé snímky.|
|[Přehled scénářů](storyboards-overview.md)|Popisuje způsob použití scénářů s více časovými osami k vytváření složitých animací.|
|[Přehled chování časování](timing-behaviors-overview.md)|Popisuje typy a vlastnosti <xref:System.Windows.Media.Animation.Timeline> používané v animacích.|
|[Přehled událostí časování](timing-events-overview.md)|Popisuje události, které jsou k dispozici na <xref:System.Windows.Media.Animation.Timeline> a objekty <xref:System.Windows.Media.Animation.Clock> pro spouštění kódu v bodech na časové ose, jako je například spuštění, pozastavení, obnovení, přeskočení nebo zastavení.|
|[Témata s postupy](animation-and-timing-how-to-topics.md)|Obsahuje příklady kódu pro použití animací a časových os ve vaší aplikaci.|
|[Postupy: Témata hodin](clocks-how-to-topics.md)|Obsahuje příklady kódu pro použití objektu <xref:System.Windows.Media.Animation.Clock> v aplikaci.|
|[Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)|Obsahuje příklady kódu pro použití animací klíčových snímků ve vaší aplikaci.|
|[Postupy: Témata animace cesty](path-animation-how-to-topics.md)|Obsahuje příklady kódu pro použití animací cest ve vaší aplikaci.|

<a name="reference"></a>

## <a name="reference"></a>Odkaz

- <xref:System.Windows.Media.Animation.Timeline>

- <xref:System.Windows.Media.Animation.Storyboard>

- <xref:System.Windows.Media.Animation.BeginStoryboard>

- <xref:System.Windows.Media.Animation.Clock>
