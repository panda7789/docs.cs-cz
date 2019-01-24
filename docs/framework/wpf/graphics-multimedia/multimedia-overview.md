---
title: Přehled multimédií
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: aa8d1a33fb415b986bc5e058f5d198c221f9f489
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493167"
---
# <a name="multimedia-overview"></a>Přehled multimédií
Multimédií funkce v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vám umožní integrovat zvuku a videa do svých aplikací a zlepšit uživatelské prostředí. Toto téma představuje multimediální funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 
  
<a name="mediaapi"></a>   
## <a name="media-api"></a>Media API  
 <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.MediaPlayer> třídy se používají k předkládání obsahu zvuku nebo videa. Tyto třídy je možné řídit interaktivně nebo hodin. Tyto třídy můžete použít na [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 ovládací prvek přehrávání médií. Třídy, které použijete, závisí na scénáři.  
  
 <xref:System.Windows.Controls.MediaElement> je <xref:System.Windows.UIElement> , který je podporován [rozložení](../../../../docs/framework/wpf/advanced/layout.md) a můžou je využívat jako obsah mnoho ovládacích prvků. Je také možné používat ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a zároveň i kód. <xref:System.Windows.Media.MediaPlayer>, na druhé straně je navržená pro <xref:System.Windows.Media.Drawing> objektů a nemá podporu rozložení. Médium načtené pomocí možnosti <xref:System.Windows.Media.MediaPlayer> lze pouze zobrazit pomocí <xref:System.Windows.Media.VideoDrawing> nebo interakcí přímo s <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer> nelze použít v XAML.  
  
 Další informace o vykreslení objektů a kreslení kontextu najdete v tématu [výkresu objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
> [!NOTE]
>  Při distribuci média s aplikací, nelze použít jako zdroj projektu mediální soubor. V souboru projektu, musíte místo toho nastavte typ média na `Content` a nastavte `CopyToOutputDirectory` k `PreserveNewest` nebo `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Režimy přehrávání médií  
  
> [!NOTE]
>  Obě <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.MediaPlayer> mají podobné členy. Odkazy v této části najdete <xref:System.Windows.Controls.MediaElement> členy třídy. Pokud není uvedeno, členy propojené ve <xref:System.Windows.Controls.MediaElement> třídy najdete také v <xref:System.Windows.Media.MediaPlayer> třídy.  
  
 Abyste pochopili přehrávání médií v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], pochopení různých režimech, ve kterých je možné přehrát média je povinný. Obě <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.MediaPlayer> je možné ve dvou režimech různá média, nezávislé režim a režim hodiny. Režim médií závisí <xref:System.Windows.Controls.MediaElement.Clock%2A> vlastnost. Když <xref:System.Windows.Controls.MediaElement.Clock%2A> je `null`, mediální objekt je v režimu nezávislé. Když <xref:System.Windows.Controls.MediaElement.Clock%2A> je nenulové, mediální objekt je v režimu hodiny. Ve výchozím nastavení jsou objekty médií v nezávislých režimu.  
  
### <a name="independent-mode"></a>Nezávislé režimu  
 V režimu nezávislé řídí mediálního obsahu přehrávání médií. Nezávislé režim umožňuje následující možnosti:  
  
-   Média <xref:System.Uri> je možné zadat přímo.  
  
-   Přehrávání médií je možné řídit přímo.  
  
-   Média <xref:System.Windows.Controls.MediaElement.Position%2A> a <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> vlastnosti je možné upravit.  
  
 Média je načtena buď nastavením <xref:System.Windows.Controls.MediaElement> objektu <xref:System.Windows.Controls.MediaElement.Source%2A> vlastnost nebo voláním <xref:System.Windows.Media.MediaPlayer> objektu <xref:System.Windows.Media.MediaPlayer.Open%2A> metody.  
  
 Řízení přehrávání médií v nezávislých režimu, je možné metody ovládacího prvku objektu média. Dostupné metody řízení <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, a <xref:System.Windows.Controls.MediaElement.Stop%2A>. Pro <xref:System.Windows.Controls.MediaElement>, interaktivní řízení použití těchto metod je k dispozici pouze pokud <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je nastavena na <xref:System.Windows.Controls.MediaState.Manual>. Tyto metody nejsou k dispozici, když je objekt média v režimu hodiny.  
  
 Zobrazit [řízení elementu MediaElement (přehrát, pozastavit, zastavit, svazek a rychlost)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) příklad nezávislé režimu.  
  
### <a name="clock-mode"></a>Režim hodiny  
 V režimu hodiny <xref:System.Windows.Media.MediaTimeline> přehrávání médií jednotek. Hodiny režim má následující vlastnosti:  
  
-   Média <xref:System.Uri> není nastaven nepřímo prostřednictvím <xref:System.Windows.Media.MediaTimeline>.  
  
-   Přehrání média mohou být řízena hodin. Metody řízení média objektu nelze použít.  
  
-   Načtení média tak, že nastavíte <xref:System.Windows.Media.MediaTimeline> objektu <xref:System.Windows.Media.MediaTimeline.Source%2A> vlastnost, vytváření hodiny z časové osy a přiřazení hodin k objektu média. Médium se také načte tímto způsobem při <xref:System.Windows.Media.MediaTimeline> uvnitř <xref:System.Windows.Media.Animation.Storyboard> cíle <xref:System.Windows.Controls.MediaElement>.  
  
 Ovládací prvek přehrávání médií v režimu hodiny <xref:System.Windows.Media.Animation.ClockController> ovládací prvek metody se musí použít. A <xref:System.Windows.Media.Animation.ClockController> se získávají z <xref:System.Windows.Media.Animation.ClockController> vlastnost <xref:System.Windows.Media.MediaClock>. Pokud se pokusíte použít metody ovládacího prvku buď <xref:System.Windows.Controls.MediaElement> nebo <xref:System.Windows.Media.MediaPlayer> objektu v režimu hodin <xref:System.InvalidOperationException> bude vyvolána výjimka.  
  
 Zobrazit [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) Další informace o hodiny a časové rámce.  
  
 Zobrazit [řízení elementu MediaElement pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md) příklad režimu hodiny.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>Třída elementu MediaElement  
 Přidání média do aplikace je stejně jednoduché jako přidání <xref:System.Windows.Controls.MediaElement> ovládací prvek [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aplikace a poskytování <xref:System.Uri> na médium, které chcete zahrnout. Všech typů médií podporovaných [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 jsou podporovány v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Následující příklad ukazuje, jednoduché použití <xref:System.Windows.Controls.MediaElement> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 V této ukázce média přehrání automaticky poté, co je načten. Po dokončení přehrávání média médium se zavře a všechny prostředky média jsou verze (včetně grafické paměti). Toto je výchozí chování <xref:System.Windows.Controls.MediaElement> objektu a řídí <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> vlastnosti.  
  
### <a name="controlling-a-mediaelement"></a>Řízení elementu MediaElement  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> vlastnosti řídit chování <xref:System.Windows.Controls.MediaElement> při <xref:System.Windows.FrameworkElement.IsLoaded%2A> je `true` nebo `false`v uvedeném pořadí. <xref:System.Windows.Controls.MediaState> Vlastnosti nastavené na ovlivňují chování přehrávání média. Například výchozí <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Play> a ve výchozím nastavení <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Close>. To znamená, že jakmile <xref:System.Windows.Controls.MediaElement> je načten a posun začátku je dokončena, médium se začne přehrávat. Po dokončení přehrávání médií se zavře a všechny prostředky média jsou uvolněny.  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> vlastnosti nejsou jediný způsob, jak ovládací prvek přehrávání médií. V režimu hodin, můžete řídit hodin <xref:System.Windows.Controls.MediaElement> a interaktivního ovládání metody mají řídí, kdy <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement> Tato soutěž pro ovládací prvek zpracovává vyhodnocením následující priority.  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Na místě, pokud je uvolněna médií. Tím se zajistí, že všechny prostředky média se vydávají ve výchozím nastavení, i v případě <xref:System.Windows.Media.MediaClock> je přidružený <xref:System.Windows.Controls.MediaElement>.  
  
2.  <xref:System.Windows.Media.MediaClock>. Na místě, když má média <xref:System.Windows.Controls.MediaElement.Clock%2A>. Pokud je médium uvolněna, <xref:System.Windows.Media.MediaClock> se projeví až <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Manual>. Hodiny režimu přepsání vždy načteno chování <xref:System.Windows.Controls.MediaElement>.  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Na místě při načítání média.  
  
4.  Interaktivní řízení metody. V případě umístěte <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Manual>. Dostupné metody řízení <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, a <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Zobrazení elementu MediaElement  
 Chcete-li zobrazit <xref:System.Windows.Controls.MediaElement> musí mít obsah k vykreslení a bude mít jeho <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> vlastnosti nastaven na hodnotu nula, dokud nebude vložen obsah. Pouze obsah, zvuk tyto vlastnosti jsou vždy nula. V případě video obsahu jednou <xref:System.Windows.Controls.MediaElement.MediaOpened> byla vyvolána událost <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> bude sestava velikost vložená média. To znamená, že dokud nebude vložen média, <xref:System.Windows.Controls.MediaElement> nebude trvat až všechny fyzického místa na disku v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] není-li <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A> jsou nastaveny vlastnosti.  
  
 Nastavení obě <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti způsobí, že aby roztáhnout tak, aby vyplnil oblasti k dispozici pro média <xref:System.Windows.Controls.MediaElement>. Chcete-li zachovat původní poměr stran média, buď <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A> vlastnost by měla být sada, ale ne obojí. Nastavení obě <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> způsobí, že vlastnosti média, aby prezentovat velikost pevné elementu, který nemusí být žádoucí.  
  
 Abyste se vyhnuli nutnosti prvek pevné velikosti, která [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] může počáteční sekvence média. To se provádí tak, že nastavíte <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> buď <xref:System.Windows.Controls.MediaState.Play> nebo <xref:System.Windows.Controls.MediaState.Pause>. V <xref:System.Windows.Controls.MediaState.Pause> stavu média se počáteční sekvence a nabídne prvního rámce. V <xref:System.Windows.Controls.MediaState.Play> stavu, bude počáteční sekvence a spustit přehrávání média.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer Class  
 Kde jako <xref:System.Windows.Controls.MediaElement> prvek framework je třída <xref:System.Windows.Media.MediaPlayer> třídy je určen pro použití v <xref:System.Windows.Media.Drawing> objekty. Kreslení objekty se používají, když jste vzdát úroveň funkce framework zlepší výkon, nebo pokud potřebujete <xref:System.Windows.Freezable> funkce. <xref:System.Windows.Media.MediaPlayer> umožňuje využívat výhody těchto funkcí a poskytování mediálního obsahu ve vašich aplikacích. Stejně jako <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> lze použít v nezávislých nebo není hodiny režimu, ale nemá mít <xref:System.Windows.Controls.MediaElement> objektů byla uvolněna a načíst stavy. To snižuje složitost ovládací prvek přehrávání <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Řízení MediaPlayer  
 Protože <xref:System.Windows.Media.MediaPlayer> je bezstavové, existují jenom dva způsoby, jak ovládací prvek přehrávání médií.  
  
1.  Interaktivní řízení metody. Na místě v nezávislých režimu (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> vlastnost).  
  
2.  <xref:System.Windows.Media.MediaClock>. Na místě, když má média <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Zobrazení MediaPlayer  
 Technicky vzato <xref:System.Windows.Media.MediaPlayer> nelze zobrazit, protože nemá žádné fyzické reprezentace. Nicméně je možné prezentovat média v <xref:System.Windows.Media.Drawing> pomocí <xref:System.Windows.Media.VideoDrawing> třídy. Následující příklad ukazuje použití <xref:System.Windows.Media.VideoDrawing> zobrazíte média.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Zobrazit [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md) Další informace o <xref:System.Windows.Media.Drawing> objekty.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.DrawingGroup>
- [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)
- [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
