---
title: Použití světové transformace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: cc6bcca42e84580199f75c64087af6d98f476d4b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715695"
---
# <a name="using-the-world-transformation"></a><span data-ttu-id="998d5-102">Použití světové transformace</span><span class="sxs-lookup"><span data-stu-id="998d5-102">Using the World Transformation</span></span>
<span data-ttu-id="998d5-103">Světové transformace je vlastnost <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="998d5-103">The world transformation is a property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="998d5-104">Číslo, které určují Světové transformace jsou uložené v <xref:System.Drawing.Drawing2D.Matrix> objektu, který představuje matici 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="998d5-104">The numbers that specify the world transformation are stored in a <xref:System.Drawing.Drawing2D.Matrix> object, which represents a 3×3 matrix.</span></span> <span data-ttu-id="998d5-105"><xref:System.Drawing.Drawing2D.Matrix> a <xref:System.Drawing.Graphics> třídy mají několik metod k nastavení čísla v celém světě transformační matice.</span><span class="sxs-lookup"><span data-stu-id="998d5-105">The <xref:System.Drawing.Drawing2D.Matrix> and <xref:System.Drawing.Graphics> classes have several methods for setting the numbers in the world transformation matrix.</span></span>  
  
## <a name="different-types-of-transformations"></a><span data-ttu-id="998d5-106">Různé typy transformací</span><span class="sxs-lookup"><span data-stu-id="998d5-106">Different Types of Transformations</span></span>  
 <span data-ttu-id="998d5-107">V následujícím příkladu kódu nejprve vytvoří obdélník 50 × 50 a vyhledá na počátek (0, 0).</span><span class="sxs-lookup"><span data-stu-id="998d5-107">In the following example, the code first creates a 50×50 rectangle and locates it at the origin (0, 0).</span></span> <span data-ttu-id="998d5-108">Původ v levém horním rohu klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="998d5-108">The origin is at the upper-left corner of the client area.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 <span data-ttu-id="998d5-109">Následující kód použije škálování transformaci, která rozšiřuje obdélník faktorem 1,75 ve směru osy x a zmenšuje faktorem 0,5 ve směru osy y obdélníku:</span><span class="sxs-lookup"><span data-stu-id="998d5-109">The following code applies a scaling transformation that expands the rectangle by a factor of 1.75 in the x direction and shrinks the rectangle by a factor of 0.5 in the y direction:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 <span data-ttu-id="998d5-110">Výsledkem je obdélník, který je delší ve směru osy x a kratší než původní směru osy y.</span><span class="sxs-lookup"><span data-stu-id="998d5-110">The result is a rectangle that is longer in the x direction and shorter in the y direction than the original.</span></span>  
  
 <span data-ttu-id="998d5-111">Otočit obdélník místo vertikální snížení jeho kapacity, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="998d5-111">To rotate the rectangle instead of scaling it, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 <span data-ttu-id="998d5-112">Pro převod obdélníku, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="998d5-112">To translate the rectangle, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="998d5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="998d5-113">See also</span></span>
- <xref:System.Drawing.Drawing2D.Matrix>
- [<span data-ttu-id="998d5-114">Systém souřadnic a transformace</span><span class="sxs-lookup"><span data-stu-id="998d5-114">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="998d5-115">Použití transformací ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="998d5-115">Using Transformations in Managed GDI+</span></span>](using-transformations-in-managed-gdi.md)
