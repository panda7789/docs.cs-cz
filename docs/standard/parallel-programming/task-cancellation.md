---
title: Zrušení úlohy
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7fefbfd33788ea84a8daf9dfbab452802ffd50d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650738"
---
# <a name="task-cancellation"></a>Zrušení úlohy
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> třídy podporují zrušení prostřednictvím použití tokenů zrušení v rozhraní .NET Framework. Další informace najdete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md). Ve třídách úloh zahrnuje zrušení spolupráci mezi uživatelským delegátem, který představuje zrušitelnou operaci, a kódem, který požaduje zrušení.  Úspěšné zrušení zahrnuje, aby žádající kód volal <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda a uživatelský delegát operaci včas. Operace může být ukončena pomocí jedné z těchto možností:  
  
- Jednoduše vrácením z delegáta. V mnoha scénářích je toto dostatečné; Nicméně instance úlohy, která je zrušena tímto způsobem, přechází do <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> , nikoli do stavu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stavu.  
  
- Po vyvolání výjimky <xref:System.OperationCanceledException> a předáním tokenu, na který bylo zrušení požadováno. Preferovaný způsob, jak to provést, je použít <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody. Úloha, která je zrušena tímto způsobem, přechází do stavu Zrušeno, který může volající kód použít k ověření, zda úloha odpověděla na jeho žádost o zrušení.  
  
 Následující příklad zobrazuje základní vzor pro zrušení úlohy, který vyvolává výjimku. Token je předán uživatelskému delegátu a samotné instanci úlohy.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Podrobnější příklad naleznete v tématu [jak: Zrušení úlohy a jejích potomků](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Když instance úlohy spatří <xref:System.OperationCanceledException> vyvolanou v uživatelském kódu, porovná token této výjimky se svým přiřazeným tokenem (ten, který byl předán rozhraní API, jež vytvořilo úlohu). Pokud se shodují a tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost vrátí hodnotu PRAVDA, úloha to interpretuje jako potvrzení zrušení a přejde do stavu zrušeno. Pokud použijete <xref:System.Threading.Tasks.Task.Wait%2A> nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> metodu pro čekání na úlohu, potom úloha pouze nastaví svůj stav <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Pokud čekáte na úlohu přecházející do stavu zrušeno <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> výjimky (zabalené v <xref:System.AggregateException> výjimka) je vyvolána výjimka. Všimněte si, že tato výjimka označuje úspěšné zrušení namísto poruchové situace. Proto úkolu <xref:System.Threading.Tasks.Task.Exception%2A> vrátí vlastnost `null`.  
  
 Pokud token, který <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost vrací hodnotu false nebo pokud token výjimky neodpovídá úkolu v tokenu, <xref:System.OperationCanceledException> zacházeno jako s normální výjimkou, způsobí, že úloha přejde do stavu chyba. Přítomnost dalších výjimek rovněž způsobí, že úloha přejde do stavu Chyba. Stav dokončené úlohy můžete získat <xref:System.Threading.Tasks.Task.Status%2A> vlastnost.  
  
 Je možné, že úloha bude pokračovat ve zpracování některých položek poté, co bylo požádáno o zrušení.  
  
## <a name="see-also"></a>Viz také:

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [Postupy: Zrušení úlohy a jejích potomků](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
