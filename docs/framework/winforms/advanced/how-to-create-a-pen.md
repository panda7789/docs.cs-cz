---
title: 'Postupy: Vytvoření pera'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating pens
- pens [Windows Forms], creating
- Pen object
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
ms.openlocfilehash: 69fe6157c710ae63df9dbf391a5d355d1c3f9765
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148106"
---
# <a name="how-to-create-a-pen"></a><span data-ttu-id="cea64-102">Postupy: Vytvoření pera</span><span class="sxs-lookup"><span data-stu-id="cea64-102">How to: Create a Pen</span></span>
<span data-ttu-id="cea64-103">Tento příklad vytvoří <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="cea64-103">This example creates a <xref:System.Drawing.Pen> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cea64-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cea64-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cea64-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="cea64-105">Robust Programming</span></span>  
 <span data-ttu-id="cea64-106">Po dokončení používání objektů, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> objektů, měli byste zavolat <xref:System.Drawing.Pen.Dispose%2A> na ně.</span><span class="sxs-lookup"><span data-stu-id="cea64-106">After you have finished using objects that consume system resources, such as <xref:System.Drawing.Pen> objects, you should call <xref:System.Drawing.Pen.Dispose%2A> on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea64-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cea64-107">See also</span></span>

- <xref:System.Drawing.Pen>
- [<span data-ttu-id="cea64-108">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="cea64-108">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="cea64-109">Pera, čáry a obdélníky v GDI+</span><span class="sxs-lookup"><span data-stu-id="cea64-109">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
