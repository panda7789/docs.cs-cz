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
ms.openlocfilehash: 17cabde95644dbc1584dd85b99e26ff7c5cb686d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139969"
---
# <a name="task-cancellation"></a>Zrušení úlohy
Třídy <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> podporují zrušení pomocí tokenů zrušení v .NET Framework. Další informace naleznete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md). Ve třídách úloh zahrnuje zrušení spolupráci mezi uživatelským delegátem, který představuje zrušitelnou operaci, a kódem, který požaduje zrušení.  Úspěšné zrušení zahrnuje požadováný kód volající metodu <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> a uživatelský delegát ukončí operaci včas. Operace může být ukončena pomocí jedné z těchto možností:  
  
- Jednoduše vrácením z delegáta. V mnoha scénářích to stačí; instance úlohy, která je tímto způsobem zrušena, však přechází do stavu <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>, nikoli do stavu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType>.  
  
- Vyvoláním <xref:System.OperationCanceledException> a předáním tokenu, na kterém bylo zrušení požadováno. Upřednostňovaným způsobem, jak to provést, je použít metodu <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>. Úloha, která je zrušena tímto způsobem, přechází do stavu Zrušeno, který může volající kód použít k ověření, zda úloha odpověděla na jeho žádost o zrušení.  
  
 Následující příklad zobrazuje základní vzor pro zrušení úlohy, který vyvolává výjimku. Token je předán uživatelskému delegátu a samotné instanci úlohy.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Úplnější příklad naleznete v tématu [How to: Cancel a a jejích podřízených](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Když instance úlohy sleduje <xref:System.OperationCanceledException> vyvolanou uživatelským kódem, porovná token výjimky s jeho přidruženým tokenem (ten, který byl předán rozhraní API, které vytvořilo úlohu). Pokud jsou stejné a vlastnost <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> tokenu vrátí hodnotu true, úloha je interpretuje jako potvrzení zrušení a přechodů do zrušeného stavu. Pokud nepoužijete metodu <xref:System.Threading.Tasks.Task.Wait%2A> nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> k čekání na úlohu, pak tato úloha nastaví stav na <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Pokud čekáte na úlohu, která přechází do stavu Canceled, je vyvolána výjimka <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> (zabalené v <xref:System.AggregateException> výjimce). Všimněte si, že tato výjimka označuje úspěšné zrušení namísto poruchové situace. Proto vlastnost <xref:System.Threading.Tasks.Task.Exception%2A> úlohy vrátí `null`.  
  
 Vrátí-li vlastnost <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> tokenu hodnotu false nebo pokud token výjimky neodpovídá tokenu úkolu, <xref:System.OperationCanceledException> je považován za normální výjimku, což způsobí, že se úkol převede do stavu Faulted. Přítomnost dalších výjimek rovněž způsobí, že úloha přejde do stavu Chyba. Stav dokončené úlohy můžete získat ve vlastnosti <xref:System.Threading.Tasks.Task.Status%2A>.  
  
 Je možné, že úloha bude pokračovat ve zpracování některých položek poté, co bylo požádáno o zrušení.  
  
## <a name="see-also"></a>Viz také:

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [Postupy: Zrušení úlohy a podřízených elementů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
