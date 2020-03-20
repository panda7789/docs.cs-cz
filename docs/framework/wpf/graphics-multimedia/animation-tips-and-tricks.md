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
ms.openlocfilehash: 6b540448599c1e1083ed367a312ef60fceacd0d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187641"
---
# <a name="animation-tips-and-tricks"></a>Tipy a triky animace
Při práci s animacemi v WPF existuje řada tipů a triků, které mohou vaše animace lépe fungovat a ušetřit frustraci.  
  
<a name="generalissuessection"></a>
## <a name="general-issues"></a>Běžné problémy  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animace polohy posuvníku nebo posuvníku ji zamrzne  
 Pokud animujete pozici posuvníku nebo posuvníku pomocí animace, která má <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (výchozí hodnota), uživatel již nebude moci posunout posuvník nebo jezdec. Je to proto, že i v případě, že animace skončila, je stále přepsání základní hodnoty cílové vlastnosti. Chcete-li zastavit animace z přepsání vlastnosti aktuální hodnotu, odeberte ji nebo dát <xref:System.Windows.Media.Animation.FillBehavior> . <xref:System.Windows.Media.Animation.FillBehavior.Stop> Další informace a příklad naleznete v [tématu Set a Property After Animating It with a Storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animace výstupu animace nemá žádný vliv  
 Objekt, který je výstupem jiné animace, nelze animovat. Pokud například použijete <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> a <xref:System.Windows.Shapes.Shape.Fill%2A> animovat <xref:System.Windows.Shapes.Rectangle> z <xref:System.Windows.Media.RadialGradientBrush> a <xref:System.Windows.Media.SolidColorBrush>do a , nelze animovat žádné vlastnosti <xref:System.Windows.Media.RadialGradientBrush> nebo <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Nelze změnit hodnotu vlastnosti po její animaci  
 V některých případech se může zdát, že nelze změnit hodnotu vlastnosti po její animování, a to ani po ukončení animace. Je to proto, že i když animace skončila, je stále přepsání základní hodnoty vlastnosti. Chcete-li zastavit animace z přepsání vlastnosti aktuální hodnotu, odeberte ji nebo dát <xref:System.Windows.Media.Animation.FillBehavior> . <xref:System.Windows.Media.Animation.FillBehavior.Stop> Další informace a příklad naleznete v [tématu Set a Property After Animating It with a Storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Změna časové osy nemá žádný vliv  
 Ačkoli <xref:System.Windows.Media.Animation.Timeline> většina vlastností je animovatelná a může být <xref:System.Windows.Media.Animation.Timeline> vázána na data, změna hodnot vlastností aktivního se zdá, že nemá žádný vliv. Je to proto, <xref:System.Windows.Media.Animation.Timeline> že při zahájení časování systém <xref:System.Windows.Media.Animation.Timeline> časování vytvoří kopii a používá ji k vytvoření objektu. <xref:System.Windows.Media.Animation.Clock> Úprava originálu nemá žádný vliv na kopii systému.  
  
 Aby <xref:System.Windows.Media.Animation.Timeline> byly změny odrážet, musí být jeho hodiny znovu vygenerovány a použity k nahrazení dříve vytvořených hodin. Hodiny nejsou automaticky regenerovány. Následuje několik způsobů použití změn časové osy:  
  
- Pokud je časová osa <xref:System.Windows.Media.Animation.Storyboard>nebo patří do , můžete ji <xref:System.Windows.Media.Animation.BeginStoryboard> provést <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> odrážet změny opětovným použitím scénáře pomocí metody nebo metody. To má vedlejší účinek také restartování animace. V kódu můžete použít <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodu k posunu scénáře zpět do předchozí pozice.  
  
- Pokud jste použili animaci <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> přímo na <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> vlastnost pomocí metody, zavolejte metodu znovu a předat animaci, která byla změněna.  
  
- Pokud pracujete přímo na úrovni hodin, vytvořte a aplikujte novou sadu hodin a použijte je k nahrazení předchozí sady generovaných hodin.  
  
 Další informace o časových osách a hodinách naleznete v [tématu Přehled systému animace a časování](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop nefunguje podle očekávání  
 Existují časy, kdy <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> nastavení <xref:System.Windows.Media.Animation.FillBehavior.Stop> vlastnosti se zdá, že žádný vliv, například když <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> jeden <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>animace "ruce pryč" do jiného, protože má nastavení .  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Media.TranslateTransform>a . Bude <xref:System.Windows.Media.TranslateTransform> animovaný pohybovat <xref:System.Windows.Shapes.Rectangle> kolem <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Příklady v této části používají předchozí objekty k <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> zobrazení několika případů, kdy se vlastnost nechová tak, jak byste očekávali.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" a HandoffBehavior s více animacemi  
 Někdy se zdá, jako by <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> animace ignoruje svou vlastnost, když je nahrazen a druhý animace. Vezměte v následujícím příkladu, který vytvoří dva <xref:System.Windows.Media.Animation.Storyboard> objekty a používá je k animaci stejné <xref:System.Windows.Media.TranslateTransform> je uvedeno v předchozím příkladu.  
  
 První <xref:System.Windows.Media.Animation.Storyboard>, `B1`, animuje <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> vlastnost od 0 do 350, který přesune obdélník 350 pixelů vpravo. Když animace dosáhne konce své doby trvání a <xref:System.Windows.Media.TranslateTransform.X%2A> přestane přehrávání, vlastnost se vrátí na původní hodnotu, 0. V důsledku toho obdélník přesune doprava 350 pixelů a potom přeskočí zpět do původní polohy.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Druhý <xref:System.Windows.Media.Animation.Storyboard>, `B2`také animuje <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform>stejné . Vzhledem <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> k tomu, že <xref:System.Windows.Media.Animation.Storyboard> je nastavena pouze vlastnost animace v této hodnotě, animace používá aktuální hodnotu vlastnosti, kterou animuje jako počáteční hodnotu.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Pokud během přehrávání prvního <xref:System.Windows.Media.Animation.Storyboard> tlačítka klepnete na druhé tlačítko, můžete očekávat následující chování:  
  
1. První scénář končí a odešle obdélník zpět do původní polohy, protože animace má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> . <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
2. Druhý scénář se projeví a animuje z aktuální pozice, která je nyní 0, na 500.  
  
 **Ale to se nestává.** Místo toho obdélník neskočí zpět; pokračuje v pohybu doprava. Je to proto, že druhá animace používá aktuální hodnotu první animace jako počáteční hodnotu a animuje z této hodnoty na 500. Když druhá animace nahradí první, <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> protože se <xref:System.Windows.Media.Animation.FillBehavior> používá, první animace nezáleží.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior a dokončená událost  
 Další příklady ukazují jiný scénář, ve <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> kterém se zdá, že žádný vliv. Znovu příklad používá Storyboard animovat <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> od 0 do 350. Tentokrát se však příklad zaregistruje pro <xref:System.Windows.Media.Animation.Timeline.Completed> událost.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 Obslužná rutina <xref:System.Windows.Media.Animation.Timeline.Completed> události spustí jinou, <xref:System.Windows.Media.Animation.Storyboard> která animuje stejnou vlastnost z aktuální hodnoty na 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Následuje značka, která definuje druhý <xref:System.Windows.Media.Animation.Storyboard> jako prostředek.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Při spuštění <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.TranslateTransform.X%2A> , můžete očekávat, že <xref:System.Windows.Media.TranslateTransform> vlastnost animovat 0 na 350, pak se vrátí na <xref:System.Windows.Media.Animation.FillBehavior> 0 <xref:System.Windows.Media.Animation.FillBehavior.Stop>po dokončení (protože má nastavení ) a potom animovat od 0 do 500. Místo toho <xref:System.Windows.Media.TranslateTransform> animuje od 0 do 350 a pak na 500.  
  
 Je to z důvodu pořadí, ve kterém WPF vyvolává události a protože hodnoty vlastností jsou uloženy do mezipaměti a nejsou přepočítány, pokud není vlastnost zrušena. Událost <xref:System.Windows.Media.Animation.Timeline.Completed> je zpracována jako první, protože byla spuštěna kořenovou časovou osou (první). <xref:System.Windows.Media.Animation.Storyboard> V tuto chvíli <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost stále vrací svou animovanou hodnotu, protože ještě nebyla zrušena. Druhý <xref:System.Windows.Media.Animation.Storyboard> používá hodnotu uloženou v mezipaměti jako počáteční hodnotu a začne animovat.  
  
<a name="performancesection"></a>
## <a name="performance"></a>Výkon  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Animace pokračovat v běhu po navigaci mimo stránku  
 Při přechodu <xref:System.Windows.Controls.Page> od, který obsahuje spuštěné animace, tyto animace <xref:System.Windows.Controls.Page> bude pokračovat v přehrávání, dokud je uvolněno. V závislosti na navigačním systému, který používáte, může stránka, ze které přejdete, zůstat v paměti po dobu neurčitou a zároveň spotřebovává zdroje s animacemi. To je nejvíce patrné, když stránka obsahuje neustále spuštěné animace ("okolí").  
  
 Z tohoto důvodu je vhodné použít <xref:System.Windows.FrameworkElement.Unloaded> událost k odebrání animací při přechodu ze stránky.  
  
 Existují různé způsoby, jak odebrat animaci. Následující techniky lze použít k odebrání animací, které patří do <xref:System.Windows.Media.Animation.Storyboard>.  
  
- Pokud chcete <xref:System.Windows.Media.Animation.Storyboard> odebrat spuštění aktivační události, přečtěte si článek [Postup: Odebrání scénáře](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
- Chcete-li použít <xref:System.Windows.Media.Animation.Storyboard>kód k <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> odebrání , viz metoda.  
  
 Další technika může být použita bez ohledu na to, jak byla animace spuštěna.  
  
- Chcete-li odebrat animace z <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> určité vlastnosti, použijte metodu. Zadejte vlastnost, která je animována jako první parametr a `null` jako druhý. Tím odeberete všechny hodiny animace z vlastnosti.  
  
 Další informace o různých způsobech animace vlastností naleznete v [tématu Property Animation Techniques Overview](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Použití Compose HandoffBehavior spotřebovává systémové prostředky  
 Při použití <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>nebo <xref:System.Windows.Media.Animation.AnimationClock> vlastnost pomocí <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>, <xref:System.Windows.Media.Animation.Clock> všechny objekty dříve přidružené k této vlastnosti nadále využívat systémové prostředky; časovací systém tyto hodiny automaticky neodstraní.  
  
 Chcete-li se vyhnout problémům s výkonem <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>při použití velkého počtu hodin pomocí , měli byste odebrat skládání hodiny z animované vlastnosti po jejich dokončení. Existuje několik způsobů, jak odebrat hodiny.  
  
- Chcete-li odebrat všechny hodiny <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> z <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> vlastnosti, použijte metodu nebo animovaného objektu. Zadejte vlastnost, která je animována jako první parametr a `null` jako druhý. Tím odeberete všechny hodiny animace z vlastnosti.  
  
- Chcete-li <xref:System.Windows.Media.Animation.AnimationClock> odebrat konkrétní ze seznamu <xref:System.Windows.Media.Animation.Clock.Controller%2A> hodin, <xref:System.Windows.Media.Animation.AnimationClock> použijte vlastnost <xref:System.Windows.Media.Animation.ClockController>načíst <xref:System.Windows.Media.Animation.ClockController.Remove%2A> , pak <xref:System.Windows.Media.Animation.ClockController>volání metody . To se obvykle provádí <xref:System.Windows.Media.Animation.Clock.Completed> v obslužné rutině události pro hodiny. Všimněte si, že pouze kořenové hodiny mohou být řízeny <xref:System.Windows.Media.Animation.ClockController>; <xref:System.Windows.Media.Animation.Clock.Controller%2A> majetek dětských hodin se `null`vrátí . Všimněte si <xref:System.Windows.Media.Animation.Clock.Completed> také, že událost nebude volána, pokud je efektivní doba trvání hodin navždy.  V takovém případě bude uživatel muset určit, kdy zavolat <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Jedná se především o problém pro animace na objekty, které mají dlouhou životnost.  Když je objekt uvolňování, jeho hodiny budou také odpojeny a odpadky shromažďovány.  
  
 Další informace o objektech hodin naleznete v [tématu Přehled animace a časování systému](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
