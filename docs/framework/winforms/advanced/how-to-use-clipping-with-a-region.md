---
title: 'Postupy: Použití oříznutí s oblastí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
ms.openlocfilehash: cf60b32df805a49f8da2760332dc32e34209f6dc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163732"
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="6165f-102">Postupy: Použití oříznutí s oblastí</span><span class="sxs-lookup"><span data-stu-id="6165f-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="6165f-103">Jedna z vlastností objektu <xref:System.Drawing.Graphics> třída je oblast ústřižku.</span><span class="sxs-lookup"><span data-stu-id="6165f-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="6165f-104">Všechny kreslení provádí daný <xref:System.Drawing.Graphics> je omezen na oblast ústřižku tohoto objektu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="6165f-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="6165f-105">Můžete nastavit oblast ústřižku voláním <xref:System.Drawing.Graphics.SetClip%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6165f-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6165f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6165f-106">Example</span></span>  
 <span data-ttu-id="6165f-107">Následující příklad vytvoří cestu, která se skládá z jedné mnohoúhelníku.</span><span class="sxs-lookup"><span data-stu-id="6165f-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="6165f-108">Kód poté vytvoří oblast, na základě této cesty.</span><span class="sxs-lookup"><span data-stu-id="6165f-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="6165f-109">Oblast je předána <xref:System.Drawing.Graphics.SetClip%2A> metodu <xref:System.Drawing.Graphics> jsou vykreslovány vedle objektu a pak dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="6165f-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="6165f-110">Následující obrázek znázorňuje zkrácený řetězce.</span><span class="sxs-lookup"><span data-stu-id="6165f-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="6165f-111">![Clip](./media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="6165f-111">![Clip](./media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6165f-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6165f-112">Compiling the Code</span></span>  
 <span data-ttu-id="6165f-113">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="6165f-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6165f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6165f-114">See also</span></span>

- [<span data-ttu-id="6165f-115">Oblasti v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="6165f-115">Regions in GDI+</span></span>](regions-in-gdi.md)
- [<span data-ttu-id="6165f-116">Použití oblastí</span><span class="sxs-lookup"><span data-stu-id="6165f-116">Using Regions</span></span>](using-regions.md)
