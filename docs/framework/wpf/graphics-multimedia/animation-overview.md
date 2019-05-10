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
ms.openlocfilehash: e8717ca50f7275e2739be4d4ee5d677e081d552d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615981"
---
# <a name="animation-overview"></a>Přehled animace
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje výkonnou sadu funkcí grafiky a rozložení, které vám umožní vytvářet atraktivní uživatelská rozhraní a atraktivní dokumenty. Animace umožňují přitažlivým uživatelským rozhraním, ještě více efektivními a použitelný. Právě animace barvy pozadí nebo použití animovaného <xref:System.Windows.Media.Transform>, můžete vytvořit obrazovky výrazné přechody nebo poskytují užitečné vizuální prvky.  
  
 Tento přehled poskytuje úvod do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace a časování systému. Zaměřuje se na animace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů s použitím scénářů.  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>Představujeme animace  
 Animace je vytvořený pomocí rychle procházením řadu imagí, každý mírně lišit od poslední dojem. Mozek zjistí skupiny imagí jako jednu změnu scény. V film je tento dojem vytvářejí pomocí kamery, které zaznamenávají mnoho fotografie nebo rámce, každou sekundu. Snímky jsou přehrávat projektoru, cílová skupina zobrazí obrázek přesouvání.  
  
 Animace v počítači je podobná. Například program, který umožňuje kreslení obdélníku fade mimo zobrazení může vypadat takto.  
  
- Program vytvoří časovač.  
  
- Program kontroluje časovače v nastavených intervalech, které chcete zobrazit, kolik času uplynulo.  
  
- Pokaždé, když program kontroluje časovač, vypočítá aktuální hodnotu neprůhlednosti obdélníku závislosti na tom, kolik času uplynulo.  
  
- Program pak aktualizuje s použitím nové hodnoty obdélníku a překreslí ho.  
  
 Před verzí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] vývojáři měli k vytvoření a správě vlastních systémů časování nebo speciální vlastní knihovny. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnuje systém efektivní časování, který je zveřejněný prostřednictvím spravovaného kódu a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a, který se úzce integruje do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraní framework. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace usnadňuje animace ovládacích prvků a jiných grafických objektů.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpracuje veškerou práci pozadí Správa systému časování a efektivně překreslování na obrazovce. Poskytuje třídy časování, které vám umožní zaměřit se na efekty, které chcete vytvořit místo dosažení těchto účinky mechanismu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také umožňuje snadno vytvořit vlastní animace zveřejněním animace základních tříd, ze kterých může dědit třídy, k vytvoření vlastní animace. Tyto vlastní animace získáte mnoho výhod ve výkonu animace standardních tříd.  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>Systém animace vlastností WPF  
 Pokud budete rozumět tomu pár důležitých principů časování systému [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace může být jednodušší použít. Nejdůležitější je, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], animace objektů s použitím animace jejich jednotlivé vlastnosti. Například, chcete-li prvek framework růst, animujete jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti. Chcete-li objekt fade ze zobrazení, animujete jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost.  
  
 Pro vlastnosti a možnosti animace musí splňovat tři následující požadavky:  
  
- Musí být vlastnost závislosti.  
  
- Musíte ho zařadit do třídy, která dědí z <xref:System.Windows.DependencyObject> a implementuje <xref:System.Windows.Media.Animation.IAnimatable> rozhraní.  
  
