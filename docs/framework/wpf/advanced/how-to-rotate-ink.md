---
title: 'Postupy: Otočení rukopisu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], rotating
- rotating ink [WPF]
ms.assetid: fac36cc9-dd01-41ca-9bde-9d33e3790bbe
ms.openlocfilehash: 31f5d0ffb6f0fdcdaef13bc44653f8c7938ac7f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768456"
---
# <a name="how-to-rotate-ink"></a><span data-ttu-id="820ba-102">Postupy: Otočení rukopisu</span><span class="sxs-lookup"><span data-stu-id="820ba-102">How to: Rotate Ink</span></span>
## <a name="example"></a><span data-ttu-id="820ba-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="820ba-103">Example</span></span>  
 <span data-ttu-id="820ba-104">Následující příklad zkopíruje ink z <xref:System.Windows.Controls.InkCanvas> k <xref:System.Windows.Controls.Canvas> , který obsahuje <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="820ba-104">The following example copies the ink from an <xref:System.Windows.Controls.InkCanvas> to a <xref:System.Windows.Controls.Canvas> that contains an <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="820ba-105">Když ho zkopíruje rukopisu, je také otočí rukopis 90 stupňů po směru hodinových ručiček.</span><span class="sxs-lookup"><span data-stu-id="820ba-105">When the application copies the ink, it also rotates the ink 90 degrees clockwise.</span></span>  
  
 [!code-xaml[HowToRotateInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[HowToRotateInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="820ba-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="820ba-106">Example</span></span>  
 <span data-ttu-id="820ba-107">V následujícím příkladu je vlastní <xref:System.Windows.Documents.Adorner> , který otáčí tahy na <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="820ba-107">The following example is a custom <xref:System.Windows.Documents.Adorner> that rotates the strokes on an <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[AdornerForStrokes#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/RotatingAdornerForStrokes.cs#1)]
 [!code-vb[AdornerForStrokes#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/RotatingAdornerForStrokes.vb#1)]  
  
 <span data-ttu-id="820ba-108">V následujícím příkladu je [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor, který definuje <xref:System.Windows.Controls.InkPresenter> a naplní barvou.</span><span class="sxs-lookup"><span data-stu-id="820ba-108">The following example is a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that defines an <xref:System.Windows.Controls.InkPresenter> and populates it with ink.</span></span> <span data-ttu-id="820ba-109">`Window_Loaded` Obslužná rutina události přidá vlastní doplněk pro úpravy k <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="820ba-109">The `Window_Loaded` event handler adds the custom adorner to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-xaml[AdornerForStrokes#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[AdornerForStrokes#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml.cs#3)]
 [!code-vb[AdornerForStrokes#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/Window1.xaml.vb#3)]
