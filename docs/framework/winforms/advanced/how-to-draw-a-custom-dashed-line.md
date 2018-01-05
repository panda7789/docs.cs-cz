---
title: "Postupy: Kreslení vlastní přerušované čáry"
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
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 770ce290b21f7d0094a487c30079063b79a7c08d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="c1b2d-102">Postupy: Kreslení vlastní přerušované čáry</span><span class="sxs-lookup"><span data-stu-id="c1b2d-102">How to: Draw a Custom Dashed Line</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c1b2d-103">poskytuje několik dash stylů, které jsou uvedeny v <xref:System.Drawing.Drawing2D.DashStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="c1b2d-103"> provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="c1b2d-104">Pokud tyto styly standardní dash nevyhovují vašim potřebám, můžete vytvořit vlastní čárkovém vzoru.</span><span class="sxs-lookup"><span data-stu-id="c1b2d-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1b2d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1b2d-105">Example</span></span>  
 <span data-ttu-id="c1b2d-106">Kreslení vlastní přerušované čáry, do pole umístit délky čárek a mezer a přiřaďte pole jako hodnotu <xref:System.Drawing.Pen.DashPattern%2A> vlastnost <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="c1b2d-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="c1b2d-107">Následující příklad nevykresluje vlastní přerušované čáry podle pole `{5, 2, 15, 4}`.</span><span class="sxs-lookup"><span data-stu-id="c1b2d-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="c1b2d-108">Jestliže jste elementy pole vynásobit šířku pera 5, můžete získat `{25, 10, 75, 20}`.</span><span class="sxs-lookup"><span data-stu-id="c1b2d-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="c1b2d-109">Zobrazené pomlčky alternativní v délce 25 a 75 a prostory alternativní délku mezi 10 a 20.</span><span class="sxs-lookup"><span data-stu-id="c1b2d-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="c1b2d-110">Následující obrázek znázorňuje výsledné přerušovanou čáru.</span><span class="sxs-lookup"><span data-stu-id="c1b2d-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="c1b2d-111">Všimněte si, že poslední čárka musí být kratší než 25 jednotek, aby řádek můžete ukončit na (405, 5).</span><span class="sxs-lookup"><span data-stu-id="c1b2d-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="c1b2d-112">![Pera](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="c1b2d-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1b2d-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c1b2d-113">Compiling the Code</span></span>  
 <span data-ttu-id="c1b2d-114">Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="c1b2d-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="c1b2d-115">Předchozí kód vložte do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c1b2d-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b2d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1b2d-116">See Also</span></span>  
 [<span data-ttu-id="c1b2d-117">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="c1b2d-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
