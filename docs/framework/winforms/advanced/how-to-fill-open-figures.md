---
title: "Postupy: Vyplňování otevřených obrázků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c020e5f7306e73ee97dff0b492b04b5a153059cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="fd406-102">Postupy: Vyplňování otevřených obrázků</span><span class="sxs-lookup"><span data-stu-id="fd406-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="fd406-103">Cestu můžete vyplnit předáním <xref:System.Drawing.Drawing2D.GraphicsPath> do objektu <xref:System.Drawing.Graphics.FillPath%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd406-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="fd406-104"><xref:System.Drawing.Graphics.FillPath%2A> Metoda doplní cestu podle režim vyplnění (alternativní nebo vinutí) nastaveno pro cestu.</span><span class="sxs-lookup"><span data-stu-id="fd406-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="fd406-105">Pokud cesta obsahuje všech otevřených obrázků, cesta vyplněno jako v případě, že tyto údaje nebyly zavřeny.</span><span class="sxs-lookup"><span data-stu-id="fd406-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="fd406-106">Zavře obrázek podle kreslení přímku z koncového bodu pro výchozí bod.</span><span class="sxs-lookup"><span data-stu-id="fd406-106"> closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd406-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd406-107">Example</span></span>  
 <span data-ttu-id="fd406-108">Následující příklad vytvoří cestu, která má jeden otevřený útvar (oblouk) a jeden uzavřený útvar (elipsy).</span><span class="sxs-lookup"><span data-stu-id="fd406-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="fd406-109"><xref:System.Drawing.Graphics.FillPath%2A> Metoda doplní cestu podle režim vyplnění výchozí, což je <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="fd406-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="fd406-110">Následující obrázek znázorňuje výstup ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="fd406-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="fd406-111">Všimněte si, že cesta je plná (podle <xref:System.Drawing.Drawing2D.FillMode.Alternate>) jako kdyby byly otevřený útvar uzavřené přímku z koncového bodu pro výchozí bod.</span><span class="sxs-lookup"><span data-stu-id="fd406-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 <span data-ttu-id="fd406-112">![Vyplnění otevřené cesty](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span><span class="sxs-lookup"><span data-stu-id="fd406-112">![Fill Open Path](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd406-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fd406-113">Compiling the Code</span></span>  
 <span data-ttu-id="fd406-114">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="fd406-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd406-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd406-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="fd406-116">Grafické cesty v GDI+</span><span class="sxs-lookup"><span data-stu-id="fd406-116">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
