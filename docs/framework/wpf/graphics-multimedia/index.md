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
# <a name="graphics-and-multimedia"></a><span data-ttu-id="c35fa-102">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="c35fa-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="c35fa-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje podporu pro multimédia, vektorovou grafiku, animaci a kompozici obsahu, což vývojářům usnadňuje vytváření zajímavých uživatelských rozhraní a obsahu.</span><span class="sxs-lookup"><span data-stu-id="c35fa-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="c35fa-104">Pomocí sady Visual Studio můžete vytvářet vektorovou grafiku nebo složité animace a integrovat média do aplikací.</span><span class="sxs-lookup"><span data-stu-id="c35fa-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="c35fa-105">Toto téma představuje grafické, animační [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a mediální funkce aplikace , které umožňují přidávat grafiku, přechodové efekty, zvuk a video do aplikací.</span><span class="sxs-lookup"><span data-stu-id="c35fa-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="c35fa-106">Použití wpf typů ve službě systému Windows se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="c35fa-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="c35fa-107">Pokud se pokusíte použít wpf typy ve službě systému Windows, služba nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="c35fa-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="c35fa-108">Co je nového s grafikou a multimédii ve WPF 4</span><span class="sxs-lookup"><span data-stu-id="c35fa-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="c35fa-109">Bylo provedeno několik změn týkajících se grafiky a animací.</span><span class="sxs-lookup"><span data-stu-id="c35fa-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="c35fa-110">Zaokrouhlení rozložení</span><span class="sxs-lookup"><span data-stu-id="c35fa-110">Layout Rounding</span></span>

  <span data-ttu-id="c35fa-111">Když okraj objektu spadne uprostřed zařízení s obrazovými body, grafický systém nezávislý na DPI může vytvářet artefakty vykreslování, například rozmazané nebo poloprůhledné okraje.</span><span class="sxs-lookup"><span data-stu-id="c35fa-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="c35fa-112">Předchozí verze WPF zahrnuty pixel přichycení pomoci zpracovat tento případ.</span><span class="sxs-lookup"><span data-stu-id="c35fa-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="c35fa-113">Program Silverlight 2 zavedl zaokrouhlení rozvržení, což je další způsob, jak přesunout prvky tak, aby okraje spadaly na hranice celých obrazových bodů.</span><span class="sxs-lookup"><span data-stu-id="c35fa-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="c35fa-114">WPF nyní podporuje zaokrouhlení rozložení s připojenou <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> vlastností na <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="c35fa-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="c35fa-115">Složení uložené v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="c35fa-115">Cached Composition</span></span>

  <span data-ttu-id="c35fa-116">Pomocí nové <xref:System.Windows.Media.BitmapCache> a <xref:System.Windows.Media.BitmapCacheBrush> třídy, můžete ukládat do mezipaměti komplexní část vizuálního stromu jako rastrový obrázek a výrazně zlepšit dobu vykreslování.</span><span class="sxs-lookup"><span data-stu-id="c35fa-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="c35fa-117">Bitmapa zůstává reagovat na vstup uživatele, jako je například kliknutí myší, a můžete malovat na jiné prvky, stejně jako jakýkoli štětec.</span><span class="sxs-lookup"><span data-stu-id="c35fa-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="c35fa-118">Podpora pro Pixel Shader 3</span><span class="sxs-lookup"><span data-stu-id="c35fa-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="c35fa-119">WPF 4 staví na <xref:System.Windows.Media.Effects.ShaderEffect> podpoře zavedené v WPF 3.5 SP1 tím, že umožňuje aplikacím psát efekty pomocí Pixel Shader (PS) verze 3.0.</span><span class="sxs-lookup"><span data-stu-id="c35fa-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="c35fa-120">Model shaderu PS 3.0 je sofistikovanější než PS 2.0, což umožňuje ještě více efektů na podporovaný hardware.</span><span class="sxs-lookup"><span data-stu-id="c35fa-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="c35fa-121">Funkce usnadnění</span><span class="sxs-lookup"><span data-stu-id="c35fa-121">Easing Functions</span></span>

  <span data-ttu-id="c35fa-122">Můžete vylepšit animace s funkcemi náběhu/doběhu, které poskytují další kontrolu nad chováním animací.</span><span class="sxs-lookup"><span data-stu-id="c35fa-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="c35fa-123">Můžete například použít <xref:System.Windows.Media.Animation.ElasticEase> a animaci, která animaci poskytne pružné chování.</span><span class="sxs-lookup"><span data-stu-id="c35fa-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="c35fa-124">Další informace naleznete v náběh/doběhu typy v oboru <xref:System.Windows.Media.Animation> názvů.</span><span class="sxs-lookup"><span data-stu-id="c35fa-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="c35fa-125">Grafika a vykreslování</span><span class="sxs-lookup"><span data-stu-id="c35fa-125">Graphics and Rendering</span></span>

