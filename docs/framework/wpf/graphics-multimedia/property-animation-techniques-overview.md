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
ms.openlocfilehash: 0b4bf6d4963f32ad83f762fce73c805197ff9c9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181847"
---
# <a name="property-animation-techniques-overview"></a>Přehled způsobů animace vlastností
Toto téma popisuje různé přístupy pro animaci vlastností: scénáře, místní animace, hodiny a animace na snímek.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, měli byste se seznámit se základními funkcemi animace popsanými v [přehledu animací](animation-overview.md).  
  
<a name="summary"></a>
## <a name="different-ways-to-animate"></a>Různé způsoby animace  
 Vzhledem k tomu, že existuje mnoho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] různých scénářů pro animaci vlastností, poskytuje několik přístupů pro animaci vlastností.  
  
 Pro každý přístup následující tabulka označuje, zda jej lze použít na instanci, ve stylech, v šablonách ovládacích prvků nebo v šablonách dat; zda může být [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]použit v ; a zda přístup umožňuje interaktivně ovládat animaci.  "Per-Instance" odkazuje na techniku použití animace nebo scénáře přímo na instance objektu, nikoli ve stylu, šabloně ovládacího prvku nebo šabloně dat.  
  
|Animační technika|Scénáře|Podporuje XAML|Interaktivně ovladatelný|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animace scénáře|Například, <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>,<xref:System.Windows.DataTemplate>|Ano|Ano|  
|Místní animace|Na instanci|Ne|Ne|  
|Animace hodin|Na instanci|Ne|Ano|  
|Animace na snímek|Na instanci|Ne|Není dostupné.|  
  
<a name="storyboard_animations"></a>
## <a name="storyboard-animations"></a>Animace scénáře  
 Použijte <xref:System.Windows.Media.Animation.Storyboard> a, pokud chcete definovat a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]aplikovat animace v aplikaci , interaktivně ovládat animace po jejich spuštění, <xref:System.Windows.Style> <xref:System.Windows.Controls.ControlTemplate> vytvořit <xref:System.Windows.DataTemplate>složitý strom animací nebo animovat v aplikaci . Aby byl objekt <xref:System.Windows.Media.Animation.Storyboard>animován , <xref:System.Windows.FrameworkElement> musí <xref:System.Windows.FrameworkContentElement>být a nebo , <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>musí být použit k nastavení nebo . Další podrobnosti najdete v tématu [Přehled scénářů](storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> je zvláštní typ <xref:System.Windows.Media.Animation.Timeline> kontejneru, který poskytuje informace o cílení pro animace, které obsahuje. Chcete-li animovat pomocí aplikace , <xref:System.Windows.Media.Animation.Storyboard>proveďte následující tři kroky.  
  
1. Deklarujte a jednu <xref:System.Windows.Media.Animation.Storyboard> nebo více animací.  
  
2. Pomocí <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojených vlastností určete cílový objekt a vlastnost každé animace.  
  
3. (Pouze kód) Definujte <xref:System.Windows.NameScope> for <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>a nebo . Zaregistrujte názvy objektů, které <xref:System.Windows.FrameworkElement> chcete <xref:System.Windows.FrameworkContentElement>animovat s tímto nebo .  
  
4. Zahajte . <xref:System.Windows.Media.Animation.Storyboard>  
  
 Začátek <xref:System.Windows.Media.Animation.Storyboard> a aplikuje animace na vlastnosti, které animují, a spustí je. Existují dva způsoby, <xref:System.Windows.Media.Animation.Storyboard>jak začít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> : můžete použít <xref:System.Windows.Media.Animation.Storyboard> metodu poskytnutou <xref:System.Windows.Media.Animation.BeginStoryboard> třídou nebo můžete použít akci. Jediný způsob, jak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] animovat, <xref:System.Windows.Media.Animation.BeginStoryboard> je použít akci. Akci <xref:System.Windows.Media.Animation.BeginStoryboard> lze použít v <xref:System.Windows.EventTrigger>oblasti <xref:System.Windows.Trigger>, <xref:System.Windows.DataTrigger>vlastnost nebo .  
  
 V následující tabulce jsou uvedena <xref:System.Windows.Media.Animation.Storyboard> různá místa, kde je podporována každá technika zahájení: na instanci, styl, šablonu ovládacího prvku a šablonu dat.  
  
