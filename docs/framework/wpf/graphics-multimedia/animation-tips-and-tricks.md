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
ms.openlocfilehash: df4aa7f3bf046ec871333f665ab77fa460c4095c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252100"
---
# <a name="animation-tips-and-tricks"></a>Tipy a triky animace
Při práci s animací v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], existuje několik tipů a triků, které můžete provést vašich animacích líp fungovat a uložit frustrace.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Obecné problémy  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animace polohy posuvníku nebo posuvník se zablokuje ho  
 Pokud je vlastnost pozice posuvníku nebo posuvník pomocí animace, který má <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (výchozí hodnota), uživatel se už se moct přesunout posuvník nebo posuvník. To je proto, že i v případě, že animace ukončena, ho pořád přepisuje vlastnost target základní hodnoty. Zastavíte animaci z aktuální hodnota vlastnosti přepsání, odeberte ji nebo jí <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Další informace a příklad najdete v tématu [nastavit vlastnost Po animaci pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animace výstup animace nemá žádný vliv  
 Nelze animovat objekt, který se nachází výstup z jiné animace. Například, pokud použijete <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> pro animaci <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> z <xref:System.Windows.Media.RadialGradientBrush> k <xref:System.Windows.Media.SolidColorBrush>, všechny vlastnosti nelze animovat <xref:System.Windows.Media.RadialGradientBrush> nebo <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Nelze změnit hodnotu vlastnosti po animaci  
 V některých případech se může zobrazit, že nelze změnit hodnotu vlastnosti po je byl animovat, dokonce i po ukončení animace. To je proto, že i v případě, že animace ukončena, ho pořád přepisuje základní hodnotu vlastnosti. Zastavíte animaci z aktuální hodnota vlastnosti přepsání, odeberte ji nebo jí <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Další informace a příklad najdete v tématu [nastavit vlastnost Po animaci pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Změna časovou osu nemá žádný vliv  
 I když většina <xref:System.Windows.Media.Animation.Timeline> jsou animovatelné vlastnosti a mohou být data vázány, změna hodnot vlastnosti aktivní <xref:System.Windows.Media.Animation.Timeline> zdá se, že nemají žádný vliv. Důvodem je, že, když <xref:System.Windows.Media.Animation.Timeline> je spuštěno, vytvoří kopii tohoto systému časování <xref:System.Windows.Media.Animation.Timeline> a použije ho k vytvoření <xref:System.Windows.Media.Animation.Clock> objektu. Úprava původní nemá žádný vliv na kopírování v systému.  
  
 Pro <xref:System.Windows.Media.Animation.Timeline> tak, aby odrážely změny, musí se znova vygeneroval hodiny a používá k nahrazení dříve vytvořeného hodiny. Hodiny nejsou generovány pro vás automaticky. Následuje několik způsobů, jak použít časové osy:  
  
-   Pokud je na časové ose nebo patří do <xref:System.Windows.Media.Animation.Storyboard>, můžete si je změny projeví s opakováním jeho scénáře použití <xref:System.Windows.Media.Animation.BeginStoryboard> nebo <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda. To má za následek vedlejší také restartování animace. V kódu, můžete použít <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodu pro scénáře, přejděte zpět na předchozí pozici.  
  
-   Pokud jste použili animace přímo pro vlastnost pomocí <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody, volání <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda znovu a předejte jí animace, která byla změněna.  
  
-   Při práci přímo na úrovni hodin, vytvořit a použít novou sadu hodiny a pomocí nich nahradí předchozí sadu generovanou hodiny.  
  
 Další informace o časové osy a hodiny, naleznete v tématu [animace a časování přehledu systému](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop nebude fungovat podle očekávání  
 Existují situace, při nastavení <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.FillBehavior.Stop> zdá se, že nemají žádný vliv, jako např. kdy animace "předá" do jiného vzhledem k tomu, že má <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> nastavení <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.TranslateTransform> Bude při animaci pohybovat přesunout <xref:System.Windows.Shapes.Rectangle> kolem <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Příklady v této části použít předchozí objekty k předvedení několik případů kde <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost nechová podle očekávání tak.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior = "Stop" a HandoffBehavior s více animací  
 V některých případech to vypadá jako by šlo animace ignoruje jeho <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnosti, když se nahrazuje druhé animace. V následujícím příkladu, který vytvoří dva trvat <xref:System.Windows.Media.Animation.Storyboard> objekty a používá stejné animovat <xref:System.Windows.Media.TranslateTransform> je znázorněno v předchozím příkladu.  
  
 První <xref:System.Windows.Media.Animation.Storyboard>, `B1`, animuje <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> od 0 do 350, který přesune obdélník 350 pixelů na pravé straně. Při dosažení konce jeho trvání animace a zastaví přehrávání, <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost vrátí na původní hodnotu, 0. V důsledku toho obdélník přesune do pravé 350 pixelů a pak přejde zpět na původní pozici.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Druhá <xref:System.Windows.Media.Animation.Storyboard>, `B2`, také animuje <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost stejného <xref:System.Windows.Media.TranslateTransform>. Protože pouze <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> vlastnosti animace v tomto <xref:System.Windows.Media.Animation.Storyboard> je nastaven, animace používá aktuální hodnotu vlastnosti se animuje jako svou výchozí hodnotu.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Pokud kliknete na druhé tlačítko při prvním <xref:System.Windows.Media.Animation.Storyboard> je přehrávání, by se dalo očekávat následující chování:  
  
1.  První scénář ukončí a odešle obdélník zpět do původní polohy, protože má animace <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2.  Druhý scénář se projeví a animuje od aktuální pozice, který je nyní 0 na 500.  
  
 **Ale to je, není co se stane.** Místo toho obdélník nepřejde; zpět pokračuje v přesuňte do pravé. Důvodem je skutečnost, že druhé animace používá aktuální hodnotu prvního animace jako svou výchozí hodnotu a animuje z této hodnoty na 500. Když druhé animace nahradí první, protože <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> se používá, <xref:System.Windows.Media.Animation.FillBehavior> prvního animace není důležitá.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior a dokončené události  
 Další příklady ukazují jiný scénář, ve kterém <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> zdá se, že nemají žádný vliv. Znovu, v příkladu se používá ve scénáři pro animaci <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> od 0 do 350. Ale tentokrát v příkladu zaregistruje <xref:System.Windows.Media.Animation.Timeline.Completed> událostí.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> Obslužné rutiny události spustí jiný <xref:System.Windows.Media.Animation.Storyboard> , který animuje stejnou vlastnost její aktuální hodnota na 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Následuje kód, který definuje druhý <xref:System.Windows.Media.Animation.Storyboard> jako prostředek.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Při spuštění <xref:System.Windows.Media.Animation.Storyboard>, by se dalo očekávat <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> pro animaci od 0 do 350, pak se vraťte na 0 po dokončení (protože má <xref:System.Windows.Media.Animation.FillBehavior> nastavení <xref:System.Windows.Media.Animation.FillBehavior.Stop>) a potom bude animovat z 0 na 500. Místo toho <xref:System.Windows.Media.TranslateTransform> animuje z 0 na 350 a potom na 500.  
  
 To je z důvodu pořadí, ve kterém [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vyvolává události, protože hodnoty vlastností jsou uložené v mezipaměti a nejsou přepočítány, není-li vlastnost zneplatněna. <xref:System.Windows.Media.Animation.Timeline.Completed> Událostí je zpracován jako první, protože se aktivovala na časové ose kořenové (první <xref:System.Windows.Media.Animation.Storyboard>). V tuto chvíli <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost stále vrátí hodnotou animované, protože nebyla dosud zneplatněny. Druhá <xref:System.Windows.Media.Animation.Storyboard> hodnotu uloženou v mezipaměti používá jako svou výchozí hodnotu a začne animace.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Výkon  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Vlastnost Runafter navigaci pryč z stránky i nadále animace  
 Když přejdete ze <xref:System.Windows.Controls.Page> , která obsahuje běžící animace, tyto animace budou i nadále přehrát až <xref:System.Windows.Controls.Page> je uvolněna z paměti. V závislosti na navigační systému, které používáte, stránka, která můžete procházet klávesou může zůstat v paměti pro neomezené množství času, celou dobu využívání prostředků pomocí jeho animace. Toto je nejvíce patrné, pokud stránka obsahuje neustále spuštěný animace ("prostředí").  
  
 Z tohoto důvodu je vhodné použít <xref:System.Windows.FrameworkElement.Unloaded> událostí k odebrání animace, když přejdete mimo stránku.  
  
 Existují různé způsoby, jak odstranit animaci. Následující postupy slouží k odebrání animace, které patří <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Odebrat <xref:System.Windows.Media.Animation.Storyboard> začít aktivační procedura událostí naleznete v tématu [postupy: odebrání scénáře](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
-   Při použití kódu odebrat <xref:System.Windows.Media.Animation.Storyboard>, najdete v článku <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> metody.  
  
 Další postup může použít bez ohledu na to, jak spuštění animace.  
  
-   K odebrání animace z konkrétní vlastnosti, použijte <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metody. Zadejte vlastnost animované jako první parametr a `null` jako druhý. Tato akce odebere všechny hodiny animace z vlastnosti.  
  
 Další informace o různých způsobech animace vlastností najdete v tématu [přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Použití Compose HandoffBehavior využívá systémové prostředky  
 Při použití <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>, nebo <xref:System.Windows.Media.Animation.AnimationClock> k vlastnosti pomocí <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>, jakékoli <xref:System.Windows.Media.Animation.Clock> objekty dříve přidružené k této vlastnosti budou dál spotřebovávat systémové prostředky, nebudou časování systému Tyto hodiny automaticky odeberte.  
  
 Aby se zabránilo problémům s výkonem při použití velký počet hodin používání <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, byste měli odebrat vytváření hodiny z animací vlastností po jejich dokončení. Existuje několik způsobů, jak odebrat hodin.  
  
-   Chcete-li odebrat všechny hodiny z vlastnosti, použijte <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> nebo <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metoda animovaný objekt. Zadejte vlastnost animované jako první parametr a `null` jako druhý. Tato akce odebere všechny hodiny animace z vlastnosti.  
  
-   Odebrat konkrétní <xref:System.Windows.Media.Animation.AnimationClock> ze seznamu hodiny, použijte <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnost <xref:System.Windows.Media.Animation.AnimationClock> k načtení <xref:System.Windows.Media.Animation.ClockController>, zavolejte <xref:System.Windows.Media.Animation.ClockController.Remove%2A> metodu <xref:System.Windows.Media.Animation.ClockController>. To se obvykle provádí <xref:System.Windows.Media.Animation.Clock.Completed> obslužné rutiny události pro hodin. Všimněte si, že se dá nastavit jenom kořenový hodiny podle <xref:System.Windows.Media.Animation.ClockController>; <xref:System.Windows.Media.Animation.Clock.Controller%2A> vrátí vlastnost hodin podřízené `null`. Všimněte si také, že <xref:System.Windows.Media.Animation.Clock.Completed> událost se nebude volat, pokud je účinné trvání hodin trvale.  V takovém případě bude uživatel muset zjistit, kdy se má volat <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 To je především to problém pro animací na objekty, které mají dlouhou životnost.  Pokud objekt je vynuceno uvolnění paměti, jeho hodiny se také odpojí a prováděno uvolnění paměti.  
  
 Další informace o objekty clock, naleznete v tématu [animace a časování přehledu systému](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
