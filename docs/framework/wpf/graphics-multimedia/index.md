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
ms.openlocfilehash: eb078c1116e45aa6229ef8b38b5f3c9d5f0f8824
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-and-multimedia"></a>Grafika a multimédia
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje podporu pro multimédia, vektorové grafiky, animace a obsahu složení, a usnadňuje vývojářům tvorbu zajímavé uživatelská rozhraní a obsahu. Pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], můžete vytvořit vektorová grafika nebo komplexní animace a integrovat média do svých aplikací.  
  
 Toto téma představuje funkce grafiky, animace a média [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], která umožňují přidání grafiky, přechod důsledky, zvuk a video do vaší aplikace.  
  
> [!NOTE]
>  Použití typů WPF ve službě Windows není doporučeno. Pokud budete chtít používat typy WPF ve službě Windows, službu nemusí fungovat podle očekávání.   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Co je nového v grafiky a multimédia v grafickém subsystému WPF 4  
 Několik provedly změny týkající se grafiky a animace.  
  
-   Zaokrouhlení rozložení  
  
     Když okraje objektu klesne uprostřed pixelů zařízení, můžete vytvořit grafika systému DPI nezávislé vykreslování artefaktů, jako jsou rozmazaně nebo poloprůhledné hran. Předchozí verze WPF zahrnuty pixelů uchycení a pomáhaly zvládat tento případ. Silverlight 2 zavedl zaokrouhlení rozložení, který je jiný způsob, jak přesunout elementy tak, aby okraje spadají na hranicích celou pixelů. WPF teď podporuje rozložení zaokrouhlení s <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> přidružená vlastnost na <xref:System.Windows.FrameworkElement>.  
  
-   Složení v mezipaměti  
  
     Pomocí nové <xref:System.Windows.Media.BitmapCache> a <xref:System.Windows.Media.BitmapCacheBrush> třídy, může mezipaměti komplexní součástí vizuálním stromu jako rastrový obrázek a výrazně zlepšit čas vykreslování. Bitmapy stále poměrně rychle reaguje na vstup uživatele, jako je například kliknutí myší a malovat na další prvky stejně jako všechny štětce.  
  
-   Podpora shaderu 3 pixelů  
  
     WPF 4 staví na <xref:System.Windows.Media.Effects.ShaderEffect> podpory, které jsou dostupné ve verzi WPF 3.5 SP1 tím, že aplikace k zápisu důsledky pomocí shaderu Pixel (PS) verze 3.0. Model shaderu PS 3.0 je složitější než PS 2.0, která umožňuje ještě větší vliv na podporovaný hardware.  
  
