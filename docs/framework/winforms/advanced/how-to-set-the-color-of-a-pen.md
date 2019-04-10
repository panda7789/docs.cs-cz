---
title: 'Postupy: Nastavení barvy pera'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: dc067f5a131951bf3af7adc68e11b948d40fc0ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213412"
---
# <a name="how-to-set-the-color-of-a-pen"></a>Postupy: Nastavení barvy pera
V tomto příkladu změní barvu existující <xref:System.Drawing.Pen> objektu  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Drawing.Pen> objekt s názvem `myPen`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Byste měli volat <xref:System.Drawing.Pen.Dispose%2A> na objekty, které využívají systémové prostředky (například <xref:System.Drawing.Pen> objekty) po dokončení jejich používání.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Pen>
- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Postupy: Vytvoření pera](how-to-create-a-pen.md)
- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
- [Pera, čáry a obdélníky v GDI+](pens-lines-and-rectangles-in-gdi.md)
