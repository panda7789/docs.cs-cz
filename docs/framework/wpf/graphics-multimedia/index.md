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
ms.openlocfilehash: 8636afcc5b63b71dc729812a7f3eb4945ba49494
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112034"
---
# <a name="graphics-and-multimedia"></a>Grafika a multimédia

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje podporu pro multimédia, vektorovou grafiku, animaci a kompozici obsahu, což vývojářům usnadňuje vytváření zajímavých uživatelských rozhraní a obsahu. Pomocí sady Visual Studio můžete vytvářet vektorovou grafiku nebo složité animace a integrovat média do aplikací.

Toto téma představuje grafické, animační [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a mediální funkce aplikace , které umožňují přidávat grafiku, přechodové efekty, zvuk a video do aplikací.

> [!NOTE]
> Použití wpf typů ve službě systému Windows se důrazně nedoporučuje. Pokud se pokusíte použít wpf typy ve službě systému Windows, služba nemusí fungovat podle očekávání.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Co je nového s grafikou a multimédii ve WPF 4

Bylo provedeno několik změn týkajících se grafiky a animací.

- Zaokrouhlení rozložení

  Když okraj objektu spadne uprostřed zařízení s obrazovými body, grafický systém nezávislý na DPI může vytvářet artefakty vykreslování, například rozmazané nebo poloprůhledné okraje. Předchozí verze WPF zahrnuty pixel přichycení pomoci zpracovat tento případ. Program Silverlight 2 zavedl zaokrouhlení rozvržení, což je další způsob, jak přesunout prvky tak, aby okraje spadaly na hranice celých obrazových bodů. WPF nyní podporuje zaokrouhlení rozložení s připojenou <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> vlastností na <xref:System.Windows.FrameworkElement>.

- Složení uložené v mezipaměti

  Pomocí nové <xref:System.Windows.Media.BitmapCache> a <xref:System.Windows.Media.BitmapCacheBrush> třídy, můžete ukládat do mezipaměti komplexní část vizuálního stromu jako rastrový obrázek a výrazně zlepšit dobu vykreslování. Bitmapa zůstává reagovat na vstup uživatele, jako je například kliknutí myší, a můžete malovat na jiné prvky, stejně jako jakýkoli štětec.

- Podpora pro Pixel Shader 3

  WPF 4 staví na <xref:System.Windows.Media.Effects.ShaderEffect> podpoře zavedené v WPF 3.5 SP1 tím, že umožňuje aplikacím psát efekty pomocí Pixel Shader (PS) verze 3.0. Model shaderu PS 3.0 je sofistikovanější než PS 2.0, což umožňuje ještě více efektů na podporovaný hardware.

- Funkce usnadnění

  Můžete vylepšit animace s funkcemi náběhu/doběhu, které poskytují další kontrolu nad chováním animací. Můžete například použít <xref:System.Windows.Media.Animation.ElasticEase> a animaci, která animaci poskytne pružné chování. Další informace naleznete v náběh/doběhu typy v oboru <xref:System.Windows.Media.Animation> názvů.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Grafika a vykreslování

WPF obsahuje podporu pro vysoce kvalitní 2D grafiku. Funkce zahrnuje stopy, geometrie, obrazy, tvary a transformace. Další informace naleznete v [tématu Graphics](graphics.md). Vykreslování grafických prvků je založeno na <xref:System.Windows.Media.Visual> třídě. Struktura vizuálních objektů na obrazovce je popsána vizuálním stromem. Další informace naleznete v [tématu Přehled vykreslení grafiky WPF](wpf-graphics-rendering-overview.md).

### <a name="2d-shapes"></a>2D obrazce

WPF poskytuje knihovnu běžně používaných vektorově kreslených 2D tvarů, jako jsou obdélníky a elipsy, které ukazují následující obrázek.

![Diagram znázorňující elipsy a obdélníky.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Tyto vnitřní wpf tvary nejsou pouze tvary: jsou programovatelné prvky, které implementují mnoho funkcí, které očekáváte od většiny běžných ovládacích prvků, které zahrnují vstup klávesnice a myši. Následující příklad ukazuje, jak <xref:System.Windows.UIElement.MouseUp> zpracovat událost <xref:System.Windows.Shapes.Ellipse> vydopravené klepnutím na prvek.

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

Následující obrázek znázorňuje výstup [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro předchozí značky a kód na pozadí.

![Okno se zprávou s nápisem "Klikli jste na elipsu!"](./media/index/messagebox-text-output.png)

Další informace naleznete [v tématu Obrazce a základní výkres v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md). Úvodní ukázka viz [Ukázka prvků tvarů](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).

### <a name="2d-geometries"></a>2D geometrie

Pokud 2D obrazce, které poskytuje WPF, nejsou dostatečné, můžete použít podporu WPF pro geometrie a cesty k vytvoření vlastní. Následující obrázek znázorňuje, jak můžete pomocí geometrií vytvářet tvary jako stopu výkresu a oříznout další prvky WPF.

![Snímek obrazovky znázorňující, jak můžete k vytváření obrazců použít geometrie.](./media/index/use-geometries-create-shapes.png)

Další informace naleznete v [tématu Přehled geometrie](geometry-overview.md). Úvodní vzorek viz [Vzorek geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).

### <a name="2d-effects"></a>2D efekty

WPF poskytuje knihovnu 2D tříd, které můžete použít k vytvoření různých efektů. Schopnost 2D vykreslování [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] WPF umožňuje malovat prvky, které mají přechody, rastrové obrázky, výkresy a videa; a manipulovat s nimi pomocí otočení, změny velikosti a zkosení. Následující obrázek uvádí příklad mnoha efektů, kterých můžete dosáhnout pomocí stop WPF.

![Obrázek znázorňující různé stopy WPF a prvky malby.](./media/index/brushes-paint-elements.png)

Další informace naleznete v tématu [Přehled stop y WPF](wpf-brushes-overview.md). Úvodní vzorek viz [Vzorek štětců](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).

<a name="rendering"></a>

## <a name="3d-rendering"></a>3D vykreslování

WPF poskytuje sadu funkcí 3D vykreslování, které se integrují [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s podporou 2D grafiky ve WPF, abyste mohli vytvořit více vzrušujícího rozložení a vizualizace dat. Na jednom konci spektra umožňuje WPF vykreslit 2D obrazy na povrchy 3D tvarů, což ukazuje následující obrázek.

![Snímek obrazovky s ukázkou 3D obrazců s různými texturami](./media/index/visual-three-dimensional-shape.png)

Další informace naleznete v tématu [Přehled 3D grafiky](3-d-graphics-overview.md). Úvodní vzorek viz [3D vzorek těles](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animace

Pomocí animace můžete provádět růst, chvění, otáčení a slábnutí ovládacích prvků a prvků; a vytvářet zajímavé přechody stránek a další. Vzhledem k tomu, že WPF umožňuje animovat většinu vlastností, můžete nejen animovat většinu objektů WPF, můžete také použít WPF k animaci vlastních objektů, které vytvoříte.

![Snímek obrazovky s animovanou krychli](./media/index/animate-custom-objects.png)

Další informace naleznete v [tématu Přehled animace](animation-overview.md). Úvodní ukázku naleznete v galerii [příkladů animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

<a name="media"></a>

## <a name="media"></a>Média

Obrázky, video a zvuk jsou způsoby, jak přenášet informace a uživatelské prostředí bohaté na média.

### <a name="images"></a>Image

Obrázky, které obsahují ikony, pozadí a dokonce i části animací, jsou základní součástí většiny aplikací. Vzhledem k tomu, že často potřebujete používat obrázky, WPF zveřejňuje schopnost pracovat s nimi různými způsoby. Následující obrázek znázorňuje pouze jeden z těchto způsobů.

![Ukázkový snímek obrazovky s stylingem](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Další informace naleznete v [tématu Přehled zpracování obrázků](imaging-overview.md).

### <a name="video-and-audio"></a>Video a zvuk

Základním rysem grafických schopností WPF je poskytnout nativní podporu pro práci s multimédii, která zahrnuje video a audio. Následující příklad ukazuje, jak vložit přehrávač médií do aplikace.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>je schopen přehrávat video i zvuk a je dostatečně rozšiřitelný, aby umožnil snadné vytváření vlastních ubru.

Další informace naleznete v přehledu [multimédií](multimedia-overview.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Postupy: Témata animace a časování](animation-and-timing-how-to-topics.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled multimédií](multimedia-overview.md)