- K dispozici musí být typ kompatibilní animace. (Pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neposkytne, můžete vytvořit svoje vlastní. Zobrazit [Přehled vlastních animací](custom-animations-overview.md).)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje mnoho objektů, které mají <xref:System.Windows.Media.Animation.IAnimatable> vlastnosti. Ovládací prvky jako například <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.TabControl>a také <xref:System.Windows.Controls.Panel> a <xref:System.Windows.Shapes.Shape> objekty dědit z <xref:System.Windows.DependencyObject>. Většina jejich vlastnosti jsou vlastnosti závislosti.  
  
 Můžete použít animace téměř odkudkoli, která zahrnuje v styly a šablony ovládacích prvků. Animace nemusí být vizuálu. objekty, které nejsou součástí uživatelského rozhraní, pokud splňují kritéria, které jsou popsány v této části lze animovat.  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Příklad: Ujistěte se, elementu Fade do zobrazení  
 Tento příklad ukazuje způsob použití [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace animace změní hodnota vlastnosti závislosti. Použije <xref:System.Windows.Media.Animation.DoubleAnimation>, což je typ animace, který generuje <xref:System.Double> hodnoty pro animaci <xref:System.Windows.UIElement.Opacity%2A> vlastnost <xref:System.Windows.Shapes.Rectangle>. V důsledku toho <xref:System.Windows.Shapes.Rectangle> sníží (zesvětlí) do zobrazení.  
  
 První část v příkladu vytvoří <xref:System.Windows.Shapes.Rectangle> elementu. Následující kroky ukazují, jak vytvořit animaci a použijte ji pro obdélníku <xref:System.Windows.UIElement.Opacity%2A> vlastnost.
  
 Následující ukazuje, jak vytvořit <xref:System.Windows.Shapes.Rectangle> prvek <xref:System.Windows.Controls.StackPanel> v XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 Následující ukazuje, jak vytvořit <xref:System.Windows.Shapes.Rectangle> prvek <xref:System.Windows.Controls.StackPanel> v kódu.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>Část 1: Vytvoření doubleanimation –  
 Jedním ze způsobů, aby element fade do zobrazení je animace jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost. Protože <xref:System.Windows.UIElement.Opacity%2A> vlastnost je typu <xref:System.Double>, budete potřebovat animaci, která vytváří hodnoty double. A <xref:System.Windows.Media.Animation.DoubleAnimation> je jeden takový animace. A <xref:System.Windows.Media.Animation.DoubleAnimation> vytvoří přechod mezi dvěma hodnotami double. Chcete-li určit její výchozí hodnotu, nastavte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost. K určení jeho koncovou hodnotu, nastavíte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost.  
  
1. Hodnota krytí `1.0` stane zcela neprůhledný objekt a hodnotu neprůhlednosti `0.0` umožňuje úplně skrytá. Animace přechod z `1.0` k `0.0` nastavíte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost `1.0` a jeho <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost `0.0`. Následující ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.DoubleAnimation> v XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     Následující ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.DoubleAnimation> v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2. V dalším kroku je nutné zadat <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Animace Určuje, jak dlouho trvá přejděte od počáteční hodnoty cílové hodnoty. Následující ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pět sekund v XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     Následující ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pět sekund v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3. Předchozí kód jsme si ukázali, animace, která změní z `1.0` k `0.0`, což způsobí, že cílový element, která má vyblednout z stane zcela neprůhledný na úplně skrytá. Chcete-li element fade zpět do zobrazení po zmizí, nastavte <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost animace `true`. Chcete-li animaci opakování po neomezenou dobu, nastavte jeho <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Následující ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnosti v XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     Následující ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastností v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>Část 2: Vytvořit scénář  
 Použijte animaci k objektu, vytvořit <xref:System.Windows.Media.Animation.Storyboard> a použít <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené vlastnosti, které chcete zadat objekt a animovat vlastnost.  
  
1. Vytvořte <xref:System.Windows.Media.Animation.Storyboard> a přidat animaci jako jeho podřízených. Následující ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.Storyboard> v XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]    
  
     Chcete-li vytvořit <xref:System.Windows.Media.Animation.Storyboard> v kódu, deklarujte <xref:System.Windows.Media.Animation.Storyboard> proměnné na úrovni třídy.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     Potom inicializujte <xref:System.Windows.Media.Animation.Storyboard> a přidat animaci jako jeho podřízených.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2. <xref:System.Windows.Media.Animation.Storyboard> Musí vědět, kde použít animace. Použití <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> připojené vlastnosti a určit tak objekt, který má animovat. Následující ukazuje, jak nastavit cílový název <xref:System.Windows.Media.Animation.DoubleAnimation> k `MyRectangle` v XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     Následující ukazuje, jak nastavit cílový název <xref:System.Windows.Media.Animation.DoubleAnimation> k `MyRectangle` v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3. Použití <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené vlastnosti k určení vlastností pro animaci. Následující příklad zobrazuje konfiguraci animace k cíli <xref:System.Windows.UIElement.Opacity%2A> vlastnost <xref:System.Windows.Shapes.Rectangle> v XAML.
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     Následující příklad zobrazuje konfiguraci animace k cíli <xref:System.Windows.UIElement.Opacity%2A> vlastnost <xref:System.Windows.Shapes.Rectangle> v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 Další informace o <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> syntaxi a další příklady najdete v článku [přehled scénářů](storyboards-overview.md).  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Část 3 (XAML): Scénář přidružit aktivační události  
 Nejjednodušší způsob, jak použít a začít <xref:System.Windows.Media.Animation.Storyboard> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , je použít aktivační procedura událostí. Tato část ukazuje, jak přidružit <xref:System.Windows.Media.Animation.Storyboard> triggerem v XAML.  
  
