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
ms.openlocfilehash: 8dad10fbfb0dfb34fee6a5640b1a49e7fb234479
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520744"
---
# <a name="how-to-create-a-solid-brush"></a><span data-ttu-id="ea469-102">Postupy: Vytvoření plného štětce</span><span class="sxs-lookup"><span data-stu-id="ea469-102">How to: Create a Solid Brush</span></span>
<span data-ttu-id="ea469-103">Tento příklad vytvoří <xref:System.Drawing.SolidBrush> objektu, která mohou být využívána <xref:System.Drawing.Graphics> objekt pro vyplnění tvarů.</span><span class="sxs-lookup"><span data-stu-id="ea469-103">This example creates a <xref:System.Drawing.SolidBrush> object that can be used by a <xref:System.Drawing.Graphics> object for filling shapes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea469-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea469-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ea469-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ea469-105">Robust Programming</span></span>  
 <span data-ttu-id="ea469-106">Po dokončení jejich používání by měly volat <xref:System.IDisposable.Dispose%2A> u objektů, které využívají systémové prostředky, například štětce objekty.</span><span class="sxs-lookup"><span data-stu-id="ea469-106">After you have finished using them, you should call <xref:System.IDisposable.Dispose%2A> on objects that consume system resources, such as brush objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea469-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea469-107">See Also</span></span>  
 <xref:System.Drawing.SolidBrush>  
 <xref:System.Drawing.Brush>  
 [<span data-ttu-id="ea469-108">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="ea469-108">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="ea469-109">Štětce a vyplněné obrazce v GDI+</span><span class="sxs-lookup"><span data-stu-id="ea469-109">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 [<span data-ttu-id="ea469-110">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="ea469-110">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
