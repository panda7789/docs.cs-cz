---
title: 'Postupy: Umístění podřízených elementů pomocí vlastností připojených k plátnu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: 886440304dc1bebdcfae66676254bef7ac35457d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552371"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a><span data-ttu-id="a0158-102">Postupy: Umístění podřízených elementů pomocí vlastností připojených k plátnu</span><span class="sxs-lookup"><span data-stu-id="a0158-102">How to: Use the Attached Properties of Canvas to Position Child Elements</span></span>
<span data-ttu-id="a0158-103">Tento příklad ukazuje, jak používat připojené vlastnosti <xref:System.Windows.Controls.Canvas> na pozici podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="a0158-103">This example shows how to use the attached properties of <xref:System.Windows.Controls.Canvas> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0158-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0158-104">Example</span></span>  
 <span data-ttu-id="a0158-105">Následující příklad přidá čtyři <xref:System.Windows.Controls.Button> elementy jako podřízené prvky nadřazený <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="a0158-105">The following example adds four <xref:System.Windows.Controls.Button> elements as child elements of a parent <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="a0158-106">Každý podřízený element představuje jedinečné připojené vlastnost <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, a <xref:System.Windows.Controls.Canvas.Top%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0158-106">Each child element represents a distinct attached property of <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, and <xref:System.Windows.Controls.Canvas.Top%2A>.</span></span> <span data-ttu-id="a0158-107">Každý <xref:System.Windows.Controls.Button> je umístěn relativně k nadřazené <xref:System.Windows.Controls.Canvas> a s ohledem na jeho hodnotu přiřazenou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a0158-107">Each <xref:System.Windows.Controls.Button> is positioned relative to the parent <xref:System.Windows.Controls.Canvas> and according to its assigned property value.</span></span>  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a0158-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0158-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="a0158-109">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="a0158-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="a0158-110">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="a0158-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [<span data-ttu-id="a0158-111">Přehled přidružených vlastností</span><span class="sxs-lookup"><span data-stu-id="a0158-111">Attached Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
