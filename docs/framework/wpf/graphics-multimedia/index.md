---
title: Grafika a multimédia
description: Objevte funkce multimédií Windows Presentation Foundation (WPF). Přidejte do svých aplikací grafiku, efekty přechodu, zvuk a video.
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
ms.openlocfilehash: ba52e78564484f7714ab0035a5e1861766b72bbf
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853682"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="2d3ff-104">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="2d3ff-104">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="2d3ff-105">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje podporu pro multimédia, vektorovou grafiku, animaci a kompozici obsahu, což vývojářům usnadňuje vytváření zajímavých uživatelských rozhraní a obsahu.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-105">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="2d3ff-106">Pomocí sady Visual Studio můžete vytvářet vektorová grafika nebo složitá animace a integrovat multimédia do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-106">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="2d3ff-107">V tomto tématu se seznámíte s grafickými, animačními a mediálními funkcemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , které umožňují přidat do aplikací grafiku, efekty přechodu, zvuk a video.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-107">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2d3ff-108">Použití typů WPF ve službě systému Windows se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="2d3ff-109">Pokud se pokusíte použít typy WPF ve službě systému Windows, služba nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-109">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="2d3ff-110">Co je nového u grafiky a multimédií v WPF 4</span><span class="sxs-lookup"><span data-stu-id="2d3ff-110">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="2d3ff-111">V souvislosti s grafikou a animacemi byly provedeny některé změny.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-111">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="2d3ff-112">Zaoblení rozložení</span><span class="sxs-lookup"><span data-stu-id="2d3ff-112">Layout Rounding</span></span>

  <span data-ttu-id="2d3ff-113">Když okraj objektu spadá do středu zařízení v pixelech, může grafický systém nezávislý na DPI vytvořit artefakty vykreslování, jako je rozmazaný nebo částečně transparentní okraj.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-113">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="2d3ff-114">Předchozí verze WPF zahrnovaly přichycení k pixelům, které vám pomůžou s tímto případem pracovat.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-114">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="2d3ff-115">Program Silverlight 2 představil zaoblení rozložení, což je jiný způsob, jak přesunout prvky tak, aby hrany klesly na celé celé pixelové hranice.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-115">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="2d3ff-116">WPF teď podporuje zaokrouhlování rozložení s <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> připojenou vlastností on <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="2d3ff-116">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="2d3ff-117">Kompozice v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="2d3ff-117">Cached Composition</span></span>

  <span data-ttu-id="2d3ff-118">Pomocí nových <xref:System.Windows.Media.BitmapCache> <xref:System.Windows.Media.BitmapCacheBrush> tříd a můžete ukládat složitou část vizuálního stromu do mezipaměti a významně zlepšit dobu vykreslování.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-118">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="2d3ff-119">Rastrový obrázek zůstává reagovat na vstup uživatele, jako je například kliknutí myší, a můžete ho malovat na jiné prvky stejně jako u libovolného štětce.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-119">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="2d3ff-120">Podpora funkce Pixel Shader 3</span><span class="sxs-lookup"><span data-stu-id="2d3ff-120">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="2d3ff-121">WPF 4 sestavuje na <xref:System.Windows.Media.Effects.ShaderEffect> podporu představené v wpf 3,5 SP1 tím, že umožňuje aplikacím zapisovat efekty pomocí funkce pixel shader (PS) verze 3,0.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-121">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="2d3ff-122">Model shaderu PS 3,0 je propracovanější než PS 2,0, který umožňuje ještě více efektů na podporovaném hardwaru.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-122">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="2d3ff-123">Funkce usnadnění</span><span class="sxs-lookup"><span data-stu-id="2d3ff-123">Easing Functions</span></span>

  <span data-ttu-id="2d3ff-124">Animace můžete vylepšit funkcemi usnadnění, což vám poskytne další kontrolu nad chováním animací.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-124">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="2d3ff-125">Například můžete použít na animaci a dát tak animaci k funkci <xref:System.Windows.Media.Animation.ElasticEase> pružiny.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-125">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="2d3ff-126">Další informace naleznete v tématu typy náběh a doběh v <xref:System.Windows.Media.Animation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-126">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="2d3ff-127">Grafika a vykreslování</span><span class="sxs-lookup"><span data-stu-id="2d3ff-127">Graphics and Rendering</span></span>

