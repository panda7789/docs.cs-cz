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
# <a name="graphics-and-multimedia"></a><span data-ttu-id="ebfc2-102">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="ebfc2-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="ebfc2-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje podporu pro multimédia, vektorovou grafiku, animaci a kompozici obsahu, což vývojářům usnadňuje vytváření zajímavých uživatelských rozhraní a obsahu.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="ebfc2-104">Pomocí sady Visual Studio můžete vytvářet vektorová grafika nebo složitá animace a integrovat multimédia do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="ebfc2-105">V tomto tématu se seznámíte s grafickými, animačními a mediálními funkcemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které umožňují přidat do svých aplikací grafiku, efekty přechodu, zvuk a video.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="ebfc2-106">Použití typů WPF ve službě systému Windows se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="ebfc2-107">Pokud se pokusíte použít typy WPF ve službě systému Windows, služba nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="ebfc2-108">Co je nového u grafiky a multimédií v WPF 4</span><span class="sxs-lookup"><span data-stu-id="ebfc2-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="ebfc2-109">V souvislosti s grafikou a animacemi byly provedeny některé změny.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="ebfc2-110">Zaoblení rozložení</span><span class="sxs-lookup"><span data-stu-id="ebfc2-110">Layout Rounding</span></span>

  <span data-ttu-id="ebfc2-111">Když okraj objektu spadá do středu zařízení v pixelech, může grafický systém nezávislý na DPI vytvořit artefakty vykreslování, jako je rozmazaný nebo částečně transparentní okraj.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="ebfc2-112">Předchozí verze WPF zahrnovaly přichycení k pixelům, které vám pomůžou s tímto případem pracovat.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="ebfc2-113">Program Silverlight 2 představil zaoblení rozložení, což je jiný způsob, jak přesunout prvky tak, aby hrany klesly na celé celé pixelové hranice.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="ebfc2-114">WPF teď podporuje zaokrouhlování rozložení s vlastností <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> připojenou v <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="ebfc2-115">Kompozice v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="ebfc2-115">Cached Composition</span></span>

  <span data-ttu-id="ebfc2-116">Pomocí nových tříd <xref:System.Windows.Media.BitmapCache> a <xref:System.Windows.Media.BitmapCacheBrush> můžete složitou část vizuálního stromu ukládat do mezipaměti a významně zlepšit dobu vykreslování.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="ebfc2-117">Rastrový obrázek zůstává reagovat na vstup uživatele, jako je například kliknutí myší, a můžete ho malovat na jiné prvky stejně jako u libovolného štětce.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="ebfc2-118">Podpora funkce Pixel Shader 3</span><span class="sxs-lookup"><span data-stu-id="ebfc2-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="ebfc2-119">WPF 4 sestavuje podporu <xref:System.Windows.Media.Effects.ShaderEffect> zavedenou v WPF 3,5 SP1 tím, že umožňuje aplikacím zapisovat efekty pomocí funkce pixel shader (PS) verze 3,0.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="ebfc2-120">Model shaderu PS 3,0 je propracovanější než PS 2,0, který umožňuje ještě více efektů na podporovaném hardwaru.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="ebfc2-121">Funkce usnadnění</span><span class="sxs-lookup"><span data-stu-id="ebfc2-121">Easing Functions</span></span>

  <span data-ttu-id="ebfc2-122">Animace můžete vylepšit funkcemi usnadnění, což vám poskytne další kontrolu nad chováním animací.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="ebfc2-123">Můžete například použít <xref:System.Windows.Media.Animation.ElasticEase> k animaci, aby animace mohla působit na jaře.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="ebfc2-124">Další informace naleznete v tématu typy náběh a doběh v oboru názvů <xref:System.Windows.Media.Animation>.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="ebfc2-125">Grafika a vykreslování</span><span class="sxs-lookup"><span data-stu-id="ebfc2-125">Graphics and Rendering</span></span>

