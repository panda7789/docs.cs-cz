---
title: Přehled multimédií
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: d4abf4d9fd324ffbf2737dc686c02e50ca1a8a5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181876"
---
# <a name="multimedia-overview"></a>Přehled multimédií
Multimediální funkce [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umožňují integrovat zvuk a video do vašich aplikací a zlepšit tak uživatelské prostředí. Toto téma představuje multimediální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]funkce aplikace .  

<a name="mediaapi"></a>
## <a name="media-api"></a>Rozhraní API pro média  
 <xref:System.Windows.Controls.MediaElement> Třídy <xref:System.Windows.Media.MediaPlayer> a slouží k prezentaci zvukového nebo obrazového obsahu. Tyto třídy lze ovládat interaktivně nebo pomocí hodin. Tyto třídy lze použít v ovládacím prvku Microsoft Windows Media Player 10 pro přehrávání médií. Jakou třídu používáte, závisí na scénáři.  
  
 <xref:System.Windows.Controls.MediaElement><xref:System.Windows.UIElement> je, který je podporován [rozložení](../advanced/layout.md) a mohou být spotřebovány jako obsah mnoha ovládacích prvků. Je také použitelný [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] v stejně jako kód. <xref:System.Windows.Media.MediaPlayer>, na druhé straně, <xref:System.Windows.Media.Drawing> je určen pro objekty a postrádá podporu rozvržení. Média načtená <xref:System.Windows.Media.MediaPlayer> pomocí a lze <xref:System.Windows.Media.VideoDrawing> zobrazit pouze pomocí <xref:System.Windows.Media.DrawingContext>nebo přímou interakcí s . <xref:System.Windows.Media.MediaPlayer>nelze použít v XAML.  
  
 Další informace o nakreslených objektech a kontextu kreslení naleznete v [tématu Přehled objektů kreslení](drawing-objects-overview.md).  
  
> [!NOTE]
> Při distribuci médií s aplikací nelze použít mediální soubor jako zdroj projektu. V souboru projektu je nutné místo `Content` toho `CopyToOutputDirectory` nastavit `PreserveNewest` `Always`typ média a nastavit na nebo .  
  
<a name="mediaplaybackmodes"></a>
## <a name="media-playback-modes"></a>Režimy přehrávání médií  
  
> [!NOTE]
> Oba <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> a mají podobné členy. Odkazy v této části <xref:System.Windows.Controls.MediaElement> odkazují na členy třídy. Není-li výslovně uvedeno, <xref:System.Windows.Controls.MediaElement> členy spojené ve třídě <xref:System.Windows.Media.MediaPlayer> lze také nalézt ve třídě.  
  
 Chcete-li porozumět [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]přehrávání médií v aplikaci , je vyžadováno pochopení různých režimů, ve kterých lze přehrávat média. Oba <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> a mohou být použity ve dvou různých režimech médií, nezávislý režim a režim hodin. Režim média je určen <xref:System.Windows.Controls.MediaElement.Clock%2A> vlastností. Pokud <xref:System.Windows.Controls.MediaElement.Clock%2A> `null`je , objekt média je v nezávislém režimu. Pokud <xref:System.Windows.Controls.MediaElement.Clock%2A> je non-null, objekt média je v režimu hodiny. Ve výchozím nastavení jsou objekty médií v nezávislém režimu.  
  
### <a name="independent-mode"></a>Nezávislý režim  
 V nezávislém režimu podporuje mediální obsah přehrávání médií. Nezávislý režim umožňuje následující možnosti:  
  
- Média <xref:System.Uri> lze zadat přímo.  
  
- Přehrávání médií lze přímo ovládat.  
  
- Média <xref:System.Windows.Controls.MediaElement.Position%2A> a <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> vlastnosti lze upravit.  
  
 Médium je načteno <xref:System.Windows.Controls.MediaElement> nastavením <xref:System.Windows.Controls.MediaElement.Source%2A> vlastnosti objektu nebo <xref:System.Windows.Media.MediaPlayer.Open%2A> voláním metody objektu. <xref:System.Windows.Media.MediaPlayer>  
  
 Pro řízení přehrávání médií v nezávislém režimu lze použít metody řízení objektu média. Dostupné kontrolní metody <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>jsou <xref:System.Windows.Controls.MediaElement.Close%2A>, <xref:System.Windows.Controls.MediaElement.Stop%2A>, a . Pro <xref:System.Windows.Controls.MediaElement>interaktivní ovládací prvek pomocí těchto <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> metod je <xref:System.Windows.Controls.MediaState.Manual>k dispozici pouze v případě, že je nastavena na . Tyto metody nejsou k dispozici, pokud je objekt média v režimu hodin.  
  
 Viz [Ovládání MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) pro příklad nezávislého režimu.  
  
