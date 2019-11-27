---
title: Vyladění aplikace s modifikátorem Async
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 51786993cf16cd12b39cde3d47832191b3fdca8d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345835"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Vyladění aplikace v asynchronním prostředí (Visual Basic)
Můžete přidat přesnost a flexibilitu pro asynchronní aplikace pomocí metod a vlastností, které <xref:System.Threading.Tasks.Task> typ zpřístupňuje. Témata v této části ukazují příklady, které používají <xref:System.Threading.CancellationToken> a důležité `Task` metody, jako jsou <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Pomocí `WhenAny` a `WhenAll`můžete snadněji spustit více úkolů a očekávat jejich dokončení monitorováním jedné úlohy.  
  
- `WhenAny` vrátí úkol, který se dokončí, když se dokončí kterákoli úloha v kolekci.  
  
     Příklady použití `WhenAny`naleznete v tématu [zrušení zbývajících asynchronních úloh po dokončení jedné z nich (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)a [spuštění několika asynchronních úloh a jejich zpracování po dokončení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` vrátí úlohu, která se dokončí po dokončení všech úloh v kolekci.  
  
     Další informace a příklad, který používá `WhenAll`, naleznete v tématu [How to: Extending the Async průvodce pomocí Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Tato část obsahuje následující příklady.  
  
- [Zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zrušení asynchronních úloh po určitém časovém intervalu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [Zrušení zbývajících asynchronních úloh po dokončení jednoho z nich (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Spuštění několika asynchronních úloh a jejich zpracování po dokončení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.  
  
 Projekty vytvoří uživatelské rozhraní, které obsahuje tlačítko, které spustí proces, a tlačítko, které ho zruší, jak ukazuje následující obrázek. Tlačítka jsou pojmenována `startButton` a `cancelButton`.  
  
 ![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialogové okno s tlačítkem Spustit a zastavit")  
  
 Z Async Sample si můžete stáhnout kompletní projekty Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
