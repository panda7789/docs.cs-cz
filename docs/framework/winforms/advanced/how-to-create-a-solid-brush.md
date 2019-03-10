---
title: 'Postupy: Vytvoření plného štětce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
ms.openlocfilehash: d7fb7c11a69cae69210dd2eece3336bc40c505c7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711977"
---
# <a name="how-to-create-a-solid-brush"></a>Postupy: Vytvoření plného štětce
Tento příklad vytvoří <xref:System.Drawing.SolidBrush> objekt, který můžete používat <xref:System.Drawing.Graphics> objekt pro vyplnění tvarů.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Po dokončení jejich používání byste měli volat <xref:System.IDisposable.Dispose%2A> na objekty, které využívají systémové prostředky, jako jsou štětce objekty.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.SolidBrush>
- <xref:System.Drawing.Brush>
- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Štětce a vyplněné obrazce v GDI+](brushes-and-filled-shapes-in-gdi.md)
- [Použití štětce k vyplnění obrazců](using-a-brush-to-fill-shapes.md)
