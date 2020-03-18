---
title: Jemné doladění asynchronní aplikace (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cff50e62ff62b70e97e7ea6e03714326d774e407
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970232"
---
# <a name="fine-tuning-your-async-application-c"></a>Jemné doladění asynchronní aplikace (C#)
Můžete přidat přesnost a flexibilitu asynchronní aplikace pomocí metod <xref:System.Threading.Tasks.Task> a vlastností, které typ zpřístupňuje. Témata v této části ukazují <xref:System.Threading.CancellationToken> příklady, které používají a důležité `Task` metody, jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> jsou a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Pomocí `WhenAny` aplikace `WhenAll`a můžete snadněji spustit více úkolů a čekat na jejich dokončení sledováním jednoho úkolu.  
  
- `WhenAny`vrátí úlohu, která se dokončí po dokončení libovolné úlohy v kolekci.  
  
     Příklady, které `WhenAny`používají , naleznete v [tématu Zrušení zbývajících asynchronních úloh po dokončení jednoho (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) a [spuštění více asynchronních úloh a jejich zpracování po dokončení (C#).](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
- `WhenAll`vrátí úkol, který se dokončí po dokončení všech úkolů v kolekci.  
  
     Další informace a příklad, `WhenAll`který používá , naleznete [v tématu Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Tato část obsahuje následující příklady.  
  
- [Zrušte asynchronní úlohu nebo seznam úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zrušit asynchronní úkoly po časovém období (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Zrušit zbývající asynchronní úlohy po dokončení jedné (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Spuštění více asynchronních úloh a jejich zpracování po dokončení (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
 Projekty vytvořit uzpole, která obsahuje tlačítko, které spustí proces a tlačítko, které jej zruší, jak ukazuje následující obrázek. Tlačítka jsou `startButton` pojmenována a `cancelButton`.  
  
 ![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialogové okno s tlačítkem Start a Stop")  
  
 Můžete si stáhnout kompletní Windows Presentation Foundation (WPF) projekty z [Async Ukázka: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování s asynchronní a await (C#)](./index.md)
