---
title: "Grafika a multimédia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 013ae46e2d90a9eda42d33e95e590812489fa04b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="cd7c4-102">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="cd7c4-102">Graphics and Multimedia</span></span>
<a name="introduction"></a>
<span data-ttu-id="cd7c4-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje podporu pro multimédia, vektorové grafiky, animace a obsahu složení, a usnadňuje vývojářům tvorbu zajímavé uživatelská rozhraní a obsahu.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="cd7c4-104">Pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], můžete vytvořit vektorová grafika nebo komplexní animace a integrovat média do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-104">Using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you can create vector graphics or complex animations and integrate media into your applications.</span></span>  
  
 <span data-ttu-id="cd7c4-105">Toto téma představuje funkce grafiky, animace a média [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], která umožňují přidání grafiky, přechod důsledky, zvuk a video do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd7c4-106">Použití typů WPF ve službě Windows není doporučeno.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="cd7c4-107">Pokud budete chtít používat typy WPF ve službě Windows, službu nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="cd7c4-108">Co je nového v grafiky a multimédia v grafickém subsystému WPF 4</span><span class="sxs-lookup"><span data-stu-id="cd7c4-108">What's New with Graphics and Multimedia in WPF 4</span></span>  
 <span data-ttu-id="cd7c4-109">Několik provedly změny týkající se grafiky a animace.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-109">Several changes have been made related to graphics and animations.</span></span>  
  
-   <span data-ttu-id="cd7c4-110">Zaokrouhlení rozložení</span><span class="sxs-lookup"><span data-stu-id="cd7c4-110">Layout Rounding</span></span>  
  
     <span data-ttu-id="cd7c4-111">Když okraje objektu klesne uprostřed pixelů zařízení, můžete vytvořit grafika systému DPI nezávislé vykreslování artefaktů, jako jsou rozmazaně nebo poloprůhledné hran.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="cd7c4-112">Předchozí verze WPF zahrnuty pixelů uchycení a pomáhaly zvládat tento případ.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="cd7c4-113">Silverlight 2 zavedl zaokrouhlení rozložení, který je jiný způsob, jak přesunout elementy tak, aby okraje spadají na hranicích celou pixelů.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="cd7c4-114">WPF teď podporuje rozložení zaokrouhlení s <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> přidružená vlastnost na <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>  
  
-   <span data-ttu-id="cd7c4-115">Složení v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="cd7c4-115">Cached Composition</span></span>  
  
     <span data-ttu-id="cd7c4-116">Pomocí nové <xref:System.Windows.Media.BitmapCache> a <xref:System.Windows.Media.BitmapCacheBrush> třídy, může mezipaměti komplexní součástí vizuálním stromu jako rastrový obrázek a výrazně zlepšit čas vykreslování.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="cd7c4-117">Bitmapy stále poměrně rychle reaguje na vstup uživatele, jako je například kliknutí myší a malovat na další prvky stejně jako všechny štětce.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>  
  
-   <span data-ttu-id="cd7c4-118">Podpora shaderu 3 pixelů</span><span class="sxs-lookup"><span data-stu-id="cd7c4-118">Pixel Shader 3 Support</span></span>  
  
     <span data-ttu-id="cd7c4-119">WPF 4 staví na <xref:System.Windows.Media.Effects.ShaderEffect> podpory, které jsou dostupné ve verzi WPF 3.5 SP1 tím, že aplikace k zápisu důsledky pomocí shaderu Pixel (PS) verze 3.0.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="cd7c4-120">Model shaderu PS 3.0 je složitější než PS 2.0, která umožňuje ještě větší vliv na podporovaný hardware.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>  
  
-   <span data-ttu-id="cd7c4-121">Funkce usnadnění</span><span class="sxs-lookup"><span data-stu-id="cd7c4-121">Easing Functions</span></span>  
  
     <span data-ttu-id="cd7c4-122">Můžete vylepšit animace pomocí funkce usnadnění, které umožňují další kontrolu nad chováním animace.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="cd7c4-123">Například můžete použít <xref:System.Windows.Media.Animation.ElasticEase> do animace umožnit animace pružné chování.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="cd7c4-124">Další informace najdete v tématu nejvýraznější typy v <xref:System.Windows.Media.Animation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a><span data-ttu-id="cd7c4-125">Grafika a vykreslování</span><span class="sxs-lookup"><span data-stu-id="cd7c4-125">Graphics and Rendering</span></span>  
 <span data-ttu-id="cd7c4-126">WPF zahrnuje podporu pro 2D grafiky vysoké kvality.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="cd7c4-127">Funkce zahrnuje štětce, geometrie, obrázků, tvarů a transformace.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="cd7c4-128">Další informace najdete v tématu [grafiky](../../../../docs/framework/wpf/graphics-multimedia/graphics.md).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-128">For more information, see [Graphics](../../../../docs/framework/wpf/graphics-multimedia/graphics.md).</span></span> <span data-ttu-id="cd7c4-129">Je na základě vykreslování grafické elementy <xref:System.Windows.Media.Visual> třídy.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="cd7c4-130">Struktura vizuální objekty na obrazovce je popsána ve vizuálním stromu.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="cd7c4-131">Další informace najdete v tématu [vykreslování přehled grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-131">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
