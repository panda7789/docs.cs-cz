---
title: "Přehled animace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
caps.latest.revision: "73"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15eeb27d493cd1138b0d3d41b55a57228a226a11
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="animation-overview"></a>Přehled animace
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje výkonnou sadu funkcí grafika a rozložení, které umožňují vytvářet atraktivní uživatelská rozhraní a přitažlivými dokumentů. Animace můžete nastavit atraktivní uživatelské rozhraní i více spectacular a dá se použít. Právě animace barvu pozadí nebo použití animovaný <xref:System.Windows.Media.Transform>, můžete vytvořit přechody výrazné obrazovky nebo poskytují užitečné vizuální upozornění.  
  
 Tento přehled obsahuje úvod do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace a časování systému. Zaměřuje se na animace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů s použitím scénářů.  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>Úvod animace  
 Animace je dojem vytvořený rychle cyklického řadu bitové kopie se každý mírně lišit od poslední. Mozku zjistí skupiny bitové kopie jako jeden změna scény. V filmy je tato iluzi vytvořili pomocí kamery, které zaznamenávají mnoho fotografií nebo rámce, každou sekundu. Snímky jsou přehrávat projektoru, cílová skupina zobrazí obrázek přesouvání.  
  
 Animace v počítači je podobný. Například může program, který slouží kreslení obdélníku Objevování mimo zobrazení práce následujícím způsobem.  
  
-   Program vytvoří časovač.  
  
-   Program zkontroluje časovač ve stanovených intervalech, které chcete zobrazit, kolik času uplynul.  
  
-   Pokaždé, když program zkontroluje časovač, vypočítá aktuální hodnota neprůhlednosti pro rámeček založené na jak dlouho uplynul.  
  
-   Program pak aktualizuje rámeček se nová hodnota a překreslí ho.  
  
 Před verzí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] vývojáři museli vytvářet a spravovat vlastní systémy časování a použít speciální vlastní knihovny. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zahrnuje efektivní časování systému, který je zveřejněný prostřednictvím spravovaného kódu a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a který je úzce integrována do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]animace usnadňuje animace ovládací prvky a další grafické objekty.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zpracovává všechny pracovní servisní Správa časování systému a efektivně překreslování obrazovky. Poskytuje třídy časování, které vám umožní soustředit se na důsledky, které chcete vytvořit, místo mechanismů dosažení těchto účinky. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také umožňuje snadno vytvářet své vlastní animace vystavení animace základní třídy, ze kterých může dědit vlastnosti třídy, k vytvoření vlastní animace. Tato vlastní animace získáte mnoho výkonnostních výhod třídy standardní animace.  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>WPF vlastnost animace systému  
 Pokud budete rozumět tomu pár důležitých principů systému časování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace může být snazší použít. Nejdůležitější předpokládají, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], animace objektů použitím animace na jejich jednotlivé vlastnosti. Například aby element framework růst, můžete animace jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti. Chcete-li objekt zmizí ze zobrazení, animace jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost.  
  
 Pro vlastnost, která má animace možnosti musí splňovat následující tři požadavky:  
  
-   Musí být vlastnost závislosti.  
  
-   Musíte ho zařadit do třídy, která dědí z <xref:System.Windows.DependencyObject> a implementuje <xref:System.Windows.Media.Animation.IAnimatable> rozhraní.  
  