<span data-ttu-id="c35fa-126">WPF obsahuje podporu pro vysoce kvalitní 2D grafiku.</span><span class="sxs-lookup"><span data-stu-id="c35fa-126">WPF includes support for high quality 2D graphics.</span></span> <span data-ttu-id="c35fa-127">Funkce zahrnuje stopy, geometrie, obrazy, tvary a transformace.</span><span class="sxs-lookup"><span data-stu-id="c35fa-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="c35fa-128">Další informace naleznete v [tématu Graphics](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="c35fa-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="c35fa-129">Vykreslování grafických prvků je založeno na <xref:System.Windows.Media.Visual> třídě.</span><span class="sxs-lookup"><span data-stu-id="c35fa-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="c35fa-130">Struktura vizuálních objektů na obrazovce je popsána vizuálním stromem.</span><span class="sxs-lookup"><span data-stu-id="c35fa-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="c35fa-131">Další informace naleznete v [tématu Přehled vykreslení grafiky WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c35fa-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="c35fa-132">2D obrazce</span><span class="sxs-lookup"><span data-stu-id="c35fa-132">2D Shapes</span></span>

<span data-ttu-id="c35fa-133">WPF poskytuje knihovnu běžně používaných vektorově kreslených 2D tvarů, jako jsou obdélníky a elipsy, které ukazují následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="c35fa-133">WPF provides a library of commonly used, vector-drawn 2D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagram znázorňující elipsy a obdélníky.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="c35fa-135">Tyto vnitřní wpf tvary nejsou pouze tvary: jsou programovatelné prvky, které implementují mnoho funkcí, které očekáváte od většiny běžných ovládacích prvků, které zahrnují vstup klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="c35fa-135">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="c35fa-136">Následující příklad ukazuje, jak <xref:System.Windows.UIElement.MouseUp> zpracovat událost <xref:System.Windows.Shapes.Ellipse> vydopravené klepnutím na prvek.</span><span class="sxs-lookup"><span data-stu-id="c35fa-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="c35fa-137">Následující obrázek znázorňuje výstup [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro předchozí značky a kód na pozadí.</span><span class="sxs-lookup"><span data-stu-id="c35fa-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Okno se zprávou s nápisem "Klikli jste na elipsu!"](./media/index/messagebox-text-output.png)

