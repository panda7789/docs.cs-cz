---
title: "Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49e03a8d886ccd4ed6e4b2a19692c1874f5928ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech
Celá řada komponent poskytují možnost provedení práci asynchronně. <xref:System.Media.SoundPlayer> a <xref:System.Windows.Forms.PictureBox> součásti, například umožňuje načíst vyznívá a bitové kopie "v pozadí", zatímco hlavní vlákno stále spuštěna bez přerušení.  
  
 Použití asynchronních metod na třídu, která podporuje [na základě událostí přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) může být stejně jednoduché jako obslužné rutiny události se připojuje k součásti *MethodName* `Completed` události stejně jako ostatní události. Při volání *MethodName* `Async` metoda, vaše aplikace bude dál běžet bez přerušení, dokud *MethodName* `Completed` událost se vyvolá. V obslužné rutině událostí, můžete zkontrolovat <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr k určení, pokud asynchronní operace úspěšně dokončena, nebo pokud byla zrušena.  
  
 Další informace o používání obslužných rutin událostí najdete v tématu [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Následující postup ukazuje, jak použít funkci asynchronní načítání bitové kopie systému <xref:System.Windows.Forms.PictureBox> ovládacího prvku.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Chcete-li povolit asynchronně načíst obrázek ovládacího prvku PictureBox  
  
1.  Vytvoření instance <xref:System.Windows.Forms.PictureBox> součásti do formuláře.  
  
2.  Obslužné rutiny události pro přiřazení <xref:System.Windows.Forms.PictureBox.LoadCompleted> událostí.  
  
     Zkontrolujte chyby, ke kterým mohlo dojít během asynchronní stahování. Toto je také kde kontrolovat zrušení.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  Přidat dvě tlačítka, nazývá `loadButton` a `cancelLoadButton`, do svého formuláře. Přidat <xref:System.Windows.Forms.Control.Click> obslužné rutiny události spuštění a stahování zrušte.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  Spusťte svoji aplikaci.  
  
     Jak pokračuje stažení bitové kopie, volně přesouvat formuláře a minimalizovat ji nemaximalizujte.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NENÍ v sestavení: Více vláken v jazyce Visual Basic](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)
