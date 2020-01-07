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
ms.openlocfilehash: f9d27ce50376c3a494a546a23cd5d7409b4c475a
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636624"
---
# <a name="graphics-and-multimedia"></a>Grafika a multimédia

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje podporu pro multimédia, vektorovou grafiku, animaci a kompozici obsahu, což vývojářům usnadňuje vytváření zajímavých uživatelských rozhraní a obsahu. Pomocí sady Visual Studio můžete vytvářet vektorová grafika nebo složitá animace a integrovat multimédia do svých aplikací.

V tomto tématu se seznámíte s grafickými, animačními a mediálními funkcemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které umožňují přidat do svých aplikací grafiku, efekty přechodu, zvuk a video.

> [!NOTE]
> Použití typů WPF ve službě systému Windows se důrazně nedoporučuje. Pokud se pokusíte použít typy WPF ve službě systému Windows, služba nemusí fungovat podle očekávání.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Co je nového u grafiky a multimédií v WPF 4

V souvislosti s grafikou a animacemi byly provedeny některé změny.

- Zaoblení rozložení

  Když okraj objektu spadá do středu zařízení v pixelech, může grafický systém nezávislý na DPI vytvořit artefakty vykreslování, jako je rozmazaný nebo částečně transparentní okraj. Předchozí verze WPF zahrnovaly přichycení k pixelům, které vám pomůžou s tímto případem pracovat. Program Silverlight 2 představil zaoblení rozložení, což je jiný způsob, jak přesunout prvky tak, aby hrany klesly na celé celé pixelové hranice. WPF teď podporuje zaokrouhlování rozložení s vlastností <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> připojenou v <xref:System.Windows.FrameworkElement>.

- Kompozice v mezipaměti

  Pomocí nových tříd <xref:System.Windows.Media.BitmapCache> a <xref:System.Windows.Media.BitmapCacheBrush> můžete složitou část vizuálního stromu ukládat do mezipaměti a významně zlepšit dobu vykreslování. Rastrový obrázek zůstává reagovat na vstup uživatele, jako je například kliknutí myší, a můžete ho malovat na jiné prvky stejně jako u libovolného štětce.

- Podpora funkce Pixel Shader 3

  WPF 4 sestavuje podporu <xref:System.Windows.Media.Effects.ShaderEffect> zavedenou v WPF 3,5 SP1 tím, že umožňuje aplikacím zapisovat efekty pomocí funkce pixel shader (PS) verze 3,0. Model shaderu PS 3,0 je propracovanější než PS 2,0, který umožňuje ještě více efektů na podporovaném hardwaru.

- Funkce usnadnění

  Animace můžete vylepšit funkcemi usnadnění, což vám poskytne další kontrolu nad chováním animací. Můžete například použít <xref:System.Windows.Media.Animation.ElasticEase> k animaci, aby animace mohla působit na jaře. Další informace naleznete v tématu typy náběh a doběh v oboru názvů <xref:System.Windows.Media.Animation>.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Grafika a vykreslování

WPF zahrnuje podporu pro vysoce kvalitní 2D grafiku. Mezi tyto funkce patří štětce, geometrií, obrázky, tvary a transformace. Další informace najdete v tématu [Grafika](graphics.md). Vykreslování grafických prvků je založeno na třídě <xref:System.Windows.Media.Visual>. Struktura vizuálních objektů na obrazovce je popsána ve vizuálním stromu. Další informace naleznete v tématu [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).

### <a name="2-d-shapes"></a>2D obrazce

WPF poskytuje knihovnu běžně používaných dvojrozměrných 2D tvarů, jako jsou obdélníky a tři tečky, které jsou znázorněny na následujícím obrázku.

