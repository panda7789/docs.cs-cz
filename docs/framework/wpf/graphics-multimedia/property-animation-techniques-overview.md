---
title: Přehled způsobů animace vlastností
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
ms.openlocfilehash: 032a26788b9097461cb2270e251ca80c56c1c336
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="property-animation-techniques-overview"></a>Přehled způsobů animace vlastností
Toto téma popisuje různé přístupy k animace vlastnosti: scénářů, místní animace, hodiny a animací za snímků.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit, v tomto tématu, měli byste se seznámit s animace základní funkce popsané v [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="summary"></a>   
## <a name="different-ways-to-animate"></a>Různé způsoby, jak animace  
 Vzhledem k tomu, že existuje mnoho různých scénářů pro animace vlastnosti, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje několik přístupů pro animace vlastnosti.  
  
 Pro každý přístup následující tabulka uvádí, zda může být použit jednotlivých instancí, styly, řízení šablony nebo šablony dat; zda lze použít v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; a jestli přístup umožňuje interaktivně řízení animace.  "Jednotlivých instancí" odkazuje na techniku použití animaci nebo storyboard přímo do instance objektu, nikoli v styl, řízení šablony nebo šablony data.  
  
|Animace technika|Scénáře|Podporuje XAML|Interaktivně ovladatelné|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Scénáře animace|Jednotlivých instancí, <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.DataTemplate>|Ano|Ano|  
|Místní animace|Jednotlivých instancí|Ne|Ne|  
|Hodiny animace|Jednotlivých instancí|Ne|Ano|  
|Animace na snímku|Jednotlivých instancí|Ne|Není k dispozici|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>Scénáře animace  
 Použití <xref:System.Windows.Media.Animation.Storyboard> Pokud chcete definovat a použít své animace v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], interaktivně řídit své animace po spuštění, vytvořit komplexní stromu animací nebo animace v <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> nebo <xref:System.Windows.DataTemplate>. Pro objekt tak, aby se animovaný podle <xref:System.Windows.Media.Animation.Storyboard>, musí být <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, nebo se musí použít k nastavení <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Další podrobnosti najdete v tématu [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> , je zvláštním typem kontejneru <xref:System.Windows.Media.Animation.Timeline> poskytující cílení informace pro animace obsahuje. Pro animaci s <xref:System.Windows.Media.Animation.Storyboard>, dokončete následující tři kroky.  
  
1.  Deklarace <xref:System.Windows.Media.Animation.Storyboard> a jeden nebo více animace.  
  
2.  Použití <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> připojené vlastnosti k určení cílového objektu a vlastnost každý animace.  
  
3.  (Pouze kód) Definování <xref:System.Windows.NameScope> pro <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Zaregistrovat názvy objektů k animace s třídou <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>.  
  
4.  Začněte <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Od <xref:System.Windows.Media.Animation.Storyboard> platí animací pro vlastnosti se animace a spustí je. Existují dva způsoby, jak začít <xref:System.Windows.Media.Animation.Storyboard>: můžete použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda poskytované <xref:System.Windows.Media.Animation.Storyboard> třídy, nebo můžete použít <xref:System.Windows.Media.Animation.BeginStoryboard> akce. Jediný způsob, jak animace v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , je použít <xref:System.Windows.Media.Animation.BeginStoryboard> akce. A <xref:System.Windows.Media.Animation.BeginStoryboard> akce mohou být používány <xref:System.Windows.EventTrigger>, vlastnost <xref:System.Windows.Trigger>, nebo <xref:System.Windows.DataTrigger>.  
  
 V následující tabulce jsou uvedeny různých místech kde každý <xref:System.Windows.Media.Animation.Storyboard> začít technika je podporována: jednotlivých instancí, styl, šablony správy a datová šablona.  
  
|Scénáře je spuštěno pomocí...|Jednotlivých instancí|Styl|Šablony správy|Datová šablona|Příklad|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.EventTrigger>|Ano|Ano|Ano|Ano|[Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a vlastnost <xref:System.Windows.Trigger>|Ne|Ano|Ano|Ano|[Spuštění animace při změně hodnoty vlastnosti](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.DataTrigger>|Ne|Ano|Ano|Ano|[Postupy: aktivace animace při změně dat](http://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> – Metoda|Ano|Ne|Ne|Ne|[Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Další informace o <xref:System.Windows.Media.Animation.Storyboard> objekty, najdete [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
## <a name="local-animations"></a>Místní animace  
 Místní animací poskytují pohodlný způsob pro animaci vlastnost závislosti všech <xref:System.Windows.Media.Animation.Animatable> objektu. Místní animací použijte, pokud chcete použít jeden animace do vlastnosti a vy nemusíte interaktivně řízení animace po jeho spuštění. Na rozdíl od <xref:System.Windows.Media.Animation.Storyboard> animace, místní animace můžete animace objekt, který není přidružený <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Nemusíte definovat <xref:System.Windows.NameScope> pro tento typ animace.  
  
 Místní animace lze použít pouze v kódu a nemůže být definovaný ve styly, řízení šablony nebo šablony data. Místní animace nejde kontrolovat interaktivně po jeho spuštění.  
  
 Chcete-li animace pomocí místní animace, proveďte následující kroky.  
  
1.  Vytvoření <xref:System.Windows.Media.Animation.AnimationTimeline> objektu.  
  
2.  Použití <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda objektu, který chcete použít animace <xref:System.Windows.Media.Animation.AnimationTimeline> pro vlastnost, která zadáte.  
  
 Následující příklad ukazuje, jak animace barva šířky a pozadí <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Hodiny animace  
 Použití <xref:System.Windows.Media.MediaPlayer.Clock%2A> objekty, když chcete bez použití animace <xref:System.Windows.Media.Animation.Storyboard> a chcete vytvořit komplexní časování stromy nebo interaktivně řízení animací po spuštění. Hodiny objektů můžete použít pro animaci vlastnost závislosti všech <xref:System.Windows.Media.Animation.Animatable> objektu.  
  
 Nemůžete použít <xref:System.Windows.Media.Animation.Clock> objekty přímo do animace v styly, řídit šablony nebo šablony data. (Systém animace a načasování ve skutečnosti používat <xref:System.Windows.Media.Animation.Clock> objekty, které se použije animaci v styly, šablon ovládacích prvků a šablony data, ale musíte vytvořit ty <xref:System.Windows.Media.Animation.Clock> objekty pro vás z <xref:System.Windows.Media.Animation.Storyboard>. Další informace o vztahu mezi <xref:System.Windows.Media.Animation.Storyboard> objekty a <xref:System.Windows.Media.Animation.Clock> objekty, najdete [animace a přehled systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).)  
  
 Chcete-li použít jeden <xref:System.Windows.Media.Animation.Clock> na vlastnost, proveďte následující kroky.  
  
1.  Vytvoření <xref:System.Windows.Media.Animation.AnimationTimeline> objektu.  
  
2.  Použití <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> metodu <xref:System.Windows.Media.Animation.AnimationTimeline> vytvořit <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3.  Použití <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metoda objektu, který chcete použít animace <xref:System.Windows.Media.Animation.AnimationClock> pro vlastnost zadáte.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.AnimationClock> a použijte ho pro dvě podobné vlastnosti.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Vytvoření stromu časování a používat ho postupné animaci vlastnosti, dokončete následující kroky.  
  
1.  Použití <xref:System.Windows.Media.Animation.ParallelTimeline> a <xref:System.Windows.Media.Animation.AnimationTimeline> objekty, které chcete vytvořit stromu časování.  
  
2.  Použití <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> kořenové <xref:System.Windows.Media.Animation.ParallelTimeline> k vytvoření <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3.  Iterace <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> z <xref:System.Windows.Media.Animation.ClockGroup> a použít jeho podřízené <xref:System.Windows.Media.Animation.Clock> objekty. Pro každou <xref:System.Windows.Media.Animation.AnimationClock> podřízené, použijte <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metoda objektu, který chcete použít animace <xref:System.Windows.Media.Animation.AnimationClock> pro vlastnost zadáte  
  
 Další informace o objektech hodiny najdete v tématu [animace a přehled systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Animace na jednotlivých: Obejít animace a systému časování  
 Tuto metodu použijte, když potřebujete zcela vynechat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému animace. Jedním scénářem, tento přístup je fyziky animací, kde každý krok v animaci vyžaduje objekty, které chcete být přepočítávány podle poslední sadu objekt interakce.  
  
 Jednotlivé snímky animace nemůže být definovaný uvnitř styly, řízení šablony nebo šablony data.  
  
 Pro animaci jednotlivých snímcích, si zaregistrujete <xref:System.Windows.Media.CompositionTarget.Rendering> události objektu, který obsahuje objekty, které chcete animace. Tato metoda obslužné rutiny události získá volá se jednou za snímek. Každý čas, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals trvalou vykreslování data ve vizuálním stromu napříč stromu složení metodu obslužné rutiny událostí je volána.  
  
 V vaší obslužné rutiny událostí proveďte ať výpočty jsou nezbytné, aby vaše efekt animace a nastavte vlastnosti objektů, které chcete animace s těmito hodnotami.  
  
 Získat prezentace čas pro aktuální rámec, <xref:System.EventArgs> přidružen k této události lze převést jako <xref:System.Windows.Media.RenderingEventArgs>, která poskytnout <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> vlastnost, která vám pomůže získat aktuální snímek je vykreslování čas.  
  
 Další informace najdete v tématu <xref:System.Windows.Media.CompositionTarget.Rendering> stránky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Přehled animace a systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