<span data-ttu-id="2d3ff-128">WPF zahrnuje podporu vysoce kvalitní 2D grafiky.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-128">WPF includes support for high quality 2D graphics.</span></span> <span data-ttu-id="2d3ff-129">Mezi tyto funkce patří štětce, geometrií, obrázky, tvary a transformace.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-129">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="2d3ff-130">Další informace najdete v tématu [Grafika](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-130">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="2d3ff-131">Vykreslování grafických prvků je založeno na <xref:System.Windows.Media.Visual> třídě.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-131">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="2d3ff-132">Struktura vizuálních objektů na obrazovce je popsána ve vizuálním stromu.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-132">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="2d3ff-133">Další informace naleznete v tématu [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-133">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="2d3ff-134">2D obrazce</span><span class="sxs-lookup"><span data-stu-id="2d3ff-134">2D Shapes</span></span>

<span data-ttu-id="2d3ff-135">WPF poskytuje knihovnu běžně používaných 2D 2D tvarů, jako jsou obdélníky a tři tečky, které jsou znázorněny na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-135">WPF provides a library of commonly used, vector-drawn 2D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagram znázorňující elipsy a obdélníky.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="2d3ff-137">Tyto vnitřní tvary WPF nejsou pouze tvary: Jedná se o programovatelné prvky, které implementují mnoho funkcí, které očekáváte od nejběžnějších ovládacích prvků, které zahrnují vstup z klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-137">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="2d3ff-138">Následující příklad ukazuje, jak zpracovat <xref:System.Windows.UIElement.MouseUp> událost vyvolanou kliknutím na <xref:System.Windows.Shapes.Ellipse> prvek.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-138">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="2d3ff-139">Následující ilustrace ukazuje výstup předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky a kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-139">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Okno se zprávou, že jste klikli na elipsu!](./media/index/messagebox-text-output.png)