![Diagram znázorňující elipsy a obdélníky.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Tyto vnitřní tvary WPF nejsou pouze tvary: Jedná se o programovatelné prvky, které implementují mnoho funkcí, které očekáváte od nejběžnějších ovládacích prvků, které zahrnují vstup z klávesnice a myši. Následující příklad ukazuje, jak zpracovat událost <xref:System.Windows.UIElement.MouseUp> vyvolána kliknutím na <xref:System.Windows.Shapes.Ellipse> elementu.

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

Následující ilustrace ukazuje výstup pro předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky a kód na pozadí.

![Okno se zprávou, že jste klikli na elipsu!](./media/index/messagebox-text-output.png)

Další informace naleznete v tématu [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md). Úvodní vzorek naleznete v tématu [Ukázka prvků tvaru](https://go.microsoft.com/fwlink/?LinkID=160037).

### <a name="2-d-geometries"></a>2D geometrií

Když 2D obrazce, které WPF poskytuje, nejsou dostačující, můžete použít podporu WPF pro geometrií a cesty a vytvořit vlastní. Následující obrázek ukazuje, jak lze použít geometrií k vytváření tvarů, jako štětec kresby a k vystřihování dalších prvků WPF.

![Snímek obrazovky znázorňující, jak můžete pomocí geometrií vytvořit obrazce.](./media/index/use-geometries-create-shapes.png)

Další informace najdete v tématu [geometrie Overview](geometry-overview.md). Úvodní ukázku najdete v tématu [geometrií Sample](https://go.microsoft.com/fwlink/?LinkID=159989).

### <a name="2-d-effects"></a>2D efekty

WPF poskytuje knihovnu 2D tříd, které lze použít k vytvoření celé řady efektů. Funkce 2D vykreslování WPF poskytuje možnost malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které mají přechody, bitmapy, kresby a videa; a k manipulaci s nimi použijte otáčení, škálování a zkosení. Následující ilustrace obsahuje příklad mnoha efektů, které lze dosáhnout pomocí štětců WPF.

![Ilustrace znázorňující různé prvky WPF štětců a malování.](./media/index/brushes-paint-elements.png)

Další informace najdete v tématu [Přehled štětců WPF](wpf-brushes-overview.md). Úvodní vzorek naleznete v tématu [Ukázka štětce](https://go.microsoft.com/fwlink/?LinkID=159973).

<a name="rendering"></a>

## <a name="3-d-rendering"></a>trojrozměrné vykreslování

WPF poskytuje sadu 3D možností vykreslování, které se integrují s podporou 2D grafiky v WPF, aby bylo možné vytvořit zajímavější rozložení, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]a vizualizaci dat. Na jednom konci spektra umožňuje WPF vykreslování 2D imagí na povrchy 3D tvarů, které ukazují následující ilustrace.

![Snímek obrazovky s ukázkami znázorňující 3D obrazce s různými texturami](./media/index/visual-three-dimensional-shape.png)

Další informace najdete v tématu [Přehled 3D grafiky](3-d-graphics-overview.md). Úvodní vzorek najdete v tématu [Ukázka 3-D plných ukázek](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animace

Pomocí animace můžete měnit, protřepe, zesílit a mizet ovládací prvky a prvky. a k vytváření zajímavých přechodů stránky a dalších. Vzhledem k tomu, že WPF umožňuje animovat většinu vlastností, nestačí pouze animovat většinu objektů WPF, můžete také použít WPF k animaci vlastních objektů, které vytvoříte.

![Snímek obrazovky s animovanou datovou krychlí](./media/index/animate-custom-objects.png)

Další informace najdete v tématu [Přehled animací](animation-overview.md). Úvodní vzorek najdete v tématu [animace příklad Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).

<a name="media"></a>

## <a name="media"></a>Médium

Obrázky, videa a zvuky jsou mediální a bohatě náročné způsoby, jak vyjádřit informace a uživatelské prostředí.

### <a name="images"></a>Obrázky

Obrázky, které obsahují ikony, pozadí a dokonce i části animací, jsou základní součástí většiny aplikací. Vzhledem k tomu, že je často potřeba použít image, WPF nabízí možnost pracovat s nimi různými způsoby. Následující ilustrace znázorňuje pouze jeden z těchto způsobů.

![Ukázka stylu snímku obrazovky](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Další informace najdete v tématu [Přehled imagí](imaging-overview.md).

### <a name="video-and-audio"></a>Video a zvuk

Základní funkcí grafických schopností WPF je poskytnout nativní podporu pro práci s multimédii, která zahrnuje video a zvuk. Následující příklad ukazuje, jak vložit přehrávač médií do aplikace.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement> může přehrávat video i zvuk a je dostatečně rozšiřitelný, aby bylo možné snadno vytvořit vlastní uživatelská rozhraní.

Další informace najdete v tématu [Přehled multimédií](multimedia-overview.md).

## <a name="see-also"></a>Viz také:

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
