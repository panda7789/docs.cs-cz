---
title: 'Postupy: Použití gama korekce na přechod'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: 7290b7901714e9b71bda3f85f930f5331b8fd4ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077326"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="8e3ef-102">Postupy: Použití gama korekce na přechod</span><span class="sxs-lookup"><span data-stu-id="8e3ef-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="8e3ef-103">Můžete povolit gama korekce na štětec lineárního přechodu nastavením stopy <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="8e3ef-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="8e3ef-104">Korekce gama lze zakázat nastavením <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="8e3ef-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="8e3ef-105">Korekce gama je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="8e3ef-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e3ef-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e3ef-106">Example</span></span>  
 <span data-ttu-id="8e3ef-107">Tento příklad vytvoří štětec lineárního přechodu a používá tento štětce k vyplnění dvou obdélníků.</span><span class="sxs-lookup"><span data-stu-id="8e3ef-107">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="8e3ef-108">První obdélníku je vyplněný bez gama korekce a druhý obdélníku je vyplněna gama korekce.</span><span class="sxs-lookup"><span data-stu-id="8e3ef-108">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="8e3ef-109">Následující obrázek znázorňuje dvě plného obdélníků.</span><span class="sxs-lookup"><span data-stu-id="8e3ef-109">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="8e3ef-110">Horní obdélník, který nemá gama korekce, zobrazí se tmavě uprostřed.</span><span class="sxs-lookup"><span data-stu-id="8e3ef-110">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="8e3ef-111">Zdá se, že dolní části obdélníku, jehož gama korekce mít další míra jednotné.</span><span class="sxs-lookup"><span data-stu-id="8e3ef-111">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 <span data-ttu-id="8e3ef-112">![Gradient](./media/gammagradient1.png "gammagradient1")</span><span class="sxs-lookup"><span data-stu-id="8e3ef-112">![Gradient](./media/gammagradient1.png "gammagradient1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e3ef-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8e3ef-113">Compiling the Code</span></span>  
 <span data-ttu-id="8e3ef-114">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8e3ef-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3ef-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e3ef-115">See also</span></span>

- <xref:System.Drawing.Drawing2D.LinearGradientBrush>
- [<span data-ttu-id="8e3ef-116">Použití štětce přechodu k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="8e3ef-116">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
