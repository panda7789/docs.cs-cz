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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004403"
---
# <a name="how-to-create-a-pen"></a>Postupy: Vytvoření pera
Tento příklad vytvoří <xref:System.Drawing.Pen> objektu.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Po dokončení používání objektů, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> objektů, měli byste zavolat <xref:System.Drawing.Pen.Dispose%2A> na ně.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Pen>
- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Pera, čáry a obdélníky v GDI+](pens-lines-and-rectangles-in-gdi.md)
