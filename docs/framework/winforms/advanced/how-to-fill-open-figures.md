---
title: 'Postupy: Vyplňování otevřených obrázků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: addcf959e429974b9306353abb743bb2bb3114e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781428"
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="e49df-102">Postupy: Vyplňování otevřených obrázků</span><span class="sxs-lookup"><span data-stu-id="e49df-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="e49df-103">Můžete přejít k vyplnění cestu předáním <xref:System.Drawing.Drawing2D.GraphicsPath> objektu <xref:System.Drawing.Graphics.FillPath%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e49df-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="e49df-104"><xref:System.Drawing.Graphics.FillPath%2A> Metoda vyplní cestu podle režim vyplnění (alternativní nebo vinutí) aktuálně nastavený pro danou cestu.</span><span class="sxs-lookup"><span data-stu-id="e49df-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="e49df-105">Pokud cesta obsahuje všechny otevřených obrázků, cesta je vyplněné, jakoby nebyly uzavřeny tyto údaje.</span><span class="sxs-lookup"><span data-stu-id="e49df-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="e49df-106">Zavře elementu figure podle Kreslení rovné čáry z koncového bodu pro výchozí bod.</span><span class="sxs-lookup"><span data-stu-id="e49df-106">closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e49df-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e49df-107">Example</span></span>  
 <span data-ttu-id="e49df-108">Následující příklad vytvoří cestu, která má jeden otevřeného elementu figure (oblouku) a jednoho elementu figure uzavřený (Elipsa).</span><span class="sxs-lookup"><span data-stu-id="e49df-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="e49df-109"><xref:System.Drawing.Graphics.FillPath%2A> Metoda vyplní cestu podle výchozí režim výplně, což je <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="e49df-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="e49df-110">Následující obrázek znázorňuje výstup tohoto ukázkového kódu.</span><span class="sxs-lookup"><span data-stu-id="e49df-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="e49df-111">Všimněte si, že ji naplní (podle <xref:System.Drawing.Drawing2D.FillMode.Alternate>) jako kdyby bylo uzavřeno otevřený útvar rovnou linii od její koncový bod pro výchozí bod.</span><span class="sxs-lookup"><span data-stu-id="e49df-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 ![Diagram, který zobrazuje výstup FillPath – metoda](./media/how-to-fill-open-figures/fill-path-alternate-mode.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e49df-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e49df-113">Compiling the Code</span></span>  
 <span data-ttu-id="e49df-114">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e49df-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49df-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e49df-115">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="e49df-116">Grafické cesty v GDI+</span><span class="sxs-lookup"><span data-stu-id="e49df-116">Graphics Paths in GDI+</span></span>](graphics-paths-in-gdi.md)