-   Funkce usnadnění  
  
     Můžete vylepšit animace pomocí funkce usnadnění, které umožňují další kontrolu nad chováním animace. Například můžete použít <xref:System.Windows.Media.Animation.ElasticEase> do animace umožnit animace pružné chování. Další informace najdete v tématu nejvýraznější typy v <xref:System.Windows.Media.Animation> oboru názvů.  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a>Grafika a vykreslování  
 WPF zahrnuje podporu pro 2D grafiky vysoké kvality. Funkce zahrnuje štětce, geometrie, obrázků, tvarů a transformace. Další informace najdete v tématu [grafiky](../../../../docs/framework/wpf/graphics-multimedia/graphics.md). Je na základě vykreslování grafické elementy <xref:System.Windows.Media.Visual> třídy. Struktura vizuální objekty na obrazovce je popsána ve vizuálním stromu. Další informace najdete v tématu [vykreslování přehled grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
### <a name="2-d-shapes"></a>2D obrazce  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]poskytuje knihovnu běžně používané, vector vykreslené [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] tvary, například obdélníků a tři tečky, které na následujícím obrázku.  
  
 ![Výpustky a obdélníky](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 Tyto vnitřní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tvarů nejsou jenom tvarů: jsou programovatelný prvků, které implementují řadu funkcí, které byste očekávali od většiny běžných ovládacích prvků, které zahrnují klávesnici a myš vstup. Následující příklad ukazuje, jak bude zpracováván <xref:System.Windows.UIElement.MouseUp> kliknutím vyvolaná událost <xref:System.Windows.Shapes.Ellipse> elementu.  
  
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
  
 Následující obrázek ukazuje výstup pro předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu.  
  
 ![Okno s textem "kliknuli jste na tlačítko se třemi tečkami & č. 33;" ] (../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Další informace najdete v tématu [tvarů a základní kreslení v přehledu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md). Úvodní ukázka, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
### <a name="2-d-geometries"></a>2D geometrie  
 Když [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obrazce, který [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje nestačí, můžete použít [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podpora geometrie a cesty k vytvoření vlastní. Následující obrázek ukazuje, jak můžete pomocí geometrie vytvořit tvarů, jako kreslení štětce a dalších oříznutí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy.  
  
 ![Různé použití cesty](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 Další informace najdete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md). Úvodní ukázka, najdete v části [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
### <a name="2-d-effects"></a>2D efekty  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]poskytuje knihovnu [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] třídy, které můžete použít k vytvoření různé efekty. [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] Možnosti vykreslování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje schopnost malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, které mají přechody, rastrové obrázky, kresby a videa; a s nimi manipulovat s použitím otáčení škálování a zkosení. Následující obrázek poskytuje příklad mnoho důsledky můžete dosáhnout pomocí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] štětce.  
  
 ![Ilustrace různých štětců](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 Další informace najdete v tématu [WPF štětce přehled](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md). Úvodní ukázka, najdete v části [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a>3D vykreslení  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]poskytuje sadu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] možnosti vykreslování, které se integrují s [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiky podporují v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] v pořadí pro vytvoření zajímavější rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]a vizualizace dat sady. Na jednom konci spektra [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje vykreslení [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] bitové kopie na povrchy [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] tvary, které ukazuje následující obrázek.  
  
 ![Snímek obrazovky Visual3D –](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Další informace najdete v tématu [3D přehled grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md). Úvodní ukázka, najdete v části [3D ukázka pevné](http://go.microsoft.com/fwlink/?LinkID=159964).  
  
<a name="animation"></a>   
## <a name="animation"></a>Animace  
 Používat animace k vytvoření a ovládacích prvků růst, zatřesením, číselníků a vykreslit; a vytvořit zajímavé přechody stránek a další. Protože [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje pro animaci většinu vlastností, ne jenom můžete animace většinu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objekty, můžete použít také [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pro animaci vlastní objekty, které vytvoříte.  
  
 ![Bitové kopie animovaný datové krychle](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Úvodní ukázka, najdete v části [animace příklad Galerie](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
<a name="media"></a>   
## <a name="media"></a>Média  
 Obrázky, videa a zvuku způsoby média bohaté zdůraznění informace a uživatelské prostředí.  
  
### <a name="images"></a>Obrázky  
 Bitové kopie, které obsahují ikony, pozadí a to i v části animací, jsou součástí základní většinu aplikací. Protože často budete muset použít Image, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zpřístupňuje schopnost pracovat s nimi mnoha různými způsoby. Následující obrázek znázorňuje právě jeden z těchto způsobů.  
  
 ![Snímek obrazovky stylů](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
 Další informace najdete v tématu [Imaging přehled](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="video-and-audio"></a>Videa a zvuku  
 Základní funkce grafické možnosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je poskytnout nativní podporu pro práci s multimédia, která zahrnuje videa a zvuku. Následující příklad ukazuje, jak přehrávač médií vložení do aplikace.  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement>může přehrávání videa a zvuku a je dostatečně extensible umožňující snadné vytváření vlastní [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
 Další informace najdete v tématu [multimédia přehled](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Media3D>  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Přehled objektů Shape a základního kreslení ve WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Animace a časování](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [3D grafiky](http://msdn.microsoft.com/en-us/565c1f3c-235b-47de-b05b-3b53ed63f1b8)  
 [Multimédia](http://msdn.microsoft.com/en-us/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
