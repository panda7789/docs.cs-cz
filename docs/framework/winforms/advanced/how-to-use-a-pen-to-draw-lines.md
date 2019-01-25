---
title: 'Postupy: Kreslení čar pomocí pera'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: e24d02c2c6ab7537f968c013eb91838eb0bb812a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730929"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="3a238-102">Postupy: Kreslení čar pomocí pera</span><span class="sxs-lookup"><span data-stu-id="3a238-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="3a238-103">Kreslení čar, je nutné <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="3a238-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="3a238-104"><xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawLine%2A> metody a <xref:System.Drawing.Pen> ukládá funkce na řádku, jako je barva a šířka.</span><span class="sxs-lookup"><span data-stu-id="3a238-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a238-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a238-105">Example</span></span>  
 <span data-ttu-id="3a238-106">Následující příklad nakreslí čáru z (20, 10) na (300, 100).</span><span class="sxs-lookup"><span data-stu-id="3a238-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="3a238-107">První příkaz používá <xref:System.Drawing.Pen.%23ctor%2A> konstruktoru třídy pro vytváření černého pera.</span><span class="sxs-lookup"><span data-stu-id="3a238-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="3a238-108">Jeden argument předaný do <xref:System.Drawing.Pen.%23ctor%2A> je konstruktor <xref:System.Drawing.Color> objekt vytvořený pomocí <xref:System.Drawing.Color.FromArgb%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="3a238-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="3a238-109">Hodnoty použité k vytvoření <xref:System.Drawing.Color> objektu – (255, 0, 0, 0), odpovídají alfa, červené, zelené a modré součásti barvy.</span><span class="sxs-lookup"><span data-stu-id="3a238-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="3a238-110">Tyto hodnoty definují neprůhledné černé pera.</span><span class="sxs-lookup"><span data-stu-id="3a238-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3a238-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3a238-111">Compiling the Code</span></span>  
 <span data-ttu-id="3a238-112">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3a238-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a238-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a238-113">See also</span></span>
- <xref:System.Drawing.Pen>
- [<span data-ttu-id="3a238-114">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="3a238-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="3a238-115">Pera, čáry a obdélníky v GDI+</span><span class="sxs-lookup"><span data-stu-id="3a238-115">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
