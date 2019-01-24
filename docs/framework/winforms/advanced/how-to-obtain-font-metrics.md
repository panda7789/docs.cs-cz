---
title: 'Postupy: Získání metriky písma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 5e37725363640bd02fc3e0f62f66d21151b497fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657256"
---
# <a name="how-to-obtain-font-metrics"></a><span data-ttu-id="85379-102">Postupy: Získání metriky písma</span><span class="sxs-lookup"><span data-stu-id="85379-102">How to: Obtain Font Metrics</span></span>
<span data-ttu-id="85379-103"><xref:System.Drawing.FontFamily> Třída poskytuje následující metody, které načítají různé metriky pro konkrétní řady a styl kombinace:</span><span class="sxs-lookup"><span data-stu-id="85379-103">The <xref:System.Drawing.FontFamily> class provides the following methods that retrieve various metrics for a particular family/style combination:</span></span>  
  
-   <span data-ttu-id="85379-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="85379-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="85379-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="85379-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="85379-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="85379-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="85379-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="85379-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span></span>  
  
 <span data-ttu-id="85379-108">Hodnoty vrácené z těchto metod jsou v písma návrhu jednotek, takže se platí bez ohledu na velikost a jednotek určitého <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="85379-108">The numbers returned by these methods are in font design units, so they are independent of the size and units of a particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="85379-109">Následující obrázek znázorňuje různé metriky.</span><span class="sxs-lookup"><span data-stu-id="85379-109">The following illustration shows the various metrics.</span></span>  
  
 <span data-ttu-id="85379-110">![Písma textu](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span><span class="sxs-lookup"><span data-stu-id="85379-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span></span>  
  
## <a name="example"></a><span data-ttu-id="85379-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="85379-111">Example</span></span>  
 <span data-ttu-id="85379-112">Následující příklad zobrazuje metriky pro pravidelné styl řady Arial písmo.</span><span class="sxs-lookup"><span data-stu-id="85379-112">The following example displays the metrics for the regular style of the Arial font family.</span></span> <span data-ttu-id="85379-113">Kód vytvoří také <xref:System.Drawing.Font> objektu (podle Arial řady) s velikost 16 pixelů a zobrazení metrik (v pixelech) o tomto konkrétním <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="85379-113">The code also creates a <xref:System.Drawing.Font> object (based on the Arial family) with size 16 pixels and displays the metrics (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="85379-114">Následující obrázek znázorňuje výstup tohoto ukázkového kódu.</span><span class="sxs-lookup"><span data-stu-id="85379-114">The following illustration shows the output of the example code.</span></span>  
  
 <span data-ttu-id="85379-115">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span><span class="sxs-lookup"><span data-stu-id="85379-115">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span></span>  
  
 <span data-ttu-id="85379-116">Poznámka: první dva řádky výstupního předchozím obrázku.</span><span class="sxs-lookup"><span data-stu-id="85379-116">Note the first two lines of output in the preceding illustration.</span></span> <span data-ttu-id="85379-117"><xref:System.Drawing.Font> o velikosti 16, vrátí objekt a <xref:System.Drawing.FontFamily> objekt vrátí výšku em 2 048.</span><span class="sxs-lookup"><span data-stu-id="85379-117">The <xref:System.Drawing.Font> object returns a size of 16, and the <xref:System.Drawing.FontFamily> object returns an em height of 2,048.</span></span> <span data-ttu-id="85379-118">Tyto dvě čísla (16 a 2 048) jsou klíčem k převodu mezi písma návrhu jednotky a jednotek (v tomto případu pixelů) <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="85379-118">These two numbers (16 and 2,048) are the key to converting between font design units and the units (in this case pixels) of the <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="85379-119">Například můžete převedete ascent z návrhu jednotek na pixelech následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="85379-119">For example, you can convert the ascent from design units to pixels as follows:</span></span>  
  
 <span data-ttu-id="85379-120">![Písma textu](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span><span class="sxs-lookup"><span data-stu-id="85379-120">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span></span>  
  
 <span data-ttu-id="85379-121">Následující kód umístí text svisle tak, že nastavíte <xref:System.Drawing.PointF.Y%2A> datový člen třídy <xref:System.Drawing.PointF> objektu.</span><span class="sxs-lookup"><span data-stu-id="85379-121">The following code positions text vertically by setting the <xref:System.Drawing.PointF.Y%2A> data member of a <xref:System.Drawing.PointF> object.</span></span> <span data-ttu-id="85379-122">Souřadnice y prodloužen o `font.Height` pro každého nového řádku textu.</span><span class="sxs-lookup"><span data-stu-id="85379-122">The y-coordinate is increased by `font.Height` for each new line of text.</span></span> <span data-ttu-id="85379-123"><xref:System.Drawing.Font.Height%2A> Vlastnost <xref:System.Drawing.Font> objekt vrátí řádkování (v pixelech) o tomto konkrétním <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="85379-123">The <xref:System.Drawing.Font.Height%2A> property of a <xref:System.Drawing.Font> object returns the line spacing (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="85379-124">V tomto příkladu číslo vrácen podle <xref:System.Drawing.Font.Height%2A> je 19.</span><span class="sxs-lookup"><span data-stu-id="85379-124">In this example, the number returned by <xref:System.Drawing.Font.Height%2A> is 19.</span></span> <span data-ttu-id="85379-125">Všimněte si, že toto je stejné jako číslo (zaokrouhleno na celé číslo) získala při převodu řádkování metrika na pixelech.</span><span class="sxs-lookup"><span data-stu-id="85379-125">Note that this is the same as the number (rounded up to an integer) obtained by converting the line-spacing metric to pixels.</span></span>  
  
 <span data-ttu-id="85379-126">Všimněte si, že výška em (také nazývané velikost nebo em velikost) není součet ascent a sestup.</span><span class="sxs-lookup"><span data-stu-id="85379-126">Note that the em height (also called size or em size) is not the sum of the ascent and the descent.</span></span> <span data-ttu-id="85379-127">Součet hodnot ascent a sestup se nazývá výška buňky.</span><span class="sxs-lookup"><span data-stu-id="85379-127">The sum of the ascent and the descent is called the cell height.</span></span> <span data-ttu-id="85379-128">Výška buňky minus interní úvodního rovná Výška em.</span><span class="sxs-lookup"><span data-stu-id="85379-128">The cell height minus the internal leading is equal to the em height.</span></span> <span data-ttu-id="85379-129">Výška buňky a externí úvodního rovná řádkování.</span><span class="sxs-lookup"><span data-stu-id="85379-129">The cell height plus the external leading is equal to the line spacing.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85379-130">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="85379-130">Compiling the Code</span></span>  
 <span data-ttu-id="85379-131">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="85379-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85379-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85379-132">See also</span></span>
- [<span data-ttu-id="85379-133">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85379-133">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="85379-134">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="85379-134">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
