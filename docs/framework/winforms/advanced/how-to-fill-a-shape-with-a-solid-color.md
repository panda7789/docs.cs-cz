---
title: 'Postupy: Vyplnění obrazce plnou barvou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: 576042d9d8e7a7f77d5375b7dfafafdc63b3e824
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601958"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="7820b-102">Postupy: Vyplnění obrazce plnou barvou</span><span class="sxs-lookup"><span data-stu-id="7820b-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="7820b-103">K vyplnění obrazce plnou barvou, vytvořit <xref:System.Drawing.SolidBrush> objektu a pak předejte, který <xref:System.Drawing.SolidBrush> objektu jako argument pro jednu z metod výplň <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="7820b-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="7820b-104">Následující příklad ukazuje, jak vyplnit elipsu s červenou barvu.</span><span class="sxs-lookup"><span data-stu-id="7820b-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7820b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7820b-105">Example</span></span>  
 <span data-ttu-id="7820b-106">V následujícím kódu <xref:System.Drawing.SolidBrush.%23ctor%2A> přebírá konstruktor <xref:System.Drawing.Color> objektu jako svůj jediný argument.</span><span class="sxs-lookup"><span data-stu-id="7820b-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="7820b-107">Hodnot použitých <xref:System.Drawing.Color.FromArgb%2A> metoda představují alfa, červené, zelené a modré součásti barvy.</span><span class="sxs-lookup"><span data-stu-id="7820b-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="7820b-108">Všechny tyto hodnoty musí být v rozsahu 0 až 255.</span><span class="sxs-lookup"><span data-stu-id="7820b-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="7820b-109">První 255 znamená, že se barva úplně neprůhledná a druhý 255 znamená, že je hodnota červené na plné intenzity.</span><span class="sxs-lookup"><span data-stu-id="7820b-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="7820b-110">Dvě nuly znamená, že součásti zelené a modré mít intenzitu zrcadlových 0.</span><span class="sxs-lookup"><span data-stu-id="7820b-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="7820b-111">Předány čtyři číslice (0, 0, 100, 60) <xref:System.Drawing.Graphics.FillEllipse%2A> metody zadejte umístění a velikost ohraničující obdélník elipsy.</span><span class="sxs-lookup"><span data-stu-id="7820b-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="7820b-112">Obdélník má levého horního rohu (0, 0), 100 šířku a výšku 60.</span><span class="sxs-lookup"><span data-stu-id="7820b-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7820b-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7820b-113">Compiling the Code</span></span>  
 <span data-ttu-id="7820b-114">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7820b-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7820b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7820b-115">See also</span></span>
- [<span data-ttu-id="7820b-116">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="7820b-116">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
