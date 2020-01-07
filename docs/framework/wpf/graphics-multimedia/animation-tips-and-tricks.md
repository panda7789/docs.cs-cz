---
title: Tipy a triky animace
ms.date: 03/30/2017
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
ms.openlocfilehash: ef59631663e6cf1c98adfed77a2dbdb6ca124fa1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636026"
---
# <a name="animation-tips-and-tricks"></a>Tipy a triky animace
Při práci s animacemi v prostředí WPF je k dispozici několik tipů a štychů, díky kterým můžete animace lépe vylepšit a ušetřit tak frustrace.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Běžné problémy  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animování pozice posuvníku nebo posuvníku, který ho zablokuje  
 Pokud animujete polohu posuvníku nebo posuvníku pomocí animace, která má <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (výchozí hodnota), uživatel už nebude moct přesunout posuvník nebo posuvník. To je způsobeno tím, že i když animace skončila, stále Přepisuje základní hodnotu vlastnosti target. Chcete-li zastavit animaci před přepsáním aktuální hodnoty vlastnosti, odeberte ji nebo ji poskytněte <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Další informace a příklad naleznete v tématu [nastavení vlastnosti po animaci pomocí scénáře](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animování výstupu animace nemá žádný vliv.  
 Nelze animovat objekt, který je výstupem jiné animace. Pokud například použijete <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> k animaci <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> ze <xref:System.Windows.Media.RadialGradientBrush> na <xref:System.Windows.Media.SolidColorBrush>, nemůžete animovat žádné vlastnosti <xref:System.Windows.Media.RadialGradientBrush> nebo <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Po animaci nejde změnit hodnotu vlastnosti.  
 V některých případech se může zdát, že po ukončení animace nemůžete změnit hodnotu vlastnosti. To je způsobeno tím, že i když se animace ukončí, je stále přepsána základní hodnota vlastnosti. Chcete-li zastavit animaci před přepsáním aktuální hodnoty vlastnosti, odeberte ji nebo ji poskytněte <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Další informace a příklad naleznete v tématu [nastavení vlastnosti po animaci pomocí scénáře](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Změna časové osy nemá žádný vliv.  
 I když je většina <xref:System.Windows.Media.Animation.Timeline> vlastností animovaná a může být vázaná na data, změna hodnot vlastností aktivní <xref:System.Windows.Media.Animation.Timeline> zřejmě nemá žádný vliv. To je způsobeno tím, že při zahájení <xref:System.Windows.Media.Animation.Timeline> vytvoří systém časování kopii <xref:System.Windows.Media.Animation.Timeline> a použije ji k vytvoření objektu <xref:System.Windows.Media.Animation.Clock>. Úprava původního objektu nemá žádný vliv na kopírování systému.  
  
 Aby se u <xref:System.Windows.Media.Animation.Timeline> projevily změny, musí se jejich hodiny znovu vygenerovat a použít k nahrazení dříve vytvořených hodin. Hodiny se negenerují automaticky. Následující je několik způsobů, jak použít změny časové osy:  
  
- Pokud je časová osa nebo patří do <xref:System.Windows.Media.Animation.Storyboard>, můžete se odrážet změny tím, že se jejich scénář znovu použije pomocí <xref:System.Windows.Media.Animation.BeginStoryboard> nebo <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody. To má vedlejší účinek také k restartování animace. V kódu můžete použít metodu <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> k posunutí scénáře zpátky na předchozí pozici.  
  
- Pokud jste animaci použili přímo na vlastnost pomocí metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>, zavolejte metodu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> znovu a předejte ji do animace, která byla upravena.  
  
- Pokud pracujete přímo na úrovni hodin, vytvořte a použijte novou sadu hodin a použijte ji k nahrazení předchozí sady generovaných hodin.  
  
 Další informace o časových osách a hodinách najdete v tématu [Přehled systému pro animace a časování](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior. stop nefunguje podle očekávání.  
 Při nastavení vlastnosti <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> tak, aby <xref:System.Windows.Media.Animation.FillBehavior.Stop> zřejmě nedocházelo k žádnému účinku, například když se jedna animace "neuplatní" na jinou, protože má <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> nastavení <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.TranslateTransform> bude animovaný a přesune <xref:System.Windows.Shapes.Rectangle> kolem <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Příklady v této části používají předchozí objekty k předvedení několika případů, kdy se vlastnost <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> neprojeví, jak byste ji mohli očekávat.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior = "Stop" a HandoffBehavior s více animacemi  
 Někdy se zdá, že animace ignoruje svou vlastnost <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>, když je nahrazena druhou animací. Proveďte následující příklad, který vytvoří dva objekty <xref:System.Windows.Media.Animation.Storyboard> a použije je k animaci stejného <xref:System.Windows.Media.TranslateTransform>, jak je znázorněno v předchozím příkladu.  
  
 První <xref:System.Windows.Media.Animation.Storyboard>, `B1`, animuje vlastnost <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> z 0 do 350, což přesouvá obdélník 350 pixelů vpravo. Když animace dosáhne konce své doby trvání a zastaví se přehrávání, vlastnost <xref:System.Windows.Media.TranslateTransform.X%2A> se vrátí na původní hodnotu 0. Výsledkem je, že se obdélník přesune do pravého 350ého pixelu a pak přejde zpátky na původní pozici.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Druhý <xref:System.Windows.Media.Animation.Storyboard>, `B2`, také animuje vlastnost <xref:System.Windows.Media.TranslateTransform.X%2A> stejného <xref:System.Windows.Media.TranslateTransform>. Vzhledem k tomu, že je nastavena pouze vlastnost <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> animace v tomto <xref:System.Windows.Media.Animation.Storyboard>, animace používá aktuální hodnotu vlastnosti, kterou animuje jako počáteční hodnotu.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Pokud kliknete na druhé tlačítko při přehrávání prvního <xref:System.Windows.Media.Animation.Storyboard>, může to očekávat následující chování:  
  
1. První scénář končí a pošle obdélník zpátky do původní pozice, protože animace má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2. Druhý scénář se projeví a Animuje z aktuální pozice, což je nyní 0 až 500.  
  
 **Ale to není to, co se stane.** Místo toho obdélník neskočí zpět; pokračuje se v pohybu doprava. Důvodem je, že druhá animace používá aktuální hodnotu první animace jako počáteční hodnotu a animace z této hodnoty na 500. Když druhá animace nahradí první, protože se používá <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace><xref:System.Windows.Media.Animation.HandoffBehavior>, nezáleží <xref:System.Windows.Media.Animation.FillBehavior> první animace.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior a dokončená událost  
 Další příklady ukazují jiný scénář, ve kterém <xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> zřejmě nemá žádný vliv. V příkladu se znovu používá scénář pro animaci vlastnosti <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> z 0 do 350. Tentokrát ale ukázkový registr pro událost <xref:System.Windows.Media.Animation.Timeline.Completed>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 Obslužná rutina události <xref:System.Windows.Media.Animation.Timeline.Completed> spustí další <xref:System.Windows.Media.Animation.Storyboard>, která animuje stejnou vlastnost z aktuální hodnoty na 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Následuje označení, které definuje druhý <xref:System.Windows.Media.Animation.Storyboard> jako prostředek.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Při spuštění <xref:System.Windows.Media.Animation.Storyboard>můžete očekávat, že vlastnost <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> má být animována z 0 do 350, pak po dokončení vrátit na 0 (protože má <xref:System.Windows.Media.Animation.FillBehavior> nastavení <xref:System.Windows.Media.Animation.FillBehavior.Stop>) a pak animovat z 0 na 500. Místo toho se <xref:System.Windows.Media.TranslateTransform> animuje od 0 do 350 a potom do 500.  
  
 Důvodem je pořadí, ve kterém WPF vyvolává události a protože hodnoty vlastností jsou ukládány do mezipaměti a nejsou přepočítány, pokud je vlastnost neověřena. Událost <xref:System.Windows.Media.Animation.Timeline.Completed> se zpracovává jako první, protože ji aktivovala Kořenová časová osa (první <xref:System.Windows.Media.Animation.Storyboard>). V tuto chvíli vlastnost <xref:System.Windows.Media.TranslateTransform.X%2A> stále vrátí svou animovanou hodnotu, protože dosud nebyla zrušena její platnost. Druhý <xref:System.Windows.Media.Animation.Storyboard> jako počáteční hodnotu používá hodnotu uloženou v mezipaměti a začne animovat.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Výkon  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Po přechodu pryč ze stránky jsou animace pořád spuštěné.  
 Když opustíte <xref:System.Windows.Controls.Page>, který obsahuje spuštěné animace, budou se tyto animace nadále přehrávat, dokud se <xref:System.Windows.Controls.Page> nevygeneruje paměti. V závislosti na používaném navigačním systému může stránka, na kterou jste přešli, zůstat v paměti po dobu neurčitou, a to vše, když se prostředky zabírají s animacemi. Tato možnost je nejužitečnější, když stránka obsahuje neustále běžící animace ("okolí").  
  
 Z tohoto důvodu je vhodné použít událost <xref:System.Windows.FrameworkElement.Unloaded> k odebrání animací při opuštění stránky.  
  
 Existují různé způsoby, jak odebrat animaci. Následující techniky lze použít k odebrání animací, které patří do <xref:System.Windows.Media.Animation.Storyboard>.  
  
- Chcete-li odebrat <xref:System.Windows.Media.Animation.Storyboard>, kterou jste začali s triggerem události, přečtěte si téma [How to: Remove a scénář](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
- Chcete-li použít kód pro odebrání <xref:System.Windows.Media.Animation.Storyboard>, přečtěte si část <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> metoda.  
  
 Další technika může být použita bez ohledu na to, jak byla animace spuštěna.  
  
- Chcete-li odebrat animace z konkrétní vlastnosti, použijte metodu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>. Zadejte vlastnost animovanou jako první parametr a `null` jako druhý. Tím se odeberou všechny hodiny z animace z vlastnosti.  
  
 Další informace o různých způsobech animace vlastností naleznete v tématu [Přehled postupů animace vlastností](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Použití HandoffBehavioru pro vytváření spotřebovává systémové prostředky.  
 Když použijete <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>nebo <xref:System.Windows.Media.Animation.AnimationClock> na vlastnost pomocí <xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.HandoffBehavior>, budou všechny <xref:System.Windows.Media.Animation.Clock> objekty dříve přidružené k této vlastnosti nadále spotřebovávat systémové prostředky; systém časování tyto hodiny nebude automaticky odebírat.  
  
 Aby nedocházelo k problémům s výkonem při použití většího počtu hodin pomocí <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, měli byste po dokončení odebrat z animovaných vlastností ty hodiny. Existuje několik způsobů, jak odebrat hodiny.  
  
- Chcete-li odebrat všechny hodiny z vlastnosti, použijte metodu <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> nebo <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> animovaného objektu. Zadejte vlastnost animovanou jako první parametr a `null` jako druhý. Tím se odeberou všechny hodiny z animace z vlastnosti.  
  
- Chcete-li ze seznamu hodin odebrat konkrétní <xref:System.Windows.Media.Animation.AnimationClock>, použijte vlastnost <xref:System.Windows.Media.Animation.Clock.Controller%2A> <xref:System.Windows.Media.Animation.AnimationClock> k načtení <xref:System.Windows.Media.Animation.ClockController>a pak zavolejte metodu <xref:System.Windows.Media.Animation.ClockController.Remove%2A> <xref:System.Windows.Media.Animation.ClockController>. To se obvykle provádí v obslužné rutině události <xref:System.Windows.Media.Animation.Clock.Completed> pro hodiny. Všimněte si, že <xref:System.Windows.Media.Animation.ClockController>lze ovládat pouze kořenové hodiny; vlastnost <xref:System.Windows.Media.Animation.Clock.Controller%2A> podřízených hodin vrátí `null`. Všimněte si také, že událost <xref:System.Windows.Media.Animation.Clock.Completed> nebude volána, pokud je doba platnosti hodin navždy.  V takovém případě bude uživatel muset určit, kdy volat <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 To je primárně problém pro animace objektů, které mají dlouhou životnost.  Když je objekt uvolněn z paměti, jeho hodiny budou také odpojeny a uvolňovány paměti.  
  
 Další informace o objektech hodin naleznete v tématu [Přehled systému pro animace a časování](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
