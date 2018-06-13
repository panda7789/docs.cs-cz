---
title: Přehled multimédií
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 7a986125cff1ff4812528212fa3aee7689af1f16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566428"
---
# <a name="multimedia-overview"></a>Přehled multimédií
Funkce multimédií [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vám umožní integrovat audio a video do svých aplikací k vylepšení zkušeností uživatelů. Toto téma představuje multimédií funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 
  
<a name="mediaapi"></a>   
## <a name="media-api"></a>Rozhraní API média  
 <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.MediaPlayer> třídy se používají k prezentovat obsah zvuku a videa. Tyto třídy lze řídit, interaktivní nebo hodinami. Tyto třídy můžete použít na [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 řízení pro přehrávání médií. Třídy, které použijete, závisí na scénáři.  
  
 <xref:System.Windows.Controls.MediaElement> je <xref:System.Windows.UIElement> který je podporován [rozložení](../../../../docs/framework/wpf/advanced/layout.md) a mohou být využívány jako obsah mnoho ovládacích prvků. Je také použít v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a zároveň i kód. <xref:System.Windows.Media.MediaPlayer>, na druhé straně je určená pro <xref:System.Windows.Media.Drawing> objekty a chybí podpora rozložení. Médium načtené pomocí možnosti <xref:System.Windows.Media.MediaPlayer> lze pouze zobrazit pomocí <xref:System.Windows.Media.VideoDrawing> nebo interakcí přímo s <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer> nelze použít v jazyce XAML.  
  
 Další informace o kreslení objekty a kreslení kontextu najdete v tématu [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
> [!NOTE]
>  Při distribuci média s vaší aplikací, nelze použít soubor média jako prostředek projektu. V souboru projektu, musíte místo toho nastavit typ média na `Content` a nastavte `CopyToOutputDirectory` k `PreserveNewest` nebo `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Režimy přehrávání média  
  
> [!NOTE]
>  Obě <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.MediaPlayer> mají podobné členy. Odkazy v této části najdete <xref:System.Windows.Controls.MediaElement> třídy členy. Pokud není uvedeno jinak, členy propojené s v <xref:System.Windows.Controls.MediaElement> třída najdete také v <xref:System.Windows.Media.MediaPlayer> třídy.  
  
 Abyste pochopili přehrávání médií v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], představu o různé režimy, ve kterých bude možné přehrát média se vyžaduje. Obě <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.MediaPlayer> mohou být používány dva režimy různá média, nezávislé režim a režim hodiny. Režim média je dáno <xref:System.Windows.Controls.MediaElement.Clock%2A> vlastnost. Když <xref:System.Windows.Controls.MediaElement.Clock%2A> je `null`, objekt média je v režimu nezávislé. Když <xref:System.Windows.Controls.MediaElement.Clock%2A> je jinou hodnotu než null, objekt média je v režimu hodiny. Ve výchozím nastavení média objekty jsou v režimu nezávislé.  
  
### <a name="independent-mode"></a>Nezávislé režimu  
 V režimu nezávislé jednotky mediálního obsahu přehrávání médií. Nezávislé režim umožňuje následující možnosti:  
  
-   Na médiu <xref:System.Uri> lze zadat přímo.  
  
-   Přehrávání médií lze řídit přímo.  
  
-   Na médiu <xref:System.Windows.Controls.MediaElement.Position%2A> a <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> vlastnosti můžete změnit.  
  
 False buď nastavením <xref:System.Windows.Controls.MediaElement> objektu <xref:System.Windows.Controls.MediaElement.Source%2A> vlastnost nebo voláním <xref:System.Windows.Media.MediaPlayer> objektu <xref:System.Windows.Media.MediaPlayer.Open%2A> metoda.  
  
 K řízení přehrávání médií v nezávislých režimu, lze použít metody řízení objekt média. Dostupné metody řízení <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, a <xref:System.Windows.Controls.MediaElement.Stop%2A>. Pro <xref:System.Windows.Controls.MediaElement>, interaktivní ovládacího prvku pomocí těchto metod je k dispozici pouze při <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je nastaven na <xref:System.Windows.Controls.MediaState.Manual>. Tyto metody jsou k dispozici, pokud je objekt média v režimu hodiny.  
  
 V tématu [řízení MediaElement (Play, pozastavení, zastavení, svazku a rychlost)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) příklad nezávislé režimu.  
  
### <a name="clock-mode"></a>Hodiny režimu  
 V režimu hodiny <xref:System.Windows.Media.MediaTimeline> přehrávání jednotky média. Hodiny režim má následující vlastnosti:  
  
-   Na médiu <xref:System.Uri> není nastaven nepřímo prostřednictvím <xref:System.Windows.Media.MediaTimeline>.  
  
-   Přehrávání médií se dá nastavit podle hodiny. Metody řízení objekt médium nelze použít.  
  
-   False nastavením <xref:System.Windows.Media.MediaTimeline> objektu <xref:System.Windows.Media.MediaTimeline.Source%2A> vlastnost, vytváření hodiny ze časové osy a přiřazování hodiny k objektu média. Médium je také načíst tímto způsobem při <xref:System.Windows.Media.MediaTimeline> uvnitř <xref:System.Windows.Media.Animation.Storyboard> cíle <xref:System.Windows.Controls.MediaElement>.  
  
 Přehrávání médií ovládací prvek v režimu hodiny <xref:System.Windows.Media.Animation.ClockController> metody řízení se musí použít. A <xref:System.Windows.Media.Animation.ClockController> se získávají z <xref:System.Windows.Media.Animation.ClockController> vlastnost <xref:System.Windows.Media.MediaClock>. Pokud se pokusíte použít metody řízení buď <xref:System.Windows.Controls.MediaElement> nebo <xref:System.Windows.Media.MediaPlayer> objektů v režimu hodiny <xref:System.InvalidOperationException> bude vyvolána.  
  
 Najdete v článku [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) Další informace o hodiny a časové osy.  
  
 V tématu [řídit MediaElement pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md) příklad režimu hodiny.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement – třída  
 Přidání média do aplikace je jednoduché, přidávání <xref:System.Windows.Controls.MediaElement> řídit k [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aplikace a poskytování <xref:System.Uri> na médium, které chcete zahrnout. Všechny typy médií podporovanými [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 jsou podporovány v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Následující příklad ukazuje jednoduchý využití <xref:System.Windows.Controls.MediaElement> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 V této ukázce se média hraje automaticky, jakmile je načten. Po dokončení přehrávání média média se zavře a všechny prostředky média jsou verze (včetně grafické paměti). Toto je výchozí chování <xref:System.Windows.Controls.MediaElement> objektu a řídí <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> vlastnosti.  
  
### <a name="controlling-a-mediaelement"></a>Řízení MediaElement  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> vlastnosti řídí chování <xref:System.Windows.Controls.MediaElement> při <xref:System.Windows.FrameworkElement.IsLoaded%2A> je `true` nebo `false`, v uvedeném pořadí. <xref:System.Windows.Controls.MediaState> Jsou nastaveny vlastnosti ovlivnit chování přehrávání média. Například výchozí <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Play> a ve výchozím nastavení <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Close>. To znamená, že jakmile <xref:System.Windows.Controls.MediaElement> je načteno a posun začátku je dokončena, začne přehrávat média. Po dokončení přehrávání média se zavře a uvolnění prostředků všechna média.  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> vlastnosti nejsou jediný způsob, jak ovládat média přehrávání. V režimu hodiny, můžete řídit hodiny <xref:System.Windows.Controls.MediaElement> a metody řízení interaktivní máte řídit, kdy <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement> Tato soutěž o řízení zpracovává vyhodnocením následující priority.  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Na místě, pokud je odpojen médií. To zajistí, že všechny prostředky média vydávají ve výchozím nastavení, i v případě <xref:System.Windows.Media.MediaClock> přidružen <xref:System.Windows.Controls.MediaElement>.  
  
2.  <xref:System.Windows.Media.MediaClock>. Na místě, když má média <xref:System.Windows.Controls.MediaElement.Clock%2A>. Pokud je médium odpojen, <xref:System.Windows.Media.MediaClock> vstoupí v platnost stejně dlouho jako <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Manual>. Hodiny režimu vždy přepsání načíst chování <xref:System.Windows.Controls.MediaElement>.  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Na místě, když je načten média.  
  
4.  Interaktivní řízení metody. V umístění, kdy <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Manual>. Dostupné metody řízení <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, a <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Zobrazení MediaElement  
 K zobrazení <xref:System.Windows.Controls.MediaElement> musí mít obsah k vykreslení a bude mít jeho <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> vlastnosti nastaven na hodnotu nula, dokud nebude obsah vložen. Pro zvuk pouze obsah tyto vlastnosti jsou vždy nula. Video obsahu jednou <xref:System.Windows.Controls.MediaElement.MediaOpened> vyvolána událost <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> bude sestava velikost vložená média. To znamená, že dokud média je načtena, <xref:System.Windows.Controls.MediaElement> nebude trvat až všechny fyzického místa na disku v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Pokud <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A> jsou nastaveny vlastnosti.  
  
 Obě nastavení <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti způsobí, že média, aby se roztáhnou tak, aby vyplnil celou oblast stanovené <xref:System.Windows.Controls.MediaElement>. Pro zachování původního poměru stran obrázku je médium buď <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A> vlastnost by měla být sadu, ale ne obojí. Obě nastavení <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti způsobí, že médium, které má k dispozici v elementu pevné velikosti, která nemusí být žádoucí.  
  
 Abyste se vyhnuli nutnosti element pevnou velikostí, které [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete počáteční sekvence média. To se provádí nastavením <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> buď <xref:System.Windows.Controls.MediaState.Play> nebo <xref:System.Windows.Controls.MediaState.Pause>. V <xref:System.Windows.Controls.MediaState.Pause> stavu, bude počáteční sekvence média a nabídne první snímek. V <xref:System.Windows.Controls.MediaState.Play> stavu, bude počáteční sekvence a začít přehrávat média.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Media Player – třída  
 Kde jako <xref:System.Windows.Controls.MediaElement> třída je framework element <xref:System.Windows.Media.MediaPlayer> třída je určen k použití v <xref:System.Windows.Media.Drawing> objekty. Kreslení objekty se používají, když můžete vzdát úrovně funkce framework získat výhody výkonu nebo když potřebujete <xref:System.Windows.Freezable> funkce. <xref:System.Windows.Media.MediaPlayer> umožňuje využívat výhody těchto funkcí současně mediální obsah ve svých aplikacích. Jako <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> lze použít v nezávislých nebo není taktovací režimu, ale nemá mít <xref:System.Windows.Controls.MediaElement> uvolněna a načíst stavy objektu. Tím se snižuje složitost řízení přehrávání <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Řízení Media Player  
 Protože <xref:System.Windows.Media.MediaPlayer> je bezstavové, existují pouze dva způsoby řízení přehrávání médií.  
  
1.  Interaktivní řízení metody. Na místě v nezávislých režimu (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> vlastnost).  
  
2.  <xref:System.Windows.Media.MediaClock>. Na místě, když má média <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Zobrazení Media Player  
 Technicky <xref:System.Windows.Media.MediaPlayer> nelze zobrazit, protože má žádné fyzické reprezentace. Však může sloužit k dispozici média v <xref:System.Windows.Media.Drawing> pomocí <xref:System.Windows.Media.VideoDrawing> třídy. Následující příklad ukazuje použití <xref:System.Windows.Media.VideoDrawing> zobrazíte média.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Najdete v článku [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md) Další informace o <xref:System.Windows.Media.Drawing> objekty.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.DrawingGroup>  
 [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
