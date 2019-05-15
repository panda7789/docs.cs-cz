---
title: 'Postupy: Ruční správa grafiky uložené do vyrovnávací paměti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 2cdcebd4e47996841ad58213d9c6252a6a3dd7b6
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591835"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Postupy: Ruční správa grafiky uložené do vyrovnávací paměti
Pro pokročilejší scénáře dvojité vyrovnávací paměti můžete použít třídy rozhraní .NET Framework do implementovat vlastní logiku na dvojité ukládání do vyrovnávací paměti. Je třída, která je zodpovědná za přidělení a správa jednotlivých grafické vyrovnávací paměti <xref:System.Drawing.BufferedGraphicsContext> třídy. Každá aplikace má vlastní výchozí <xref:System.Drawing.BufferedGraphicsContext> , který spravuje všechny výchozí dvojité ukládání do vyrovnávací paměti pro příslušnou aplikaci. Odkaz na tuto instanci lze načíst voláním <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>K získání odkazu na výchozí hodnotu BufferedGraphicsContext  
  
- Nastavte <xref:System.Drawing.BufferedGraphicsManager.Current%2A> vlastnost, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  Není potřeba volat `Dispose` metodu <xref:System.Drawing.BufferedGraphicsContext> odkaz, který jste dostali z <xref:System.Drawing.BufferedGraphicsManager> třídy. <xref:System.Drawing.BufferedGraphicsManager> Zpracovává všechna přidělení paměti a distribuce pro výchozí <xref:System.Drawing.BufferedGraphicsContext> instancí.  
  
     Pro graficky náročné aplikace, jako je animace, můžete někdy výkon lze zvýšit pomocí vyhrazené <xref:System.Drawing.BufferedGraphicsContext> místo <xref:System.Drawing.BufferedGraphicsContext> poskytované <xref:System.Drawing.BufferedGraphicsManager>. To umožňuje vytvářet a spravovat grafické vyrovnávací paměti jednotlivě, aniž by platili správy všechny ostatní ve vyrovnávací paměti grafiky přidruženého k aplikaci, když paměti spotřebované aplikací bude větší nároky na výkon.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Chcete-li vytvořit vyhrazený BufferedGraphicsContext  
  
- Deklarace a vytvořit novou instanci třídy <xref:System.Drawing.BufferedGraphicsContext> třídy, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.BufferedGraphicsContext>
- [Grafiky s dvojitou vyrovnávací pamětí](double-buffered-graphics.md)
- [Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti](how-to-manually-render-buffered-graphics.md)
