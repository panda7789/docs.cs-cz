---
title: 'Postupy: Zrušení úlohy a podřízených elementů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb520169f8e7925862d415a4dfb65af09263b0d2
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266823"
---
# <a name="how-to-cancel-a-task-and-its-children"></a>Postupy: Zrušení úlohy a podřízených elementů
Tyto příklady znázorňují, jak provádět následující úkoly:  
  
1.  Vytvořit a spustit zrušitelný úkol.  
  
2.  Předat token zrušení do uživatelského delegáta a volitelně do instance úlohy.  
  
3.  Zaznamenat a odpovědět na požadavek na zrušení v uživatelském delegátu.  
  
4.  Volitelně oznámit na volajícím vlákně, že byl úkol zrušen.  
  
 Volající vlákno nevynucuje ukončení úkolu, ale pouze signalizuje, že je požadováno zrušení. Pokud je úkol již spuštěn, musí žádost oznámit a přiměřeně na ni zareagovat uživatelský delegát. Pokud je zrušení požadováno před spuštěním úlohy, není uživatelský delegát nikdy spuštěn a objekt úlohy přejde do stavu Zrušeno.  
  
## <a name="example"></a>Příklad  
 Tento příklad znázorňuje způsob ukončení úlohy <xref:System.Threading.Tasks.Task> a příslušných podřízených položek v reakci na požadavek zrušení. Znázorňuje také situaci, že pokud je uživatelský delegát ukončen vyvoláním výjimky <xref:System.Threading.Tasks.TaskCanceledException>, může volající vlákno při čekání na dokončení úloh volitelně použít metodu <xref:System.Threading.Tasks.Task.Wait%2A> nebo metodu <xref:System.Threading.Tasks.Task.WaitAll%2A>. V tomto případě je nutné použít blok `try/catch`, který zpracuje výjimky na volajícím vlákně.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 Třída <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> je plně integrována s modelem zrušení, který je založen na typech <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> a <xref:System.Threading.CancellationToken?displayProperty=nameWithType>. Další informace najdete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md) a [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
- [Připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
