---
title: "Postupy: Implementace klienta asynchronního vzoru založeného na událostech"
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
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b70d4ba205d39ad8fcbc7c7f6fa1f5b34a36c98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Postupy: Implementace klienta asynchronního vzoru založeného na událostech
Následující příklad kódu ukazuje, jak používat komponenty, která dodržuje [na základě událostí přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). Formulář pro tento příklad používá `PrimeNumberCalculator` komponenty popsané v [postupy: implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Když spouštíte projekt, který používá tento příklad, uvidíte formulář "Číslo Prime kalkulačky" s mřížka a dvě tlačítka: **spustit novou úlohu** a **zrušit**. Můžete kliknout na **spustit novou úlohu** tlačítko několikrát za sebou a pro každou klikněte na asynchronní operaci se začnou výpočet lze zjistit, je prime testovací náhodně generované číslo. Formulář pravidelně zobrazí průběh a přírůstkové výsledky. Každý je přiřazena ID jedinečný úkolu. Výsledek výpočet se zobrazí v **výsledek** sloupci; Pokud číslo test není prvotní, je označeno jako **složený,** a zobrazí se jeho první dělitel.  
  
 Všechny čekající operace se dají zrušit s **zrušit** tlačítko. Můžete provedeny více výběrů.  
  
> [!NOTE]
>  Většina čísla nebudou prime. Pokud číslo prime nebyly nalezeny po několik operací dokončené, jednoduše spusťte další informace o úlohách a nakonec najdete některé prvočísel.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