### <a name="clock-mode"></a>Režim hodin  
 V režimu <xref:System.Windows.Media.MediaTimeline> hodin řídí přehrávání médií. Režim hodin má následující charakteristiky:  
  
- Média <xref:System.Uri> jsou nepřímo nastavena <xref:System.Windows.Media.MediaTimeline>prostřednictvím .  
  
- Přehrávání médií lze ovládat hodinami. Metody řízení objektu média nelze použít.  
  
- Médium se načte nastavením <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaTimeline.Source%2A> vlastnosti objektu, vytvořením hodin z časové osy a přiřazením hodin k objektu média. Tímto způsobem je také <xref:System.Windows.Media.MediaTimeline> načteno médium, pokud vnitřní <xref:System.Windows.Media.Animation.Storyboard> cíl . <xref:System.Windows.Controls.MediaElement>  
  
 Chcete-li ovládat přehrávání médií <xref:System.Windows.Media.Animation.ClockController> v režimu hodin, musí být použity metody řízení. A <xref:System.Windows.Media.Animation.ClockController> se získává <xref:System.Windows.Media.Animation.ClockController> z <xref:System.Windows.Media.MediaClock>vlastností . Pokud se pokusíte použít metody <xref:System.Windows.Controls.MediaElement> řízení <xref:System.Windows.Media.MediaPlayer> buď nebo objektu <xref:System.InvalidOperationException> v režimu hodiny, bude vyvolána.  
  
 Další informace o hodinách a časových osách najdete v přehledu [animací.](animation-overview.md)  
  
 Viz [Ovládání MediaElement pomocí Storyboard](how-to-control-a-mediaelement-by-using-a-storyboard.md) příklad režimu hodiny.  
  