1. Vytvoření <xref:System.Windows.Media.Animation.BeginStoryboard> objektu a přidružit vaše scénáře. A <xref:System.Windows.Media.Animation.BeginStoryboard> k typu <xref:System.Windows.TriggerAction> , která se vztahuje a spustí <xref:System.Windows.Media.Animation.Storyboard>.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2. Vytvoření <xref:System.Windows.EventTrigger> a přidejte <xref:System.Windows.Media.Animation.BeginStoryboard> k jeho <xref:System.Windows.EventTrigger.Actions%2A> kolekce. Nastavte <xref:System.Windows.EventTrigger.RoutedEvent%2A> vlastnost <xref:System.Windows.EventTrigger> směrované události, kterou chcete spustit <xref:System.Windows.Media.Animation.Storyboard>. (Další informace o směrované události, najdete v článku [směrovat Přehled událostí](../advanced/routed-events-overview.md).)  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3. Přidat <xref:System.Windows.EventTrigger> k <xref:System.Windows.FrameworkElement.Triggers%2A> kolekce obdélníku.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Část 3 (kód): Scénář přidružit obslužná rutina události  
 Nejjednodušší způsob, jak použít a začít <xref:System.Windows.Media.Animation.Storyboard> v kódu je použití obslužné rutiny události. Tato část ukazuje, jak přidružit <xref:System.Windows.Media.Animation.Storyboard> obslužnou rutinu v kódu.  
  
1. Zaregistrujte se <xref:System.Windows.FrameworkElement.Loaded> události obdélníku.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2. Deklarace obslužné rutiny události. V obslužné rutině události, použijte <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> způsob, jak použít scénáře.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>Kompletní příklad  
 Následující ukazuje, jak vytvořit obdélníku, který se sníží (zesvětlí) do zobrazení v XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 Následující ukazuje, jak vytvořit obdélníku, který se sníží (zesvětlí) do zobrazení v kódu.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>Typy animací  
 Protože animace hodnoty vlastností, existují jiné typy pro typy jiné vlastnosti. Animovat vlastnost, která přijímá <xref:System.Double>, například <xref:System.Windows.FrameworkElement.Width%2A> vlastnost elementu, použijte animaci, která vytváří <xref:System.Double> hodnoty. Animovat vlastnost, která přijímá <xref:System.Windows.Point>, použijte animaci, která vytváří <xref:System.Windows.Point> hodnoty a tak dále. Kvůli řadě různých typech vlastností se několik tříd animace v <xref:System.Windows.Media.Animation> oboru názvů. Naštěstí se řídí přísné zásady vytváření názvů, které usnadňuje jejich rozlišení:  
  
- \<*Typ*> animace  
  
     Známé jako "Od/Komu/kým" nebo "základní" animace, tyto animace mezi počáteční a cílové hodnoty nebo přidáním hodnoty posunu na počáteční hodnotu.  
  
    - Můžete zadat výchozí hodnotu, nastavte vlastnost From animace.  
  
    - Chcete-li zadejte koncovou hodnotu, nastavte vlastnost na animace.  
  
    - K určení hodnoty posunu, nastavte vlastnost By animace.  
  
     Příklady v tomto přehledu použít tyto animace, protože jsou nejjednodušší na používání. Animace od/Komu/kým jsou popsány podrobně v přehledu From/To/By animace.  
  
