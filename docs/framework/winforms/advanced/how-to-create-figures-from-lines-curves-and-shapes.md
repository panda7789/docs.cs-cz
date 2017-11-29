---
title: "Postupy: Vytváření obrázků z čar, křivek a obrazců"
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
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b382e0e1a627d7f61ce8ac664ac47d98c3725cad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a><span data-ttu-id="ca7fb-102">Postupy: Vytváření obrázků z čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="ca7fb-102">How to: Create Figures from Lines, Curves, and Shapes</span></span>
<span data-ttu-id="ca7fb-103">Pokud chcete vytvořit obrázek, vytvořit <xref:System.Drawing.Drawing2D.GraphicsPath>a pak volat metody, jako například <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> a <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, přidejte cestu primitiv.</span><span class="sxs-lookup"><span data-stu-id="ca7fb-103">To create a figure, construct a <xref:System.Drawing.Drawing2D.GraphicsPath>, and then call methods, such as <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, to add primitives to the path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca7fb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca7fb-104">Example</span></span>  
 <span data-ttu-id="ca7fb-105">Následující příklady kódu vytvořit cesty, které mají následující obrázky:</span><span class="sxs-lookup"><span data-stu-id="ca7fb-105">The following code examples create paths that have figures:</span></span>  
  
-   <span data-ttu-id="ca7fb-106">V prvním příkladu vytvoří cestu, která má jeden obrázek.</span><span class="sxs-lookup"><span data-stu-id="ca7fb-106">The first example creates a path that has a single figure.</span></span> <span data-ttu-id="ca7fb-107">Obrázek se skládá z jedné oblouk. Oblouk má úhel oblouku – 180 stupňů, který je ve výchozím nastavení souřadnicový systém proti směru hodinových ručiček.</span><span class="sxs-lookup"><span data-stu-id="ca7fb-107">The figure consists of a single arc. The arc has a sweep angle of –180 degrees, which is counterclockwise in the default coordinate system.</span></span>  
  
-   <span data-ttu-id="ca7fb-108">V druhém příkladu vytvoří cestu, která má dva následující obrázky.</span><span class="sxs-lookup"><span data-stu-id="ca7fb-108">The second example creates a path that has two figures.</span></span> <span data-ttu-id="ca7fb-109">První obrázek je oblouk následuje řádek.</span><span class="sxs-lookup"><span data-stu-id="ca7fb-109">The first figure is an arc followed by a line.</span></span> <span data-ttu-id="ca7fb-110">Druhý obrázek je řádek následovaný křivka následuje řádek.</span><span class="sxs-lookup"><span data-stu-id="ca7fb-110">The second figure is a line followed by a curve followed by a line.</span></span> <span data-ttu-id="ca7fb-111">První obrázek je ponechány otevřené a druhý obrázek je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="ca7fb-111">The first figure is left open, and the second figure is closed.</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca7fb-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ca7fb-112">Compiling the Code</span></span>  
 <span data-ttu-id="ca7fb-113">V předchozích příkladech jsou navrženy pro používání s formuláři Windows a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ca7fb-113">The previous examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7fb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca7fb-114">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="ca7fb-115">Sestavování a kreslení cest</span><span class="sxs-lookup"><span data-stu-id="ca7fb-115">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 [<span data-ttu-id="ca7fb-116">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="ca7fb-116">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
