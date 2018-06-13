---
title: 'Postupy: Ruční správa grafiky uložené do vyrovnávací'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: f8675582fe6bafefd94d6a740c3263e407dfd4e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523952"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Postupy: Ruční správa grafiky uložené do vyrovnávací
Pro pokročilejší scénáře dvojité vyrovnávací paměti, můžete použít [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] třídy k implementaci vlastní logiky dvojité ukládání do vyrovnávací paměti. Je třída, která přidělování a správa vyrovnávací paměti jednotlivých grafiky <xref:System.Drawing.BufferedGraphicsContext> třídy. Každá aplikace má svou vlastní výchozí <xref:System.Drawing.BufferedGraphicsContext> který spravuje všechny výchozí dvojité ukládání do vyrovnávací paměti pro tuto aplikaci. Odkaz na tuto instanci můžete načíst pomocí volání <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>Chcete-li získat odkaz na výchozí BufferedGraphicsContext  
  
-   Nastavte <xref:System.Drawing.BufferedGraphicsManager.Current%2A> vlastnost, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  Není potřeba volat `Dispose` metodu <xref:System.Drawing.BufferedGraphicsContext> odkaz, který jste dostali od <xref:System.Drawing.BufferedGraphicsManager> třídy. <xref:System.Drawing.BufferedGraphicsManager> Zpracovává všechny přidělování paměti a distribuci pro výchozí <xref:System.Drawing.BufferedGraphicsContext> instance.  
  
     Pro graficky náročné aplikace, jako je například animace, může někdy zlepšit výkon pomocí vyhrazená <xref:System.Drawing.BufferedGraphicsContext> místo <xref:System.Drawing.BufferedGraphicsContext> poskytované <xref:System.Drawing.BufferedGraphicsManager>. To umožňuje vytvářet a spravovat vyrovnávací paměti grafiky samostatně, aniž by docházelo k správy všechny ostatní ve vyrovnávací paměti obrázky přidružené aplikace, když bude paměť spotřebovávají aplikace větší nároky na výkon.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Chcete-li vytvořit vyhrazený BufferedGraphicsContext  
  
-   Deklarace a vytvořit novou instanci třídy <xref:System.Drawing.BufferedGraphicsContext> třídy, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.BufferedGraphicsContext>  
 [Grafiky s dvojitou vyrovnávací pamětí](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
