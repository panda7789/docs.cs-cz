---
title: 'Postupy: Ruční vykreslení grafiky uložené do vyrovnávací paměti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: a6655652a7c5dedb8e183356688972c07a705cbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931838"
---
# <a name="how-to-manually-render-buffered-graphics"></a>Postupy: Ruční vykreslení grafiky uložené do vyrovnávací paměti
Pokud spravujete vlastní grafiku ve vyrovnávací paměti, budete muset vytvořit a vykreslit grafické vyrovnávací paměti. Můžete vytvořit instance <xref:System.Drawing.BufferedGraphics> třídy, které jsou spojeny s kreslicími plochami na obrazovce <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> voláním metody. Tato metoda vytvoří <xref:System.Drawing.BufferedGraphics> instanci, která je přidružena k určité ploše vykreslování, jako je například formulář nebo ovládací prvek. Po vytvoření <xref:System.Drawing.BufferedGraphics> instance můžete grafiku nakreslit do vyrovnávací paměti, kterou představuje <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnost. Po provedení všech grafických operací můžete zkopírovat obsah vyrovnávací paměti na obrazovku voláním <xref:System.Drawing.BufferedGraphics.Render%2A> metody.  
  
> [!NOTE]
> Pokud provedete vlastní vykreslování, spotřeba paměti se zvýší, i když zvýšení může být jen slabé.  
  
### <a name="to-manually-display-buffered-graphics"></a>Ruční zobrazení grafiky uložené do vyrovnávací paměti  
  
1. Získejte odkaz na instanci <xref:System.Drawing.BufferedGraphicsContext> třídy. Další informace najdete v tématu [jak: Ručně spravovat grafiku](how-to-manually-manage-buffered-graphics.md)uloženou v vyrovnávací paměti.  
  
2. Vytvořte instanci <xref:System.Drawing.BufferedGraphics> třídy <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> voláním metody, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. Nakreslete grafiku do vyrovnávací paměti grafiky nastavením <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnosti. Příklad:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. Až dokončíte všechny operace kreslení do vyrovnávací paměti grafiky, zavolejte <xref:System.Drawing.BufferedGraphics.Render%2A> metodu pro vykreslení vyrovnávací paměti, buď na kreslicí plochu přidruženou k této vyrovnávací paměti, nebo na zadanou plochu kresby, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. Po dokončení vykreslování grafiky zavolejte `Dispose` metodu <xref:System.Drawing.BufferedGraphics> v instanci, abyste uvolnili systémové prostředky.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [Grafiky s dvojitou vyrovnávací pamětí](double-buffered-graphics.md)
- [Postupy: Ruční správa grafiky uložené do vyrovnávací paměti](how-to-manually-manage-buffered-graphics.md)
