---
title: 'Postupy: Nastavení barvy pera'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: a2645112950be88cbc569e0be7889c0f1019223d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710379"
---
# <a name="how-to-set-the-color-of-a-pen"></a><span data-ttu-id="f77e8-102">Postupy: Nastavení barvy pera</span><span class="sxs-lookup"><span data-stu-id="f77e8-102">How to: Set the Color of a Pen</span></span>
<span data-ttu-id="f77e8-103">V tomto příkladu změní barvu existující <xref:System.Drawing.Pen> objektu</span><span class="sxs-lookup"><span data-stu-id="f77e8-103">This example changes the color of a pre-existing <xref:System.Drawing.Pen> object</span></span>  
  
## <a name="example"></a><span data-ttu-id="f77e8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f77e8-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f77e8-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f77e8-105">Compiling the Code</span></span>  
 <span data-ttu-id="f77e8-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f77e8-106">This example requires:</span></span>  
  
-   <span data-ttu-id="f77e8-107">A <xref:System.Drawing.Pen> objekt s názvem `myPen`.</span><span class="sxs-lookup"><span data-stu-id="f77e8-107">A <xref:System.Drawing.Pen> object named `myPen`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f77e8-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f77e8-108">Robust Programming</span></span>  
 <span data-ttu-id="f77e8-109">Byste měli volat <xref:System.Drawing.Pen.Dispose%2A> na objekty, které využívají systémové prostředky (například <xref:System.Drawing.Pen> objekty) po dokončení jejich používání.</span><span class="sxs-lookup"><span data-stu-id="f77e8-109">You should call <xref:System.Drawing.Pen.Dispose%2A> on objects that consume system resources (such as <xref:System.Drawing.Pen> objects) after you are finished using them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f77e8-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f77e8-110">See also</span></span>
- <xref:System.Drawing.Pen>
- [<span data-ttu-id="f77e8-111">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="f77e8-111">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="f77e8-112">Postupy: Vytvoření pera</span><span class="sxs-lookup"><span data-stu-id="f77e8-112">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="f77e8-113">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="f77e8-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="f77e8-114">Pera, čáry a obdélníky v GDI+</span><span class="sxs-lookup"><span data-stu-id="f77e8-114">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