<span data-ttu-id="c35fa-139">Další informace naleznete [v tématu Obrazce a základní výkres v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c35fa-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="c35fa-140">Úvodní ukázka viz [Ukázka prvků tvarů](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="c35fa-140">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="c35fa-141">2D geometrie</span><span class="sxs-lookup"><span data-stu-id="c35fa-141">2D Geometries</span></span>

<span data-ttu-id="c35fa-142">Pokud 2D obrazce, které poskytuje WPF, nejsou dostatečné, můžete použít podporu WPF pro geometrie a cesty k vytvoření vlastní.</span><span class="sxs-lookup"><span data-stu-id="c35fa-142">When the 2D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="c35fa-143">Následující obrázek znázorňuje, jak můžete pomocí geometrií vytvářet tvary jako stopu výkresu a oříznout další prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="c35fa-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Snímek obrazovky znázorňující, jak můžete k vytváření obrazců použít geometrie.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="c35fa-145">Další informace naleznete v [tématu Přehled geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c35fa-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="c35fa-146">Úvodní vzorek viz [Vzorek geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="c35fa-146">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="c35fa-147">2D efekty</span><span class="sxs-lookup"><span data-stu-id="c35fa-147">2D Effects</span></span>

<span data-ttu-id="c35fa-148">WPF poskytuje knihovnu 2D tříd, které můžete použít k vytvoření různých efektů.</span><span class="sxs-lookup"><span data-stu-id="c35fa-148">WPF provides a library of 2D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="c35fa-149">Schopnost 2D vykreslování [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] WPF umožňuje malovat prvky, které mají přechody, rastrové obrázky, výkresy a videa; a manipulovat s nimi pomocí otočení, změny velikosti a zkosení.</span><span class="sxs-lookup"><span data-stu-id="c35fa-149">The 2D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="c35fa-150">Následující obrázek uvádí příklad mnoha efektů, kterých můžete dosáhnout pomocí stop WPF.</span><span class="sxs-lookup"><span data-stu-id="c35fa-150">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Obrázek znázorňující různé stopy WPF a prvky malby.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="c35fa-152">Další informace naleznete v tématu [Přehled stop y WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c35fa-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="c35fa-153">Úvodní vzorek viz [Vzorek štětců](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="c35fa-153">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3d-rendering"></a><span data-ttu-id="c35fa-154">3D vykreslování</span><span class="sxs-lookup"><span data-stu-id="c35fa-154">3D Rendering</span></span>

<span data-ttu-id="c35fa-155">WPF poskytuje sadu funkcí 3D vykreslování, které se integrují [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s podporou 2D grafiky ve WPF, abyste mohli vytvořit více vzrušujícího rozložení a vizualizace dat.</span><span class="sxs-lookup"><span data-stu-id="c35fa-155">WPF provides a set of 3D rendering capabilities that integrate with 2D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="c35fa-156">Na jednom konci spektra umožňuje WPF vykreslit 2D obrazy na povrchy 3D tvarů, což ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="c35fa-156">At one end of the spectrum, WPF enables you to render 2D images onto the surfaces of 3D shapes, which the following illustration demonstrates.</span></span>

![Snímek obrazovky s ukázkou 3D obrazců s různými texturami](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="c35fa-158">Další informace naleznete v tématu [Přehled 3D grafiky](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c35fa-158">For more information, see [3D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="c35fa-159">Úvodní vzorek viz [3D vzorek těles](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="c35fa-159">For an introductory sample, see [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="c35fa-160">Animace</span><span class="sxs-lookup"><span data-stu-id="c35fa-160">Animation</span></span>

<span data-ttu-id="c35fa-161">Pomocí animace můžete provádět růst, chvění, otáčení a slábnutí ovládacích prvků a prvků; a vytvářet zajímavé přechody stránek a další.</span><span class="sxs-lookup"><span data-stu-id="c35fa-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="c35fa-162">Vzhledem k tomu, že WPF umožňuje animovat většinu vlastností, můžete nejen animovat většinu objektů WPF, můžete také použít WPF k animaci vlastních objektů, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="c35fa-162">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Snímek obrazovky s animovanou krychli](./media/index/animate-custom-objects.png)

<span data-ttu-id="c35fa-164">Další informace naleznete v [tématu Přehled animace](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c35fa-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="c35fa-165">Úvodní ukázku naleznete v galerii [příkladů animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="c35fa-165">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="c35fa-166">Média</span><span class="sxs-lookup"><span data-stu-id="c35fa-166">Media</span></span>

<span data-ttu-id="c35fa-167">Obrázky, video a zvuk jsou způsoby, jak přenášet informace a uživatelské prostředí bohaté na média.</span><span class="sxs-lookup"><span data-stu-id="c35fa-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="c35fa-168">Image</span><span class="sxs-lookup"><span data-stu-id="c35fa-168">Images</span></span>

<span data-ttu-id="c35fa-169">Obrázky, které obsahují ikony, pozadí a dokonce i části animací, jsou základní součástí většiny aplikací.</span><span class="sxs-lookup"><span data-stu-id="c35fa-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="c35fa-170">Vzhledem k tomu, že často potřebujete používat obrázky, WPF zveřejňuje schopnost pracovat s nimi různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="c35fa-170">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="c35fa-171">Následující obrázek znázorňuje pouze jeden z těchto způsobů.</span><span class="sxs-lookup"><span data-stu-id="c35fa-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="c35fa-172">![Ukázkový snímek obrazovky s stylingem](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="c35fa-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="c35fa-173">Další informace naleznete v [tématu Přehled zpracování obrázků](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c35fa-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="c35fa-174">Video a zvuk</span><span class="sxs-lookup"><span data-stu-id="c35fa-174">Video and Audio</span></span>

<span data-ttu-id="c35fa-175">Základním rysem grafických schopností WPF je poskytnout nativní podporu pro práci s multimédii, která zahrnuje video a audio.</span><span class="sxs-lookup"><span data-stu-id="c35fa-175">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="c35fa-176">Následující příklad ukazuje, jak vložit přehrávač médií do aplikace.</span><span class="sxs-lookup"><span data-stu-id="c35fa-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="c35fa-177"><xref:System.Windows.Controls.MediaElement>je schopen přehrávat video i zvuk a je dostatečně rozšiřitelný, aby umožnil snadné vytváření vlastních ubru.</span><span class="sxs-lookup"><span data-stu-id="c35fa-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="c35fa-178">Další informace naleznete v přehledu [multimédií](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c35fa-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c35fa-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="c35fa-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="c35fa-180">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="c35fa-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="c35fa-181">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="c35fa-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="c35fa-182">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="c35fa-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="c35fa-183">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="c35fa-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="c35fa-184">Postupy: Témata animace a časování</span><span class="sxs-lookup"><span data-stu-id="c35fa-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="c35fa-185">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="c35fa-185">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="c35fa-186">Přehled multimédií</span><span class="sxs-lookup"><span data-stu-id="c35fa-186">Multimedia Overview</span></span>](multimedia-overview.md)