- \<*Type*>AnimationUsingKeyFrames  
  
     Animace klíčových snímků jsou výkonnější než animace od/Komu/kým, protože můžete zadat libovolný počet cílových hodnot a dokonce i řídit metodu interpolace. Některé typy lze animovat pouze s použitím animací klíčových snímků. Animace klíčových snímků jsou popsány podrobně [přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
- \<*Type*>AnimationUsingPath  
  
     Animace cesty umožňují použití geometrické cesty za účelem vytvoření animovaný hodnot.  
  
- \<*Typ*> AnimationBase  
  
     Abstraktní třídu, která animuje při jeho, implementaci \< *typ*> hodnota. Tato třída slouží jako základní třída pro \< *typ*> animace a \< *typ*> AnimationUsingKeyFrames třídy. Budete muset řešit přímo tyto třídy pouze v případě, že chcete vytvořit vlastní animace. Jinak použijte \< *typ*> animaci nebo klíčového snímku\<*typ*> animace.  
  
 Ve většině případů budete chtít použít \< *typ*> animace třídy, jako například <xref:System.Windows.Media.Animation.DoubleAnimation> a <xref:System.Windows.Media.Animation.ColorAnimation>.  
  
 Následující tabulka ukazuje několik běžných typů animace a některé vlastnosti, které se používají.  
  
|Typ vlastnosti|Odpovídající basic (od/Komu/kým) animace|Odpovídající animace klíčových snímků|Odpovídající animace cesty|Příklad použití|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Žádný|Animace <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> nebo <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animace <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animace <xref:System.Windows.Media.EllipseGeometry.Center%2A> pozici <xref:System.Windows.Media.EllipseGeometry>.|  
|<xref:System.String>|Žádné|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Žádný|Animace <xref:System.Windows.Controls.TextBlock.Text%2A> z <xref:System.Windows.Controls.TextBlock> nebo <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>Jsou časové osy animací  
 Dědí všechny typy animací <xref:System.Windows.Media.Animation.Timeline> třídy; proto všechny animace jsou speciální typy časové osy. A <xref:System.Windows.Media.Animation.Timeline> definuje část času. Můžete zadat *chování časování* časové osy: jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, kolikrát je opakované a dokonce i jak rychlé uvedení postupuje pro něj.  
  
 Protože je animace <xref:System.Windows.Media.Animation.Timeline>, také představuje segment čas. Animace také vypočítá výstupní hodnoty při jejich postupu ale jeho určenému segmentu čas (nebo <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Animace průběhu, nebo "hraje" aktualizuje vlastnost, která je přidružena.  
  
 Jsou tři časování často používané vlastnosti <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.  
  
#### <a name="the-duration-property"></a>Vlastnost doby trvání  
 Jak už jsme zmínili časovou osu reprezentuje segment, který času. Délka tohoto segmentu je určena <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy, což je obvykle určena pomocí <xref:System.Windows.Duration.TimeSpan%2A> hodnotu. Po časové ose dosáhne konce jeho trvání, dokončení iterace.  
  
 Animace používá jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnosti k určení jeho aktuální hodnota. Pokud nezadáte <xref:System.Windows.Media.Animation.Timeline.Duration%2A> hodnotu pro animaci, používá 1 sekundu, což je výchozí hodnota.  
  
 Následující syntaxe znázorňuje zjednodušenou verzi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] atribut syntaxe <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost.  
  
*hodiny* `:` *minut* `:` *sekund*
  
 Následující tabulka ukazuje několik <xref:System.Windows.Duration> nastavení a jejich výsledné hodnoty.  
  
|Nastavení|Výsledná hodnota|  
|-------------|---------------------|  
|0:0:5.5|5.5 sekund.|  
|0:30:5.5|30 minut a 5.5 sekund.|  
|1:30:5.5|1 hodiny, 30 minut a 5.5 sekund.|  
  
 Jeden ze způsobů, jak určit <xref:System.Windows.Duration> v kódu je použít <xref:System.TimeSpan.FromSeconds%2A> metodu pro vytvoření <xref:System.TimeSpan>, potom deklarovat novou <xref:System.Windows.Duration> struktury, která pomocí <xref:System.TimeSpan>.  
  
 Další informace o <xref:System.Windows.Duration> hodnoty a kompletní [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] syntaxe, naleznete v tématu <xref:System.Windows.Duration> struktury.  
  
#### <a name="autoreverse"></a>AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Vlastnost určí, zda je časové ose přehraje zpětně po dosažení konce jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Pokud nastavíte tuto vlastnost animace `true`, animace obrátí po dosažení konce jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, přehrávání koncovou hodnotu zpět na výchozí hodnotu. Ve výchozím nastavení, tato vlastnost je `false`.  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Vlastnost určuje, kolikrát časovou osu přehrávání. Ve výchozím nastavení, mají časové osy nepředstavuje počet iterací z `1.0`, což znamená, že jeden hrají čas a Neopakovat vůbec.  
  
 Další informace o těchto vlastností a další, najdete v článku [přehled chování časování](timing-behaviors-overview.md).  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>Použití animace do vlastnosti  
 Různé typy animací a jejich časování vlastnosti v předchozích částech. Tato část ukazuje, jak použít animace na vlastnost, která má být animován. <xref:System.Windows.Media.Animation.Storyboard> objekty poskytují jedním ze způsobů použití animací na vlastnosti. A <xref:System.Windows.Media.Animation.Storyboard> je *časové osy kontejneru* poskytující cílení informace pro animace obsahuje.  
  
### <a name="targeting-objects-and-properties"></a>Cílení objektů a vlastností  
 <xref:System.Windows.Media.Animation.Storyboard> Třída poskytuje <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené vlastnosti. Nastavením těchto vlastností na animace dáte animace jak animovat. Ale předtím, než animace můžete cílit na objekt, objekt se musí obvykle předávat název.  
  
 Přiřazuje se název, který má <xref:System.Windows.FrameworkElement> se liší od přiřazení název, který má <xref:System.Windows.Freezable> objektu. Většina ovládací prvky a panelů jsou prvky rozhraní; Většina čistě grafických objektů, jako jsou štětce, transformace a geometrie, jsou však zablokovatelných objektů. Pokud si nejste jisti, zda je typ <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.Freezable>, odkazovat **hierarchie dědičnosti** část její referenční dokumentaci.  
  
- Chcete-li <xref:System.Windows.FrameworkElement> cíl animace musíte pojmenovat je tak, že nastavíte její <xref:System.Windows.FrameworkElement.Name%2A> vlastnost. V kódu, musíte taky použít <xref:System.Windows.FrameworkElement.RegisterName%2A> metody pro registraci názvu elementu na stránce, do které patří.  
  
- Chcete-li <xref:System.Windows.Freezable> cíl animace v objektu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít [x: Name – direktiva](../../xaml-services/x-name-directive.md) přiřadit název. V kódu, vám stačí použít <xref:System.Windows.FrameworkElement.RegisterName%2A> metody pro registraci objektu se stránkou, do které patří.  
  
 Následující části poskytují příklad názvy elementu v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a kódu. Podrobnější informace o pojmenování a zacílení, najdete v článku [přehled scénářů](storyboards-overview.md).  
  
### <a name="applying-and-starting-storyboards"></a>Použití a spuštění scénáře  
 Pro spuštění scénáře v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], přidružíte ho <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Je objekt, který popisuje, jaká opatření je třeba provést, když dojde k určité události. Může být jeden z těchto akcí <xref:System.Windows.Media.Animation.BeginStoryboard> akce, který používáte ke spuštění scénář. Aktivační události jsou v principu podobná obslužné rutiny událostí, protože umožňují určit, jak vaše aplikace reaguje na konkrétní události. Na rozdíl od obslužné rutiny událostí, může být aktivační události jsou plně popsány v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; není vyžadován žádný kód.  
  
 Spustit <xref:System.Windows.Media.Animation.Storyboard> v kódu, můžete použít <xref:System.Windows.EventTrigger> nebo použijte <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu <xref:System.Windows.Media.Animation.Storyboard> třídy.  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>Interaktivní řízení scénáře  
 Předchozí příklad ukázal, jak začít <xref:System.Windows.Media.Animation.Storyboard> při výskytu události. Můžete také interaktivní řízení <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění: můžete pozastavit, obnovit, zastavit, přejděte na svůj, hledání a odeberte <xref:System.Windows.Media.Animation.Storyboard>. Další informace a příklad, který ukazuje, jak interaktivní řízení <xref:System.Windows.Media.Animation.Storyboard>, najdete v článku [přehled scénářů](storyboards-overview.md).  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>Co se stane po ukončení animace?  
 <xref:System.Windows.Media.Animation.FillBehavior> Vlastnost určuje, jak časové osy chová při jeho ukončení. Ve výchozím nastavení, spustí časovou osu <xref:System.Windows.Media.Animation.ClockState.Filling> po ukončení. Animace, která je <xref:System.Windows.Media.Animation.ClockState.Filling> uchovává svou hodnotu závěrečný výstup.  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation> v předchozím příkladu nekončí protože jeho <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> je nastavena na <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Následující příklad animuje pomocí podobných animace obdélníku. Na rozdíl od předchozího příkladu <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> a <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnosti této animace jsou ponechány na výchozích hodnotách. Proto se animace postupu z 1 na 0 více než pět sekund a poté se zastaví.  
  
 [!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 Protože jeho <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> nebylo změněno z jeho výchozí hodnotu, která je <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, animace drží konečnou hodnotu 0, při jeho ukončení. Proto <xref:System.Windows.UIElement.Opacity%2A> z obdélník zůstane v umístění 0 po animace končí. Pokud jste nastavili <xref:System.Windows.UIElement.Opacity%2A> obdélníku s jinou hodnotou kódu se nemají žádný vliv, protože animaci je stále by to mělo dopad <xref:System.Windows.UIElement.Opacity%2A> vlastnost.  
  
 Jeden způsob, jak získat ovládací prvek animované vlastnosti v kódu je použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metodu a zadejte hodnotu null pro <xref:System.Windows.Media.Animation.AnimationTimeline> parametr. Další informace a příklad najdete v tématu [nastavit vlastnost Po animaci pomocí scénáře](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
 Všimněte si, že i když nastavení hodnoty vlastnosti, která má <xref:System.Windows.Media.Animation.ClockState.Active> nebo <xref:System.Windows.Media.Animation.ClockState.Filling> animace se neprojeví, změňte hodnotu vlastnosti. Další informace najdete v tématu [animace a časování přehledu systému](animation-and-timing-system-overview.md).  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>Vytváření datových vazeb a animace animace  
 Většina vlastností animace mohou být data vázaná nebo neanimuje; Například lze animovat <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation>. Vzhledem ke způsobu časování systém funguje, ale data, která vázané nebo animovaný animace není chovají se jako další data vázaná nebo neanimuje objekty. Porozumět jejich chování, dobré pochopit, co to znamená použijte animaci k vlastnosti.  
  
 Přečtěte si v příkladu v předchozí části, které jsme si ukázali, jak animovat <xref:System.Windows.UIElement.Opacity%2A> obdélníku. Při načtení obdélníku v předchozím příkladu jeho aktivační událost se vztahuje <xref:System.Windows.Media.Animation.Storyboard>. Časování systému vytvoří kopii <xref:System.Windows.Media.Animation.Storyboard> a jeho animace. Tyto kopie jsou zmražená (jen pro čtení) a <xref:System.Windows.Media.Animation.Clock> z nich jsou vytvořeny objekty. Tyto hodiny vykonávají samotnou práci animace cílové vlastnosti.  
  
 Časování systému vytvoří účtovat poplatky za <xref:System.Windows.Media.Animation.DoubleAnimation> a použije ho k objektu a vlastnost, která je určená <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> z <xref:System.Windows.Media.Animation.DoubleAnimation>. V tomto případě platí časování systému hodiny tak, aby <xref:System.Windows.UIElement.Opacity%2A> vlastnost v objektu, který je pojmenován "MyRectangle."  
  
 I když se vytvoří také hodin pro <xref:System.Windows.Media.Animation.Storyboard>, hodiny neplatí pro žádné vlastnosti. Jeho účelem je potřeba zkontrolovat jeho podřízených hodiny, hodiny, který je vytvořen pro <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Pro animaci tak, aby odrážely změny dat vazby nebo animace musí být znovu vygenerován hodiny. Hodiny nejsou generovány pro vás automaticky. Chcete-li animaci, aby odrážely změny, znovu použít jeho scénáře s využitím <xref:System.Windows.Media.Animation.BeginStoryboard> nebo <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody. Při použití těchto metod, restartuje se animace. V kódu, můžete použít <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metoda shift scénáři zpět na předchozí pozici.  
  
 Příklad dat vázány animace, najdete v části [klíč křivkový animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160011). Další informace o tom, jak systém animace a časování funguje, najdete v části [animace a časování přehledu systému](animation-and-timing-system-overview.md).  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>Další způsoby pro animaci  
 Příklady v tomto přehledu ukazují, jak pro animaci pomocí scénáře. Při použití kódu lze animovat několika jinými způsoby. Další informace najdete v tématu [přehled způsobů animace vlastností](property-animation-techniques-overview.md).  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>Ukázky animace  
 Následující ukázky vám můžou pomoct vám začít přidání animace do vašich aplikací.  
  
- [Od, Komu a kdo ukázkové cílové hodnoty animace](https://go.microsoft.com/fwlink/?LinkID=159988)  
  
     Ukazuje různé od/Komu/kým nastavení.  
  
- [Ukázka chování časování animace](https://go.microsoft.com/fwlink/?LinkID=159970)  
  
     Ukazuje různé způsoby, jak můžete řídit chování časování animace. Tento příklad také ukazuje jak k datům vazby cílové hodnoty animace.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled animace a systému časování](animation-and-timing-system-overview.md)|Popisuje, jak časování systému používá <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Clock> třídy, které vám umožňují vytvářet animace.|  
|[Tipy a triky animace](animation-tips-and-tricks.md)|Obsahuje užitečné tipy pro řešení problémů s použitím animací, jako je například výkon.|  
|[Přehled vlastních animací](custom-animations-overview.md)|Popisuje, jak rozšířit systém animace pomocí klíčových snímků, třídy animace nebo zpětná volání za snímků.|  
|Přehled animace od/komu/kým|Popisuje, jak vytvořit animaci, která přechází mezi dvěma hodnotami.|  
|[Přehled animací klíčových snímků](key-frame-animations-overview.md)|Popisuje, jak vytvořit animaci s více hodnotami Cíl, včetně možnosti řídit metodu interpolace.|  
|[Funkce uvolnění](easing-functions.md)|Vysvětluje, jak použít vašich animacích získáte realistické chování, jako je například skákání matematické vzorce.|  
|[Přehled animací cesty](path-animations-overview.md)|Popisuje, jak se přesunout nebo otočit objekt komplexní cestě.|  
|[Přehled způsobů animace vlastností](property-animation-techniques-overview.md)|Popisuje animace vlastnosti pomocí scénáře, místní animace, hodiny a za snímků animace.|  
|[Přehled scénářů](storyboards-overview.md)|Popisuje způsob použití scénářů s více časové osy k vytvoření složitých animace.|  
|[Přehled chování časování](timing-behaviors-overview.md)|Popisuje <xref:System.Windows.Media.Animation.Timeline> typy a vlastnosti používané ve animace.|  
|[Přehled událostí časování](timing-events-overview.md)|Popisuje události, které jsou k dispozici na <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Clock> objekty pro provádění kódu na místech na časové ose, jako například začít, pozastavení, obnovení, přeskočit nebo zastavit.|  
|[Témata s postupy](animation-and-timing-how-to-topics.md)|Obsahuje příklady kódu pro použití animace a časových os ve vaší aplikaci.|  
|[Postupy: Témata hodin](clocks-how-to-topics.md)|Obsahuje příklady kódu pro použití <xref:System.Windows.Media.Animation.Clock> objektu v aplikaci.|  
|[Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)|Obsahuje příklady kódu pro použití animací klíčových snímků v aplikaci.|  
|[Postupy: Témata animace cesty](path-animation-how-to-topics.md)|Obsahuje příklady kódu pro použití animace cesty ve vaší aplikaci.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>
