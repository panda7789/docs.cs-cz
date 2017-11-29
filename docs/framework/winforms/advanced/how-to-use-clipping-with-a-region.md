---
title: "Postupy: Použití oříznutí s oblastí"
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
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b57ffa91a41900e10aa921bd42509b1288134ff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="04fb7-102">Postupy: Použití oříznutí s oblastí</span><span class="sxs-lookup"><span data-stu-id="04fb7-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="04fb7-103">Jedna z vlastností <xref:System.Drawing.Graphics> třída je klip oblast.</span><span class="sxs-lookup"><span data-stu-id="04fb7-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="04fb7-104">Všechny kreslení provádí danou <xref:System.Drawing.Graphics> objekt je omezen na oblasti klip této <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="04fb7-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="04fb7-105">Oblasti klip můžete nastavit tak, že zavoláte <xref:System.Drawing.Graphics.SetClip%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="04fb7-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04fb7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="04fb7-106">Example</span></span>  
 <span data-ttu-id="04fb7-107">Následující příklad vytvoří cestu, která se skládá z jedné mnohoúhelníku.</span><span class="sxs-lookup"><span data-stu-id="04fb7-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="04fb7-108">Potom vytvoří kód oblasti, na základě této cesty.</span><span class="sxs-lookup"><span data-stu-id="04fb7-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="04fb7-109">Oblast je předána <xref:System.Drawing.Graphics.SetClip%2A> metodu <xref:System.Drawing.Graphics> jsou vykreslovány objekt a potom dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="04fb7-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="04fb7-110">Následující obrázek znázorňuje oříznutí řetězce.</span><span class="sxs-lookup"><span data-stu-id="04fb7-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="04fb7-111">![Klip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="04fb7-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="04fb7-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="04fb7-112">Compiling the Code</span></span>  
 <span data-ttu-id="04fb7-113">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="04fb7-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04fb7-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="04fb7-114">See Also</span></span>  
 [<span data-ttu-id="04fb7-115">Oblasti v GDI +</span><span class="sxs-lookup"><span data-stu-id="04fb7-115">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [<span data-ttu-id="04fb7-116">Použití oblastí</span><span class="sxs-lookup"><span data-stu-id="04fb7-116">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
