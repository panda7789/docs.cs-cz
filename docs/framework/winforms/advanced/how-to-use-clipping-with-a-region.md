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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163732"
---
# <a name="how-to-use-clipping-with-a-region"></a>Postupy: Použití oříznutí s oblastí
Jedna z vlastností objektu <xref:System.Drawing.Graphics> třída je oblast ústřižku. Všechny kreslení provádí daný <xref:System.Drawing.Graphics> je omezen na oblast ústřižku tohoto objektu <xref:System.Drawing.Graphics> objektu. Můžete nastavit oblast ústřižku voláním <xref:System.Drawing.Graphics.SetClip%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří cestu, která se skládá z jedné mnohoúhelníku. Kód poté vytvoří oblast, na základě této cesty. Oblast je předána <xref:System.Drawing.Graphics.SetClip%2A> metodu <xref:System.Drawing.Graphics> jsou vykreslovány vedle objektu a pak dva řetězce.  
  
 Následující obrázek znázorňuje zkrácený řetězce.  
  
 ![Clip](./media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- [Oblasti v rozhraní GDI+](regions-in-gdi.md)
- [Použití oblastí](using-regions.md)
