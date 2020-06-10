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
ms.openlocfilehash: ecc54ad9453343f6306b0133fa180abd0db46f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596420"
---
# <a name="graphics-and-multimedia"></a>Grafika a multimédia

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje podporu pro multimédia, vektorovou grafiku, animaci a kompozici obsahu, což vývojářům usnadňuje vytváření zajímavých uživatelských rozhraní a obsahu. Pomocí sady Visual Studio můžete vytvářet vektorová grafika nebo složitá animace a integrovat multimédia do svých aplikací.

V tomto tématu se seznámíte s grafickými, animačními a mediálními funkcemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , které umožňují přidat do aplikací grafiku, efekty přechodu, zvuk a video.

> [!NOTE]
> Použití typů WPF ve službě systému Windows se důrazně nedoporučuje. Pokud se pokusíte použít typy WPF ve službě systému Windows, služba nemusí fungovat podle očekávání.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Co je nového u grafiky a multimédií v WPF 4

V souvislosti s grafikou a animacemi byly provedeny některé změny.

- Zaoblení rozložení

  Když okraj objektu spadá do středu zařízení v pixelech, může grafický systém nezávislý na DPI vytvořit artefakty vykreslování, jako je rozmazaný nebo částečně transparentní okraj. Předchozí verze WPF zahrnovaly přichycení k pixelům, které vám pomůžou s tímto případem pracovat. Program Silverlight 2 představil zaoblení rozložení, což je jiný způsob, jak přesunout prvky tak, aby hrany klesly na celé celé pixelové hranice. WPF teď podporuje zaokrouhlování rozložení s <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> připojenou vlastností on <xref:System.Windows.FrameworkElement> .

- Kompozice v mezipaměti

  Pomocí nových <xref:System.Windows.Media.BitmapCache> <xref:System.Windows.Media.BitmapCacheBrush> tříd a můžete ukládat složitou část vizuálního stromu do mezipaměti a významně zlepšit dobu vykreslování. Rastrový obrázek zůstává reagovat na vstup uživatele, jako je například kliknutí myší, a můžete ho malovat na jiné prvky stejně jako u libovolného štětce.

- Podpora funkce Pixel Shader 3

  WPF 4 sestavuje na <xref:System.Windows.Media.Effects.ShaderEffect> podporu představené v wpf 3,5 SP1 tím, že umožňuje aplikacím zapisovat efekty pomocí funkce pixel shader (PS) verze 3,0. Model shaderu PS 3,0 je propracovanější než PS 2,0, který umožňuje ještě více efektů na podporovaném hardwaru.

- Funkce usnadnění

  Animace můžete vylepšit funkcemi usnadnění, což vám poskytne další kontrolu nad chováním animací. Například můžete použít na animaci a dát tak animaci k funkci <xref:System.Windows.Media.Animation.ElasticEase> pružiny. Další informace naleznete v tématu typy náběh a doběh v <xref:System.Windows.Media.Animation> oboru názvů.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Grafika a vykreslování

WPF zahrnuje podporu vysoce kvalitní 2D grafiky. Mezi tyto funkce patří štětce, geometrií, obrázky, tvary a transformace. Další informace najdete v tématu [Grafika](graphics.md). Vykreslování grafických prvků je založeno na <xref:System.Windows.Media.Visual> třídě. Struktura vizuálních objektů na obrazovce je popsána ve vizuálním stromu. Další informace naleznete v tématu [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).

### <a name="2d-shapes"></a>2D obrazce

WPF poskytuje knihovnu běžně používaných 2D 2D tvarů, jako jsou obdélníky a tři tečky, které jsou znázorněny na následujícím obrázku.

![Diagram znázorňující elipsy a obdélníky.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Tyto vnitřní tvary WPF nejsou pouze tvary: Jedná se o programovatelné prvky, které implementují mnoho funkcí, které očekáváte od nejběžnějších ovládacích prvků, které zahrnují vstup z klávesnice a myši. Následující příklad ukazuje, jak zpracovat <xref:System.Windows.UIElement.MouseUp> událost vyvolanou kliknutím na <xref:System.Windows.Shapes.Ellipse> prvek.

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

Následující ilustrace ukazuje výstup předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky a kódu na pozadí.

![Okno se zprávou, že jste klikli na elipsu!](./media/index/messagebox-text-output.png)

Další informace naleznete v tématu [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md). Úvodní vzorek naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).

