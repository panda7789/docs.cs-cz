---
title: Přehled multimédií
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 44059fe96a0deeda18f0abd9079100b55be98e77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929623"
---
# <a name="multimedia-overview"></a>Přehled multimédií
Funkce multimédií v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umožňují integrovat zvuk a video do svých aplikací, aby se zlepšila činnost koncového uživatele. V tomto tématu se seznámíte s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]funkcemi multimédií.  

<a name="mediaapi"></a>   
## <a name="media-api"></a>Rozhraní API pro multimédia  
 Třídy <xref:System.Windows.Controls.MediaElement> a<xref:System.Windows.Media.MediaPlayer> se používají k prezentaci zvukového nebo obrazového obsahu. Tyto třídy je možné řídit interaktivně nebo podle času. Tyto třídy lze použít na [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 ovládacích prvků pro přehrávání multimédií. Kterou třídu použijete, závisí na scénáři.  
  
 <xref:System.Windows.Controls.MediaElement>je, který je podporován rozložením a lze jej spotřebovat jako obsah mnoha ovládacích prvků. [](../advanced/layout.md) <xref:System.Windows.UIElement> Je také možné použít i [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] v kódu. <xref:System.Windows.Media.MediaPlayer>na druhé straně je navržen pro <xref:System.Windows.Media.Drawing> objekty a neobsahuje podporu rozložení. Médium načtené pomocí <xref:System.Windows.Media.MediaPlayer> lze prezentovat pouze <xref:System.Windows.Media.VideoDrawing> pomocí nebo <xref:System.Windows.Media.DrawingContext>přímo v interakci s. <xref:System.Windows.Media.MediaPlayer>nelze použít v jazyce XAML.  
  
 Další informace o vykreslování objektů a kontextu vykreslování naleznete v tématu [Přehled nakreslených objektů](drawing-objects-overview.md).  
  
> [!NOTE]
> Při distribuci médií do aplikace nemůžete použít mediální soubor jako prostředek projektu. V souboru projektu je nutné místo toho `Content` nastavit typ média na `CopyToOutputDirectory` `PreserveNewest` hodnotu nebo `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Režimy přehrávání multimédií  
  
> [!NOTE]
> <xref:System.Windows.Controls.MediaElement> A<xref:System.Windows.Media.MediaPlayer> mají podobné členy. Odkazy v této části odkazují na <xref:System.Windows.Controls.MediaElement> členy třídy. Pokud není výslovně uvedeno jinak, mohou být také <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> ve třídě nalezeny členy spojené s ve třídě.  
  
 Pro lepší pochopení přehrávání multimédií [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]v nástroji je potřeba pochopit různé režimy, ve kterých se dá médium přehrát. Obojí <xref:System.Windows.Controls.MediaElement> i<xref:System.Windows.Media.MediaPlayer> lze použít ve dvou různých režimech médií, režim nezávislého režimu a hodin. Režim multimédií je určený <xref:System.Windows.Controls.MediaElement.Clock%2A> vlastností. V takovém případě <xref:System.Windows.Controls.MediaElement.Clock%2A> je objekt média v nenezávislém režimu. `null` <xref:System.Windows.Controls.MediaElement.Clock%2A> Pokud není null, je objekt média v režimu hodiny. Ve výchozím nastavení jsou mediální objekty v nezávislém režimu.  
  
### <a name="independent-mode"></a>Nezávislý režim  
 V nezávislém režimu Media Content Drives přehrávání médií. Nezávislý režim umožňuje následující možnosti:  
  
- Médium je <xref:System.Uri> možné přímo zadat.  
  
- Přehrávání médií je možné přímo ovládat.  
  
- Je <xref:System.Windows.Controls.MediaElement.Position%2A> možné upravit <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> vlastnosti a média.  
  
 Médium je načteno <xref:System.Windows.Controls.MediaElement> buď nastavením <xref:System.Windows.Controls.MediaElement.Source%2A> <xref:System.Windows.Media.MediaPlayer> vlastnosti objektu, nebo voláním <xref:System.Windows.Media.MediaPlayer.Open%2A> metody objektu.  
  
 Chcete-li ovládat přehrávání médií v nezávislém režimu, lze použít metody ovládacího prvku Media Object. K dispozici jsou <xref:System.Windows.Controls.MediaElement.Play%2A>metody ovládacího prvku <xref:System.Windows.Controls.MediaElement.Close%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Stop%2A>a. Pro <xref:System.Windows.Controls.MediaElement>interaktivní řízení pomocí těchto metod je k dispozici pouze v <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> případě, že <xref:System.Windows.Controls.MediaState.Manual>je nastavena na. Tyto metody nejsou k dispozici, pokud je objekt média v režimu hodin.  
  
 Příklad nezávislého režimu najdete v tématu [řízení a MediaElement (přehrát, pozastavit, zastavit, svazek a rychlost)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) .  
  
### <a name="clock-mode"></a>Režim hodin  
 V režimu <xref:System.Windows.Media.MediaTimeline> hodiny jednotka přehrávání médií. Režim hodin má následující vlastnosti:  
  
- Médium je nepřímo nastaveno <xref:System.Windows.Media.MediaTimeline>prostřednictvím. <xref:System.Uri>  
  
- Přehrávání multimédií se dá řídit hodinami. Řídicí metody objektu multimédia nelze použít.  
  
- Médium je načteno nastavením <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaTimeline.Source%2A> vlastnosti objektu, vytvořením času z časové osy a přiřazením času objektu média. Médium je načteno také <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> v případě, že v cíli a <xref:System.Windows.Controls.MediaElement>.  
  
 Chcete-li ovládat přehrávání médií v režimu hodin <xref:System.Windows.Media.Animation.ClockController> , je nutné použít metody ovládacího prvku. A <xref:System.Windows.Media.Animation.ClockController> je získán <xref:System.Windows.Media.Animation.ClockController> z vlastnosti <xref:System.Windows.Media.MediaClock>. Pokud se pokusíte použít metody <xref:System.Windows.Controls.MediaElement> ovládacího prvku objektu nebo <xref:System.Windows.Media.MediaPlayer> <xref:System.InvalidOperationException> v režimu hodin, bude vyvolána výjimka.  
  
 Další informace o hodinách a časových osách najdete v [přehledu animace](animation-overview.md) .  
  
 Příklad režimu hodin naleznete v tématu [řízení MediaElement pomocí scénáře](how-to-control-a-mediaelement-by-using-a-storyboard.md) .  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement – třída  
 Přidání médií do aplikace je jednoduché jako přidání <xref:System.Windows.Controls.MediaElement> ovládacího prvku [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplikace a poskytnutí <xref:System.Uri> média, které chcete zahrnout. Všechny typy médií, které [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] podporuje 10, jsou [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]podporované v. Následující příklad ukazuje jednoduché použití <xref:System.Windows.Controls.MediaElement> v nástroji v. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 V této ukázce se médium automaticky přehrává ihned po jeho načtení. Po přehrání média se médium zavře a všechny mediální prostředky se uvolní (včetně paměti videa). Toto je výchozí chování <xref:System.Windows.Controls.MediaElement> objektu a je řízeno <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> vlastnostmi a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> .  
  
### <a name="controlling-a-mediaelement"></a>Řízení MediaElement  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Vlastnosti a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> určují<xref:System.Windows.FrameworkElement.IsLoaded%2A> chování funkce whennebo`false`vuvedeném pořadí. `true` <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.MediaState> Vlastnosti jsou nastaveny tak, aby ovlivnily chování přehrávání multimédií. Výchozí <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> hodnota je <xref:System.Windows.Controls.MediaState.Play> například a výchozí <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> hodnota je <xref:System.Windows.Controls.MediaState.Close>. To znamená, že <xref:System.Windows.Controls.MediaElement> Jakmile se načte a předvádění dokončí, médium se začne přehrávat. Po dokončení přehrávání se média zavřou a uvolní se všechny mediální prostředky.  
  
 Vlastnosti <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> a<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> nejsou jediným způsobem, jak ovládat přehrávání multimédií. V režimu hodin můžou hodiny ovládat <xref:System.Windows.Controls.MediaElement> ovládací prvky a interaktivní ovládací prvky, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> když jsou <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement>zpracovává tuto soutěž pro řízení vyhodnocením následujících priorit.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Na místě, když se uvolní médium. Tím se zajistí, že se všechny mediální prostředky vydávají ve výchozím nastavení <xref:System.Windows.Media.MediaClock> , a to i <xref:System.Windows.Controls.MediaElement>v případě, že je přidružená k.  
  
2. <xref:System.Windows.Media.MediaClock>. V případě, že médium má <xref:System.Windows.Controls.MediaElement.Clock%2A>. Pokud je médium uvolněné, projeví <xref:System.Windows.Media.MediaClock> se to tak dlouho <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> , dokud je <xref:System.Windows.Controls.MediaState.Manual>. Režim hodin vždy Přepisuje nahrané chování <xref:System.Windows.Controls.MediaElement>.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. V případě, že je médium načteno.  
  
4. Metody interaktivního ovládacího prvku. Na místě, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> kdy <xref:System.Windows.Controls.MediaState.Manual>je. K dispozici jsou <xref:System.Windows.Controls.MediaElement.Play%2A>metody ovládacího prvku <xref:System.Windows.Controls.MediaElement.Close%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Stop%2A>a.  
  
### <a name="displaying-a-mediaelement"></a>Zobrazení MediaElement  
 Chcete-li <xref:System.Windows.Controls.MediaElement> zobrazit, musí mít obsah k vykreslení a bude <xref:System.Windows.FrameworkElement.ActualWidth%2A> mít vlastnost a <xref:System.Windows.FrameworkElement.ActualHeight%2A> vlastnosti nastavené na hodnotu nula, dokud nebude načten obsah. U zvukového obsahu jsou tyto vlastnosti vždycky nulové. V případě obsahu videa se po <xref:System.Windows.Controls.MediaElement.MediaOpened> <xref:System.Windows.FrameworkElement.ActualWidth%2A> vyvolání události a <xref:System.Windows.FrameworkElement.ActualHeight%2A> nahlásí velikost načteného média. To znamená, že dokud nebude médium načteno <xref:System.Windows.Controls.MediaElement> , nebude zabírat žádné fyzické místo [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] v, pokud <xref:System.Windows.FrameworkElement.Width%2A> nejsou nastaveny <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti nebo.  
  
 Nastavení vlastností <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.MediaElement>a způsobí, že se média roztáhnou, aby se vyplnila oblast zadaná pro. <xref:System.Windows.FrameworkElement.Width%2A> Aby se zachoval původní poměr stran, musí být vlastnost nebo <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> nastavená na hodnotu, ale ne obojí. Nastavení vlastností <xref:System.Windows.FrameworkElement.Height%2A> a způsobí, že médium bude přítomno v pevné velikosti prvků, která nemusí být žádoucí. <xref:System.Windows.FrameworkElement.Width%2A>  
  
 Aby nedošlo k elementu pevné velikosti, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] který může předvádět médium. To se provádí nastavením <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Play> na nebo <xref:System.Windows.Controls.MediaState.Pause>. <xref:System.Windows.Controls.MediaState.Pause> Ve stavu bude médium předem navráceno a bude prezentovat první snímek. <xref:System.Windows.Controls.MediaState.Play> Ve stavu bude médium předvedeno a začne hrát.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer – třída  
 Tam, kde <xref:System.Windows.Media.Drawing> je <xref:System.Windows.Controls.MediaElement> třída prvkem architektury, je Třídanavrženapropoužití<xref:System.Windows.Media.MediaPlayer> v objektech. Vykreslování objektů se používá, když můžete využít funkce na úrovni rozhraní a získat tak výhody výkonu nebo když <xref:System.Windows.Freezable> potřebujete funkce. <xref:System.Windows.Media.MediaPlayer>umožňuje využít tyto funkce při poskytování mediálního obsahu ve vašich aplikacích. Podobně <xref:System.Windows.Controls.MediaElement>jako <xref:System.Windows.Media.MediaPlayer> , lze použít v nezávislém nebo hodinovém režimu, <xref:System.Windows.Controls.MediaElement> ale nemá nenačtený a načtený stav objektu. Tím se sníží složitost <xref:System.Windows.Media.MediaPlayer>ovládacího prvku přehrávání.  
  
### <a name="controlling-mediaplayer"></a>Řízení MediaPlayer  
 Protože <xref:System.Windows.Media.MediaPlayer> je stav bez stavu, existují dva způsoby, jak ovládat přehrávání médií.  
  
1. Metody interaktivního ovládacího prvku. V případě v nezávislém režimu (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> vlastnost).  
  
2. <xref:System.Windows.Media.MediaClock>. V případě, že médium má <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Zobrazení MediaPlayer  
 Technicky, <xref:System.Windows.Media.MediaPlayer> nelze zobrazit, protože nemá žádné fyzické reprezentace. Lze ji však použít k prezentaci médií v <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.VideoDrawing> nástroji pomocí třídy. Následující příklad ukazuje použití a <xref:System.Windows.Media.VideoDrawing> k zobrazení média.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Další informace o <xref:System.Windows.Media.Drawing> objektech naleznete v tématu [Přehled nakreslených objektů](drawing-objects-overview.md) .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.DrawingGroup>
- [Rozložení](../advanced/layout.md)
- [Témata s postupy](audio-and-video-how-to-topics.md)
