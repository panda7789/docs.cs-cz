---
title: "Postupy: Použití kresby jako zdroje obrázku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e0fe8f7d3633143348693c95d92dd2715bd0442
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a><span data-ttu-id="dd459-102">Postupy: Použití kresby jako zdroje obrázku</span><span class="sxs-lookup"><span data-stu-id="dd459-102">How to: Use a Drawing as an Image Source</span></span>
<span data-ttu-id="dd459-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Drawing> jako <xref:System.Windows.Controls.Image.Source%2A> pro <xref:System.Windows.Controls.Image> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dd459-103">This example shows how to use a <xref:System.Windows.Media.Drawing> as the <xref:System.Windows.Controls.Image.Source%2A> for an <xref:System.Windows.Controls.Image> control.</span></span> <span data-ttu-id="dd459-104">K zobrazení <xref:System.Windows.Media.Drawing> s <xref:System.Windows.Controls.Image> řídit, použijte <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> ovládacího prvku <xref:System.Windows.Controls.Image.Source%2A> a nastavte <xref:System.Windows.Media.DrawingImage> objektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> vlastnost kreslení chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="dd459-104">To display a <xref:System.Windows.Media.Drawing> with an <xref:System.Windows.Controls.Image> control, use a <xref:System.Windows.Media.DrawingImage> as the <xref:System.Windows.Controls.Image> control's <xref:System.Windows.Controls.Image.Source%2A> and set the <xref:System.Windows.Media.DrawingImage> object's <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> property to the drawing you want to display.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd459-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd459-105">Example</span></span>  
 <span data-ttu-id="dd459-106">Následující příklad používá <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládacího prvku pro zobrazení <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="dd459-106">The following example uses a <xref:System.Windows.Media.DrawingImage> and an <xref:System.Windows.Controls.Image> control to display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="dd459-107">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="dd459-107">This example produces the following output:</span></span>  
  
 <span data-ttu-id="dd459-108">![Objekt GeometryDrawing sestávající ze dvou výpustky](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="dd459-108">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
<span data-ttu-id="dd459-109">DrawingImage</span><span class="sxs-lookup"><span data-stu-id="dd459-109">A DrawingImage</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="dd459-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd459-110">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="dd459-111">Vykreslení obrázku pomocí ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="dd459-111">Draw an Image Using ImageDrawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [<span data-ttu-id="dd459-112">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="dd459-112">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="dd459-113">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="dd459-113">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="dd459-114">PresentationOptions:Freeze – atribut</span><span class="sxs-lookup"><span data-stu-id="dd459-114">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
