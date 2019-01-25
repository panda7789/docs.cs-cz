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
ms.openlocfilehash: 8d2825ff738ffc50ba9a438024db27aff5686a0d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661383"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Postupy: Implementace klienta asynchronního vzoru založeného na událostech
Následující příklad kódu ukazuje, jak použít komponentu, která dodržuje [založený na událostech přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). Formulář pro tento příklad používá `PrimeNumberCalculator` komponenty popsané v [jak: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Při spuštění projektu, který se používá v tomto příkladu se zobrazí "Kalkulačka Prime číslo" formulář s tabulkou a dvě tlačítka: **Spustit novou úlohu** a **zrušit**. Můžete kliknout **spustit novou úlohu** tlačítko několikrát za sebou a pro každou klikněte na asynchronní operace se začne výpočtu k určení, zda je číslo náhodně vygenerovaného testu prime. Formulář zobrazí pravidelně průběh a výsledky přírůstkové. Každá operace se přiřadí ID jedinečné úkolu. Výsledek výpočtu se zobrazí v **výsledek** sloupec; Pokud číslo testu není primární, je označena jako **složené,** a zobrazí se jeho první dělitel.  
  
 Všechny čekající operace může být zrušen pomocí **zrušit** tlačítko. Nelze realizovat více výběrů.  
  
> [!NOTE]
>  Většina čísel nebude primární. Pokud po několika dokončené operace s nebyla nalezena Prvočíslo, jednoduše spustit více úkolů a nakonec najdete některé prvočísel.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
