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
ms.openlocfilehash: 9c3c9c5c63194b1dee8314a1ef96497a8b78b5ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520731"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="74444-102">Postupy: Použití gama korekce na přechod</span><span class="sxs-lookup"><span data-stu-id="74444-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="74444-103">Korekce gama pro lineární štětce přechodu můžete povolit tak stopy <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="74444-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="74444-104">Korekce gama můžete zakázat nastavením <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="74444-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="74444-105">Korekce gama ve výchozím nastavení vypnutá.</span><span class="sxs-lookup"><span data-stu-id="74444-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74444-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="74444-106">Example</span></span>  
 <span data-ttu-id="74444-107">Tento příklad vytvoří lineární štětce přechodu a použije tento stopy k zadání dvou tvaru.</span><span class="sxs-lookup"><span data-stu-id="74444-107">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="74444-108">První obdélníku, naplní bez korekce gama a druhý rámeček je vyplněn korekce gama.</span><span class="sxs-lookup"><span data-stu-id="74444-108">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="74444-109">Následující obrázek znázorňuje dvou vyplněný tvaru.</span><span class="sxs-lookup"><span data-stu-id="74444-109">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="74444-110">Horní obdélníku, která nemá korekce gama, zobrazí se tmavý uprostřed.</span><span class="sxs-lookup"><span data-stu-id="74444-110">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="74444-111">Dolní obdélníku, který má korekce gama, zdá má další uniform intenzitou.</span><span class="sxs-lookup"><span data-stu-id="74444-111">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 <span data-ttu-id="74444-112">![Přechodu](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span><span class="sxs-lookup"><span data-stu-id="74444-112">![Gradient](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74444-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="74444-113">Compiling the Code</span></span>  
 <span data-ttu-id="74444-114">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="74444-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74444-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="74444-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [<span data-ttu-id="74444-116">Použití štětce přechodu k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="74444-116">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
