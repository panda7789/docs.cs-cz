---
title: 'Postupy: Vytvoření štětce jednotné barvy'
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
ms.openlocfilehash: ed9ec1f52b41c83b3cc6e36dedf97f1c00db42e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213438"
---
# <a name="how-to-create-a-solid-brush"></a>Postupy: Vytvoření štětce jednotné barvy
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
