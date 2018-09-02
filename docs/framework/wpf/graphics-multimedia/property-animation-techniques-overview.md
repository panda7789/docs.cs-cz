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
ms.openlocfilehash: 438b59aa4aa4213960e0bc3d479a2b949f6d374e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395959"
---
# <a name="property-animation-techniques-overview"></a>Přehled způsobů animace vlastností
Toto téma popisuje různé přístupy k animace vlastností: scénáře, místní animace, hodiny a za snímků animace.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, byste měli znát základní animace funkce popsané v [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="summary"></a>   
## <a name="different-ways-to-animate"></a>Různé způsoby, jak animace  
 Vzhledem k tomu, že existuje mnoho různých scénářů pro animaci vlastnosti, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje několik přístupů pro animaci vlastnosti.  
  
 Pro každý přístup následující tabulka udává, jestli je možné použít jednotlivé instance, styly, šablony ovládacích prvků nebo data šablony. jestli je možné použít v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; a zda tento přístup umožňuje interaktivní řízení animace.  "Za instanci" odkazuje na postup použití animaci nebo scénáře přímo do instance objektu, nikoli ve stylu, šablony ovládacího prvku nebo šablony.  
  
|Animace technika|Scénáře|Podporuje XAML|Může interaktivně ovládat|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animace scénáře|Jednotlivé instance, <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.DataTemplate>|Ano|Ano|  
|Místní animace|Jednotlivé instance|Ne|Ne|  
|Hodiny animace|Jednotlivé instance|Ne|Ano|  
|Na snímku animace|Jednotlivé instance|Ne|Není k dispozici|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>Animacemi scénáře  
 Použití <xref:System.Windows.Media.Animation.Storyboard> když chcete k definování a použití vašeho animací v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], interaktivní řízení animace po spuštění, vytvoření komplexní stromu animace nebo animace v <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> nebo <xref:System.Windows.DataTemplate>. Animovat pomocí objektu <xref:System.Windows.Media.Animation.Storyboard>, musí být <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, nebo musí být použit k nastavení <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Další podrobnosti najdete v tématu [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> je speciální typ kontejneru <xref:System.Windows.Media.Animation.Timeline> poskytující cílení informace pro animace obsahuje. Pro animaci s <xref:System.Windows.Media.Animation.Storyboard>, proveďte následující tři kroky.  
  
1.  Deklarace <xref:System.Windows.Media.Animation.Storyboard> a jeden nebo více animace.  
  
2.  Použití <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> připojené vlastnosti k určení cílového objektu a vlastnost každou animaci.  
  
3.  (Pouze kód) Definování <xref:System.Windows.NameScope> pro <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Registrace názvy objektů pro animaci s ním <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>.  
  
4.  Začněte <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Začíná <xref:System.Windows.Media.Animation.Storyboard> animace se vztahuje na vlastnosti, animace a spustí je. Existují dva způsoby, jak začít <xref:System.Windows.Media.Animation.Storyboard>: můžete použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody poskytované <xref:System.Windows.Media.Animation.Storyboard> třídy, nebo můžete použít <xref:System.Windows.Media.Animation.BeginStoryboard> akce. Jediný způsob, jak animovat v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , je použít <xref:System.Windows.Media.Animation.BeginStoryboard> akce. A <xref:System.Windows.Media.Animation.BeginStoryboard> akce lze použít v <xref:System.Windows.EventTrigger>, vlastnost <xref:System.Windows.Trigger>, nebo <xref:System.Windows.DataTrigger>.  
  
 V následující tabulce jsou uvedeny na různých místech kde každý <xref:System.Windows.Media.Animation.Storyboard> začít technikou je podporováno: jednotlivé instance, styl, šablony ovládacího prvku a šablony.  
  
|Scénář je nezačali používat...|Jednotlivé instance|Styl|Šablony ovládacího prvku|Datové šablony|Příklad|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.EventTrigger>|Ano|Ano|Ano|Ano|[Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a vlastnosti <xref:System.Windows.Trigger>|Ne|Ano|Ano|Ano|[Spuštění animace při změně hodnoty vlastnosti](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.DataTrigger>|Ne|Ano|Ano|Ano|[Postupy: spuštění animace při změně dat](https://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> – Metoda|Ano|Ne|Ne|Ne|[Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Další informace o <xref:System.Windows.Media.Animation.Storyboard> objekty, najdete [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
## <a name="local-animations"></a>Místní animace  
 Místní animace poskytují pohodlný způsob, jak animovat vlastnost závislosti žádné <xref:System.Windows.Media.Animation.Animatable> objektu. Místní animace použijte, pokud chcete použít jeden animace do vlastnosti a není nutné interaktivní řízení animace po jeho spuštění. Na rozdíl od <xref:System.Windows.Media.Animation.Storyboard> animace, místní animace lze animovat objekt, který není spojen s <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Také není nutné definovat <xref:System.Windows.NameScope> pro tento typ animace.  
  
 Místní animace se dá použít jenom v kódu a nemůže být definován v styly, šablony ovládacích prvků nebo datové šablony. Místní animace nemůže ovlivnit interaktivně po jeho spuštění.  
  
 Pro animaci, pomocí místní animace, proveďte následující kroky.  
  
1.  Vytvoření <xref:System.Windows.Media.Animation.AnimationTimeline> objektu.  
  
2.  Použití <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody objektu, který má být animován použít <xref:System.Windows.Media.Animation.AnimationTimeline> na vlastnost, která zadáte.  
  
 Následující příklad ukazuje, jak animovat barva šířku a na pozadí <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Hodiny animace  
 Použití <xref:System.Windows.Media.MediaPlayer.Clock%2A> objektů, pokud chcete animovat bez použití <xref:System.Windows.Media.Animation.Storyboard> a chcete vytvořit komplexní časový stromy nebo po spuštění interaktivní řízení animací. Objekty Clock můžete použít pro animaci vlastnosti závislosti žádné <xref:System.Windows.Media.Animation.Animatable> objektu.  
  
 Nemůžete použít <xref:System.Windows.Media.Animation.Clock> objekty přímo pro animaci ve stylech, řídit šablony nebo šablony. (Ve skutečnosti používá animace a časování systému <xref:System.Windows.Media.Animation.Clock> objekty animace v styly, šablony ovládacích prvků a šablon dat, ale musíte vytvořit tyto <xref:System.Windows.Media.Animation.Clock> objekty pro vás z <xref:System.Windows.Media.Animation.Storyboard>. Další informace o vztahu mezi <xref:System.Windows.Media.Animation.Storyboard> objekty a <xref:System.Windows.Media.Animation.Clock> objekty, najdete [animace a časování přehledu systému](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).)  
  
 Chcete-li použít jediné <xref:System.Windows.Media.Animation.Clock> na vlastnost, proveďte následující kroky.  
  
1.  Vytvoření <xref:System.Windows.Media.Animation.AnimationTimeline> objektu.  
  
2.  Použití <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> metodu <xref:System.Windows.Media.Animation.AnimationTimeline> k vytvoření <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3.  Použití <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metody objektu, který má být animován použít <xref:System.Windows.Media.Animation.AnimationClock> vlastnosti, které zadáte.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.AnimationClock> a použít ji pro dvě podobné vlastnosti.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Vytvoření stromu časování a jeho použití animovat vlastnosti, proveďte následující kroky.  
  
1.  Použití <xref:System.Windows.Media.Animation.ParallelTimeline> a <xref:System.Windows.Media.Animation.AnimationTimeline> objekty pro vytvoření stromu časování.  
  
2.  Použití <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> kořenové <xref:System.Windows.Media.Animation.ParallelTimeline> k vytvoření <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3.  Iterovat přes <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> z <xref:System.Windows.Media.Animation.ClockGroup> a použít jeho dceřiný <xref:System.Windows.Media.Animation.Clock> objekty. Pro každou <xref:System.Windows.Media.Animation.AnimationClock> podřízené, použijte <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metody objektu, který má být animován použít <xref:System.Windows.Media.Animation.AnimationClock> zadáte vlastnosti  
  
 Další informace o objekty Clock, najdete v článku [animace a časování přehledu systému](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Na snímku animace: Obejít animace a časování systému  
 Tuto metodu použijte, když budete chtít úplně obejít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace systému. Jeden scénář pro tento přístup je fyzika animace, kde každý krok v animaci vyžaduje objekty být přepočítány podle poslední sadu interakce s objekty.  
  
 Na snímku animace není možné definovat uvnitř styly, šablony ovládacích prvků nebo datové šablony.  
  
 Pro animaci jednotlivých snímcích, zaregistrujete <xref:System.Windows.Media.CompositionTarget.Rendering> události objektu, který obsahuje objekty, které má být animován. Tato metoda obslužné rutiny události volána jednou pro každý snímek. Pokaždé, když, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals se nazývá trvalý vykreslování data ve vizuálním stromu ve stromové struktuře kompozice metodu obslužné rutiny události.  
  
 V obslužné rutině událostí proveďte jakékoli výpočty jsou nezbytné pro vaše animace a nastavit vlastnosti objektů, které má být animován s těmito hodnotami.  
  
 Získat prezentace času pro aktuální rámec <xref:System.EventArgs> přidružený k tomuto událostí můžete přetypovat jako <xref:System.Windows.Media.RenderingEventArgs>, které poskytují <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> vlastnost, která vám umožní získat aktuální rámec v vykreslování čas.  
  
 Další informace najdete v tématu <xref:System.Windows.Media.CompositionTarget.Rendering> stránky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Přehled animace a systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
