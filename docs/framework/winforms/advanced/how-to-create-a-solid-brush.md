---
title: 'Postupy: Vytvoření plného štětce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
ms.openlocfilehash: d7fb7c11a69cae69210dd2eece3336bc40c505c7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711977"
---
# <a name="how-to-create-a-solid-brush"></a><span data-ttu-id="de039-102">Postupy: Vytvoření plného štětce</span><span class="sxs-lookup"><span data-stu-id="de039-102">How to: Create a Solid Brush</span></span>
<span data-ttu-id="de039-103">Tento příklad vytvoří <xref:System.Drawing.SolidBrush> objekt, který můžete používat <xref:System.Drawing.Graphics> objekt pro vyplnění tvarů.</span><span class="sxs-lookup"><span data-stu-id="de039-103">This example creates a <xref:System.Drawing.SolidBrush> object that can be used by a <xref:System.Drawing.Graphics> object for filling shapes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de039-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="de039-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="de039-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="de039-105">Robust Programming</span></span>  
 <span data-ttu-id="de039-106">Po dokončení jejich používání byste měli volat <xref:System.IDisposable.Dispose%2A> na objekty, které využívají systémové prostředky, jako jsou štětce objekty.</span><span class="sxs-lookup"><span data-stu-id="de039-106">After you have finished using them, you should call <xref:System.IDisposable.Dispose%2A> on objects that consume system resources, such as brush objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de039-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de039-107">See also</span></span>
- <xref:System.Drawing.SolidBrush>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="de039-108">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="de039-108">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="de039-109">Štětce a vyplněné obrazce v GDI+</span><span class="sxs-lookup"><span data-stu-id="de039-109">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
- [<span data-ttu-id="de039-110">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="de039-110">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
