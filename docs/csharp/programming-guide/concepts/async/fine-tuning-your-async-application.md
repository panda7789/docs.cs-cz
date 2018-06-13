---
title: Vyladění s modifikátorem Async aplikace (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cf4e0082fbaa2a5189646014e53f0320e16f40de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322754"
---
# <a name="fine-tuning-your-async-application-c"></a>Vyladění s modifikátorem Async aplikace (C#)
Přesnost a flexibilitu můžete přidat do aplikací asynchronní pomocí metody a vlastnosti, která <xref:System.Threading.Tasks.Task> typu, bude k dispozici. Témata v této části ukazují příklady, které používají <xref:System.Threading.CancellationToken> a důležitých `Task` metody, jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Pomocí `WhenAny` a `WhenAll`, můžete snadno zahájení více úloh a operátoru await jejich dokončení sledováním jeden úkol.  
  
-   `WhenAny` Vrátí úlohu, která se dokončí při dokončení všech úloh v kolekci.  
  
     Příklady, které používají `WhenAny`, najdete v části [zrušení zbývajících asynchronních úloh po jedné je dokončení (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) a [spuštění více úloh s modifikátorem Async a proces je jako jejich dokončení (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll` Vrátí úlohu, která je dokončena po dokončení všech úloh v kolekci.  
  
     Další informace a příklad, který používá `WhenAll`, najdete v části [postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Tato část obsahuje následující příklady.  
  
-   [Zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Zrušení asynchronních úloh po uplynutí časového intervalu (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.  
  
 Projekty vytvoření uživatelského rozhraní, která obsahuje tlačítko, které zahájí proces a tlačítko, které se zruší, jak ukazuje následující obrázek. Tlačítka jsou pojmenované `startButton` a `cancelButton`.  
  
 ![Okno WPF s tlačítko Zrušit](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "zrušení")  
  
 Si můžete stáhnout kompletní projekty Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
