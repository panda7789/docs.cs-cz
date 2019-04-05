---
title: Grafika a multimédia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: 87ae55c454a72797569de4cd944984ba18c3b2ca
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055063"
---
# <a name="graphics-and-multimedia"></a>Grafika a multimédia
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje podporu pro multimédia, vektorovou grafiku, animace a obsahu složení, a usnadňuje vývojářům umožní tvořit zajímavou uživatelská rozhraní a obsah. Pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], můžete vytvořit vektorovou grafiku nebo komplexní animace a do svých aplikací integrovat média.  
  
 Toto téma představuje funkce obrázky, animace a média [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které umožňují přidat grafiky, efektu přechodu, zvuku a videa pro vaše aplikace.  
  
> [!NOTE]
>  Použití typů WPF ve službě Windows se důrazně nedoporučuje. Pokud se pokusíte použít typy WPF ve službě Windows, služba nemusí fungovat podle očekávání.   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Co je nového v grafika a multimédia v subsystému WPF 4  
 Několik se provedly změny související grafika a animace.  
  
-   Zaokrouhlení rozložení  
  
     Při okraje objektu spadá uprostřed pixelů zařízení, můžete vytvořit systém grafiky DPI nezávislé vykreslování artefaktů, jako je například fuzzy nebo poloprůhledného hrany. Předchozí verze WPF zahrnuté přitahování a pomáhaly zvládat tento případ. Silverlight 2 zavedené zaokrouhlení rozložení, což je jiný způsob, jak se mají přesunout prvky tak, aby se okraje na hranicích celý pixelů. Nyní podporuje rozložení zaokrouhlení s WPF <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> přidružená vlastnost na <xref:System.Windows.FrameworkElement>.  
  
-   Sestavení v mezipaměti  
  
     Pomocí nového <xref:System.Windows.Media.BitmapCache> a <xref:System.Windows.Media.BitmapCacheBrush> třídy, můžete ukládat do mezipaměti komplexní součástí vizuálního stromu jako rastrový obrázek a výrazně zvýšit doba vykreslování. Rastrový obrázek stále poměrně rychle reaguje na vstup uživatele, jako je například kliknutí myší, a na další prvky, stejně jako všechny stopy malovat.  
  
-   Podpora funkce Pixel Shader 3  
  
     WPF 4 sestavení nahoře <xref:System.Windows.Media.Effects.ShaderEffect> podpory dostupné ve WPF 3.5 SP1 tím, že aplikace pro zápis účinky pomocí Pixel Shader (PS) verze 3.0. Shader model PS 3.0 je složitější než PS 2.0, která umožňuje ještě větší vliv na podporovaný hardware.  
  
-   Funkce usnadnění  
  
     Můžete zvýšit animace s funkcí usnadnění, které poskytují větší kontrolu nad chováním animace. Například můžete použít <xref:System.Windows.Media.Animation.ElasticEase> do animace poskytnout pružné chování animace. Další informace najdete v tématu uvolnění typy v <xref:System.Windows.Media.Animation> oboru názvů.  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a>Grafika a vykreslování  
 WPF obsahuje podporu pro vysoce kvalitní 2D grafika. Funkce zahrnuje štětce, geometrie, obrázků, tvarů a transformace. Další informace najdete v tématu [grafiky](graphics.md). Podle vykreslení grafické prvky <xref:System.Windows.Media.Visual> třídy. Struktura vizuální objekty na obrazovce je popsán vizuálního stromu. Další informace najdete v tématu [přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).  
  
### <a name="2-d-shapes"></a>2D obrazce  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje knihovnu běžně používané, vykreslované uživatelem vektoru [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] tvary, třeba obdélníky a symbol tří teček, které ukazuje následující obrázek.  
  
 ![Symbol tří teček a obdélníky](./media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 Tyto vnitřní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tvary nejsou jenom tvarů: jsou programovatelný prvky, které implementují mnoho funkcí, které očekáváte od většiny běžných ovládacích prvků, které zahrnují klávesnice a myši. Následující příklad ukazuje, jak zpracovat <xref:System.Windows.UIElement.MouseUp> Událost aktivovaná po kliknutí <xref:System.Windows.Shapes.Ellipse> elementu.  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  x:Class="Window1" >  
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />  
</Window>  
```  
  
```csharp  
public partial class Window1  : Window  
{  
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)  
    {  
        MessageBox.Show("You clicked the ellipse!");  
    }  
}  
```  
  
```vb  
Partial Public Class Window1  
    Inherits Window  
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)  
        MessageBox.Show("You clicked the ellipse!")  
    End Sub  
