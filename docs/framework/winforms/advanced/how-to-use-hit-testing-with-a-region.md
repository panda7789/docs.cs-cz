---
title: 'Postupy: Použití testování průchodu s oblastí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 40297fada3d042aee8c317eb787de03662f86cfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523080"
---
# <a name="how-to-use-hit-testing-with-a-region"></a><span data-ttu-id="b9347-102">Postupy: Použití testování průchodu s oblastí</span><span class="sxs-lookup"><span data-stu-id="b9347-102">How to: Use Hit Testing with a Region</span></span>
<span data-ttu-id="b9347-103">Účelem testování přístupů je určit, zda je kurzor přes daný objekt, jako je například ikony nebo tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b9347-103">The purpose of hit testing is to determine whether the cursor is over a given object, such as an icon or a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9347-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9347-104">Example</span></span>  
 <span data-ttu-id="b9347-105">Následující příklad vytvoří oblast ve tvaru plus tvořících sjednocení dvou obdélníkovou oblastí.</span><span class="sxs-lookup"><span data-stu-id="b9347-105">The following example creates a plus-shaped region by forming the union of two rectangular regions.</span></span> <span data-ttu-id="b9347-106">Předpokládáme, že proměnná `point` obsahuje umístění a klikněte na poslední.</span><span class="sxs-lookup"><span data-stu-id="b9347-106">Assume that the variable `point` holds the location of the most recent click.</span></span> <span data-ttu-id="b9347-107">Kód zkontroluje, zda `point` v oblasti ve tvaru plus.</span><span class="sxs-lookup"><span data-stu-id="b9347-107">The code checks to see whether `point` is in the plus-shaped region.</span></span> <span data-ttu-id="b9347-108">Pokud je bod je v oblasti (stiskněte klávesu), je oblast vyplněn neprůhledného red štětce.</span><span class="sxs-lookup"><span data-stu-id="b9347-108">If the point is in the region (a hit), the region is filled with an opaque red brush.</span></span> <span data-ttu-id="b9347-109">Oblast, jinak je vyplněn poloprůhledných red štětce.</span><span class="sxs-lookup"><span data-stu-id="b9347-109">Otherwise, the region is filled with a semitransparent red brush.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9347-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b9347-110">Compiling the Code</span></span>  
 <span data-ttu-id="b9347-111">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="b9347-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9347-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9347-112">See Also</span></span>  
 <xref:System.Drawing.Region>  
 [<span data-ttu-id="b9347-113">Oblasti v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="b9347-113">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [<span data-ttu-id="b9347-114">Postupy: Použití oříznutí s oblastí</span><span class="sxs-lookup"><span data-stu-id="b9347-114">How to: Use Clipping with a Region</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)
