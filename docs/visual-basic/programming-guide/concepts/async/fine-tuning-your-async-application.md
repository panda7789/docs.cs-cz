---
title: Doladění aplikace s modifikátorem Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 88b26aea0740bb4a5c5e9d87790746a708bf45a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663594"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Doladění aplikace s modifikátorem Async (Visual Basic)
Přidáte přesnost a flexibilitu asynchronním aplikací pomocí metody a vlastnosti, která <xref:System.Threading.Tasks.Task> typu bude k dispozici. Témata v této části obsahují příklady používající <xref:System.Threading.CancellationToken> a důležité `Task` metody jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 S použitím `WhenAny` a `WhenAll`, můžete snadněji spustit více úkolů a Vyčkávat na jejich dokončení při sledování jednoho úkolu.  
  
- `WhenAny` Vrátí úlohu, která se dokončí při dokončení libovolné úlohy v kolekci.  
  
     Příklady, které používají `WhenAny`, naleznete v tématu [zrušení zbývajících asynchronních úloh po jeden je úplná (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)a [spuštění více úloh s modifikátorem Async a proces je jako jejich kompletní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` Vrátí úlohu, která se dokončí po dokončení všech úloh v kolekci.  
  
     Další informace a příklad použití `WhenAll`, naleznete v tématu [jak: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Tato část obsahuje následující příklady.  
  
- [Zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zrušení asynchronních úloh po určitou dobu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [Zrušení zbývajících asynchronních úloh po jedné z nich kompletní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
 Projekty vytvářejí uživatelské rozhraní, která obsahuje tlačítko, které zahájí proces a tlačítko, které ho ruší, jak ukazuje následující obrázek. Tlačítka jsou pojmenována `startButton` a `cancelButton`.  
  
 ![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "dialogové okno s tlačítkem spouštění a zastavování")  
  
 Můžete si stáhnout kompletní projektů Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
