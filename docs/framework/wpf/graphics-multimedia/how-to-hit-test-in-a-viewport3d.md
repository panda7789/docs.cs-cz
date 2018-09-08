---
title: 'Postupy: Spuštění testu v objektu Viewport3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 297fe17b8844f7542255afcfe442fbf9b7a0d59d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140655"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="8d12a-102">Postupy: Spuštění testu v objektu Viewport3D</span><span class="sxs-lookup"><span data-stu-id="8d12a-102">How to: Hit Test in a Viewport3D</span></span>
<span data-ttu-id="8d12a-103">Tento příklad ukazuje, jak spuštění testu pro 3D vizuální prvky v <xref:System.Windows.Controls.Viewport3D>.</span><span class="sxs-lookup"><span data-stu-id="8d12a-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>  
  
 <span data-ttu-id="8d12a-104">Protože <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> vrátí informace o vytváření 2D a 3D, je možné iterovat přes výsledky testů číst pouze 3D výsledky.</span><span class="sxs-lookup"><span data-stu-id="8d12a-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <span data-ttu-id="8d12a-105"><xref:System.Windows.Media.HitTestResultBehavior> v následujícím kódu určuje způsob zpracování výsledků ověření pozice.</span><span class="sxs-lookup"><span data-stu-id="8d12a-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span>  <span data-ttu-id="8d12a-106">`UpdateResultInfo` a `UpdateMaterial` místně definované metody.</span><span class="sxs-lookup"><span data-stu-id="8d12a-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## <a name="see-also"></a><span data-ttu-id="8d12a-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d12a-107">See Also</span></span>  
 [<span data-ttu-id="8d12a-108">Spuštění testování ukázkové 3D</span><span class="sxs-lookup"><span data-stu-id="8d12a-108">3-D Hit Testing Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159959)
