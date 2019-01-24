---
title: 'Postupy: Použití testování průchodu s oblast'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 1866810b875063271e206da1fe5d6fc06f7b5de0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564302"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>Postupy: Použití testování průchodu s oblast
Účelem testování přístupů je určit, zda je kurzor nad daný objekt, jako je například ikony nebo tlačítko.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří ve tvaru plus oblast tvořící sjednocení dvě oblasti obdélníkový. Předpokládejme, že proměnná `point` obsahuje nejnovější kliknutím na umístění. Kód zkontroluje, zda `point` je v oblasti ve tvaru plus. Pokud bod nachází v oblasti (položek), je oblast vyplněna neprůhledné red štětce. V opačném případě je oblast vyplněna poloprůhledných red štětce.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.Region>
- [Oblasti v rozhraní GDI+](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)
- [Postupy: Použití oříznutí s oblastí](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)