End Class  
```  
  
 Následující obrázek znázorňuje výstup pro předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu.  
  
 ![Okno s textem "kliknutí na tři tečky&#33;"](./media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Další informace najdete v tématu [tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md). Úvodní ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
### <a name="2-d-geometries"></a>2D geometrie  
 Když [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obrazce, která [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje nestačí, můžete použít [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podpora geometrie a cesty k vytvoření vlastní. Následující obrázek ukazuje, jak můžete pomocí geometrie vytvoření tvarů, jako kreslicího štětce a další Galerie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy.  
  
 ![Různé možnosti použití cesty](./media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 Další informace najdete v tématu [přehled geometrie](geometry-overview.md). Úvodní ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
### <a name="2-d-effects"></a>2D efekty  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje knihovnu [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] třídy, které vám umožní vytvořit různé účinky. [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] Možnosti vykreslování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje vykreslení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které mají přechody, rastrových obrázků, kreseb a videa; a s nimi manipulovat s použitím otočení, škálování a zkosení. Následující obrázek poskytuje příklad mnoho efektů, můžete dosáhnout použitím [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] stopy.  
  
 ![Znázornění různých štětců](./media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 Další informace najdete v tématu [přehled štětců WPF](wpf-brushes-overview.md). Úvodní ukázku najdete v tématu [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a>3D vykreslování  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje sadu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] možnosti vykreslování, které se integrují s [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafické podpory v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vytvářet zajímavější rozložení, aby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], dat a jejich vizualizace. Na jednom konci spektra [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umožňuje vykreslit [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] bitové kopie na povrchy [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] tvary, které ukazuje následující obrázek.  
  
 ![Snímek obrazovky ukázkové Visual3D](./media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Další informace najdete v tématu [přehled 3D grafiky](3-d-graphics-overview.md). Úvodní ukázku najdete v tématu [ukázka 3D pevné](https://go.microsoft.com/fwlink/?LinkID=159964).  
  
<a name="animation"></a>   
## <a name="animation"></a>Animace  
 Použijte animaci k vytvoření ovládacích prvků a elementů růst, zatřeste, zprovozněte a fade; a vytvářejte zajímavé přechody stránek a další. Protože [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] povoluje pro animaci většinu vlastností, ne jenom můžete animace většinu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objekty, můžete použít také [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pro animaci vlastní objekty, které vytvoříte.  
  
 ![Bitové kopie animovaný datové krychle](./media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Další informace najdete v tématu [přehled animace](animation-overview.md). Úvodní ukázku najdete v tématu [animace příkladu Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
<a name="media"></a>   
## <a name="media"></a>Média  
 Obrázky, videa a zvuku způsoby média bohaté takzvané informace a uživatelské prostředí.  
  
### <a name="images"></a>Obrázky  
 Image, jako je například ikony, pozadí a dokonce i části animace, jsou základní součástí většinu aplikací. Protože často budete muset použít Image, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zpřístupňuje schopnost pracovat s nimi v mnoha různými způsoby. Následující obrázek znázorňuje pouze jedna z těchto způsobů.  
  
 ![Snímek obrazovky ukázkový používání stylů pro](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
 Další informace najdete v tématu [Imaging přehled](imaging-overview.md).  
  
### <a name="video-and-audio"></a>Videa a zvuku  
 Základní funkce grafické možnosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je poskytuje nativní podporu pro práci s multimédii, která zahrnuje videa a zvuku. Následující příklad ukazuje, jak vložit multimediální přehrávač do aplikace.  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement> dokáže přehrávání videa a zvuku a je možné rozšířit dostatečně umožňuje snadno vytvářet vlastní [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
 Další informace najdete v tématu [multimédia přehled](multimedia-overview.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Kreslení pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Postupy: Témata animace a časování](animation-and-timing-how-to-topics.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled multimédií](multimedia-overview.md)