<span data-ttu-id="ebfc2-126">WPF zahrnuje podporu pro vysoce kvalitní 2D grafiku.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="ebfc2-127">Mezi tyto funkce patří štětce, geometrií, obrázky, tvary a transformace.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="ebfc2-128">Další informace najdete v tématu [Grafika](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="ebfc2-129">Vykreslování grafických prvků je založeno na třídě <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="ebfc2-130">Struktura vizuálních objektů na obrazovce je popsána ve vizuálním stromu.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="ebfc2-131">Další informace naleznete v tématu [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2-d-shapes"></a><span data-ttu-id="ebfc2-132">2D obrazce</span><span class="sxs-lookup"><span data-stu-id="ebfc2-132">2-D Shapes</span></span>

<span data-ttu-id="ebfc2-133">WPF poskytuje knihovnu běžně používaných dvojrozměrných 2D tvarů, jako jsou obdélníky a tři tečky, které jsou znázorněny na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-133">WPF provides a library of commonly used, vector-drawn 2-D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagram znázorňující elipsy a obdélníky.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="ebfc2-135">Tyto vnitřní tvary WPF nejsou pouze tvary: Jedná se o programovatelné prvky, které implementují mnoho funkcí, které očekáváte od nejběžnějších ovládacích prvků, které zahrnují vstup z klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-135">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="ebfc2-136">Následující příklad ukazuje, jak zpracovat událost <xref:System.Windows.UIElement.MouseUp> vyvolána kliknutím na <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="ebfc2-137">Následující ilustrace ukazuje výstup pro předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky a kód na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Okno se zprávou, že jste klikli na elipsu!](./media/index/messagebox-text-output.png)

<span data-ttu-id="ebfc2-139">Další informace naleznete v tématu [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="ebfc2-140">Úvodní vzorek naleznete v tématu [Ukázka prvků tvaru](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-140">For an introductory sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>

### <a name="2-d-geometries"></a><span data-ttu-id="ebfc2-141">2D geometrií</span><span class="sxs-lookup"><span data-stu-id="ebfc2-141">2-D Geometries</span></span>

<span data-ttu-id="ebfc2-142">Když 2D obrazce, které WPF poskytuje, nejsou dostačující, můžete použít podporu WPF pro geometrií a cesty a vytvořit vlastní.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-142">When the 2-D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="ebfc2-143">Následující obrázek ukazuje, jak lze použít geometrií k vytváření tvarů, jako štětec kresby a k vystřihování dalších prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Snímek obrazovky znázorňující, jak můžete pomocí geometrií vytvořit obrazce.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="ebfc2-145">Další informace najdete v tématu [geometrie Overview](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="ebfc2-146">Úvodní ukázku najdete v tématu [geometrií Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-146">For an introductory sample, see [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>

### <a name="2-d-effects"></a><span data-ttu-id="ebfc2-147">2D efekty</span><span class="sxs-lookup"><span data-stu-id="ebfc2-147">2-D Effects</span></span>

<span data-ttu-id="ebfc2-148">WPF poskytuje knihovnu 2D tříd, které lze použít k vytvoření celé řady efektů.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-148">WPF provides a library of 2-D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="ebfc2-149">Funkce 2D vykreslování WPF poskytuje možnost malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které mají přechody, bitmapy, kresby a videa; a k manipulaci s nimi použijte otáčení, škálování a zkosení.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-149">The 2-D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="ebfc2-150">Následující ilustrace obsahuje příklad mnoha efektů, které lze dosáhnout pomocí štětců WPF.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-150">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Ilustrace znázorňující různé prvky WPF štětců a malování.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="ebfc2-152">Další informace najdete v tématu [Přehled štětců WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="ebfc2-153">Úvodní vzorek naleznete v tématu [Ukázka štětce](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-153">For an introductory sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>

<a name="rendering"></a>

## <a name="3-d-rendering"></a><span data-ttu-id="ebfc2-154">trojrozměrné vykreslování</span><span class="sxs-lookup"><span data-stu-id="ebfc2-154">3-D Rendering</span></span>

<span data-ttu-id="ebfc2-155">WPF poskytuje sadu 3D možností vykreslování, které se integrují s podporou 2D grafiky v WPF, aby bylo možné vytvořit zajímavější rozložení, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]a vizualizaci dat.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-155">WPF provides a set of 3-D rendering capabilities that integrate with 2-D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="ebfc2-156">Na jednom konci spektra umožňuje WPF vykreslování 2D imagí na povrchy 3D tvarů, které ukazují následující ilustrace.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-156">At one end of the spectrum, WPF enables you to render 2-D images onto the surfaces of 3-D shapes, which the following illustration demonstrates.</span></span>

![Snímek obrazovky s ukázkami znázorňující 3D obrazce s různými texturami](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="ebfc2-158">Další informace najdete v tématu [Přehled 3D grafiky](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-158">For more information, see [3-D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="ebfc2-159">Úvodní vzorek najdete v tématu [Ukázka 3-D plných ukázek](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-159">For an introductory sample, see [3-D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="ebfc2-160">Animace</span><span class="sxs-lookup"><span data-stu-id="ebfc2-160">Animation</span></span>

<span data-ttu-id="ebfc2-161">Pomocí animace můžete měnit, protřepe, zesílit a mizet ovládací prvky a prvky. a k vytváření zajímavých přechodů stránky a dalších.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="ebfc2-162">Vzhledem k tomu, že WPF umožňuje animovat většinu vlastností, nestačí pouze animovat většinu objektů WPF, můžete také použít WPF k animaci vlastních objektů, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-162">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Snímek obrazovky s animovanou datovou krychlí](./media/index/animate-custom-objects.png)

<span data-ttu-id="ebfc2-164">Další informace najdete v tématu [Přehled animací](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="ebfc2-165">Úvodní vzorek najdete v tématu [animace příklad Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-165">For an introductory sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="ebfc2-166">Médium</span><span class="sxs-lookup"><span data-stu-id="ebfc2-166">Media</span></span>

<span data-ttu-id="ebfc2-167">Obrázky, videa a zvuky jsou mediální a bohatě náročné způsoby, jak vyjádřit informace a uživatelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="ebfc2-168">Obrázky</span><span class="sxs-lookup"><span data-stu-id="ebfc2-168">Images</span></span>

<span data-ttu-id="ebfc2-169">Obrázky, které obsahují ikony, pozadí a dokonce i části animací, jsou základní součástí většiny aplikací.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="ebfc2-170">Vzhledem k tomu, že je často potřeba použít image, WPF nabízí možnost pracovat s nimi různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-170">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="ebfc2-171">Následující ilustrace znázorňuje pouze jeden z těchto způsobů.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="ebfc2-172">![Ukázka stylu snímku obrazovky](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="ebfc2-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="ebfc2-173">Další informace najdete v tématu [Přehled imagí](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="ebfc2-174">Video a zvuk</span><span class="sxs-lookup"><span data-stu-id="ebfc2-174">Video and Audio</span></span>

<span data-ttu-id="ebfc2-175">Základní funkcí grafických schopností WPF je poskytnout nativní podporu pro práci s multimédii, která zahrnuje video a zvuk.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-175">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="ebfc2-176">Následující příklad ukazuje, jak vložit přehrávač médií do aplikace.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="ebfc2-177"><xref:System.Windows.Controls.MediaElement> může přehrávat video i zvuk a je dostatečně rozšiřitelný, aby bylo možné snadno vytvořit vlastní uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ebfc2-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="ebfc2-178">Další informace najdete v tématu [Přehled multimédií](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ebfc2-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ebfc2-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebfc2-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="ebfc2-180">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="ebfc2-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="ebfc2-181">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="ebfc2-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="ebfc2-182">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="ebfc2-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="ebfc2-183">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="ebfc2-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="ebfc2-184">Postupy: Témata animace a časování</span><span class="sxs-lookup"><span data-stu-id="ebfc2-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="ebfc2-185">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="ebfc2-185">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="ebfc2-186">Přehled multimédií</span><span class="sxs-lookup"><span data-stu-id="ebfc2-186">Multimedia Overview</span></span>](multimedia-overview.md)
