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
ms.openlocfilehash: f5399c4151b335090f4b93be041375b8c2781afa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118115"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="58afc-102">Postupy: Vyplnění obrazce pomocí nesouvislého vzoru</span><span class="sxs-lookup"><span data-stu-id="58afc-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="58afc-103">Nesouvislého vzoru se provádí stínováním dvěma barvami: jeden pro na pozadí a jeden pro řádky, které tvoří vzor přes na pozadí.</span><span class="sxs-lookup"><span data-stu-id="58afc-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="58afc-104">Chcete-li vyplnění uzavřené obrazce pomocí nesouvislého vzoru, použijte <xref:System.Drawing.Drawing2D.HatchBrush> objektu.</span><span class="sxs-lookup"><span data-stu-id="58afc-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="58afc-105">Následující příklad ukazuje, jak vyplnit elipsu pomocí nesouvislého vzoru:</span><span class="sxs-lookup"><span data-stu-id="58afc-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="58afc-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="58afc-106">Example</span></span>  
 <span data-ttu-id="58afc-107"><xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Konstruktor má tři argumenty: Styl šrafování, barva šrafování čáry a barvu pozadí.</span><span class="sxs-lookup"><span data-stu-id="58afc-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="58afc-108">Styl šrafování argument může být libovolná hodnota od <xref:System.Drawing.Drawing2D.HatchStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="58afc-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="58afc-109">Existuje více než 50 elementů v <xref:System.Drawing.Drawing2D.HatchStyle> výčet; některé z těchto elementů jsou uvedeny v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="58afc-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="58afc-110">Následující obrázek znázorňuje vyplněnou elipsu.</span><span class="sxs-lookup"><span data-stu-id="58afc-110">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="58afc-111">![Šrafovaných vzor](./media/hatch1.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="58afc-111">![Hatch Pattern](./media/hatch1.png "hatch1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="58afc-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="58afc-112">Compiling the Code</span></span>  
 <span data-ttu-id="58afc-113">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="58afc-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58afc-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58afc-114">See also</span></span>

- [<span data-ttu-id="58afc-115">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="58afc-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
