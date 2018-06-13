---
title: 'Postupy: Kreslení čáry s ukončením'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: be492f2317d4677776cc9f89f546c935d271019b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523218"
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="ace0f-102">Postupy: Kreslení čáry s ukončením</span><span class="sxs-lookup"><span data-stu-id="ace0f-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="ace0f-103">V jednom z několika obrazců názvem čar můžete nakreslit počáteční nebo konec řádku.</span><span class="sxs-lookup"><span data-stu-id="ace0f-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ace0f-104"> podporuje několik čar, například zaokrouhlit, hranaté, kosočtverec a šipku.</span><span class="sxs-lookup"><span data-stu-id="ace0f-104"> supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ace0f-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ace0f-105">Example</span></span>  
 <span data-ttu-id="ace0f-106">Můžete zadat čar na začátku řádku (počáteční cap), konci řádku (zakončení) nebo pomlček na přerušovanou čáru (dash cap).</span><span class="sxs-lookup"><span data-stu-id="ace0f-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="ace0f-107">Následující příklad kreslení čáry s šipkou na jednom konci a zaokrouhlí zakončení na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="ace0f-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="ace0f-108">Na obrázku vidíte výsledný řádek:</span><span class="sxs-lookup"><span data-stu-id="ace0f-108">The illustration shows the resulting line:</span></span>  
  
 <span data-ttu-id="ace0f-109">![Pera](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span><span class="sxs-lookup"><span data-stu-id="ace0f-109">![Pens](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ace0f-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ace0f-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ace0f-111">Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="ace0f-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="ace0f-112">Vložit příklad kódu do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události předávání `e` jako <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="ace0f-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace0f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ace0f-113">See Also</span></span>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [<span data-ttu-id="ace0f-114">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ace0f-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="ace0f-115">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="ace0f-115">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
