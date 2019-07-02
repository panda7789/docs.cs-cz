---
title: 'Postupy: Propojení čar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 362ce0c701d6e5f640fecd143a60cf471045629c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505863"
---
# <a name="how-to-join-lines"></a><span data-ttu-id="8062c-102">Postupy: Propojení čar</span><span class="sxs-lookup"><span data-stu-id="8062c-102">How to: Join Lines</span></span>
<span data-ttu-id="8062c-103">Spojení čar je běžné oblasti, která je tvořen dvěma řádky, jejichž končí splňovat nebo překrývat.</span><span class="sxs-lookup"><span data-stu-id="8062c-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> <span data-ttu-id="8062c-104">Rozhraní GDI + poskytuje tři styly čar spojení: ostrý zkosení a zaokrouhlit.</span><span class="sxs-lookup"><span data-stu-id="8062c-104">GDI+ provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="8062c-105">Čára – styl propojení je vlastnost <xref:System.Drawing.Pen> třídy.</span><span class="sxs-lookup"><span data-stu-id="8062c-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="8062c-106">Při zadání styl spojení řádku <xref:System.Drawing.Pen> objektu, styl, se použijí pro všechny spojené čáry v libovolném <xref:System.Drawing.Drawing2D.GraphicsPath> objekt vykreslen pomocí pera.</span><span class="sxs-lookup"><span data-stu-id="8062c-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="8062c-107">Následující obrázek znázorňuje výsledky v příkladu spojení zkosený řádku.</span><span class="sxs-lookup"><span data-stu-id="8062c-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 ![Obrázek, na kterém připojené k doméně řádky.](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a><span data-ttu-id="8062c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8062c-109">Example</span></span>  
 <span data-ttu-id="8062c-110">Můžete zadat čára – styl propojení s použitím <xref:System.Drawing.Pen.LineJoin%2A> vlastnost <xref:System.Drawing.Pen> třídy.</span><span class="sxs-lookup"><span data-stu-id="8062c-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="8062c-111">Příklad demonstruje zkosený řádku spojení řádku vodorovné a svislé čáry.</span><span class="sxs-lookup"><span data-stu-id="8062c-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="8062c-112">V následujícím kódu, hodnota <xref:System.Drawing.Drawing2D.LineJoin.Bevel> přiřazené <xref:System.Drawing.Pen.LineJoin%2A> vlastnost je členem skupiny <xref:System.Drawing.Drawing2D.LineJoin> výčtu.</span><span class="sxs-lookup"><span data-stu-id="8062c-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="8062c-113">Ostatní členové <xref:System.Drawing.Drawing2D.LineJoin> výčtu jsou <xref:System.Drawing.Drawing2D.LineJoin.Miter> a <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="8062c-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8062c-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8062c-114">Compiling the Code</span></span>  
 <span data-ttu-id="8062c-115">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8062c-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8062c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8062c-116">See also</span></span>

- [<span data-ttu-id="8062c-117">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="8062c-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
