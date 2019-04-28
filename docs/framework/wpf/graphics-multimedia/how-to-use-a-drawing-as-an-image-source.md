---
title: 'Postupy: Použití kresby jako zdroje obrázku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: d4b91a6495e1c54400d5fbfe43b6311d908565a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769351"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a><span data-ttu-id="c274d-102">Postupy: Použití kresby jako zdroje obrázku</span><span class="sxs-lookup"><span data-stu-id="c274d-102">How to: Use a Drawing as an Image Source</span></span>
<span data-ttu-id="c274d-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Drawing> jako <xref:System.Windows.Controls.Image.Source%2A> pro <xref:System.Windows.Controls.Image> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c274d-103">This example shows how to use a <xref:System.Windows.Media.Drawing> as the <xref:System.Windows.Controls.Image.Source%2A> for an <xref:System.Windows.Controls.Image> control.</span></span> <span data-ttu-id="c274d-104">K zobrazení <xref:System.Windows.Media.Drawing> s <xref:System.Windows.Controls.Image> řídit, použijte <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> ovládacího prvku <xref:System.Windows.Controls.Image.Source%2A> a nastavit <xref:System.Windows.Media.DrawingImage> objektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> vlastnost výkresu, které chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="c274d-104">To display a <xref:System.Windows.Media.Drawing> with an <xref:System.Windows.Controls.Image> control, use a <xref:System.Windows.Media.DrawingImage> as the <xref:System.Windows.Controls.Image> control's <xref:System.Windows.Controls.Image.Source%2A> and set the <xref:System.Windows.Media.DrawingImage> object's <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> property to the drawing you want to display.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c274d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c274d-105">Example</span></span>  
 <span data-ttu-id="c274d-106">Následující příklad používá <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládací prvek pro zobrazení <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="c274d-106">The following example uses a <xref:System.Windows.Media.DrawingImage> and an <xref:System.Windows.Controls.Image> control to display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="c274d-107">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c274d-107">This example produces the following output:</span></span>  
  
 <span data-ttu-id="c274d-108">![GeometryDrawing dvě symbol tří teček](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="c274d-108">![A GeometryDrawing of two ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
<span data-ttu-id="c274d-109">DrawingImage</span><span class="sxs-lookup"><span data-stu-id="c274d-109">A DrawingImage</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c274d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c274d-110">See also</span></span>

- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="c274d-111">Vykreslení obrázku pomocí ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="c274d-111">Draw an Image Using ImageDrawing</span></span>](how-to-draw-an-image-using-imagedrawing.md)
- [<span data-ttu-id="c274d-112">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="c274d-112">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="c274d-113">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="c274d-113">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="c274d-114">PresentationOptions:Freeze – atribut</span><span class="sxs-lookup"><span data-stu-id="c274d-114">PresentationOptions:Freeze Attribute</span></span>](../advanced/presentationoptions-freeze-attribute.md)