-   K dispozici musí být typu kompatibilní animace. (Pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nenabízí, můžete vytvořit vlastní. Najdete v článku [vlastní animace přehled](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsahuje mnoho objektů, které mají <xref:System.Windows.Media.Animation.IAnimatable> vlastnosti. Ovládací prvky jako například <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.TabControl>a také <xref:System.Windows.Controls.Panel> a <xref:System.Windows.Shapes.Shape> objekty dědí <xref:System.Windows.DependencyObject>. Většina jejich vlastnosti jsou vlastnosti závislosti.  
  
 Můžete použít animací téměř odkudkoli, včetně v styly a šablon ovládacích prvků. Animace nemusí být visual; můžete animace objektů, které nejsou součástí uživatelského rozhraní, pokud splňují kritéria, která jsou popsané v této části.  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Příklad: Ujistěte se, Objevování Element směřující zobrazení  
 Tento příklad ukazuje, jak používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace animace hodnota vlastnosti závislosti. Použije <xref:System.Windows.Media.Animation.DoubleAnimation>, což je typ animace, který generuje <xref:System.Double> hodnoty pro animaci <xref:System.Windows.UIElement.Opacity%2A> vlastnost <xref:System.Windows.Shapes.Rectangle>. V důsledku toho <xref:System.Windows.Shapes.Rectangle> zmenšuje směřující zobrazení.  
  
 První část příkladu vytvoří <xref:System.Windows.Shapes.Rectangle> elementu. Kroky, které ukazují, jak vytvořit animace a použijte ho pro obdélníku <xref:System.Windows.UIElement.Opacity%2A> vlastnost.
  
 Následující ukazuje, jak vytvořit <xref:System.Windows.Shapes.Rectangle> element v <xref:System.Windows.Controls.StackPanel> v jazyce XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 Následující ukazuje, jak vytvořit <xref:System.Windows.Shapes.Rectangle> element v <xref:System.Windows.Controls.StackPanel> v kódu.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>Část 1: Vytvoření DoubleAnimation  
 Jedním ze způsobů k nastavení vzhledu elementu objevovat a deaktivovat zobrazení je animace jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost. Protože <xref:System.Windows.UIElement.Opacity%2A> vlastnost je typu <xref:System.Double>, budete potřebovat, který produkuje dvojité hodnoty animace. A <xref:System.Windows.Media.Animation.DoubleAnimation> je jeden takový animace. A <xref:System.Windows.Media.Animation.DoubleAnimation> vytvoří přechod mezi dvěma hodnotami double. Určit její počáteční hodnotu, nastavíte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost. Určit její koncovou hodnotu, nastavíte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost.  
  
1.  Hodnota krytí `1.0` díky objekt úplně neprůhledných a hodnota krytí `0.0` je úplně skrytá. Na přechod animace z `1.0` k `0.0` nastavíte jeho <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> vlastnost `1.0` a jeho <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost `0.0`. Následující ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.DoubleAnimation> v jazyce XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     Následující ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.DoubleAnimation> v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2.  Dále je nutné zadat <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Animace Určuje, jak dlouho trvá přechod od jeho výchozí hodnotu na hodnotu cílové. Následující ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pět sekund v jazyce XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     Následující ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pět sekund v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3.  Předchozí kód vám ukázal, animace, která přechází z `1.0` k `0.0`, což způsobí, že cíl elementu, který chcete vykreslit z zcela neprůhledný na úplně skrytá. Chcete-li element objevovat zpět do zobrazení po zmizí, nastavte <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost animace v `true`. Chcete-li animace opakování po neomezenou dobu, nastavte jeho <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Následující ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnosti v jazyce XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     Následující ukazuje, jak nastavit <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastností v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>Část 2: Vytvoření scénáře  
 Chcete-li použít animace do objektu, musíte vytvořit <xref:System.Windows.Media.Animation.Storyboard> a použít <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> připojené vlastnosti, které chcete zadat objekt a vlastností pro animaci.  
  
1.  Vytvořte <xref:System.Windows.Media.Animation.Storyboard> a jako jeho podřízených přidejte animace. Následující ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.Storyboard> v jazyce XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]    
  
     Chcete-li vytvořit <xref:System.Windows.Media.Animation.Storyboard> v kódu deklarovat <xref:System.Windows.Media.Animation.Storyboard> proměnné na úrovni třídy.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     Potom inicializujte <xref:System.Windows.Media.Animation.Storyboard> a jako jeho podřízených přidejte animace.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2.  <xref:System.Windows.Media.Animation.Storyboard> Musí vědět, kde má být použít animace. Použití <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> připojené vlastnosti a určit tak objekt, který má animace. Následující ukazuje, jak nastavit název cílové <xref:System.Windows.Media.Animation.DoubleAnimation> k `MyRectangle` v jazyce XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     Následující ukazuje, jak nastavit název cílové <xref:System.Windows.Media.Animation.DoubleAnimation> k `MyRectangle` v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3.  Použití <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> připojené vlastnosti k určení vlastností pro animaci. Následující příklad zobrazuje konfiguraci animace k cíli <xref:System.Windows.UIElement.Opacity%2A> vlastnost <xref:System.Windows.Shapes.Rectangle> v jazyce XAML.
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     Následující příklad zobrazuje konfiguraci animace k cíli <xref:System.Windows.UIElement.Opacity%2A> vlastnost <xref:System.Windows.Shapes.Rectangle> v kódu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 Další informace o <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> syntaxe a další příklady najdete v tématu [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Část 3 (XAML): Přidružení scénáři s aktivační událost  
 Nejjednodušší způsob, jak použít a spusťte <xref:System.Windows.Media.Animation.Storyboard> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , je použít aktivační události. V této části ukazuje, jak přidružit <xref:System.Windows.Media.Animation.Storyboard> se aktivační událostí v jazyce XAML.  
  
1.  Vytvoření <xref:System.Windows.Media.Animation.BeginStoryboard> objektu a přidružit vaše scénáře. A <xref:System.Windows.Media.Animation.BeginStoryboard> je typ <xref:System.Windows.TriggerAction> , platí a spustí <xref:System.Windows.Media.Animation.Storyboard>.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2.  Vytvoření <xref:System.Windows.EventTrigger> a přidejte <xref:System.Windows.Media.Animation.BeginStoryboard> k jeho <xref:System.Windows.EventTrigger.Actions%2A> kolekce. Nastavte <xref:System.Windows.EventTrigger.RoutedEvent%2A> vlastnost <xref:System.Windows.EventTrigger> směrované události, který chcete spustit <xref:System.Windows.Media.Animation.Storyboard>. (Další informace o směrované události najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).)  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3.  Přidat <xref:System.Windows.EventTrigger> k <xref:System.Windows.FrameworkElement.Triggers%2A> kolekce rámečku.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Část 3 (kód): Přidružení Storyboard obslužnou rutinu  
 Nejjednodušší způsob, jak použít a spusťte <xref:System.Windows.Media.Animation.Storyboard> v kódu je použití obslužné rutiny události. V této části ukazuje, jak přidružit <xref:System.Windows.Media.Animation.Storyboard> obslužnou rutinu v kódu.  
  
1.  Zaregistrovat <xref:System.Windows.FrameworkElement.Loaded> událostí rámečku.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2.  Deklarujte obslužné rutiny události. V obslužné rutině, použijte <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda použít scénáři.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>Kompletní příklad  
 Následující ukazuje, jak vytvořit obdélníku, která vykreslí směřující zobrazení v jazyce XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 Následující ukazuje, jak vytvořit obdélníku, která vykreslí směřující zobrazení v kódu.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>Typy animace  
 Protože animací generovat hodnoty vlastností, animace různé typy existovat různých typech vlastností. Pro animaci vlastnost, která přebírá <xref:System.Double>, například <xref:System.Windows.FrameworkElement.Width%2A> vlastnost elementu, použijte animace, která vytváří <xref:System.Double> hodnoty. Pro vlastnost, která přebírá animaci <xref:System.Windows.Point>, použijte animace, která vytváří <xref:System.Windows.Point> hodnoty a tak dále. Kvůli řadě různých typech vlastností, nejsou k dispozici několik tříd animace v <xref:System.Windows.Media.Animation> oboru názvů. Naštěstí podle striktní zásady vytváření názvů, který usnadňuje rozlišit mezi nimi:  
  
-   \<*Typ*> animace  
  
     Označuje jako "Z/do nebo By" nebo "základní" animace, tyto animace mezi počáteční a cílové hodnoty nebo přidáním hodnoty posunu na jeho výchozí hodnotu.  
  
    -   Můžete zadat výchozí hodnotu, nastavte vlastnost From animace.  
  
    -   Chcete-li určit koncovou hodnotu, nastavte vlastnost na animace.  
  
    -   Chcete-li zadat hodnoty posunu, nastavte vlastnost By animace.  
  
     Příklady v tomto přehledu použít tyto animací, protože jsou Nejjednodušším způsobem. From/k/podle animací jsou podrobně popsané v v přehledu From/To/By animace.  
  
-   \<*Typ*> AnimationUsingKeyFrames  
  
     Klíčových snímků animace jsou výkonnější než ze/k/podle animací, protože můžete zadat libovolný počet cílové hodnoty a řídit i jejich interpolace metoda. Některé typy můžete animované pouze s klíčových snímků animace. Klíčových snímků animace jsou podrobně popsány v [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   \<*Typ*> AnimationUsingPath  
  
     Cesta animací umožňují použití geometrickou cesta za účelem vytvoření animovaný hodnoty.  
  
-   \<*Typ*> AnimationBase  
  
     Abstraktní třída, která při implementaci, animuje \< *typ*> hodnota. Tato třída slouží jako základní třída pro \< *typ*> animace a \< *typ*> AnimationUsingKeyFrames třídy. Je nutné pracovat přímo s tyto třídy pouze v případě, že chcete vytvořit vlastní animace. Jinak použijte \< *typ*> animace nebo @keyframe, které určuje\<*typ*> animace.  
  
 Ve většině případů budete chtít použít \< *typ*> animace třídy, jako například <xref:System.Windows.Media.Animation.DoubleAnimation> a <xref:System.Windows.Media.Animation.ColorAnimation>.  
  
 Následující tabulka ukazuje několik běžných typů animace a některé vlastnosti, pomocí kterých se používají.  
  
|Typ vlastnosti|Odpovídající animace basic (z/do nebo podle)|Odpovídající klíčových snímků animace|Odpovídající cesta animace|Příklad použití|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Žádné|Animace <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> nebo <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animace <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animace <xref:System.Windows.Media.EllipseGeometry.Center%2A> umístit z <xref:System.Windows.Media.EllipseGeometry>.|  
|<xref:System.String>|Žádné|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Žádné|Animace <xref:System.Windows.Controls.TextBlock.Text%2A> z <xref:System.Windows.Controls.TextBlock> nebo <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>Animace jsou časové osy  
 Dědí všechny typy animace <xref:System.Windows.Media.Animation.Timeline> třídy; proto všechny animace jsou speciální typy časové osy. A <xref:System.Windows.Media.Animation.Timeline> definuje segment času. Můžete zadat *časování chování* časové osy: jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, kolikrát je opakovaný a to i v tom, jak rychlý čas hodnoty pro ni.  
  
 Protože je animace <xref:System.Windows.Media.Animation.Timeline>, také představuje segment čas. Animace také vypočítá výstupní hodnoty jako hodnoty, když jeho zadaný segment čas (nebo <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Jako animace postupuje, nebo "hraje" aktualizuje vlastnosti, který je přidružen.  
  
 Jsou tři vlastnosti často používaných časování <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.  
  
#### <a name="the-duration-property"></a>Vlastnost doba trvání  
 Jak jsme uvedli časové osy představuje segment času. Je dáno tohoto segmentu <xref:System.Windows.Media.Animation.Timeline.Duration%2A> časové osy, které je obvykle pomocí <xref:System.Windows.Duration.TimeSpan%2A> hodnotu. Když termín dosáhne konce jeho trvání, dokončil iterace.  
  
 Animace používá jeho <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnosti k určení jeho aktuální hodnotu. Pokud nezadáte <xref:System.Windows.Media.Animation.Timeline.Duration%2A> hodnotu pro animace, používá 1 sekundu, což je výchozí hodnota.  
  
 Následující syntaxe znázorňuje zjednodušenou verzi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] atribut syntaxe <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost.  
  
*čas* `:` *minut* `:` *sekund*
  
 Následující tabulka uvádí několik <xref:System.Windows.Duration> nastavení a jejich výsledných hodnot.  
  
|Nastavení|Výsledná hodnota|  
|-------------|---------------------|  
|0:0:5.5|verzi 5.5 sekund.|  
|0:30:5.5|30 minut a verzi 5.5 sekund.|  
|1:30:5.5|1 hodinu, 30 minut, a verzi 5.5 sekund.|  
  
 Jeden ze způsobů, jak určit <xref:System.Windows.Duration> v kódu má používat <xref:System.TimeSpan.FromSeconds%2A> metodu pro vytvoření <xref:System.TimeSpan>, pak deklarovat nové <xref:System.Windows.Duration> struktury, pomocí které <xref:System.TimeSpan>.  
  
 Další informace o <xref:System.Windows.Duration> hodnoty a kompletní [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] syntaxe, najdete v článku <xref:System.Windows.Duration> struktura.  
  
#### <a name="autoreverse"></a>AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Vlastnost určí, zda je termín přehraje zpětné po jeho dosáhne konce své <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Pokud nastavíte tuto vlastnost animace na `true`, animace obrátí po jeho dosáhne konce své <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, přehrává z jeho koncovou hodnotu zpět na výchozí hodnotu. Ve výchozím nastavení, tato vlastnost je `false`.  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Vlastnost určuje, kolikrát hraje časové osy. Ve výchozím nastavení, časové osy mít iterace `1.0`, což znamená, že jeden hrají čas a neopakujte vůbec.  
  
 Další informace o těchto vlastností a ostatní uživatele, najdete v článku [časování chování přehled](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>Použití animace do vlastnosti  
 V předchozích částech popisují různé typy animací a jejich vlastnosti časování. Tato část uvádí, jak se má použít pro vlastnost, kterou chcete animace animace. <xref:System.Windows.Media.Animation.Storyboard>objekty zadat jeden způsob, jak použít animace do vlastnosti. A <xref:System.Windows.Media.Animation.Storyboard> je *časová osa kontejneru* poskytující cílení informace pro animace obsahuje.  
  
### <a name="targeting-objects-and-properties"></a>Cílení na objekty a vlastnosti  
 <xref:System.Windows.Media.Animation.Storyboard> Třída poskytuje <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> přidružené vlastnosti. Nastavením těchto vlastností na animace se zjistit animace co animace. Ale předtím, než animace, můžete vybrat objekt, objekt je obvykle třeba věnovat, název.  
  
 Název přiřazení <xref:System.Windows.FrameworkElement> se liší od přiřazení název, který <xref:System.Windows.Freezable> objektu. Většina ovládacích prvků a panelů jsou elementy framework; Většina čistě grafické objekty, například štětce, transformace a geometrie, ale jsou zmrazitelné objekty. Pokud si nejste jisti, zda je typ <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.Freezable>, naleznete **hierarchie dědičnosti** část jeho referenční dokumentaci.  
  
-   Chcete-li <xref:System.Windows.FrameworkElement> animace cíl, můžete zadat název nastavením jeho <xref:System.Windows.FrameworkElement.Name%2A> vlastnost. V kódu, musíte také použít <xref:System.Windows.FrameworkElement.RegisterName%2A> metody pro registraci s hledanou stránkou, do které patří název elementu.  
  
-   Chcete-li <xref:System.Windows.Freezable> objektu cíl animace v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít [x: Name – direktiva](../../../../docs/framework/xaml-services/x-name-directive.md) přiřadit název. V kódu právě používáte <xref:System.Windows.FrameworkElement.RegisterName%2A> metody pro registraci s hledanou stránkou, ke kterému patří objekt.  
  
 Uveďte příklad názvy elementu v následujících částech [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a kód. Podrobnější informace o pojmenování a cílení na najdete v tématu [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="applying-and-starting-storyboards"></a>Použití a spuštění scénářů  
 Ke spuštění scénáře v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], přidružíte <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Je objekt, který popisuje, jaké akce se má provést při zadané události. Může být jeden z těchto akcí <xref:System.Windows.Media.Animation.BeginStoryboard> akce, která se používá ke spuštění vaše scénáře. Aktivační události jsou v principu podobná obslužné rutiny událostí, protože ty umožňují určit, jak bude vaše aplikace reagovat na určité události. Na rozdíl od obslužné rutiny událostí, může být podrobně popsány v aktivační události [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; není třeba žádný další kód.  
  
 Spuštění <xref:System.Windows.Media.Animation.Storyboard> v kódu, můžete použít <xref:System.Windows.EventTrigger> nebo použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu <xref:System.Windows.Media.Animation.Storyboard> – třída.  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>Interaktivně řízení scénáře  
 Předchozí příklad ukázal, jak začít <xref:System.Windows.Media.Animation.Storyboard> při výskytu události. Můžete také interaktivně řídit <xref:System.Windows.Media.Animation.Storyboard> po zahájení: můžete pozastavit, pokračovat, zastavit, přechodu na jeho výplně období, Hledat a odebrat <xref:System.Windows.Media.Animation.Storyboard>. Další informace a příklad, který ukazuje, jak interaktivně řízení <xref:System.Windows.Media.Animation.Storyboard>, najdete v článku [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>Co se stane po ukončení animace?  
 <xref:System.Windows.Media.Animation.FillBehavior> Vlastnost určuje, jak časové osy chová při jeho ukončení. Ve výchozím nastavení, spustí časové osy <xref:System.Windows.Media.Animation.ClockState.Filling> při ukončení. Animace, která je <xref:System.Windows.Media.Animation.ClockState.Filling> obsahuje jeho hodnota závěrečný výstup.  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation> v předchozím příkladu na konci protože jeho <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> je nastavena na <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Následující příklad animuje obdélníku pomocí podobné animace. Na rozdíl od předchozí příklad <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> a <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnosti této animace jsou ponechány na jejich výchozí hodnoty. Proto animace hodnoty z 1 na 0, více než pět sekund a poté se zastaví.  
  
 [!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 Protože jeho <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> nebyl změněn z jeho výchozí hodnotu, která je <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, animace obsahuje ho konečná hodnota 0, pokud ho ukončí. Proto <xref:System.Windows.UIElement.Opacity%2A> z obdélníku zůstane v umístění 0 po animace ukončí. Pokud nastavíte <xref:System.Windows.UIElement.Opacity%2A> obdélníku s jinou hodnotou kódu pravděpodobně mít žádný vliv, protože stále ovlivňuje animace <xref:System.Windows.UIElement.Opacity%2A> vlastnost.  
  
 Je možné znovu získat kontrolu animovaný vlastnosti v kódu použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda a zadejte hodnotu null pro <xref:System.Windows.Media.Animation.AnimationTimeline> parametr. Další informace a příklady naleznete v tématu [vlastnost po animace ho nastavit s scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
 Všimněte si, že, i když nastavení hodnotu vlastnosti, která má <xref:System.Windows.Media.Animation.ClockState.Active> nebo <xref:System.Windows.Media.Animation.ClockState.Filling> animace se zobrazí mít žádný vliv, změňte hodnotu vlastnosti. Další informace najdete v tématu [animace a přehled systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>Datové vazby a animace animace  
 Většina animace vlastnosti mohou být data svázaný nebo animovaný; Například můžete animace <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation>. Kvůli způsobu práce časování systému, ale data, která vázané nebo animovaný animací nefungují jako další data tak, svázaný nebo animovaný objekty. Zjistit jejich chování pomáhá pochopit, co znamená použití animace do vlastnosti.  
  
 Najdete v příkladu v předchozím oddílu, který vám ukázal, jak animace <xref:System.Windows.UIElement.Opacity%2A> obdélník. Při načítání obdélníku v předchozím příkladu platí jeho aktivační událost <xref:System.Windows.Media.Animation.Storyboard>. Systém časování vytvoří kopii <xref:System.Windows.Media.Animation.Storyboard> a jeho animace. Tyto kopie zmrazené (jen pro čtení) a <xref:System.Windows.Media.Animation.Clock> vytvoření objektů z nich. Tyto hodiny vykonávají samotnou práci animace cílové vlastnosti.  
  
 Systém časování vytvoří hodiny pro <xref:System.Windows.Media.Animation.DoubleAnimation> a použije je tento objekt a vlastnost, která je zadána <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> z <xref:System.Windows.Media.Animation.DoubleAnimation>. V takovém případě časování systému se vztahuje na hodiny <xref:System.Windows.UIElement.Opacity%2A> vlastnost v objektu, který má název "MyRectangle."  
  
 I když hodiny, které se také vytvoří pro <xref:System.Windows.Media.Animation.Storyboard>, hodiny nebude použito žádné vlastnosti. Jejím účelem je k jeho podřízených hodiny, hodiny, která jsou vytvořena pro řízení <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Pro animace tak, aby odrážela vazba nebo animace změny dat musí být znovu vygenerovat jeho hodiny. Hodiny nejsou znovu vygenerovat pro vás automaticky. Aby se projevily změny animace, použijte jeho storyboard pomocí <xref:System.Windows.Media.Animation.BeginStoryboard> nebo <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda. Při práci s některým z těchto metod, animace se restartuje. V kódu, můžete použít <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metoda se posunou scénáři zpět na předchozí pozici.  
  
 Příklad dat vázaný animace, najdete v části [klíč křivkový animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160011). Další informace o fungování animace a načasování systému najdete v tématu [animace a přehled systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>Další způsoby animace  
 Příklady v tomto přehledu ukazují, jak animace pomocí scénářů. Při použití kódu můžete animace několik jinými způsoby. Další informace najdete v tématu [vlastnost animace techniky přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>Animace – ukázky  
 Následující ukázky můžete spustit přidání animace do vaší aplikace.  
  
-   [Z, k a ukázkové hodnoty Target animace](http://go.microsoft.com/fwlink/?LinkID=159988)  
  
     Ukazuje různé z/do nebo pomocí nastavení.  
  
-   [Ukázka chování časování animace](http://go.microsoft.com/fwlink/?LinkID=159970)  
  
     Ukazuje různé způsoby, můžete řídit chování časování animace. Tento příklad také ukazuje jak k datům vázat hodnotu cílové animace.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Animace a časování přehled systému](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)|Popisuje, jak se používá systém časování <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Clock> třídy, které vám umožňují vytvořit animace.|  
|[Animace tipy a triky](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)|Uvádí užitečné tipy pro řešení problémů s animací, jako je například výkon.|  
|[Přehled vlastní animace](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)|Popisuje, jak rozšířit systém animace pomocí klíčových snímků, animace třídy nebo zpětná volání za rámce.|  
|Přehled animace od/komu/kým|Popisuje postup vytvoření animace, která přechází mezi dvěma hodnotami.|  
|[Přehled animací jednotlivých klíč](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)|Popisuje postup vytvoření s více hodnotami Cíl, včetně možnosti řízení metodu interpolace animace.|  
|[Funkce usnadnění](../../../../docs/framework/wpf/graphics-multimedia/easing-functions.md)|Vysvětluje, jak chcete použít pro své animace realistické chování, například skákání matematické vzorce.|  
|[Přehled animací cesta](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)|Popisuje, jak přesunout nebo otočení objektu podél komplexní cesty.|  
|[Vlastnost animace techniky – přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)|Popisuje vlastnost animace pomocí scénářů, místní animací, hodiny a animací za snímků.|  
|[Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)|Popisuje, jak vytvořit komplexní animace pomocí scénářů s více časových os.|  
|[Přehled chování časování](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)|Popisuje <xref:System.Windows.Media.Animation.Timeline> typy a vlastnosti používané ve animace.|  
|[Přehled událostí časování](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)|Popisuje, k dispozici na události <xref:System.Windows.Media.Animation.Timeline> a <xref:System.Windows.Media.Animation.Clock> objekty pro spouštění kódu v bodech v časové ose, jako třeba začít, pozastavení, obnovení, přeskočit nebo zastavit.|  
|[Postupy: témata](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)|Obsahuje příklady kódu pro použití animace a časové osy v aplikaci.|  
|[Postupy: témata hodiny](../../../../docs/framework/wpf/graphics-multimedia/clocks-how-to-topics.md)|Obsahuje příklady kódu pro použití <xref:System.Windows.Media.Animation.Clock> objektu ve vaší aplikaci.|  
|[Postupy: témata klíč rámce](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)|Obsahuje příklady kódu pro použití animací jednotlivých klíč ve vaší aplikaci.|  
|[Postupy: témata cesta animace](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)|Obsahuje příklady kódu pro použití cesty animací ve vaší aplikaci.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>
