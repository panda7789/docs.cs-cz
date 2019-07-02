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
ms.openlocfilehash: d2184a8d7d7f24b8f631818608ab4bcdb89857c7
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506032"
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="5f956-102">Postupy: Kreslení vlastní přerušované čáry</span><span class="sxs-lookup"><span data-stu-id="5f956-102">How to: Draw a Custom Dashed Line</span></span>
<span data-ttu-id="5f956-103">Rozhraní GDI + poskytuje několik styly čar, které jsou uvedeny v <xref:System.Drawing.Drawing2D.DashStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="5f956-103">GDI+ provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="5f956-104">Pokud tyto styly standardní dash nevyhovují vašim potřebám, můžete vytvořit vlastní dash vzor.</span><span class="sxs-lookup"><span data-stu-id="5f956-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f956-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f956-105">Example</span></span>  
 <span data-ttu-id="5f956-106">Kreslení vlastní přerušované čáry, umístěte délek pomlčky a mezery v poli a přiřaďte pole jako hodnotu <xref:System.Drawing.Pen.DashPattern%2A> vlastnost <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="5f956-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="5f956-107">Následující příklad kreslení vlastní přerušované čáry podle pole `{5, 2, 15, 4}`.</span><span class="sxs-lookup"><span data-stu-id="5f956-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="5f956-108">Pokud je šířka pera 5 vynásobit prvky pole, můžete získat `{25, 10, 75, 20}`.</span><span class="sxs-lookup"><span data-stu-id="5f956-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="5f956-109">Alternativní zobrazené pomlčky v délce 25 a 75 a mezery alternativní délku 10 až 20.</span><span class="sxs-lookup"><span data-stu-id="5f956-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="5f956-110">Následující obrázek znázorňuje výsledný přerušované čáry.</span><span class="sxs-lookup"><span data-stu-id="5f956-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="5f956-111">Všimněte si, že poslední dash musí být kratší než 25 jednotky tak, aby můžete konec řádku (405, 5).</span><span class="sxs-lookup"><span data-stu-id="5f956-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="5f956-112">![Obrázek, který ukazuje na přerušovanou čáru. ](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="5f956-112">![Illustration that shows a dashed line.](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f956-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5f956-113">Compiling the Code</span></span>  
 <span data-ttu-id="5f956-114">Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="5f956-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="5f956-115">Předchozí kód vložte do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="5f956-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f956-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f956-116">See also</span></span>

- [<span data-ttu-id="5f956-117">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="5f956-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
