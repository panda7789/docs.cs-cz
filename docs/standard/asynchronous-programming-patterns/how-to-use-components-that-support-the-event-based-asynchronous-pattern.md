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
ms.openlocfilehash: 9ac98b5c576c065f8944714c72b492539e0d2f05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "61870237"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech
Mnoho součástí poskytují možnost provádění jejich práce asynchronně. <xref:System.Media.SoundPlayer> Komponenty <xref:System.Windows.Forms.PictureBox> a například umožňují načíst zvuky a obrázky "na pozadí", zatímco hlavní vlákno pokračuje v provozu bez přerušení.  
  
 Použití asynchronních metod ve třídě, která podporuje [přehled asynchronních vzorů založených na událostech,](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) může být stejně jednoduché jako připojení obslužné rutiny události k události _MethodName_**completed** komponenty, stejně jako u jakékoli jiné události. Při volání _MethodName_**Async** metoda, aplikace bude pokračovat v provozu bez přerušení, dokud _MethodName_**Completed** událost je aktivována. V obslužné rutině <xref:System.ComponentModel.AsyncCompletedEventArgs> události můžete zkontrolovat parametr a zjistit, zda byla asynchronní operace úspěšně dokončena nebo zda byla zrušena.  
  
 Další informace o použití obslužných rutin událostí naleznete v [tématu Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Následující postup ukazuje, jak používat asynchronní načítání bitových obrázků schopnosti ovládacího <xref:System.Windows.Forms.PictureBox> prvku.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Povolení ovládacího prvku PictureBox pro asynchronní načtení bitové kopie  
  
1. Vytvořte instanci součásti <xref:System.Windows.Forms.PictureBox> ve formuláři.  
  
2. Přiřaďte k <xref:System.Windows.Forms.PictureBox.LoadCompleted> události obslužnou rutinu události.  
  
     Zkontrolujte všechny chyby, ke kterým mohlo dojít během asynchronního stahování zde. To je také místo, kde můžete zkontrolovat zrušení.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3. Do formuláře přidejte dvě tlačítka s názvem `loadButton` a `cancelLoadButton`. Přidejte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí a spusťte a zrušte stahování.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4. Spusťte aplikaci.  
  
     Jak stahování obrázku pokračuje, můžete formulář volně přesouvat, minimalizovat a maximalizovat.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
