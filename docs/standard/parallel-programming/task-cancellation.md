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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139969"
---
# <a name="task-cancellation"></a>Zrušení úlohy
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Třídy <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> a podporují zrušení pomocí tokenů zrušení v rozhraní .NET Framework. Další informace naleznete [v tématu Zrušení v tématu Spravovaná vlákna](../../../docs/standard/threading/cancellation-in-managed-threads.md). Ve třídách úloh zahrnuje zrušení spolupráci mezi uživatelským delegátem, který představuje zrušitelnou operaci, a kódem, který požaduje zrušení.  Úspěšné zrušení zahrnuje žádající kód <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> volání metody a delegát uživatele ukončení operace včas. Operace může být ukončena pomocí jedné z těchto možností:  
  
- Jednoduše vrácením z delegáta. V mnoha scénářích je to dostačující; instance úkolu, která je tímto způsobem zrušena, <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> však přechází <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> do stavu, nikoli do stavu.  
  
- Vyvoláním <xref:System.OperationCanceledException> a předánítoken, na kterém bylo požadováno zrušení. Upřednostňovaným způsobem, jak to <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> provést, je použití metody. Úloha, která je zrušena tímto způsobem, přechází do stavu Zrušeno, který může volající kód použít k ověření, zda úloha odpověděla na jeho žádost o zrušení.  
  
 Následující příklad zobrazuje základní vzor pro zrušení úlohy, který vyvolává výjimku. Token je předán uživatelskému delegátu a samotné instanci úlohy.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Podrobnější příklad najdete v [tématu Jak zrušit úkol a jeho podřízené úkoly](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Když instance úlohy <xref:System.OperationCanceledException> pozoruje vyvolána uživatelským kódem, porovná token výjimky s přidruženým tokenem (ten, který byl předán rozhraní API, které vytvořilo úlohu). Pokud jsou stejné a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost tokenu vrátí hodnotu true, úkol interpretuje to jako potvrzení zrušení a přechody do stavu Zrušeno. Pokud nepoužijete <xref:System.Threading.Tasks.Task.Wait%2A> metodu nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> k čekání na úkol, úkol <xref:System.Threading.Tasks.TaskStatus.Canceled>pouze nastaví svůj stav na .  
  
 Pokud čekáte na Task, který přechází do stavu <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> Zrušeno, je <xref:System.AggregateException> vyvolána výjimka (zabalená ve výjimce). Všimněte si, že tato výjimka označuje úspěšné zrušení namísto poruchové situace. Proto vrátí <xref:System.Threading.Tasks.Task.Exception%2A> `null`vlastnost úkolu .  
  
 Pokud <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost tokenu vrátí false nebo pokud token výjimky neodpovídá tokenu <xref:System.OperationCanceledException> Úlohy, je považován za normální výjimku, což způsobí, že Task přejde do chybovaného stavu. Přítomnost dalších výjimek rovněž způsobí, že úloha přejde do stavu Chyba. Můžete získat stav dokončeného úkolu <xref:System.Threading.Tasks.Task.Status%2A> ve vlastnosti.  
  
 Je možné, že úloha bude pokračovat ve zpracování některých položek poté, co bylo požádáno o zrušení.  
  
## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [Postupy: Zrušení úlohy a podřízených elementů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
