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
ms.openlocfilehash: aff1771af12a9f59127a9f21f4b692d6214c457d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-pen"></a>Postupy: Vytvoření pera
Tento příklad vytvoří <xref:System.Drawing.Pen> objektu.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Po ukončení používání objektů, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> objekty, by měly volat <xref:System.Drawing.Pen.Dispose%2A> na ně.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Pen>  
 [Začínáme s programováním grafiky](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Pera, čáry a obdélníky v GDI+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
