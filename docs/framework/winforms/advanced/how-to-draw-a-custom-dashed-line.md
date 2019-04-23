---
title: 'Postupy: Kreslení vlastní přerušované čáry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 8dc1ad41cf8067bea5b811ca126ad29f5a600f69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109184"
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="2d286-102">Postupy: Kreslení vlastní přerušované čáry</span><span class="sxs-lookup"><span data-stu-id="2d286-102">How to: Draw a Custom Dashed Line</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2d286-103">poskytuje několik styly čar, které jsou uvedeny v <xref:System.Drawing.Drawing2D.DashStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="2d286-103">provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="2d286-104">Pokud tyto styly standardní dash nevyhovují vašim potřebám, můžete vytvořit vlastní dash vzor.</span><span class="sxs-lookup"><span data-stu-id="2d286-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d286-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d286-105">Example</span></span>  
 <span data-ttu-id="2d286-106">Kreslení vlastní přerušované čáry, umístěte délek pomlčky a mezery v poli a přiřaďte pole jako hodnotu <xref:System.Drawing.Pen.DashPattern%2A> vlastnost <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="2d286-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="2d286-107">Následující příklad kreslení vlastní přerušované čáry podle pole `{5, 2, 15, 4}`.</span><span class="sxs-lookup"><span data-stu-id="2d286-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="2d286-108">Pokud je šířka pera 5 vynásobit prvky pole, můžete získat `{25, 10, 75, 20}`.</span><span class="sxs-lookup"><span data-stu-id="2d286-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="2d286-109">Alternativní zobrazené pomlčky v délce 25 a 75 a mezery alternativní délku 10 až 20.</span><span class="sxs-lookup"><span data-stu-id="2d286-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="2d286-110">Následující obrázek znázorňuje výsledný přerušované čáry.</span><span class="sxs-lookup"><span data-stu-id="2d286-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="2d286-111">Všimněte si, že poslední dash musí být kratší než 25 jednotky tak, aby můžete konec řádku (405, 5).</span><span class="sxs-lookup"><span data-stu-id="2d286-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="2d286-112">![Obrázek, který ukazuje na přerušovanou čáru. ](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="2d286-112">![Illustration that shows a dashed line.](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d286-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2d286-113">Compiling the Code</span></span>  
 <span data-ttu-id="2d286-114">Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="2d286-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="2d286-115">Předchozí kód vložte do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="2d286-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d286-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d286-116">See also</span></span>

- [<span data-ttu-id="2d286-117">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="2d286-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
