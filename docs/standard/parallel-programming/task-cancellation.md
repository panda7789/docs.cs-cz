---
title: "Zrušení úlohy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 106c89ca9fcfb8bbab23b982cdc524ff78d21d15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="task-cancellation"></a>Zrušení úlohy
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> třídy podporují zrušení prostřednictvím použití tokenů zrušení v rozhraní .NET Framework. Další informace najdete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md). Ve třídách úloh zahrnuje zrušení spolupráci mezi uživatelským delegátem, který představuje zrušitelnou operaci, a kódem, který požaduje zrušení.  Úspěšné zrušení zahrnuje vyžádání volání kódu <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda a uživatelského delegáta operaci včas. Operace může být ukončena pomocí jedné z těchto možností:  
  
-   Jednoduše vrácením z delegáta. V mnoha případech je toto dostatečné; ale instance úlohy, která je zrušena tímto způsobem přechází do <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> stavu, aby <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stavu.  
  
-   Po vyvolání výjimky <xref:System.OperationCanceledException> a předání tokenu, na kterém bylo požadováno zrušení. Preferovaný způsob, jak to udělat, je použití <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metoda. Úloha, která je zrušena tímto způsobem, přechází do stavu Zrušeno, který může volající kód použít k ověření, zda úloha odpověděla na jeho žádost o zrušení.  
  
 Následující příklad zobrazuje základní vzor pro zrušení úlohy, který vyvolává výjimku. Token je předán uživatelskému delegátu a samotné instanci úlohy.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Více kompletní příklad najdete v tématu [postupy: zrušení úlohy a její podřízené položky](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Pokud instance úlohy dodržuje <xref:System.OperationCanceledException> vyvolané uživatelského kódu, porovná token této výjimky se jeho přidružené token (ten, který byl předán rozhraní API, vytvoření úlohy). Pokud jsou stejné a je token <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost vrací hodnotu true, úloha to interpretuje jako potvrzení zrušení a přejde do stavu zrušeno. Pokud nepoužijete <xref:System.Threading.Tasks.Task.Wait%2A> nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> metodu pro čekání na úlohu, pak úlohu právě nastaví její stav na <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Pokud čekáte na úlohu, která přechází do stavu zrušeno, <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> výjimky (uzavřen do <xref:System.AggregateException> výjimka) je vyvolána výjimka. Všimněte si, že tato výjimka označuje úspěšné zrušení namísto poruchové situace. Proto úkolu <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost vrátí `null`.  
  
 Pokud je token <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost vrací hodnotu false nebo pokud token výjimky neodpovídá úlohy je token, <xref:System.OperationCanceledException> považuje jako normální výjimka, která způsobuje úlohy k přechodu do stavu chybný. Přítomnost dalších výjimek rovněž způsobí, že úloha přejde do stavu Chyba. Můžete získat stav dokončené úlohy <xref:System.Threading.Tasks.Task.Status%2A> vlastnost.  
  
 Je možné, že úloha bude pokračovat ve zpracování některých položek poté, co bylo požádáno o zrušení.  
  
## <a name="see-also"></a>Viz také  
 [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 [Postupy: zrušení úlohy a její podřízené položky](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
