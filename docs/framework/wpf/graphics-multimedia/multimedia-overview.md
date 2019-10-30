---
title: Přehled multimédií
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 42d0d388e859b556d23b7fc81931cd61470ba541
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039802"
---
# <a name="multimedia-overview"></a>Přehled multimédií
Funkce multimédií v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umožňují integrovat zvuk a video do svých aplikací, aby se zlepšila činnost koncového uživatele. V tomto tématu se seznámíte s funkcemi multimédií [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>   
## <a name="media-api"></a>Rozhraní API pro multimédia  
 Třídy <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.MediaPlayer> slouží k prezentaci zvukového nebo obrazového obsahu. Tyto třídy je možné řídit interaktivně nebo podle času. Tyto třídy lze použít na ovládacím prvku Microsoft Windows Media Player 10 pro přehrávání multimédií. Kterou třídu použijete, závisí na scénáři.  
  
 <xref:System.Windows.Controls.MediaElement> je <xref:System.Windows.UIElement>, který je podporován [rozložením](../advanced/layout.md) a lze jej spotřebovat jako obsah mnoha ovládacích prvků. Je také možné použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kód. <xref:System.Windows.Media.MediaPlayer>je na druhé straně navržená pro <xref:System.Windows.Media.Drawing> objekty a nemá podporu rozložení. Médium načtené pomocí <xref:System.Windows.Media.MediaPlayer> lze prezentovat pouze pomocí <xref:System.Windows.Media.VideoDrawing> nebo přímo v interakci s <xref:System.Windows.Media.DrawingContext>. v jazyce XAML nelze použít <xref:System.Windows.Media.MediaPlayer>.  
  
 Další informace o vykreslování objektů a kontextu vykreslování naleznete v tématu [Přehled nakreslených objektů](drawing-objects-overview.md).  
  
> [!NOTE]
> Při distribuci médií do aplikace nemůžete použít mediální soubor jako prostředek projektu. V souboru projektu musíte místo toho nastavit typ média na `Content` a nastavit `CopyToOutputDirectory` na `PreserveNewest` nebo `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Režimy přehrávání multimédií  
  
> [!NOTE]
> <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.MediaPlayer> mají podobné členy. Odkazy v této části odkazují na členy třídy <xref:System.Windows.Controls.MediaElement>. Pokud není výslovně uvedeno jinak, mohou být členy propojené s ve třídě <xref:System.Windows.Controls.MediaElement> také nalezeny ve třídě <xref:System.Windows.Media.MediaPlayer>.  
  
 Chcete-li porozumět přehrávání multimédií v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], je nutné pochopit různé režimy, ve kterých lze přehrávat média. <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.MediaPlayer> lze použít ve dvou různých režimech médií, režimu nezávislého režimu a hodin. Režim multimédií určuje vlastnost <xref:System.Windows.Controls.MediaElement.Clock%2A>. Pokud je <xref:System.Windows.Controls.MediaElement.Clock%2A> `null`, je objekt média v nenezávislém režimu. Pokud <xref:System.Windows.Controls.MediaElement.Clock%2A> je jiný než null, je objekt média v režimu hodiny. Ve výchozím nastavení jsou mediální objekty v nezávislém režimu.  
  
### <a name="independent-mode"></a>Nezávislý režim  
 V nezávislém režimu Media Content Drives přehrávání médií. Nezávislý režim umožňuje následující možnosti:  
  
- <xref:System.Uri> médií je možné přímo zadat.  
  
- Přehrávání médií je možné přímo ovládat.  
  
- Je možné upravit <xref:System.Windows.Controls.MediaElement.Position%2A> a vlastnosti <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> médií.  
  
 Médium je načteno buď nastavením vlastnosti <xref:System.Windows.Controls.MediaElement.Source%2A> objektu <xref:System.Windows.Controls.MediaElement>, nebo voláním metody <xref:System.Windows.Media.MediaPlayer.Open%2A> objektu <xref:System.Windows.Media.MediaPlayer>.  
  
 Chcete-li ovládat přehrávání médií v nezávislém režimu, lze použít metody ovládacího prvku Media Object. K dispozici jsou metody ovládacího prvku <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>a <xref:System.Windows.Controls.MediaElement.Stop%2A>. Pro <xref:System.Windows.Controls.MediaElement>interaktivní řízení pomocí těchto metod je k dispozici pouze v případě, že je <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> nastavena na <xref:System.Windows.Controls.MediaState.Manual>. Tyto metody nejsou k dispozici, pokud je objekt média v režimu hodin.  
  
 Příklad nezávislého režimu najdete v tématu [řízení a MediaElement (přehrát, pozastavit, zastavit, svazek a rychlost)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) .  
  
### <a name="clock-mode"></a>Režim hodin  
 V režimu hodin <xref:System.Windows.Media.MediaTimeline> jednotky přehrávání médií. Režim hodin má následující vlastnosti:  
  
- <xref:System.Uri> média je nepřímo nastaveno prostřednictvím <xref:System.Windows.Media.MediaTimeline>.  
  
- Přehrávání multimédií se dá řídit hodinami. Řídicí metody objektu multimédia nelze použít.  
  
- Médium se načte nastavením vlastnosti <xref:System.Windows.Media.MediaTimeline.Source%2A> objektu <xref:System.Windows.Media.MediaTimeline>, vytvořením času z časové osy a přiřazením času objektu multimédia. Médium je také načteno tímto způsobem, když <xref:System.Windows.Media.MediaTimeline> uvnitř <xref:System.Windows.Media.Animation.Storyboard> cílí na <xref:System.Windows.Controls.MediaElement>.  
  
 Chcete-li ovládat přehrávání médií v režimu hodin, je nutné použít metody ovládacího prvku <xref:System.Windows.Media.Animation.ClockController>. <xref:System.Windows.Media.Animation.ClockController> se získá z vlastnosti <xref:System.Windows.Media.Animation.ClockController> <xref:System.Windows.Media.MediaClock>. Pokud se pokusíte použít metody ovládacího prvku <xref:System.Windows.Controls.MediaElement> nebo <xref:System.Windows.Media.MediaPlayer> v režimu hodin, bude vyvolána <xref:System.InvalidOperationException>.  
  
 Další informace o hodinách a časových osách najdete v [přehledu animace](animation-overview.md) .  
  
 Příklad režimu hodin naleznete v tématu [řízení MediaElement pomocí scénáře](how-to-control-a-mediaelement-by-using-a-storyboard.md) .  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement – třída  
 Přidání médií do aplikace je jednoduché jako přidání ovládacího prvku <xref:System.Windows.Controls.MediaElement> do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aplikace a poskytnutí <xref:System.Uri> na médium, které chcete zahrnout. V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]se podporují všechny typy médií podporované Microsoft Windows Media Player 10. Následující příklad ukazuje jednoduché použití <xref:System.Windows.Controls.MediaElement> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 V této ukázce se médium automaticky přehrává ihned po jeho načtení. Po přehrání média se médium zavře a všechny mediální prostředky se uvolní (včetně paměti videa). Toto je výchozí chování objektu <xref:System.Windows.Controls.MediaElement> a je ovládáno vlastnostmi <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>.  
  
### <a name="controlling-a-mediaelement"></a>Řízení MediaElement  
 Vlastnosti <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> řídí chování <xref:System.Windows.Controls.MediaElement> při <xref:System.Windows.FrameworkElement.IsLoaded%2A> `true` nebo `false`v uvedeném pořadí. <xref:System.Windows.Controls.MediaState> vlastností jsou nastaveny tak, aby ovlivnily chování přehrávání multimédií. Například výchozí <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> je <xref:System.Windows.Controls.MediaState.Play> a výchozí <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Close>. To znamená, že jakmile se <xref:System.Windows.Controls.MediaElement> načte a předvádění se dokončí, médium se začne přehrávat. Po dokončení přehrávání se média zavřou a uvolní se všechny mediální prostředky.  
  
 Vlastnosti <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> nejsou jediným způsobem, jak ovládat přehrávání médií. V režimu hodin můžou hodiny řídit <xref:System.Windows.Controls.MediaElement> a interaktivní ovládací prvky mají kontrolu, když je <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement> zpracovává tuto soutěž pro řízení hodnocením následujících priorit.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Na místě, když se uvolní médium. Tím se zajistí, že se všechny mediální prostředky vydávají ve výchozím nastavení, a to i v případě, že je k <xref:System.Windows.Controls.MediaElement>přidružená <xref:System.Windows.Media.MediaClock>.  
  
2. <xref:System.Windows.Media.MediaClock>. Na místě, kde médium obsahuje <xref:System.Windows.Controls.MediaElement.Clock%2A>. Pokud je médium odpojené, <xref:System.Windows.Media.MediaClock> se projeví, dokud <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>. Režim hodin vždy Přepisuje nahrané chování <xref:System.Windows.Controls.MediaElement>.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. V případě, že je médium načteno.  
  
4. Metody interaktivního ovládacího prvku. V případě, že je <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>. K dispozici jsou metody ovládacího prvku <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>a <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Zobrazení MediaElement  
 Chcete-li zobrazit <xref:System.Windows.Controls.MediaElement> musí mít obsah k vykreslení a bude mít <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> vlastnosti nastaveny na nulu, dokud není načten obsah. U zvukového obsahu jsou tyto vlastnosti vždycky nulové. V případě obsahu videa se po vyvolání události <xref:System.Windows.Controls.MediaElement.MediaOpened> <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> nahlásí velikost načteného média. To znamená, že dokud nebude médium načteno, <xref:System.Windows.Controls.MediaElement> nebude mít žádný fyzický prostor v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], pokud nejsou nastaveny vlastnosti <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A>.  
  
 Nastavení <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> vlastností způsobí, že se média roztáhnou, aby se vyplnila plocha zadaná pro <xref:System.Windows.Controls.MediaElement>. Chcete-li zachovat původní poměr stran, musí být buď vlastnost <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A> nastavena, ale ne obojí. Nastavení <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> vlastností způsobí, že médium bude přítomno v pevné velikosti prvku, která nemusí být žádoucí.  
  
 Aby nedošlo k elementu pevné velikosti, který může [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] předvádět médium. To se provádí nastavením <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> na <xref:System.Windows.Controls.MediaState.Play> nebo <xref:System.Windows.Controls.MediaState.Pause>. Ve stavu <xref:System.Windows.Controls.MediaState.Pause> bude médium předem navráceno a bude prezentovat první snímek. Ve stavu <xref:System.Windows.Controls.MediaState.Play> bude médium předvedeno a začne hrát.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer – třída  
 Kde je jako třída <xref:System.Windows.Controls.MediaElement> prvkem rozhraní, je třída <xref:System.Windows.Media.MediaPlayer> navržena pro použití v objektech <xref:System.Windows.Media.Drawing>. Kreslení objektů se používá, když můžete pomocí funkcí na úrovni rozhraní, které nabízí, získat výhody výkonu nebo když potřebujete <xref:System.Windows.Freezable> funkce. <xref:System.Windows.Media.MediaPlayer> vám umožní využít tyto funkce při poskytování mediálního obsahu ve vašich aplikacích. Podobně jako <xref:System.Windows.Controls.MediaElement><xref:System.Windows.Media.MediaPlayer> lze použít v nezávislém nebo hodinovém režimu, ale nemá Nenačtené a načteelné stavy objektu <xref:System.Windows.Controls.MediaElement>. Tím se sníží složitost ovládacího prvku přehrávání <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Řízení MediaPlayer  
 Vzhledem k tomu, že <xref:System.Windows.Media.MediaPlayer> je Bezstavová, existují dva způsoby, jak ovládat přehrávání médií.  
  
1. Metody interaktivního ovládacího prvku. V případě, že je v nezávislém režimu (`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A> vlastnost).  
  
2. <xref:System.Windows.Media.MediaClock>. Na místě, kde médium obsahuje <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Zobrazení MediaPlayer  
 Technicky, <xref:System.Windows.Media.MediaPlayer> nelze zobrazit, protože nemá žádnou fyzickou reprezentaci. Dá se ale použít k prezentaci médií v <xref:System.Windows.Media.Drawing> pomocí <xref:System.Windows.Media.VideoDrawing> třídy. Následující příklad ukazuje použití <xref:System.Windows.Media.VideoDrawing> k zobrazení média.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.Drawing>ch objektech naleznete v tématu [Přehled nakreslených objektů](drawing-objects-overview.md) .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.DrawingGroup>
- [Rozložení](../advanced/layout.md)
- [Témata s postupy](audio-and-video-how-to-topics.md)
