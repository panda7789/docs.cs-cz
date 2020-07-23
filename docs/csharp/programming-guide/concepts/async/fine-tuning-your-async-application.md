---
title: Vyladění aplikace s modifikátorem Async (C#)
description: Tyto příklady jazyka C# používají CancellationToken a důležité metody úloh, jako je Task. WhenAll a Task. WhenAny pro vyladění asynchronních aplikací.
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 46457f889a78932e306d2bd21dca666625d744eb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925316"
---
# <a name="fine-tuning-your-async-application-c"></a>Vyladění aplikace s modifikátorem Async (C#)
Můžete přidat přesnost a flexibilitu pro asynchronní aplikace pomocí metod a vlastností, které <xref:System.Threading.Tasks.Task> typ zpřístupňuje. Témata v této části obsahují příklady, které používají <xref:System.Threading.CancellationToken> a důležité `Task` metody, jako jsou <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> .  
  
 Pomocí `WhenAny` a `WhenAll` můžete snadněji spustit více úkolů a očekávat jejich dokončení monitorováním jedné úlohy.  
  
- `WhenAny`Vrátí úkol, který se dokončí po dokončení libovolné úlohy v kolekci.  
  
     Příklady použití `WhenAny` naleznete v tématu [zrušení zbývajících asynchronních úloh po dokončení jedné z nich (c#)](./cancel-remaining-async-tasks-after-one-is-complete.md) a [spuštění několika asynchronních úloh a jejich zpracování po dokončení (c#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`Vrátí úkol, který se dokončí po dokončení všech úloh v kolekci.  
  
     Další informace a příklad, který používá `WhenAll` , najdete v tématu [postup rozšiřování asynchronního návodu pomocí Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Tato část obsahuje následující příklady.  
  
- [Zrušení asynchronní úlohy nebo seznamu úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zrušení asynchronních úloh po určitém časovém intervalu (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Zrušení zbývajících asynchronních úloh po dokončení jedné z nich (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Spuštění více asynchronních úloh a jejich zpracování po dokončení (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.  
  
 Projekty vytvoří uživatelské rozhraní, které obsahuje tlačítko, které spustí proces, a tlačítko, které ho zruší, jak ukazuje následující obrázek. Tlačítka jsou pojmenována `startButton` a `cancelButton` .  
  
 ![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialogové okno s tlačítkem Spustit a zastavit")  
  
 Z Async Sample si můžete stáhnout kompletní projekty Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](./index.md)
