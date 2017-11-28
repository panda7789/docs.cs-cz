---
title: "Postupy: Získání metriky písma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b45f3f903c02d056fc457b652b01fb7b59413a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-font-metrics"></a><span data-ttu-id="a6146-102">Postupy: Získání metriky písma</span><span class="sxs-lookup"><span data-stu-id="a6146-102">How to: Obtain Font Metrics</span></span>
<span data-ttu-id="a6146-103"><xref:System.Drawing.FontFamily> Třída poskytuje následující metody, které načíst různé metriky pro konkrétní rodiny/styl kombinace:</span><span class="sxs-lookup"><span data-stu-id="a6146-103">The <xref:System.Drawing.FontFamily> class provides the following methods that retrieve various metrics for a particular family/style combination:</span></span>  
  
-   <span data-ttu-id="a6146-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="a6146-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="a6146-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="a6146-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="a6146-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="a6146-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="a6146-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="a6146-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span></span>  
  
 <span data-ttu-id="a6146-108">Hodnoty vrácené tyto metody jsou v jednotkách návrhu písma, proto jsou nezávislé na velikost a jednotky konkrétní <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="a6146-108">The numbers returned by these methods are in font design units, so they are independent of the size and units of a particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="a6146-109">Následující obrázek ukazuje různé metriky.</span><span class="sxs-lookup"><span data-stu-id="a6146-109">The following illustration shows the various metrics.</span></span>  
  
 <span data-ttu-id="a6146-110">![Text písem](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span><span class="sxs-lookup"><span data-stu-id="a6146-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6146-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6146-111">Example</span></span>  
 <span data-ttu-id="a6146-112">Následující příklad zobrazí metriky pro regulární styl typu Arial.</span><span class="sxs-lookup"><span data-stu-id="a6146-112">The following example displays the metrics for the regular style of the Arial font family.</span></span> <span data-ttu-id="a6146-113">Kód také vytvoří <xref:System.Drawing.Font> objektu (podle Arial rodiny) s 16 pixelů velikost a zobrazí metriky (v pixelech) pro tuto konkrétní <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="a6146-113">The code also creates a <xref:System.Drawing.Font> object (based on the Arial family) with size 16 pixels and displays the metrics (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="a6146-114">Následující obrázek znázorňuje výstup ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="a6146-114">The following illustration shows the output of the example code.</span></span>  
  
 <span data-ttu-id="a6146-115">![Text písem](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span><span class="sxs-lookup"><span data-stu-id="a6146-115">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span></span>  
  
 <span data-ttu-id="a6146-116">Všimněte si výstupu v předchozí ilustraci první dva řádky.</span><span class="sxs-lookup"><span data-stu-id="a6146-116">Note the first two lines of output in the preceding illustration.</span></span> <span data-ttu-id="a6146-117"><xref:System.Drawing.Font> Objekt vrátí velikost 16 a <xref:System.Drawing.FontFamily> em výška 2 048 vrátí objekt.</span><span class="sxs-lookup"><span data-stu-id="a6146-117">The <xref:System.Drawing.Font> object returns a size of 16, and the <xref:System.Drawing.FontFamily> object returns an em height of 2,048.</span></span> <span data-ttu-id="a6146-118">Tato dvě čísla (16 a 2 048) jsou klíčem k převod mezi písma návrhu jednotky a jednotek (v pixelech tento případu) <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="a6146-118">These two numbers (16 and 2,048) are the key to converting between font design units and the units (in this case pixels) of the <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="a6146-119">Například můžete převést stoupání z návrhu jednotek pixelů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a6146-119">For example, you can convert the ascent from design units to pixels as follows:</span></span>  
  
 <span data-ttu-id="a6146-120">![Text písem](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span><span class="sxs-lookup"><span data-stu-id="a6146-120">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span></span>  
  
 <span data-ttu-id="a6146-121">Následující kód umisťuje textu ve svislém směru nastavením <xref:System.Drawing.PointF.Y%2A> data členem <xref:System.Drawing.PointF> objektu.</span><span class="sxs-lookup"><span data-stu-id="a6146-121">The following code positions text vertically by setting the <xref:System.Drawing.PointF.Y%2A> data member of a <xref:System.Drawing.PointF> object.</span></span> <span data-ttu-id="a6146-122">Souřadnice y je zvýšen `font.Height` u každého nového řádku textu.</span><span class="sxs-lookup"><span data-stu-id="a6146-122">The y-coordinate is increased by `font.Height` for each new line of text.</span></span> <span data-ttu-id="a6146-123"><xref:System.Drawing.Font.Height%2A> Vlastnost <xref:System.Drawing.Font> objekt vrátí mezery mezi řádky (v pixelech) pro tuto konkrétní <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="a6146-123">The <xref:System.Drawing.Font.Height%2A> property of a <xref:System.Drawing.Font> object returns the line spacing (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="a6146-124">V tomto příkladu počet vrácených <xref:System.Drawing.Font.Height%2A> je 19.</span><span class="sxs-lookup"><span data-stu-id="a6146-124">In this example, the number returned by <xref:System.Drawing.Font.Height%2A> is 19.</span></span> <span data-ttu-id="a6146-125">Všimněte si, že toto je stejné jako číslo (zaokrouhlený nahoru na celé číslo) získala při převodu metrika mezery mezi řádky na pixelů.</span><span class="sxs-lookup"><span data-stu-id="a6146-125">Note that this is the same as the number (rounded up to an integer) obtained by converting the line-spacing metric to pixels.</span></span>  
  
 <span data-ttu-id="a6146-126">Všimněte si, Výška em (také nazývané velikost velikost nebo em) není součet výstup a klesání.</span><span class="sxs-lookup"><span data-stu-id="a6146-126">Note that the em height (also called size or em size) is not the sum of the ascent and the descent.</span></span> <span data-ttu-id="a6146-127">Součet výstup a klesání nazývá výška buňky.</span><span class="sxs-lookup"><span data-stu-id="a6146-127">The sum of the ascent and the descent is called the cell height.</span></span> <span data-ttu-id="a6146-128">Výška buňky minus interní úvodní výšce em rovná.</span><span class="sxs-lookup"><span data-stu-id="a6146-128">The cell height minus the internal leading is equal to the em height.</span></span> <span data-ttu-id="a6146-129">Výška buňky plus externí úvodního se rovná mezery mezi řádky.</span><span class="sxs-lookup"><span data-stu-id="a6146-129">The cell height plus the external leading is equal to the line spacing.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6146-130">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a6146-130">Compiling the Code</span></span>  
 <span data-ttu-id="a6146-131">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="a6146-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6146-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6146-132">See Also</span></span>  
 [<span data-ttu-id="a6146-133">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6146-133">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="a6146-134">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="a6146-134">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
