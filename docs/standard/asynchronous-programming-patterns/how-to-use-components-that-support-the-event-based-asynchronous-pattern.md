---
title: 'Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: 68b376d00762238b810f6463463aa78c492a1a1f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078350"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech
Řada komponent poskytují možnost asynchronní provádění své práce. <xref:System.Media.SoundPlayer> a <xref:System.Windows.Forms.PictureBox> komponenty, například umožňuje načíst podle názvu dalo čekat a Image "v pozadí" i když hlavní podproces stále spuštěná bez přerušení.  
  
 Použití asynchronních metod na třídu, která podporuje [založený na událostech přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) může být stejně snadné jako obslužná rutina události se připojuje k součásti *MethodName *** dokončeno** události stejně jako ostatní události. Při volání *MethodName *** asynchronní** metodu, aplikace bude pokračovat běží nepřetržitě až do *MethodName *** dokončeno** událost se vyvolá. V obslužné rutině události, můžete zkontrolovat <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr určují, jestli asynchronní operace úspěšně dokončena nebo pokud byla zrušena.  
  
 Další informace o používání obslužných rutin událostí, naleznete v tématu [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Následující postup ukazuje, jak použít asynchronní načítání obrázku funkce <xref:System.Windows.Forms.PictureBox> ovládacího prvku.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Aby ovládací prvek PictureBox asynchronně načíst image  
  
1.  Vytvoření instance <xref:System.Windows.Forms.PictureBox> komponentu do formuláře.  
  
2.  Přiřadit obslužnou rutinu události pro <xref:System.Windows.Forms.PictureBox.LoadCompleted> událostí.  
  
     Vyhledejte všechny chyby, které mohly nastat během asynchronní stahování. Toto je také ve kterém můžete zkontrolovat zrušení.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  Přidat dvě tlačítka, volá `loadButton` a `cancelLoadButton`, do svého formuláře. Přidat <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí spuštění a zrušit stahování.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  Spusťte aplikaci.  
  
     Jak pokračuje stažení bitové kopie, volně přesouvat formuláře a minimalizovat ji nemaximalizujte.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
