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
ms.openlocfilehash: a0d4d92d7201c4ac09eadd11d8f2e38a3c80c287
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713130"
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="ab5a0-102">Postupy: Kreslení čáry s ukončením</span><span class="sxs-lookup"><span data-stu-id="ab5a0-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="ab5a0-103">V jednom z několika obrazců volá ukončením lze nakreslit začátek nebo konec řádku.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="ab5a0-104">podporuje několik ukončením, jako je kruhové, čtverec, kosočtverce a šipky.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-104">supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab5a0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab5a0-105">Example</span></span>  
 <span data-ttu-id="ab5a0-106">Můžete zadat čar na začátku řádku (start cap), konci řádku (zakončení) nebo pomlčky na přerušovanou čáru (dash cap).</span><span class="sxs-lookup"><span data-stu-id="ab5a0-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="ab5a0-107">V následujícím příkladu kreslení čáry s šipkou na jednom konci a kruhové zakončení na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="ab5a0-108">Na obrázku vidíte výsledný řádek:</span><span class="sxs-lookup"><span data-stu-id="ab5a0-108">The illustration shows the resulting line:</span></span>  
  
 <span data-ttu-id="ab5a0-109">![Pera](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span><span class="sxs-lookup"><span data-stu-id="ab5a0-109">![Pens](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ab5a0-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ab5a0-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ab5a0-111">Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="ab5a0-112">Vložit příklad kódu do <xref:System.Windows.Forms.Control.Paint> obslužná rutina události předávání `e` jako <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5a0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab5a0-113">See also</span></span>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [<span data-ttu-id="ab5a0-114">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab5a0-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="ab5a0-115">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="ab5a0-115">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
