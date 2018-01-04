---
title: "Postupy: Nastavení zarážek v kresleném textu"
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
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2acc46a9a3fa2c84138cd9a168113f88ab08e4a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="9bdf0-102">Postupy: Nastavení zarážek v kresleném textu</span><span class="sxs-lookup"><span data-stu-id="9bdf0-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="9bdf0-103">Můžete nastavení zarážek tabulátorů pro text voláním <xref:System.Drawing.StringFormat.SetTabStops%2A> metodu <xref:System.Drawing.StringFormat> objekt a následné předání, <xref:System.Drawing.StringFormat> do objektu <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> – třída.</span><span class="sxs-lookup"><span data-stu-id="9bdf0-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bdf0-104"><xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Nemá nepodporuje přidání zarážek tabulátorů vykresleného textu, i když můžete rozšířit stávající karta přestane používat <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> příznak.</span><span class="sxs-lookup"><span data-stu-id="9bdf0-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bdf0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9bdf0-105">Example</span></span>  
 <span data-ttu-id="9bdf0-106">Následující příklad ilustruje zarážek na 150, 250 a 350.</span><span class="sxs-lookup"><span data-stu-id="9bdf0-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="9bdf0-107">Kód zobrazí záložkách seznam názvů a výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="9bdf0-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="9bdf0-108">Následující obrázek znázorňuje záložkách text.</span><span class="sxs-lookup"><span data-stu-id="9bdf0-108">The following illustration shows the tabbed text.</span></span>  
  
 <span data-ttu-id="9bdf0-109">![Text písem](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span><span class="sxs-lookup"><span data-stu-id="9bdf0-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span></span>  
  
 <span data-ttu-id="9bdf0-110">Následující kód předá dva argumenty, které mají <xref:System.Drawing.StringFormat.SetTabStops%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9bdf0-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="9bdf0-111">Druhý argument je pole, které obsahuje posuny kartě.</span><span class="sxs-lookup"><span data-stu-id="9bdf0-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="9bdf0-112">První argument předaný <xref:System.Drawing.StringFormat.SetTabStops%2A> je 0, což značí, že první posunutí v poli se měří od pozice 0, je levý okraj ohraničující obdélník.</span><span class="sxs-lookup"><span data-stu-id="9bdf0-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9bdf0-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9bdf0-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="9bdf0-114">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="9bdf0-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bdf0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bdf0-115">See Also</span></span>  
 [<span data-ttu-id="9bdf0-116">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="9bdf0-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="9bdf0-117">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="9bdf0-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
