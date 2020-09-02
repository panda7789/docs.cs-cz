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
ms.openlocfilehash: e23a9b28cff9428cbc8896515ce71db85c832243
ms.sourcegitcommit: b78018c850590dfc0348301e1748b779c28604cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89379145"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech
Řada komponent nabízí možnost asynchronního provádění jejich práce. <xref:System.Media.SoundPlayer>Komponenty a <xref:System.Windows.Forms.PictureBox> například umožňují načíst zvuky a obrázky "na pozadí", zatímco vaše hlavní vlákno pokračuje v běhu bez přerušení.  
  
 Použití asynchronních metod pro třídu, která podporuje [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md) , může být jednoduché jako připojení obslužné rutiny události k události _methodName_**Completed** , stejně jako u jakékoli jiné události. Při volání**asynchronní** metody _methodName_bude aplikace nadále běžet bez přerušení, dokud nedojde k vyvolání události _methodName_**Completed** . V obslužné rutině události můžete ověřit <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr a zjistit, zda byla asynchronní operace úspěšně dokončena nebo zda byla zrušena.  
  
 Další informace o použití obslužných rutin událostí najdete v tématu [Přehled obslužných rutin událostí](../../framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Následující postup ukazuje, jak použít asynchronní funkce načítání obrázků <xref:System.Windows.Forms.PictureBox> ovládacího prvku.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Povolení ovládacího prvku PictureBox k asynchronnímu načtení obrázku  
  
1. <xref:System.Windows.Forms.PictureBox>Ve formuláři vytvořte instanci komponenty.  
  
2. Přiřaďte události obslužnou rutinu události <xref:System.Windows.Forms.PictureBox.LoadCompleted> .  
  
     Podívejte se na chyby, ke kterým mohlo během asynchronního stahování dojít. Toto je také místo, kde kontrolujete zrušení.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#5)]  
  
3. Do formuláře přidejte dvě tlačítka, která se nazývají `loadButton` a `cancelLoadButton` . Přidejte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí, které chcete spustit, a zrušte stahování.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#4)]  
  
4. Spusťte aplikaci.  
  
     Při stahování obrázku můžete formulář přesunout volně, minimalizovat a maximalizovat.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Spuštění operace na pozadí](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)