|Scénář se začíná používat...|Na instanci|Styl|Šablona ovládacího prvku|Šablona dat|Příklad|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>a<xref:System.Windows.EventTrigger>|Ano|Ano|Ano|Ano|[Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>a nemovitost<xref:System.Windows.Trigger>|Ne|Ano|Ano|Ano|[Spuštění animace při změně hodnoty vlastnosti](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>a a<xref:System.Windows.DataTrigger>|Ne|Ano|Ano|Ano|[Postup: Spuštění animace při změně dat](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|Metoda <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Ano|Ne|Ne|Ne|[Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Další informace <xref:System.Windows.Media.Animation.Storyboard> o objektech naleznete v přehledu [scénářů](storyboards-overview.md).  
  
## <a name="local-animations"></a>Místní animace  
 Místní animace poskytují pohodlný způsob, jak animovat <xref:System.Windows.Media.Animation.Animatable> vlastnost závislosti libovolného objektu. Místní animace použijte, pokud chcete použít jednu animaci na vlastnost a po spuštění není nutné ji interaktivně řídit. Na <xref:System.Windows.Media.Animation.Storyboard> rozdíl od animace může místní animace animovat objekt, který není přidružen k a <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Také není třeba definovat <xref:System.Windows.NameScope> pro tento typ animace.  
  
 Místní animace lze použít pouze v kódu a nelze je definovat ve stylech, šablonách ovládacích prvků nebo šablonách dat. Místní animaci nelze po spuštění interaktivně ovládat.  
  
 Chcete-li animovat pomocí místní animace, proveďte následující kroky.  
  
1. Vytvořte <xref:System.Windows.Media.Animation.AnimationTimeline> objekt.  
  
2. Použijte <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metodu objektu, který chcete animovat použít <xref:System.Windows.Media.Animation.AnimationTimeline> na vlastnost, kterou zadáte.  
  
 Následující příklad ukazuje, jak animovat šířku <xref:System.Windows.Controls.Button>a barvu pozadí .  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Animace hodin  
 Objekty používejte, <xref:System.Windows.Media.MediaPlayer.Clock%2A> pokud chcete animovat bez použití <xref:System.Windows.Media.Animation.Storyboard> a chcete vytvořit složité stromy časování nebo interaktivně řídit animace po jejich spuštění. Objekty Clock můžete použít k animaci <xref:System.Windows.Media.Animation.Animatable> vlastnosti závislosti libovolného objektu.  
  
 Objekty <xref:System.Windows.Media.Animation.Clock> nelze použít přímo k animaci stylů, šablon ovládacích prvků nebo šablon dat. (Systém animace a časování <xref:System.Windows.Media.Animation.Clock> ve skutečnosti používá objekty k animaci stylů, šablon <xref:System.Windows.Media.Animation.Clock> ovládacích prvků <xref:System.Windows.Media.Animation.Storyboard>a šablon dat, ale musí tyto objekty vytvořit z rozhraní . Další informace o vztahu <xref:System.Windows.Media.Animation.Storyboard> mezi <xref:System.Windows.Media.Animation.Clock> objekty a objekty naleznete v tématu [Přehled systému animace a časování](animation-and-timing-system-overview.md).)  
  
 Chcete-li <xref:System.Windows.Media.Animation.Clock> použít jeden vlastnost, proveďte následující kroky.  
  
1. Vytvořte <xref:System.Windows.Media.Animation.AnimationTimeline> objekt.  
  
2. Pomocí <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> metody a <xref:System.Windows.Media.Animation.AnimationTimeline> vytvořte <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3. Použijte <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metodu objektu, který chcete animovat použít <xref:System.Windows.Media.Animation.AnimationClock> na vlastnost, kterou zadáte.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.Animation.AnimationClock> vytvořit a použít na dvě podobné vlastnosti.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Chcete-li vytvořit strom časování a použít jeho animovat vlastnosti, proveďte následující kroky.  
  
1. Použití <xref:System.Windows.Media.Animation.ParallelTimeline> <xref:System.Windows.Media.Animation.AnimationTimeline> a objekty k vytvoření stromu časování.  
  
2. Pomocí <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> kořenového <xref:System.Windows.Media.Animation.ParallelTimeline> adresáře <xref:System.Windows.Media.Animation.ClockGroup>vytvořte .  
  
3. Iterate prostřednictvím <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> <xref:System.Windows.Media.Animation.ClockGroup> a použít <xref:System.Windows.Media.Animation.Clock> jeho podřízené objekty. Pro <xref:System.Windows.Media.Animation.AnimationClock> každé dítě <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> použijte metodu objektu, který chcete <xref:System.Windows.Media.Animation.AnimationClock> animovat, a použijte ji na zadanou vlastnost.  
  
 Další informace o objektech Clock naleznete v tématu [Přehled systému animace a časování](animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Animace na snímek: Obejít animační a časovací systém  
 Tento přístup použijte, pokud potřebujete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zcela obejít animační systém. Jeden scénář pro tento přístup je fyzika animace, kde každý krok v animaci vyžaduje objekty, které mají být přepočítány na základě poslední sadu interakcí objektu.  
  
 Animace pro posuzované na snímek nelze definovat uvnitř stylů, šablon ovládacích prvků nebo šablon dat.  
  
 Chcete-li animovat snímek po <xref:System.Windows.Media.CompositionTarget.Rendering> snímku, zaregistrujte se pro událost objektu, který obsahuje objekty, které chcete animovat. Tato metoda obslužné rutiny události se nazývá jednou za snímek. Pokaždé, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] když zařazuje trvalá data vykreslování ve vizuálním stromu do stromu složení, je volána metoda obslužné rutiny události.  
  
 V obslužné rutině události proveďte všechny výpočty, které jsou nezbytné pro animační efekt, a nastavte vlastnosti objektů, které chcete animovat s těmito hodnotami.  
  
 Chcete-li získat čas prezentace pro <xref:System.EventArgs> aktuální snímek, přidružené <xref:System.Windows.Media.RenderingEventArgs>k této <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> události lze přetypovat jako , které poskytují vlastnost, kterou můžete použít k získání aktuálního rámce vykreslování čas.  
  
 Další informace naleznete <xref:System.Windows.Media.CompositionTarget.Rendering> na stránce.  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
- [Animace a časování přehledu systému](animation-and-timing-system-overview.md)
- [Přehled vlastností závislosti](../advanced/dependency-properties-overview.md)