### <a name="2d-geometries"></a>2D geometrií

Pokud 2D obrazce, které WPF poskytuje, nejsou dostačující, můžete použít podporu WPF pro geometrií a cesty a vytvořit vlastní. Následující obrázek ukazuje, jak lze použít geometrií k vytváření tvarů, jako štětec kresby a k vystřihování dalších prvků WPF.

![Snímek obrazovky znázorňující, jak můžete pomocí geometrií vytvořit obrazce.](./media/index/use-geometries-create-shapes.png)

Další informace najdete v tématu [geometrie Overview](geometry-overview.md). Úvodní ukázku najdete v tématu [geometrií Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).

### <a name="2d-effects"></a>2D efekty

WPF poskytuje knihovnu 2D tříd, které lze použít k vytvoření celé řady efektů. Funkce 2D vykreslování WPF poskytuje možnost malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které mají přechody, bitmapy, kresby a videa, a manipulovat s nimi pomocí rotace, škálování a zkosení. Následující ilustrace obsahuje příklad mnoha efektů, které lze dosáhnout pomocí štětců WPF.

![Ilustrace znázorňující různé prvky WPF štětců a malování.](./media/index/brushes-paint-elements.png)

Další informace najdete v tématu [Přehled štětců WPF](wpf-brushes-overview.md). Úvodní vzorek naleznete v tématu [Ukázka štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).

<a name="rendering"></a>

## <a name="3d-rendering"></a>Prostorové vykreslování

WPF poskytuje sadu 3D funkcí vykreslování, které se integrují s podporou 2D grafiky v WPF, aby bylo možné vytvořit zajímavější rozložení, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a vizualizaci dat. Na jednom konci spektra umožňuje WPF vykreslovat 2D obrázky na povrchu 3D tvarů, který ukazuje následující obrázek.

![Snímek obrazovky s ukázkou znázorňující tvary 3D s různými texturami](./media/index/visual-three-dimensional-shape.png)

Další informace najdete v tématu [Přehled 3D grafiky](3-d-graphics-overview.md). Úvodní vzorek najdete v tématu [Ukázka prostorových plných](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animace

Pomocí animace můžete měnit, protřepe, zesílit a mizet ovládací prvky a prvky. a k vytváření zajímavých přechodů stránky a dalších. Vzhledem k tomu, že WPF umožňuje animovat většinu vlastností, nestačí pouze animovat většinu objektů WPF, můžete také použít WPF k animaci vlastních objektů, které vytvoříte.

![Snímek obrazovky s animovanou datovou krychlí](./media/index/animate-custom-objects.png)

Další informace najdete v tématu [Přehled animací](animation-overview.md). Úvodní vzorek najdete v tématu [animace příklad Galerie](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

<a name="media"></a>

## <a name="media"></a>Média

Obrázky, videa a zvuky jsou mediální a bohatě náročné způsoby, jak vyjádřit informace a uživatelské prostředí.

### <a name="images"></a>Image

Obrázky, které obsahují ikony, pozadí a dokonce i části animací, jsou základní součástí většiny aplikací. Vzhledem k tomu, že je často potřeba použít image, WPF nabízí možnost pracovat s nimi různými způsoby. Následující ilustrace znázorňuje pouze jeden z těchto způsobů.

![Ukázka stylu snímku obrazovky](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Další informace najdete v tématu [Přehled imagí](imaging-overview.md).

### <a name="video-and-audio"></a>Video a zvuk

Základní funkcí grafických schopností WPF je poskytnout nativní podporu pro práci s multimédii, která zahrnuje video a zvuk. Následující příklad ukazuje, jak vložit přehrávač médií do aplikace.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>je schopný přehrávat video i zvuk a je dostatečně rozšiřitelný, aby bylo možné snadno vytvořit vlastní uživatelská rozhraní.

Další informace najdete v tématu [Přehled multimédií](multimedia-overview.md).

## <a name="see-also"></a>Viz také

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