<span data-ttu-id="2d3ff-141">Další informace naleznete v tématu [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-141">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="2d3ff-142">Úvodní vzorek naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-142">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="2d3ff-143">2D geometrií</span><span class="sxs-lookup"><span data-stu-id="2d3ff-143">2D Geometries</span></span>

<span data-ttu-id="2d3ff-144">Pokud 2D obrazce, které WPF poskytuje, nejsou dostačující, můžete použít podporu WPF pro geometrií a cesty a vytvořit vlastní.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-144">When the 2D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="2d3ff-145">Následující obrázek ukazuje, jak lze použít geometrií k vytváření tvarů, jako štětec kresby a k vystřihování dalších prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-145">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Snímek obrazovky znázorňující, jak můžete pomocí geometrií vytvořit obrazce.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="2d3ff-147">Další informace najdete v tématu [geometrie Overview](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-147">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="2d3ff-148">Úvodní ukázku najdete v tématu [geometrií Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-148">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="2d3ff-149">2D efekty</span><span class="sxs-lookup"><span data-stu-id="2d3ff-149">2D Effects</span></span>

<span data-ttu-id="2d3ff-150">WPF poskytuje knihovnu 2D tříd, které lze použít k vytvoření celé řady efektů.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-150">WPF provides a library of 2D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="2d3ff-151">Funkce 2D vykreslování WPF poskytuje možnost malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které mají přechody, bitmapy, kresby a videa, a manipulovat s nimi pomocí rotace, škálování a zkosení.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-151">The 2D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="2d3ff-152">Následující ilustrace obsahuje příklad mnoha efektů, které lze dosáhnout pomocí štětců WPF.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-152">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Ilustrace znázorňující různé prvky WPF štětců a malování.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="2d3ff-154">Další informace najdete v tématu [Přehled štětců WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-154">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="2d3ff-155">Úvodní vzorek naleznete v tématu [Ukázka štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-155">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3d-rendering"></a><span data-ttu-id="2d3ff-156">Prostorové vykreslování</span><span class="sxs-lookup"><span data-stu-id="2d3ff-156">3D Rendering</span></span>

<span data-ttu-id="2d3ff-157">WPF poskytuje sadu 3D funkcí vykreslování, které se integrují s podporou 2D grafiky v WPF, aby bylo možné vytvořit zajímavější rozložení, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a vizualizaci dat.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-157">WPF provides a set of 3D rendering capabilities that integrate with 2D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="2d3ff-158">Na jednom konci spektra umožňuje WPF vykreslovat 2D obrázky na povrchu 3D tvarů, který ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-158">At one end of the spectrum, WPF enables you to render 2D images onto the surfaces of 3D shapes, which the following illustration demonstrates.</span></span>

![Snímek obrazovky s ukázkou znázorňující tvary 3D s různými texturami](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="2d3ff-160">Další informace najdete v tématu [Přehled 3D grafiky](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-160">For more information, see [3D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="2d3ff-161">Úvodní vzorek najdete v tématu [Ukázka prostorových plných](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-161">For an introductory sample, see [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="2d3ff-162">Animace</span><span class="sxs-lookup"><span data-stu-id="2d3ff-162">Animation</span></span>

<span data-ttu-id="2d3ff-163">Pomocí animace můžete měnit, protřepe, zesílit a mizet ovládací prvky a prvky. a k vytváření zajímavých přechodů stránky a dalších.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-163">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="2d3ff-164">Vzhledem k tomu, že WPF umožňuje animovat většinu vlastností, nestačí pouze animovat většinu objektů WPF, můžete také použít WPF k animaci vlastních objektů, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-164">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Snímek obrazovky s animovanou datovou krychlí](./media/index/animate-custom-objects.png)

<span data-ttu-id="2d3ff-166">Další informace najdete v tématu [Přehled animací](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-166">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="2d3ff-167">Úvodní vzorek najdete v tématu [animace příklad Galerie](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-167">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="2d3ff-168">Média</span><span class="sxs-lookup"><span data-stu-id="2d3ff-168">Media</span></span>

<span data-ttu-id="2d3ff-169">Obrázky, videa a zvuky jsou mediální a bohatě náročné způsoby, jak vyjádřit informace a uživatelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-169">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="2d3ff-170">Image</span><span class="sxs-lookup"><span data-stu-id="2d3ff-170">Images</span></span>

<span data-ttu-id="2d3ff-171">Obrázky, které obsahují ikony, pozadí a dokonce i části animací, jsou základní součástí většiny aplikací.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-171">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="2d3ff-172">Vzhledem k tomu, že je často potřeba použít image, WPF nabízí možnost pracovat s nimi různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-172">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="2d3ff-173">Následující ilustrace znázorňuje pouze jeden z těchto způsobů.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-173">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="2d3ff-174">![Ukázka stylu snímku obrazovky](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="2d3ff-174">![Styling sample screenshot](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="2d3ff-175">Další informace najdete v tématu [Přehled imagí](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-175">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="2d3ff-176">Video a zvuk</span><span class="sxs-lookup"><span data-stu-id="2d3ff-176">Video and Audio</span></span>

<span data-ttu-id="2d3ff-177">Základní funkcí grafických schopností WPF je poskytnout nativní podporu pro práci s multimédii, která zahrnuje video a zvuk.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-177">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="2d3ff-178">Následující příklad ukazuje, jak vložit přehrávač médií do aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-178">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="2d3ff-179"><xref:System.Windows.Controls.MediaElement>je schopný přehrávat video i zvuk a je dostatečně rozšiřitelný, aby bylo možné snadno vytvořit vlastní uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d3ff-179"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="2d3ff-180">Další informace najdete v tématu [Přehled multimédií](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d3ff-180">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d3ff-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d3ff-181">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="2d3ff-182">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="2d3ff-182">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="2d3ff-183">Tvary a základní kresby v přehledu WPF</span><span class="sxs-lookup"><span data-stu-id="2d3ff-183">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="2d3ff-184">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="2d3ff-184">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="2d3ff-185">Kreslení pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="2d3ff-185">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="2d3ff-186">Postupy: Témata animace a časování</span><span class="sxs-lookup"><span data-stu-id="2d3ff-186">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="2d3ff-187">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="2d3ff-187">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="2d3ff-188">Přehled multimédií</span><span class="sxs-lookup"><span data-stu-id="2d3ff-188">Multimedia Overview</span></span>](multimedia-overview.md)
