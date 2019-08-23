---
title: Vyladění asynchronní aplikace (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: a7c730992a9bbb4853b6451323e1c49bd19bdf42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924436"
---
# <a name="fine-tuning-your-async-application-c"></a>Vyladění asynchronní aplikace (C#)
Můžete přidat přesnost a flexibilitu pro asynchronní aplikace pomocí metod a vlastností, které <xref:System.Threading.Tasks.Task> typ zpřístupňuje. Témata v této části obsahují příklady, které používají <xref:System.Threading.CancellationToken> a důležité `Task` metody, jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> jsou <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>a.  
  
 Pomocí `WhenAny` a`WhenAll`můžete snadněji spustit více úkolů a očekávat jejich dokončení monitorováním jedné úlohy.  
  
- `WhenAny`Vrátí úkol, který se dokončí po dokončení libovolné úlohy v kolekci.  
  
     Příklady použití `WhenAny`naleznete v tématu [zrušení zbývajících asynchronních úloh po dokončení jedné z nichC#()](./cancel-remaining-async-tasks-after-one-is-complete.md) a [spuštění několika asynchronních úloh a jejich zpracování po dokončeníC#()](./start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`Vrátí úkol, který se dokončí po dokončení všech úloh v kolekci.  
  
     Další informace a příklad, který používá `WhenAll`, naleznete v tématu [How to: Pomocí Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)rozšíříte asynchronní návod.  
  
 Tato část obsahuje následující příklady.  
  
- [Zrušení asynchronní úlohy nebo seznamu úkolůC#()](./cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zrušení asynchronních úloh po uplynutí časového intervalu (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Zrušení zbývajících asynchronních úloh po dokončení jedné zC#nich ()](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Spuštění několika asynchronních úloh a jejich zpracování po dokončení (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.  
  
 Projekty vytvoří uživatelské rozhraní, které obsahuje tlačítko, které spustí proces, a tlačítko, které ho zruší, jak ukazuje následující obrázek. Tlačítka jsou `startButton` pojmenována `cancelButton`a.  
  
 ![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialogové okno s tlačítkem Spustit a zastavit")  
  
 Kompletní projekty Windows Presentation Foundation (WPF) si můžete stáhnout z [Async Sample: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování s modifikátorem Async aC#operátoru Await ()](./index.md)