<a name="mediaelement"></a>
## <a name="mediaelement-class"></a>Třída MediaElement  
 Přidání média do aplikace je stejně <xref:System.Windows.Controls.MediaElement> jednoduché [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako přidání ovládacího prvku do aplikace a poskytnutí <xref:System.Uri> média, které chcete zahrnout. Všechny typy médií podporované programem Microsoft Windows [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Media Player 10 jsou podporovány v aplikaci . Následující příklad ukazuje jednoduché použití <xref:System.Windows.Controls.MediaElement> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]in .  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 V této ukázce se médium přehraje automaticky, jakmile je načteno. Po dokončení přehrávání média se médium zavře a uvolní se všechny prostředky médií (včetně grafické paměti). Toto je výchozí <xref:System.Windows.Controls.MediaElement> chování objektu a <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> je řízen a vlastnosti.  
  
### <a name="controlling-a-mediaelement"></a>Ovládání prvku MediaElement  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Vlastnosti <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> a řídí chování <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.FrameworkElement.IsLoaded%2A> when `true` `false`is nebo , v uvedeném pořadí. Vlastnosti <xref:System.Windows.Controls.MediaState> jsou nastaveny tak, aby ovlivnily chování přehrávání médií. Například výchozí <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Play> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> výchozí <xref:System.Windows.Controls.MediaState.Close>je . To znamená, že <xref:System.Windows.Controls.MediaElement> jakmile je načten a preroll je kompletní, média začne hrát. Po dokončení přehrávání je médium uzavřeno a uvolněny všechny prostředky médií.  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Vlastnosti <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> a nejsou jediným způsobem, jak ovládat přehrávání médií. V režimu hodin, hodiny <xref:System.Windows.Controls.MediaElement> mohou ovládat a interaktivní <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> metody <xref:System.Windows.Controls.MediaState.Manual>řízení mají řízení, když je . <xref:System.Windows.Controls.MediaElement>soutěže o kontrolu tím, že vyhodnotí následující priority.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Na místě při uvolnění média. Tím je zajištěno, že všechny prostředky médií <xref:System.Windows.Media.MediaClock> jsou uvolněny <xref:System.Windows.Controls.MediaElement>ve výchozím nastavení, i když je přidružen k .  
  
2. <xref:System.Windows.Media.MediaClock>. Na místě, pokud <xref:System.Windows.Controls.MediaElement.Clock%2A>má médium . Pokud je médium <xref:System.Windows.Media.MediaClock> uvolněno, projeví <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> se <xref:System.Windows.Controls.MediaState.Manual>toto médium, dokud je . Režim hodiny vždy přepíše načtené chování <xref:System.Windows.Controls.MediaElement>.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Na místě při načtení média.  
  
4. Interaktivní metody řízení. Na místě, kdy <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Manual>. Dostupné kontrolní metody <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>jsou <xref:System.Windows.Controls.MediaElement.Close%2A>, <xref:System.Windows.Controls.MediaElement.Stop%2A>, a .  
  
### <a name="displaying-a-mediaelement"></a>Zobrazení prvku MediaElement  
 Chcete-li <xref:System.Windows.Controls.MediaElement> zobrazit, musí mít obsah k <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> vykreslení a bude mít své a vlastnosti nastaveny na nulu, dokud nebude obsah načten. Pro obsah pouze zvuk, tyto vlastnosti jsou vždy nula. Pro video obsah, <xref:System.Windows.Controls.MediaElement.MediaOpened> jakmile událost <xref:System.Windows.FrameworkElement.ActualWidth%2A> byla <xref:System.Windows.FrameworkElement.ActualHeight%2A> vyvolána a bude hlásit velikost načteného média. To znamená, že dokud <xref:System.Windows.Controls.MediaElement> médium je načten, nebude [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zabírají žádné fyzické místo v pokud <xref:System.Windows.FrameworkElement.Width%2A> jsou nastaveny vlastnosti nebo. <xref:System.Windows.FrameworkElement.Height%2A>  
  
 Nastavení <xref:System.Windows.FrameworkElement.Width%2A> vlastností <xref:System.Windows.FrameworkElement.Height%2A> a způsobí, že se médium roztáhne <xref:System.Windows.Controls.MediaElement>a vyplní oblast určenou pro rozhraní . Chcete-li zachovat původní poměr stran <xref:System.Windows.FrameworkElement.Width%2A> média, měla by být nastavena vlastnost nebo, <xref:System.Windows.FrameworkElement.Height%2A> nikoli však obě. Nastavení <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> a způsobí, že médium prezentovat v pevné velikosti prvku, který nemusí být žádoucí.  
  
 Aby nedošlo k vytvoření prvku [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pevné velikosti, který může předem vytvořit médium. To se provádí <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> nastavením <xref:System.Windows.Controls.MediaState.Play> <xref:System.Windows.Controls.MediaState.Pause>buď nebo . Ve <xref:System.Windows.Controls.MediaState.Pause> stavu média předvedou a představí první snímek. Ve <xref:System.Windows.Controls.MediaState.Play> stavu, média budou preroll a začnou hrát.  
  
<a name="mediaplayer"></a>
## <a name="mediaplayer-class"></a>Třída MediaPlayer  
 Kde jako <xref:System.Windows.Controls.MediaElement> třída je prvek <xref:System.Windows.Media.MediaPlayer> framework, třída je <xref:System.Windows.Media.Drawing> určena pro použití v objektech. Nakreslené objekty se používají, když můžete obětovat <xref:System.Windows.Freezable> prvky úrovně architektury k získání výhod výkonu nebo když potřebujete funkce. <xref:System.Windows.Media.MediaPlayer>umožňuje využívat tyto funkce při poskytování mediálního obsahu ve vašich aplikacích. Stejně jako <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> lze použít v nezávislém <xref:System.Windows.Controls.MediaElement> nebo hodinovém režimu, ale nemá uvolněné a načtené stavy objektu. Tím se snižuje složitost řízení <xref:System.Windows.Media.MediaPlayer>přehrávání .  
  
### <a name="controlling-mediaplayer"></a>Ovládání přehrávače Médií  
 Vzhledem k tomu, <xref:System.Windows.Media.MediaPlayer> že je bezstavová, existují pouze dva způsoby, jak ovládat přehrávání médií.  
  
1. Interaktivní metody řízení. Na místě, když`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> v nezávislém režimu (vlastnost).  
  
2. <xref:System.Windows.Media.MediaClock>. Na místě, pokud <xref:System.Windows.Media.MediaPlayer.Clock%2A>má médium .  
  
### <a name="displaying-a-mediaplayer"></a>Zobrazení přehrávače MediaPlayer  
 Technicky nelze <xref:System.Windows.Media.MediaPlayer> zobrazit, protože nemá žádnou fyzickou reprezentaci. Však lze použít k prezentaci <xref:System.Windows.Media.Drawing> média <xref:System.Windows.Media.VideoDrawing> v using třídy. Následující příklad ukazuje použití a <xref:System.Windows.Media.VideoDrawing> k zobrazení média.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.Drawing> objektech naleznete v [přehledu objektů kreslení.](drawing-objects-overview.md)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.DrawingGroup>
- [Rozložení](../advanced/layout.md)
- [Témata s postupy](audio-and-video-how-to-topics.md)
