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
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968604"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Postupy: Ruční správa grafiky uložené do vyrovnávací paměti
Pro pokročilejší scénáře s dvojitou vyrovnávací pamětí můžete použít třídy .NET Framework k implementaci vlastní logiky s dvojitou vyrovnávací pamětí. Třída zodpovědná za přidělení a správu jednotlivých vyrovnávacích pamětí grafiky je <xref:System.Drawing.BufferedGraphicsContext> třída. Každá aplikace má svou vlastní výchozí <xref:System.Drawing.BufferedGraphicsContext> hodnotu, která spravuje všechny výchozí dvojité ukládání do vyrovnávací paměti pro tuto aplikaci. Odkaz na tuto instanci lze načíst voláním metody <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>Získání odkazu na výchozí BufferedGraphicsContext  
  
- <xref:System.Drawing.BufferedGraphicsManager.Current%2A> Nastavte vlastnost, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > Nemusíte volat `Dispose` metodu <xref:System.Drawing.BufferedGraphicsContext> na odkaz <xref:System.Drawing.BufferedGraphicsManager> , který obdržíte od třídy. Zpracovává veškerou alokaci a distribuci paměti pro výchozí <xref:System.Drawing.BufferedGraphicsContext> instance. <xref:System.Drawing.BufferedGraphicsManager>  
  
     Pro graficky náročné aplikace, jako je například animace, můžete někdy zvýšit výkon pomocí vyhrazeného <xref:System.Drawing.BufferedGraphicsContext> místo <xref:System.Drawing.BufferedGraphicsContext> , které poskytuje <xref:System.Drawing.BufferedGraphicsManager>. To umožňuje vytvářet a spravovat vyrovnávací paměti grafiky jednotlivě, aniž by došlo ke zvýšení výkonu při správě všech ostatních grafických objektů přidružených k vaší aplikaci, i když paměť spotřebovaná aplikací bude větší.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Vytvoření vyhrazeného BufferedGraphicsContext  
  
- Deklarujte a vytvořte novou instanci <xref:System.Drawing.BufferedGraphicsContext> třídy, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.BufferedGraphicsContext>
- [Grafiky s dvojitou vyrovnávací pamětí](double-buffered-graphics.md)
- [Postupy: Ruční vykreslování grafiky uložené do vyrovnávací paměti](how-to-manually-render-buffered-graphics.md)
