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
ms.openlocfilehash: 58ee58577b9ff71112103abb4d33c8b85d3c806f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59481350"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="ae0a4-102">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="ae0a4-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="ae0a4-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje podporu pro multimédia, vektorovou grafiku, animace a obsahu složení, a usnadňuje vývojářům umožní tvořit zajímavou uživatelská rozhraní a obsah.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="ae0a4-104">Pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], můžete vytvořit vektorovou grafiku nebo komplexní animace a do svých aplikací integrovat média.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-104">Using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="ae0a4-105">Toto téma představuje funkce obrázky, animace a média [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které umožňují přidat grafiky, efektu přechodu, zvuku a videa pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="ae0a4-106">Použití typů WPF ve službě Windows se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="ae0a4-107">Pokud se pokusíte použít typy WPF ve službě Windows, služba nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="ae0a4-108">Co je nového v grafika a multimédia v subsystému WPF 4</span><span class="sxs-lookup"><span data-stu-id="ae0a4-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="ae0a4-109">Několik se provedly změny související grafika a animace.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="ae0a4-110">Zaokrouhlení rozložení</span><span class="sxs-lookup"><span data-stu-id="ae0a4-110">Layout Rounding</span></span>

  <span data-ttu-id="ae0a4-111">Při okraje objektu spadá uprostřed pixelů zařízení, můžete vytvořit systém grafiky DPI nezávislé vykreslování artefaktů, jako je například fuzzy nebo poloprůhledného hrany.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="ae0a4-112">Předchozí verze WPF zahrnuté přitahování a pomáhaly zvládat tento případ.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="ae0a4-113">Silverlight 2 zavedené zaokrouhlení rozložení, což je jiný způsob, jak se mají přesunout prvky tak, aby se okraje na hranicích celý pixelů.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="ae0a4-114">Nyní podporuje rozložení zaokrouhlení s WPF <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> přidružená vlastnost na <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="ae0a4-115">Sestavení v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="ae0a4-115">Cached Composition</span></span>

  <span data-ttu-id="ae0a4-116">Pomocí nového <xref:System.Windows.Media.BitmapCache> a <xref:System.Windows.Media.BitmapCacheBrush> třídy, můžete ukládat do mezipaměti komplexní součástí vizuálního stromu jako rastrový obrázek a výrazně zvýšit doba vykreslování.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="ae0a4-117">Rastrový obrázek stále poměrně rychle reaguje na vstup uživatele, jako je například kliknutí myší, a na další prvky, stejně jako všechny stopy malovat.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="ae0a4-118">Podpora funkce Pixel Shader 3</span><span class="sxs-lookup"><span data-stu-id="ae0a4-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="ae0a4-119">WPF 4 sestavení nahoře <xref:System.Windows.Media.Effects.ShaderEffect> podpory dostupné ve WPF 3.5 SP1 tím, že aplikace pro zápis účinky pomocí Pixel Shader (PS) verze 3.0.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="ae0a4-120">Shader model PS 3.0 je složitější než PS 2.0, která umožňuje ještě větší vliv na podporovaný hardware.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="ae0a4-121">Funkce usnadnění</span><span class="sxs-lookup"><span data-stu-id="ae0a4-121">Easing Functions</span></span>

  <span data-ttu-id="ae0a4-122">Můžete zvýšit animace s funkcí usnadnění, které poskytují větší kontrolu nad chováním animace.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="ae0a4-123">Například můžete použít <xref:System.Windows.Media.Animation.ElasticEase> do animace poskytnout pružné chování animace.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="ae0a4-124">Další informace najdete v tématu uvolnění typy v <xref:System.Windows.Media.Animation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="ae0a4-125">Grafika a vykreslování</span><span class="sxs-lookup"><span data-stu-id="ae0a4-125">Graphics and Rendering</span></span>

<span data-ttu-id="ae0a4-126">WPF obsahuje podporu pro vysoce kvalitní 2D grafika.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="ae0a4-127">Funkce zahrnuje štětce, geometrie, obrázků, tvarů a transformace.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="ae0a4-128">Další informace najdete v tématu [grafiky](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="ae0a4-129">Podle vykreslení grafické prvky <xref:System.Windows.Media.Visual> třídy.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="ae0a4-130">Struktura vizuální objekty na obrazovce je popsán vizuálního stromu.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="ae0a4-131">Další informace najdete v tématu [přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2-d-shapes"></a><span data-ttu-id="ae0a4-132">2D obrazce</span><span class="sxs-lookup"><span data-stu-id="ae0a4-132">2-D Shapes</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="ae0a4-133">poskytuje knihovnu běžně používané, vykreslované uživatelem vektoru [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] tvary, třeba obdélníky a symbol tří teček, které ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-133">provides a library of commonly used, vector-drawn [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagram znázorňující tři tečky a obdélníky.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="ae0a4-135">Tyto vnitřní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tvary nejsou jenom tvarů: jsou programovatelný prvky, které implementují mnoho funkcí, které očekáváte od většiny běžných ovládacích prvků, které zahrnují klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="ae0a4-136">Následující příklad ukazuje, jak zpracovat <xref:System.Windows.UIElement.MouseUp> Událost aktivovaná po kliknutí <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="ae0a4-137">Následující obrázek znázorňuje výstup pro předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Zprávy pole oznámením o "Jste klikli na tři tečky!"](./media/index/messagebox-text-output.png)

<span data-ttu-id="ae0a4-139">Další informace najdete v tématu [tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="ae0a4-140">Úvodní ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-140">For an introductory sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>

### <a name="2-d-geometries"></a><span data-ttu-id="ae0a4-141">2D geometrie</span><span class="sxs-lookup"><span data-stu-id="ae0a4-141">2-D Geometries</span></span>

<span data-ttu-id="ae0a4-142">Když [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obrazce, která [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje nestačí, můžete použít [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podpora geometrie a cesty k vytvoření vlastní.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-142">When the [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="ae0a4-143">Následující obrázek ukazuje, jak můžete pomocí geometrie vytvoření tvarů, jako kreslicího štětce a další Galerie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>

![Snímek obrazovky ukazující, jak můžete geometrie pro vytvoření tvarů.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="ae0a4-145">Další informace najdete v tématu [přehled geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="ae0a4-146">Úvodní ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-146">For an introductory sample, see [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>

### <a name="2-d-effects"></a><span data-ttu-id="ae0a4-147">2D efekty</span><span class="sxs-lookup"><span data-stu-id="ae0a4-147">2-D Effects</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="ae0a4-148">poskytuje knihovnu [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] třídy, které vám umožní vytvořit různé účinky.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-148">provides a library of [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="ae0a4-149">[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] Možnosti vykreslování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje vykreslení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které mají přechody, rastrových obrázků, kreseb a videa; a s nimi manipulovat s použitím otočení, škálování a zkosení.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-149">The [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="ae0a4-150">Následující obrázek poskytuje příklad mnoho efektů, můžete dosáhnout použitím [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] stopy.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>

![Ilustrace znázorňující různých štětců WPF a Malování prvky.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="ae0a4-152">Další informace najdete v tématu [přehled štětců WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="ae0a4-153">Úvodní ukázku najdete v tématu [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-153">For an introductory sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>

<a name="rendering"></a>

## <a name="3-d-rendering"></a><span data-ttu-id="ae0a4-154">3D vykreslování</span><span class="sxs-lookup"><span data-stu-id="ae0a4-154">3-D Rendering</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="ae0a4-155">poskytuje sadu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] možnosti vykreslování, které se integrují s [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafické podpory v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vytvářet zajímavější rozložení, aby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], dat a jejich vizualizace.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-155">provides a set of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] rendering capabilities that integrate with [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="ae0a4-156">Na jednom konci spektra [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umožňuje vykreslit [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] bitové kopie na povrchy [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] tvary, které ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] images onto the surfaces of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] shapes, which the following illustration demonstrates.</span></span>

![Snímek obrazovky zobrazující tvarů 3D s různé textury vzorku.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="ae0a4-158">Další informace najdete v tématu [přehled 3D grafiky](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-158">For more information, see [3-D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="ae0a4-159">Úvodní ukázku najdete v tématu [ukázka 3D pevné](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-159">For an introductory sample, see [3-D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="ae0a4-160">Animace</span><span class="sxs-lookup"><span data-stu-id="ae0a4-160">Animation</span></span>

<span data-ttu-id="ae0a4-161">Použijte animaci k vytvoření ovládacích prvků a elementů růst, zatřeste, zprovozněte a fade; a vytvářejte zajímavé přechody stránek a další.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="ae0a4-162">Protože [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] povoluje pro animaci většinu vlastností, ne jenom můžete animace většinu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objekty, můžete použít také [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pro animaci vlastní objekty, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>

![Snímek obrazovky animovaný datové krychle.](./media/index/animate-custom-objects.png)

<span data-ttu-id="ae0a4-164">Další informace najdete v tématu [přehled animace](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="ae0a4-165">Úvodní ukázku najdete v tématu [animace příkladu Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-165">For an introductory sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="ae0a4-166">Média</span><span class="sxs-lookup"><span data-stu-id="ae0a4-166">Media</span></span>

<span data-ttu-id="ae0a4-167">Obrázky, videa a zvuku způsoby média bohaté takzvané informace a uživatelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="ae0a4-168">Obrázky</span><span class="sxs-lookup"><span data-stu-id="ae0a4-168">Images</span></span>

<span data-ttu-id="ae0a4-169">Image, jako je například ikony, pozadí a dokonce i části animace, jsou základní součástí většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="ae0a4-170">Protože často budete muset použít Image, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zpřístupňuje schopnost pracovat s nimi v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="ae0a4-171">Následující obrázek znázorňuje pouze jedna z těchto způsobů.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="ae0a4-172">![Snímek obrazovky ukázkový používání stylů pro](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="ae0a4-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="ae0a4-173">Další informace najdete v tématu [Imaging přehled](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="ae0a4-174">Videa a zvuku</span><span class="sxs-lookup"><span data-stu-id="ae0a4-174">Video and Audio</span></span>

<span data-ttu-id="ae0a4-175">Základní funkce grafické možnosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je poskytuje nativní podporu pro práci s multimédii, která zahrnuje videa a zvuku.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="ae0a4-176">Následující příklad ukazuje, jak vložit multimediální přehrávač do aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="ae0a4-177"><xref:System.Windows.Controls.MediaElement> dokáže přehrávání videa a zvuku a je možné rozšířit dostatečně umožňuje snadno vytvářet vlastní [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae0a4-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span></span>

<span data-ttu-id="ae0a4-178">Další informace najdete v tématu [multimédia přehled](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a4-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae0a4-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae0a4-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="ae0a4-180">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="ae0a4-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="ae0a4-181">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="ae0a4-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="ae0a4-182">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="ae0a4-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="ae0a4-183">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="ae0a4-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="ae0a4-184">Animace a časování témata s postupy</span><span class="sxs-lookup"><span data-stu-id="ae0a4-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="ae0a4-185">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="ae0a4-185">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="ae0a4-186">Přehled multimédií</span><span class="sxs-lookup"><span data-stu-id="ae0a4-186">Multimedia Overview</span></span>](multimedia-overview.md)
