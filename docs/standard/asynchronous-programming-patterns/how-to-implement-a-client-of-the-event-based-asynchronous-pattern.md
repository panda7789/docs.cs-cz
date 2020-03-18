---
title: 'Postupy: Implementace klienta asynchronního vzoru založeného na událostech'
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
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: 50aa36d2caf774638ad20323813f0de3703aab2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "69950720"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Postupy: Implementace klienta asynchronního vzoru založeného na událostech
Následující příklad kódu ukazuje, jak používat komponentu, která dodržuje [přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). Formulář pro tento příklad `PrimeNumberCalculator` používá komponentu popsanou v [návodu: Implementace komponenty, která podporuje asynchronní vzorek založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Při spuštění projektu, který používá tento příklad, se zobrazí formulář "Kalkulačka prvočísel" s mřížkou a dvěma tlačítky: **Spustit nový úkol** a **Zrušit**. Můžete klepnout na tlačítko **Spustit nový úkol** několikrát za sebou a pro každé kliknutí asynchronní operace zahájí výpočtu k určení, zda je náhodně generované číslo testu prvočíslo. Formulář bude pravidelně zobrazovat průběh a přírůstkové výsledky. Každé operaci je přiřazeno jedinečné ID úkolu. Výsledek výpočtu je zobrazen ve sloupci **Výsledek;** Pokud číslo testu není prvočíslo, je označeno jako **složené** a zobrazí se jeho první dělitel.  
  
 Všechny nevyřízené operace mohou být zrušeny pomocí tlačítka **Storno.** Lze provést více výběrů.  
  
> [!NOTE]
> Většina čísel nebude prvočíslo. Pokud jste po několika dokončených operacích nenašli prvočíslo, jednoduše spusťte další úkoly a nakonec najdete některá prvočísla.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
