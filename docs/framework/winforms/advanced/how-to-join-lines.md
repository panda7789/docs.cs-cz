---
title: "Postupy: Spojení čar"
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
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d12cc7b4b4c878ec812190fd56a1face64118ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-join-lines"></a><span data-ttu-id="46c65-102">Postupy: Spojení čar</span><span class="sxs-lookup"><span data-stu-id="46c65-102">How to: Join Lines</span></span>
<span data-ttu-id="46c65-103">Spojení čar je běžné oblasti, která je tvořen dvěma řádky, jehož elementy end splňují nebo překrývat.</span><span class="sxs-lookup"><span data-stu-id="46c65-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="46c65-104">poskytuje tři styly řádku spojení: ostrý bevelova křivka a zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="46c65-104"> provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="46c65-105">Čára – styl propojení je vlastnost <xref:System.Drawing.Pen> třídy.</span><span class="sxs-lookup"><span data-stu-id="46c65-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="46c65-106">Pokud zadáte styl řádku spojení <xref:System.Drawing.Pen> objektu, že styl spojení se použije na všechny řádky, které jsou připojené v žádném <xref:System.Drawing.Drawing2D.GraphicsPath> objekt vykreslovány pomocí pera.</span><span class="sxs-lookup"><span data-stu-id="46c65-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="46c65-107">Následující obrázek znázorňuje výsledky příklad spojení zkosení řádku.</span><span class="sxs-lookup"><span data-stu-id="46c65-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 <span data-ttu-id="46c65-108">![Pera](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span><span class="sxs-lookup"><span data-stu-id="46c65-108">![Pens](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span></span>  
  
## <a name="example"></a><span data-ttu-id="46c65-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="46c65-109">Example</span></span>  
 <span data-ttu-id="46c65-110">Styl čáry spojení můžete zadat pomocí <xref:System.Drawing.Pen.LineJoin%2A> vlastnost <xref:System.Drawing.Pen> třídy.</span><span class="sxs-lookup"><span data-stu-id="46c65-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="46c65-111">Příklad ukazuje zkosení řádku spojení mezi na vodorovném řádku a svislá čára.</span><span class="sxs-lookup"><span data-stu-id="46c65-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="46c65-112">V následujícím kódu, hodnota <xref:System.Drawing.Drawing2D.LineJoin.Bevel> přiřazené <xref:System.Drawing.Pen.LineJoin%2A> vlastnost je členem skupiny <xref:System.Drawing.Drawing2D.LineJoin> výčtu.</span><span class="sxs-lookup"><span data-stu-id="46c65-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="46c65-113">Ostatní členové <xref:System.Drawing.Drawing2D.LineJoin> jsou výčtu <xref:System.Drawing.Drawing2D.LineJoin.Miter> a <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="46c65-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46c65-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="46c65-114">Compiling the Code</span></span>  
 <span data-ttu-id="46c65-115">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="46c65-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c65-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="46c65-116">See Also</span></span>  
 [<span data-ttu-id="46c65-117">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="46c65-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
