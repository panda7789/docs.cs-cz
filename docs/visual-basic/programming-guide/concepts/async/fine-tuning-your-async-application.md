---
title: Vyladění aplikace s modifikátorem Async
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: e33f86177a3680d41ec04842dbc120713a48f61c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396646"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Vyladění aplikace v asynchronním prostředí (Visual Basic)
Můžete přidat přesnost a flexibilitu pro asynchronní aplikace pomocí metod a vlastností, které <xref:System.Threading.Tasks.Task> typ zpřístupňuje. Témata v této části obsahují příklady, které používají <xref:System.Threading.CancellationToken> a důležité `Task` metody, jako jsou <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> .  
  
 Pomocí `WhenAny` a `WhenAll` můžete snadněji spustit více úkolů a očekávat jejich dokončení monitorováním jedné úlohy.  
  
- `WhenAny`Vrátí úkol, který se dokončí po dokončení libovolné úlohy v kolekci.  
  
     Příklady, které používají `WhenAny` , najdete v článku [zrušení zbývajících asynchronních úloh po dokončení jedné operace (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)a [spuštění několika asynchronních úloh a jejich zpracování po dokončení (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`Vrátí úkol, který se dokončí po dokončení všech úloh v kolekci.  
  
     Další informace a příklad, který používá `WhenAll` , naleznete v tématu [How to: Extending the Async průvodce pomocí Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Tato část obsahuje následující příklady.  
  
- [Zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zrušení asynchronních úloh po určitém časovém intervalu (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)  
  
- [Zrušení zbývajících asynchronních úloh po dokončení jednoho z nich (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Spuštění několika asynchronních úloh a jejich zpracování po dokončení (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.  
  
 Projekty vytvoří uživatelské rozhraní, které obsahuje tlačítko, které spustí proces, a tlačítko, které ho zruší, jak ukazuje následující obrázek. Tlačítka jsou pojmenována `startButton` a `cancelButton` .  
  
 ![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialogové okno s tlačítkem Spustit a zastavit")  
  
 Z Async Sample si můžete stáhnout kompletní projekty Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](index.md)