### <a name="2-d-shapes"></a><span data-ttu-id="cd7c4-132">2D obrazce</span><span class="sxs-lookup"><span data-stu-id="cd7c4-132">2-D Shapes</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="cd7c4-133">poskytuje knihovnu běžně používané, vector vykreslené [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] tvary, například obdélníků a tři tečky, které na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-133"> provides a library of commonly used, vector-drawn [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>  
  
 <span data-ttu-id="cd7c4-134">![Výpustky a obdélníky](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")</span><span class="sxs-lookup"><span data-stu-id="cd7c4-134">![Ellipses and rectangles](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")</span></span>  
  
 <span data-ttu-id="cd7c4-135">Tyto vnitřní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tvarů nejsou jenom tvarů: jsou programovatelný prvků, které implementují řadu funkcí, které byste očekávali od většiny běžných ovládacích prvků, které zahrnují klávesnici a myš vstup.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="cd7c4-136">Následující příklad ukazuje, jak bude zpracováván <xref:System.Windows.UIElement.MouseUp> kliknutím vyvolaná událost <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>  
  
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
  
 <span data-ttu-id="cd7c4-137">Následující obrázek ukazuje výstup pro předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>  
  
 <span data-ttu-id="cd7c4-138">![Okno s textem "kliknuli jste na tlačítko se třemi tečkami & č. 33;" ] (../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")</span><span class="sxs-lookup"><span data-stu-id="cd7c4-138">![A window with the text "you clicked the ellipse&#33;"](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")</span></span>  
  
 <span data-ttu-id="cd7c4-139">Další informace najdete v tématu [tvarů a základní kreslení v přehledu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-139">For more information, see [Shapes and Basic Drawing in WPF Overview](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="cd7c4-140">Úvodní ukázka, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-140">For an introductory sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
### <a name="2-d-geometries"></a><span data-ttu-id="cd7c4-141">2D geometrie</span><span class="sxs-lookup"><span data-stu-id="cd7c4-141">2-D Geometries</span></span>  
 <span data-ttu-id="cd7c4-142">Když [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obrazce, který [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje nestačí, můžete použít [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podpora geometrie a cesty k vytvoření vlastní.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-142">When the [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="cd7c4-143">Následující obrázek ukazuje, jak můžete pomocí geometrie vytvořit tvarů, jako kreslení štětce a dalších oříznutí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>  
  
 <span data-ttu-id="cd7c4-144">![Různé použití cesty](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")</span><span class="sxs-lookup"><span data-stu-id="cd7c4-144">![Various uses of a Path](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")</span></span>  
  
 <span data-ttu-id="cd7c4-145">Další informace najdete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-145">For more information, see [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span> <span data-ttu-id="cd7c4-146">Úvodní ukázka, najdete v části [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-146">For an introductory sample, see [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
### <a name="2-d-effects"></a><span data-ttu-id="cd7c4-147">2D efekty</span><span class="sxs-lookup"><span data-stu-id="cd7c4-147">2-D Effects</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="cd7c4-148">poskytuje knihovnu [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] třídy, které můžete použít k vytvoření různé efekty.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-148"> provides a library of [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="cd7c4-149">[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] Možnosti vykreslování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje schopnost malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které mají přechody, rastrové obrázky, kresby a videa; a s nimi manipulovat s použitím otáčení škálování a zkosení.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-149">The [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="cd7c4-150">Následující obrázek poskytuje příklad mnoho důsledky můžete dosáhnout pomocí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] štětce.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>  
  
 <span data-ttu-id="cd7c4-151">![Ilustrace různých štětců](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")</span><span class="sxs-lookup"><span data-stu-id="cd7c4-151">![Illustration of different brushes](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")</span></span>  
  
 <span data-ttu-id="cd7c4-152">Další informace najdete v tématu [WPF štětce přehled](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-152">For more information, see [WPF Brushes Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).</span></span> <span data-ttu-id="cd7c4-153">Úvodní ukázka, najdete v části [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-153">For an introductory sample, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a><span data-ttu-id="cd7c4-154">3D vykreslení</span><span class="sxs-lookup"><span data-stu-id="cd7c4-154">3-D Rendering</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="cd7c4-155">poskytuje sadu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] možnosti vykreslování, které se integrují s [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiky podporují v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] v pořadí pro vytvoření zajímavější rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]a vizualizace dat sady.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-155"> provides a set of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] rendering capabilities that integrate with [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="cd7c4-156">Na jednom konci spektra [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje vykreslení [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] bitové kopie na povrchy [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] tvary, které ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] images onto the surfaces of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] shapes, which the following illustration demonstrates.</span></span>  
  
 <span data-ttu-id="cd7c4-157">![Snímek obrazovky Visual3D –](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")</span><span class="sxs-lookup"><span data-stu-id="cd7c4-157">![Visual3D sample screen shot](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")</span></span>  
  
 <span data-ttu-id="cd7c4-158">Další informace najdete v tématu [3D přehled grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-158">For more information, see [3-D Graphics Overview](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).</span></span> <span data-ttu-id="cd7c4-159">Úvodní ukázka, najdete v části [3D ukázka pevné](http://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-159">For an introductory sample, see [3-D Solids Sample](http://go.microsoft.com/fwlink/?LinkID=159964).</span></span>  
  
<a name="animation"></a>   
## <a name="animation"></a><span data-ttu-id="cd7c4-160">Animace</span><span class="sxs-lookup"><span data-stu-id="cd7c4-160">Animation</span></span>  
 <span data-ttu-id="cd7c4-161">Používat animace k vytvoření a ovládacích prvků růst, zatřesením, číselníků a vykreslit; a vytvořit zajímavé přechody stránek a další.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="cd7c4-162">Protože [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje pro animaci většinu vlastností, ne jenom můžete animace většinu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objekty, můžete použít také [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pro animaci vlastní objekty, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>  
  
 <span data-ttu-id="cd7c4-163">![Bitové kopie animovaný datové krychle](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")</span><span class="sxs-lookup"><span data-stu-id="cd7c4-163">![Images of an animated cube](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")</span></span>  
  
 <span data-ttu-id="cd7c4-164">Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-164">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="cd7c4-165">Úvodní ukázka, najdete v části [animace příklad Galerie](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-165">For an introductory sample, see [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
<a name="media"></a>   
## <a name="media"></a><span data-ttu-id="cd7c4-166">Média</span><span class="sxs-lookup"><span data-stu-id="cd7c4-166">Media</span></span>  
 <span data-ttu-id="cd7c4-167">Obrázky, videa a zvuku způsoby média bohaté zdůraznění informace a uživatelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>  
  
### <a name="images"></a><span data-ttu-id="cd7c4-168">Obrázky</span><span class="sxs-lookup"><span data-stu-id="cd7c4-168">Images</span></span>  
 <span data-ttu-id="cd7c4-169">Bitové kopie, které obsahují ikony, pozadí a to i v části animací, jsou součástí základní většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="cd7c4-170">Protože často budete muset použít Image, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zpřístupňuje schopnost pracovat s nimi mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="cd7c4-171">Následující obrázek znázorňuje právě jeden z těchto způsobů.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-171">The following illustration shows just one of those ways.</span></span>  
  
 <span data-ttu-id="cd7c4-172">![Snímek obrazovky stylů](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="cd7c4-172">![Styling sample screen shot](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>  
  
 <span data-ttu-id="cd7c4-173">Další informace najdete v tématu [Imaging přehled](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-173">For more information, see [Imaging Overview](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).</span></span>  
  
### <a name="video-and-audio"></a><span data-ttu-id="cd7c4-174">Videa a zvuku</span><span class="sxs-lookup"><span data-stu-id="cd7c4-174">Video and Audio</span></span>  
 <span data-ttu-id="cd7c4-175">Základní funkce grafické možnosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je poskytnout nativní podporu pro práci s multimédia, která zahrnuje videa a zvuku.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="cd7c4-176">Následující příklad ukazuje, jak přehrávač médií vložení do aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd7c4-176">The following example shows how to insert a media player into an application.</span></span>  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <span data-ttu-id="cd7c4-177"><xref:System.Windows.Controls.MediaElement>může přehrávání videa a zvuku a je dostatečně extensible umožňující snadné vytváření vlastní [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd7c4-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="cd7c4-178">Další informace najdete v tématu [multimédia přehled](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd7c4-178">For more information, see the [Multimedia Overview](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7c4-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd7c4-179">See Also</span></span>  
 <xref:System.Windows.Media>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Media3D>  
 [<span data-ttu-id="cd7c4-180">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="cd7c4-180">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="cd7c4-181">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="cd7c4-181">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="cd7c4-182">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="cd7c4-182">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="cd7c4-183">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="cd7c4-183">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="cd7c4-184">Animace a časování</span><span class="sxs-lookup"><span data-stu-id="cd7c4-184">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="cd7c4-185">3D grafiky</span><span class="sxs-lookup"><span data-stu-id="cd7c4-185">3-D Graphics</span></span>](http://msdn.microsoft.com/library/565c1f3c-235b-47de-b05b-3b53ed63f1b8)  
 [<span data-ttu-id="cd7c4-186">Multimédia</span><span class="sxs-lookup"><span data-stu-id="cd7c4-186">Multimedia</span></span>](http://msdn.microsoft.com/library/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
