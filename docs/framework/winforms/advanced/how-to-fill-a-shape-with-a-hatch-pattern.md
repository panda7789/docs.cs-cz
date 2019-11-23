---
title: 'Postupy: Vyplnění obrazce pomocí nesouvislého vzoru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: b80708f0ce722b1809fe49190639231e7e4c8329
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320057"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="82aac-102">Postupy: Vyplnění obrazce pomocí nesouvislého vzoru</span><span class="sxs-lookup"><span data-stu-id="82aac-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="82aac-103">Vzor šrafování se skládá ze dvou barev: jednoho pro pozadí a jeden pro čáry, které tvoří vzorek na pozadí.</span><span class="sxs-lookup"><span data-stu-id="82aac-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="82aac-104">Chcete-li vyplnit uzavřený tvar pomocí vzoru šrafování, použijte objekt <xref:System.Drawing.Drawing2D.HatchBrush>.</span><span class="sxs-lookup"><span data-stu-id="82aac-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="82aac-105">Následující příklad ukazuje, jak vyplnit elipsu vzorem šrafování:</span><span class="sxs-lookup"><span data-stu-id="82aac-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="82aac-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="82aac-106">Example</span></span>  
 <span data-ttu-id="82aac-107">Konstruktor <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> přebírá tři argumenty: styl šrafování, barva šrafované čáry a barva pozadí.</span><span class="sxs-lookup"><span data-stu-id="82aac-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="82aac-108">Argument stylu šrafování může být libovolná hodnota z výčtu <xref:System.Drawing.Drawing2D.HatchStyle>.</span><span class="sxs-lookup"><span data-stu-id="82aac-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="82aac-109">Výčet <xref:System.Drawing.Drawing2D.HatchStyle> obsahuje více než 50 prvků; v následujícím seznamu jsou uvedeny některé z těchto prvků:</span><span class="sxs-lookup"><span data-stu-id="82aac-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="82aac-110">Následující ilustrace znázorňuje Vyplněnou elipsu.</span><span class="sxs-lookup"><span data-stu-id="82aac-110">The following illustration shows the filled ellipse.</span></span>  
  
  <span data-ttu-id="82aac-111">![Snímek obrazovky toho, jak elipsa vyplněná vzorem šrafování vypadá jako.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="82aac-111">![Screenshot of what an ellipse filled with a hatch pattern looks like.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")</span></span>
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="82aac-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="82aac-112">Compiling the Code</span></span>  
 <span data-ttu-id="82aac-113">Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs>`e`, což je parametr obslužné rutiny události <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="82aac-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82aac-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82aac-114">See also</span></span>

- [<span data-ttu-id="82aac-115">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="82aac-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
