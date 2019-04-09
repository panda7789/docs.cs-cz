---
title: 'Postupy: Umístění podřízených elementů pomocí vlastností přidružených k plátnu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: 347c8502bd4c5fafcde7a142327f85bfb75b9954
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159624"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a><span data-ttu-id="d84a9-102">Postupy: Umístění podřízených elementů pomocí vlastností přidružených k plátnu</span><span class="sxs-lookup"><span data-stu-id="d84a9-102">How to: Use the Attached Properties of Canvas to Position Child Elements</span></span>
<span data-ttu-id="d84a9-103">Tento příklad ukazuje způsob použití připojené vlastnosti <xref:System.Windows.Controls.Canvas> umístění podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="d84a9-103">This example shows how to use the attached properties of <xref:System.Windows.Controls.Canvas> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d84a9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d84a9-104">Example</span></span>  
 <span data-ttu-id="d84a9-105">Následující příklad přidá čtyři <xref:System.Windows.Controls.Button> prvky jako podřízené prvky nadřazeného <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="d84a9-105">The following example adds four <xref:System.Windows.Controls.Button> elements as child elements of a parent <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="d84a9-106">Každý prvek je reprezentována <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, a <xref:System.Windows.Controls.Canvas.Top%2A>.</span><span class="sxs-lookup"><span data-stu-id="d84a9-106">Each element is represented by a <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, and <xref:System.Windows.Controls.Canvas.Top%2A>.</span></span>
<span data-ttu-id="d84a9-107">Každý <xref:System.Windows.Controls.Button> je umístěn vzhledem k nadřazeného <xref:System.Windows.Controls.Canvas> a s ohledem na její hodnota přiřazená vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d84a9-107">Each <xref:System.Windows.Controls.Button> is positioned relative to the parent <xref:System.Windows.Controls.Canvas> and according to its assigned property value.</span></span>  
  
 [!code-cpp[CanvasAttachedProperties#1](~/samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d84a9-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d84a9-108">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.Canvas.Bottom%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- <xref:System.Windows.Controls.Canvas.Right%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Button>
- [<span data-ttu-id="d84a9-109">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="d84a9-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="d84a9-110">– postupy</span><span class="sxs-lookup"><span data-stu-id="d84a9-110">How-to Topics</span></span>](canvas-how-to-topics.md)
- [<span data-ttu-id="d84a9-111">Přehled připojených vlastností</span><span class="sxs-lookup"><span data-stu-id="d84a9-111">Attached Properties Overview</span></span>](../advanced/attached-properties-overview.md)
