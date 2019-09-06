---
title: 'Postupy: Ověření pozice v objektu Viewport3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 6eb68f4668c6ea5aa8728a81fac98409896f3fd2
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373271"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="c214a-102">Postupy: Ověření pozice v objektu Viewport3D</span><span class="sxs-lookup"><span data-stu-id="c214a-102">How to: Hit Test in a Viewport3D</span></span>

<span data-ttu-id="c214a-103">Tento příklad ukazuje, jak spustit test pro 3D vizuály v <xref:System.Windows.Controls.Viewport3D>.</span><span class="sxs-lookup"><span data-stu-id="c214a-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>

<span data-ttu-id="c214a-104">Vzhledem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> k tomu, že vrátí 2D a prostorové informace, je možné iterovat výsledky testů, aby se četly jenom 3D výsledky.</span><span class="sxs-lookup"><span data-stu-id="c214a-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>

[!code-csharp[HitTest3D#HitTest3D3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
[!code-vb[HitTest3D#HitTest3D3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]

<span data-ttu-id="c214a-105"><xref:System.Windows.Media.HitTestResultBehavior> V následujícím kódu určuje způsob zpracování výsledků testu volání.</span><span class="sxs-lookup"><span data-stu-id="c214a-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span> <span data-ttu-id="c214a-106">`UpdateResultInfo`a `UpdateMaterial` jsou místně definované metody.</span><span class="sxs-lookup"><span data-stu-id="c214a-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>

[!code-csharp[HitTest3D#HitTest3D3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
[!code-vb[HitTest3D#HitTest3D3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]
