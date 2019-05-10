---
title: 'Postupy: Vytvoření lineárního přechodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: 953a1944073a8cb5b19ef072e2a523baec3a5605
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650007"
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="e05d2-102">Postupy: Vytvoření lineárního přechodu</span><span class="sxs-lookup"><span data-stu-id="e05d2-102">How to: Create a Linear Gradient</span></span>
<span data-ttu-id="e05d2-103">Rozhraní GDI + poskytuje vodorovné, svislé a diagonální lineárními přechody.</span><span class="sxs-lookup"><span data-stu-id="e05d2-103">GDI+ provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="e05d2-104">Ve výchozím nastavení změní barvu v lineárním přechodem jednotně.</span><span class="sxs-lookup"><span data-stu-id="e05d2-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="e05d2-105">Lineární přechod však můžete přizpůsobit tak, aby se barva mění, nerovnoměrné způsobem.</span><span class="sxs-lookup"><span data-stu-id="e05d2-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  

> [!NOTE]
> <span data-ttu-id="e05d2-106">V příkladech v tomto článku jsou metody, které se volají z ovládacího prvku <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e05d2-106">The examples in this article are methods that are called from a control's <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  

<span data-ttu-id="e05d2-107">Následující příklad zkopíruje řádku elipsu a obdélníku s vodorovné štětec lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="e05d2-107">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
<span data-ttu-id="e05d2-108"><xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Konstruktoru přijímá čtyři argumenty: dva body a dvěma barvami.</span><span class="sxs-lookup"><span data-stu-id="e05d2-108">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="e05d2-109">První bod (0, 10) souvisí s první barvy (červená), a druhý bod (200, 10) souvisí s druhou barvou (modrá).</span><span class="sxs-lookup"><span data-stu-id="e05d2-109">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="e05d2-110">Dle očekávání, řádku z (0, 10) na (200, 10) změní z red blue postupně.</span><span class="sxs-lookup"><span data-stu-id="e05d2-110">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="e05d2-111">10s v bodech (0, 10) a (200, 10) nejsou důležité.</span><span class="sxs-lookup"><span data-stu-id="e05d2-111">The 10s in the points (0, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="e05d2-112">Důležité je, že dva body mají stejné souřadnice druhý – řádek je propojí je vodorovný.</span><span class="sxs-lookup"><span data-stu-id="e05d2-112">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="e05d2-113">Elipsy a obdélníku také změnit postupně z red blue jako bod se souřadnicemi vodorovné přejde od 0 do 200.</span><span class="sxs-lookup"><span data-stu-id="e05d2-113">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="e05d2-114">Následující obrázek znázorňuje řádku, na tři tečky a obdélníku.</span><span class="sxs-lookup"><span data-stu-id="e05d2-114">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="e05d2-115">Všimněte si, že barva přechodu opakuje jako bod se souřadnicemi vodorovné zvýší nad 200.</span><span class="sxs-lookup"><span data-stu-id="e05d2-115">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 <span data-ttu-id="e05d2-116">![Linear Gradient](./media/cslineargradient1.png "cslineargradient1")</span><span class="sxs-lookup"><span data-stu-id="e05d2-116">![Linear Gradient](./media/cslineargradient1.png "cslineargradient1")</span></span>  
  
### <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="e05d2-117">Určený horizontální lineárními přechody</span><span class="sxs-lookup"><span data-stu-id="e05d2-117">To use horizontal linear gradients</span></span>  
  
- <span data-ttu-id="e05d2-118">Předejte modře neprůhledné červené a neprůhledné jako třetí a čtvrtý argument, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e05d2-118">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="e05d2-119">V předchozím příkladu složky barvy změnit lineárně při přesunu z vodorovné souřadnice 0 vodorovné souřadnice 200.</span><span class="sxs-lookup"><span data-stu-id="e05d2-119">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="e05d2-120">Bod, jehož první souřadnice je uprostřed mezi 0 a 200 bude mít například komponentu modrý uprostřed mezi 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="e05d2-120">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 <span data-ttu-id="e05d2-121">Rozhraní GDI + umožňuje upravit způsob, jakým barvu se liší od jednomu z okrajů přechod na druhý.</span><span class="sxs-lookup"><span data-stu-id="e05d2-121">GDI+ allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="e05d2-122">Předpokládejme, že chcete vytvořit štětce přechodu od černé se změní na červený podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="e05d2-122">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="e05d2-123">Vodorovné souřadnice</span><span class="sxs-lookup"><span data-stu-id="e05d2-123">Horizontal coordinate</span></span>|<span data-ttu-id="e05d2-124">Součásti RGB</span><span class="sxs-lookup"><span data-stu-id="e05d2-124">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="e05d2-125">0</span><span class="sxs-lookup"><span data-stu-id="e05d2-125">0</span></span>|<span data-ttu-id="e05d2-126">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="e05d2-126">(0, 0, 0)</span></span>|  
|<span data-ttu-id="e05d2-127">40</span><span class="sxs-lookup"><span data-stu-id="e05d2-127">40</span></span>|<span data-ttu-id="e05d2-128">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="e05d2-128">(128, 0, 0)</span></span>|  
|<span data-ttu-id="e05d2-129">200</span><span class="sxs-lookup"><span data-stu-id="e05d2-129">200</span></span>|<span data-ttu-id="e05d2-130">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="e05d2-130">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="e05d2-131">Upozorňujeme, že červené poloviční intenzitou při vodorovné bod se souřadnicemi je pouze 20 procent způsob od 0 do 200.</span><span class="sxs-lookup"><span data-stu-id="e05d2-131">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="e05d2-132">Následující příklad nastaví <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> vlastnost pro přidružení k tři relativní pozice tři relativní míry.</span><span class="sxs-lookup"><span data-stu-id="e05d2-132">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> property to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="e05d2-133">Stejně jako v předchozí tabulce je přidružen k relativní pozice 0.2 relativní intenzita 0,5.</span><span class="sxs-lookup"><span data-stu-id="e05d2-133">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="e05d2-134">Kód vyplní elipsu a obdélníku s štětce přechodu.</span><span class="sxs-lookup"><span data-stu-id="e05d2-134">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="e05d2-135">Následující obrázek znázorňuje výsledný tři tečky a obdélník.</span><span class="sxs-lookup"><span data-stu-id="e05d2-135">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 <span data-ttu-id="e05d2-136">![Linear Gradient](./media/cslineargradient2.png "cslineargradient2")</span><span class="sxs-lookup"><span data-stu-id="e05d2-136">![Linear Gradient](./media/cslineargradient2.png "cslineargradient2")</span></span>  

### <a name="to-customize-linear-gradients"></a><span data-ttu-id="e05d2-137">Chcete-li přizpůsobit lineárními přechody</span><span class="sxs-lookup"><span data-stu-id="e05d2-137">To customize linear gradients</span></span>  
  
- <span data-ttu-id="e05d2-138">Předejte červeně neprůhledný černý a neprůhledné jako třetí a čtvrtý argument, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e05d2-138">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="e05d2-139">Přechody v předchozích příkladech byly vodorovné; To znamená barva se změní postupně při přesunu podél jakékoli vodorovnou čáru.</span><span class="sxs-lookup"><span data-stu-id="e05d2-139">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="e05d2-140">Můžete také definovat svislé barevné přechody a Úhlopříčný přechody.</span><span class="sxs-lookup"><span data-stu-id="e05d2-140">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="e05d2-141">Následující příklad předá body (0, 0) a (200, 100) <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e05d2-141">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="e05d2-142">Modrá barva je přidružené k (0, 0), a je asociována zelenou barvu (200, 100).</span><span class="sxs-lookup"><span data-stu-id="e05d2-142">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="e05d2-143">Řádek (s 10 Šířka pera) a elipsa jsou vyplněny hodnotou štětec lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="e05d2-143">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="e05d2-144">Následující obrázek znázorňuje řádku a na tři tečky.</span><span class="sxs-lookup"><span data-stu-id="e05d2-144">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="e05d2-145">Všimněte si, že barvu v elipsa změny postupně při přesunu podél žádný řádek, který je paralelní řádku procházející (0, 0) a (200, 100).</span><span class="sxs-lookup"><span data-stu-id="e05d2-145">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 <span data-ttu-id="e05d2-146">![Linear Gradient](./media/cslineargradient3.png "cslineargradient3")</span><span class="sxs-lookup"><span data-stu-id="e05d2-146">![Linear Gradient](./media/cslineargradient3.png "cslineargradient3")</span></span>  
  
### <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="e05d2-147">Chcete-li vytvořit Úhlopříčný lineárními přechody</span><span class="sxs-lookup"><span data-stu-id="e05d2-147">To create diagonal linear gradients</span></span>  
  
- <span data-ttu-id="e05d2-148">Předejte zeleně neprůhledné modré a neprůhledné jako třetí a čtvrtý argument, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e05d2-148">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="e05d2-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e05d2-149">See also</span></span>

- [<span data-ttu-id="e05d2-150">Použití štětce přechodu k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="e05d2-150">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
- [<span data-ttu-id="e05d2-151">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e05d2-151">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
