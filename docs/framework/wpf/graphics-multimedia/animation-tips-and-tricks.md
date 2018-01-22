---
title: Tipy a triky animace
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
- troubleshooting [WPF], animation
- animations [WPF], FillBehavior property
- troubleshooting animation [WPF]
- animating objects [WPF], troubleshooting
- animation tips and tricks [WPF]
- tips and tricks [WPF], animation
- performance troubleshooting [WPF], animation
- animations [WPF], use of system resources
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 210f8ff8840f579d352cc579f80f38488b998c5a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="animation-tips-and-tricks"></a>Tipy a triky animace
Při práci s animace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], existuje několik tipy a triky, které můžete své animace poskytují lepší výkon a ušetřit před.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Obecné problémy  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animace pozice posuvníku nebo posuvníku se zablokuje se  
 Pokud animace polohy posuvníku nebo posuvníku pomocí animace, která má <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (výchozí hodnota), uživatel už nebude moci přesunout posuvník nebo posuvníku. Je to způsobeno i v případě, že animace skončila, je stále přepsání základní hodnotu pro vlastnost target. Pokud chcete zastavit animace z přepsání aktuální hodnotu vlastnosti, odeberte jej nebo poskytněte <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Další informace a příklady naleznete v tématu [vlastnost po animace ho nastavit s scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animace výstup animace nemá žádný vliv  
 Objekt, který je výstup jiné animace nemůže animace. Například, pokud používáte <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> pro animaci <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> z <xref:System.Windows.Media.RadialGradientBrush> k <xref:System.Windows.Media.SolidColorBrush>, nelze animace všechny vlastnosti <xref:System.Windows.Media.RadialGradientBrush> nebo <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Nelze změnit hodnotu vlastnosti po jeho animace  
 V některých případech může vypadat, že po je byla animovaný, i po ukončení animace nelze změnit hodnotu vlastnosti. Je to způsobeno i v případě, že animace skončila, je stále přepsání základní hodnotu vlastnosti. Pokud chcete zastavit animace z přepsání aktuální hodnotu vlastnosti, odeberte jej nebo poskytněte <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Další informace a příklady naleznete v tématu [vlastnost po animace ho nastavit s scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Změna časové osy nemá žádný vliv  
 I když většina <xref:System.Windows.Media.Animation.Timeline> vlastnosti jsou animatable a mohou být data vázány, změna hodnoty vlastností aktivní <xref:System.Windows.Media.Animation.Timeline> zdá se, že nemají žádný vliv. Je to způsobeno, když <xref:System.Windows.Media.Animation.Timeline> je spuštěno, vytvoří kopii systému časování <xref:System.Windows.Media.Animation.Timeline> a používá k vytvoření <xref:System.Windows.Media.Animation.Clock> objektu. Úprava původní nemá žádný vliv na kopie systému.  
  
 Pro <xref:System.Windows.Media.Animation.Timeline> tak, aby odrážely změny, musí být jeho hodiny se znova vygeneroval a používá k nahrazení dříve vytvořenou hodiny. Hodiny nejsou znovu vygenerovat pro vás automaticky. Následuje několik způsobů, jak použít časové osy:  
  
-   Pokud časovou osu nebo patří do <xref:System.Windows.Media.Animation.Storyboard>, můžete použít se projevily změny opakováním jeho scénáře použití <xref:System.Windows.Media.Animation.BeginStoryboard> nebo <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda. To má za následek straně také restartování animace. V kódu, můžete použít <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metoda posunut scénáři zpět na předchozí pozici.  
  
-   Pokud jste provedli animace přímo na vlastnost pomocí <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda, volání <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda znovu a předejte ji animace, která byla změněna.  
  
-   Pokud pracujete se přímo na úrovni hodiny, vytvořit a použít novou sadu hodiny a použít je k nahradí předchozí sadu generovaného hodiny.  
  
 Další informace o časové osy a hodiny najdete v tématu [animace a přehled systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop nebude fungovat dle očekávání  
 V určitých časech při nastavování <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.FillBehavior.Stop> zdá se, že nemají žádný vliv, jako např. kdy jeden animace "předá" do jiného protože má <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> nastavení <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.TranslateTransform> Bude animovaný přesunout <xref:System.Windows.Shapes.Rectangle> kolem <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Příklady v této části použijte k předvedení několik případů předchozí objekty kde <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost není chovat podle očekávání jeho.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior = "Stop" a HandoffBehavior s více animací  
 Někdy se zdá být jakoby animace ignoruje jeho <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost, když je nahrazena druhý animace. Následující příklad, který vytvoří dva trvat <xref:System.Windows.Media.Animation.Storyboard> objekty a použije je k animace stejné <xref:System.Windows.Media.TranslateTransform> v předchozím příkladu.  
  
 První <xref:System.Windows.Media.Animation.Storyboard>, `B1`, animuje <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> od 0 do 350, který přesune pixelů obdélníku 350 vpravo. Když se dosáhne konce jeho trvání animace a zastaví přehrávání, <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost vrátí k původní hodnoty, 0. V důsledku toho rámeček přesune do pravé 350 pixelů a pak přejde zpět na původní pozici.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Druhý <xref:System.Windows.Media.Animation.Storyboard>, `B2`, také animuje <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost stejné <xref:System.Windows.Media.TranslateTransform>. Protože pouze <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnost animace v tomto <xref:System.Windows.Media.Animation.Storyboard> není nastaven, animace používá aktuální hodnota vlastnosti je animuje jako jeho výchozí hodnotu.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Pokud kliknete na druhý tlačítko při první <xref:System.Windows.Media.Animation.Storyboard> je přehrávání, můžou očekávat následující chování:  
  
1.  První storyboard končí a odešle rámeček zpět na původní pozici, protože má animace <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2.  Druhý scénář se projeví a animuje od aktuální pozice, který je teď 0, na 500.  
  
 **Je to, že není co se stane, ale.** Místo toho rámeček není přejít zpět; pokračuje posunutí doprava. Je to způsobeno druhý animace používá aktuální hodnotu první animace jako jeho výchozí hodnotu a animuje z této hodnoty na 500. Když druhý animace nahradí první, protože <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> se používá, <xref:System.Windows.Media.Animation.FillBehavior> prvního nezáleží animace.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior a dokončení události  
 Další příklady ukazují další scénáře, ve kterém <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> zdá se, že nemají žádný vliv. Znovu v příkladu používá scénáře pro animaci <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> od 0 do 350. Ale tentokrát příklad zaregistruje <xref:System.Windows.Media.Animation.Timeline.Completed> událostí.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> Obslužné rutiny události spustí jiný <xref:System.Windows.Media.Animation.Storyboard> , který animuje stejnou vlastnost od aktuální hodnoty na 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Tady je kód, který definuje druhý <xref:System.Windows.Media.Animation.Storyboard> jako prostředek.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Při spuštění <xref:System.Windows.Media.Animation.Storyboard>, by se dalo očekávat <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> pro animaci od 0 do 350, pak se vraťte na hodnotu 0 až se dokončí (protože má <xref:System.Windows.Media.Animation.FillBehavior> nastavení <xref:System.Windows.Media.Animation.FillBehavior.Stop>) a pak použije animaci z 0 na 500. Místo toho <xref:System.Windows.Media.TranslateTransform> animuje od 0 do 350 a pak na 500.  
  
 Důvodem pořadí, v jakém [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vyvolává události a protože hodnoty vlastností v mezipaměti a nejsou přepočítat, pokud je vlastnost zrušena. <xref:System.Windows.Media.Animation.Timeline.Completed> Událostí je zpracován jako první, protože byla aktivována časovou osou kořenové (první <xref:System.Windows.Media.Animation.Storyboard>). V tomto okamžiku <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost stále vrátí jeho animovaný hodnotu, protože nebyla dosud zrušena. Druhý <xref:System.Windows.Media.Animation.Storyboard> používá hodnotu uloženou v mezipaměti jako jeho výchozí hodnotu a začne animace.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Výkon  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Animace nadále spustit po přechodu ze stránky  
 Když přejdete směrem od <xref:System.Windows.Controls.Page> obsahující běžící animace, tyto animace bude nadále hrát až <xref:System.Windows.Controls.Page> je uvolnění z paměti. V závislosti na navigační systému, kterou používáte, stránky, který přejdete směrem od může zůstat v paměti na neomezenou dobu, celou dobu využívání prostředků s jeho animace. Toto je nejvíce patrné, pokud stránka obsahuje nepřetržitém provozu animace ("vedlejším").  
  
 Z tohoto důvodu je vhodné použít <xref:System.Windows.FrameworkElement.Unloaded> událostí k odebrání animací, když přejdete mimo stránku.  
  
 Existují různé způsoby, jak odebrat animace. Následující postupy slouží k odebrání animace, které patří do <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Chcete-li odebrat <xref:System.Windows.Media.Animation.Storyboard> jste začali s aktivační signál události najdete v tématu [postup: Odeberte scénáře](http://msdn.microsoft.com/library/7fe39531-de2f-46a0-a69f-b783d04235ee).  
  
-   Při odebrání pomocí kódu <xref:System.Windows.Media.Animation.Storyboard>, najdete v článku <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> metoda.  
  
 Další postup může použít bez ohledu na to, jak byla animace spuštěna.  
  
-   Chcete-li odebrat animací z konkrétní vlastnosti, použijte <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metoda. Určete vlastnost probíhá animovaný jako první parametr a `null` jako druhý. Tato akce odstraní všechny hodiny animace z vlastnosti.  
  
 Další informace o různých způsobech animace vlastnosti najdete v tématu [vlastnost animace techniky přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Pomocí tvoří HandoffBehavior využívá systémové prostředky  
 Když použijete <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>, nebo <xref:System.Windows.Media.Animation.AnimationClock> vlastnost pomocí <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>, jakékoliv <xref:System.Windows.Media.Animation.Clock> objekty dříve přidružené k této vlastnosti nadále využívat systémové prostředky; časování systém není automaticky odeberte tyto hodiny.  
  
 Aby se zabránilo problémům s výkonem při aplikování velký počet hodiny pomocí <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, po dokončení, byste měli odebrat skládání hodiny z animovaný vlastnosti. Chcete-li odebrat hodiny několika způsoby.  
  
-   Chcete-li odebrat všechny hodiny z vlastnosti, použijte <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> nebo <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metodu animovaný objektu. Určete vlastnost probíhá animovaný jako první parametr a `null` jako druhý. Tato akce odstraní všechny hodiny animace z vlastnosti.  
  
-   Odebrat konkrétní <xref:System.Windows.Media.Animation.AnimationClock> ze seznamu hodiny, použijte <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnost <xref:System.Windows.Media.Animation.AnimationClock> načíst <xref:System.Windows.Media.Animation.ClockController>, potom zavolejte <xref:System.Windows.Media.Animation.ClockController.Remove%2A> metodu <xref:System.Windows.Media.Animation.ClockController>. To se obvykle provádí <xref:System.Windows.Media.Animation.Clock.Completed> obslužné rutiny události pro hodinami. Všimněte si, že pouze kořenové hodiny se dá nastavit podle <xref:System.Windows.Media.Animation.ClockController>; <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnost podřízené hodiny vrátí `null`. Všimněte si také, že <xref:System.Windows.Media.Animation.Clock.Completed> událost nebude volána, pokud je účinné trvání hodiny navždy.  V takovém případě bude uživatel muset při volání <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Toto je primárně problém pro animací na objekty, které mají dlouhou životnost.  Pokud je objekt uvolnění z paměti, jeho hodiny také bude odpojen a uklizeny.  
  
 Další informace o objektech hodiny najdete v tématu [animace a přehled systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
