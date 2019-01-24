---
title: 'Postupy: Nastavení šířky a pera a zarovnání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: d1a465fb7c1cd6d4064a077e592daefebf590714
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564822"
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="bbecc-102">Postupy: Nastavení šířky a pera a zarovnání</span><span class="sxs-lookup"><span data-stu-id="bbecc-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="bbecc-103">Když vytvoříte <xref:System.Drawing.Pen>, můžete zadat šířku pera jako jeden z argumentů konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="bbecc-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="bbecc-104">Můžete také změnit šířku pera s <xref:System.Drawing.Pen.Width%2A> vlastnost <xref:System.Drawing.Pen> třídy.</span><span class="sxs-lookup"><span data-stu-id="bbecc-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="bbecc-105">Teoretické řádek má šířku 0.</span><span class="sxs-lookup"><span data-stu-id="bbecc-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="bbecc-106">Když nakreslíte čáru, která je 1 pixelu široké, se na řádku teoretické na pixely.</span><span class="sxs-lookup"><span data-stu-id="bbecc-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="bbecc-107">Pokud nakreslení čáry, která je více než jeden pixel široké pixely se buď na řádku teoretické nebo zobrazovat na jedné straně teoretické řádku.</span><span class="sxs-lookup"><span data-stu-id="bbecc-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="bbecc-108">Můžete nastavit vlastnost zarovnání pera <xref:System.Drawing.Pen> k určení, jak bude umístěna pixelů vykresleno pomocí pera vzhledem k teoretické řádky.</span><span class="sxs-lookup"><span data-stu-id="bbecc-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="bbecc-109">Hodnoty <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, a <xref:System.Drawing.Drawing2D.PenAlignment.Inset> , která se zobrazují následující příklady kódu jsou členy <xref:System.Drawing.Drawing2D.PenAlignment> výčtu.</span><span class="sxs-lookup"><span data-stu-id="bbecc-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="bbecc-110">Následující příklad kódu nakreslí čáru dvakrát: jednou perem černé šířky 1 a posléze s zelené pera šířky 10.</span><span class="sxs-lookup"><span data-stu-id="bbecc-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="bbecc-111">Postup obměny šířku pera</span><span class="sxs-lookup"><span data-stu-id="bbecc-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="bbecc-112">Nastavte hodnotu <xref:System.Drawing.Pen.Alignment%2A> vlastnost <xref:System.Drawing.Drawing2D.PenAlignment.Center> (výchozí) k určení, že bude pixelů vykreslit zelený perem teoretické řádku na střed.</span><span class="sxs-lookup"><span data-stu-id="bbecc-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="bbecc-113">Následující obrázek znázorňuje výsledný řádek.</span><span class="sxs-lookup"><span data-stu-id="bbecc-113">The following illustration shows the resulting line.</span></span>  
  
     <span data-ttu-id="bbecc-114">![Pera](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span><span class="sxs-lookup"><span data-stu-id="bbecc-114">![Pens](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span></span>  
  
     <span data-ttu-id="bbecc-115">Následující příklad kódu kreslení obdélníku dvakrát: jednou perem černé šířky 1 a posléze s zelené pera šířky 10.</span><span class="sxs-lookup"><span data-stu-id="bbecc-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="bbecc-116">Chcete-li změnit zarovnání pera</span><span class="sxs-lookup"><span data-stu-id="bbecc-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="bbecc-117">Nastavte hodnotu <xref:System.Drawing.Pen.Alignment%2A> vlastnost <xref:System.Drawing.Drawing2D.PenAlignment.Center> k určení, že bude pixelů vykreslit zelený perem na hranici obdélník na střed.</span><span class="sxs-lookup"><span data-stu-id="bbecc-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="bbecc-118">Výsledný obdélníku na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="bbecc-118">The following illustration shows the resulting rectangle.</span></span>  
  
     <span data-ttu-id="bbecc-119">![Pera](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span><span class="sxs-lookup"><span data-stu-id="bbecc-119">![Pens](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="bbecc-120">Vytvoření inset pera</span><span class="sxs-lookup"><span data-stu-id="bbecc-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="bbecc-121">Změna zarovnání zelené pera tak, že upravíte třetí příkaz v předchozím příkladu kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="bbecc-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="bbecc-122">Pixelů na šířku zelenou čáru zobrazují na vnitřní obdélníku, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="bbecc-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="bbecc-123">![Pera](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span><span class="sxs-lookup"><span data-stu-id="bbecc-123">![Pens](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbecc-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbecc-124">See also</span></span>
- [<span data-ttu-id="bbecc-125">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="bbecc-125">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="bbecc-126">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbecc-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
