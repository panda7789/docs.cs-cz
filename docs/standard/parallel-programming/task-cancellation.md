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
ms.openlocfilehash: 9f17b11699195e5b2186d008ebefce306834ea8d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285271"
---
# <a name="task-cancellation"></a>Zrušení úlohy
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Třídy a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> podporují zrušení prostřednictvím použití tokenů zrušení v .NET Framework. Další informace naleznete v tématu [zrušení ve spravovaných vláknech](../threading/cancellation-in-managed-threads.md). Ve třídách úloh zahrnuje zrušení spolupráci mezi uživatelským delegátem, který představuje zrušitelnou operaci, a kódem, který požaduje zrušení.  Úspěšné zrušení zahrnuje požadavek, který volá <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodu, a uživatelský delegát ukončí operaci včas. Operace může být ukončena pomocí jedné z těchto možností:  
  
- Jednoduše vrácením z delegáta. V mnoha scénářích to stačí; instance úlohy, která je tímto způsobem zrušena, však přejde do <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> stavu, nikoli do <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stavu.  
  
- Vyvoláním <xref:System.OperationCanceledException> a předáním tokenu, na kterém bylo zrušení požadováno. Upřednostňovaným způsobem, jak to provést, je použít <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metodu. Úloha, která je zrušena tímto způsobem, přechází do stavu Zrušeno, který může volající kód použít k ověření, zda úloha odpověděla na jeho žádost o zrušení.  
  
 Následující příklad zobrazuje základní vzor pro zrušení úlohy, který vyvolává výjimku. Token je předán uživatelskému delegátu a samotné instanci úlohy.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Úplnější příklad naleznete v tématu [How to: Cancel a a jejích podřízených](how-to-cancel-a-task-and-its-children.md).  
  
 Když instance úlohy <xref:System.OperationCanceledException> přijme výjimku vyvolanou uživatelským kódem, porovná token výjimky s jeho přidruženým tokenem (ten, který byl předán rozhraní API, které vytvořilo úlohu). Pokud jsou stejné a vlastnost tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vrátí hodnotu true, je tato úloha interpretována jako potvrzení zrušení a přechodů do zrušeného stavu. Pokud nepoužijete <xref:System.Threading.Tasks.Task.Wait%2A> <xref:System.Threading.Tasks.Task.WaitAll%2A> metodu nebo k čekání na úlohu, pak úloha nastaví stav na <xref:System.Threading.Tasks.TaskStatus.Canceled> .  
  
 Pokud čekáte na úlohu, která přechází do stavu Canceled, <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> je vyvolána výjimka (zabalená v <xref:System.AggregateException> výjimce). Všimněte si, že tato výjimka označuje úspěšné zrušení namísto poruchové situace. Proto <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost úkolu vrátí `null` .  
  
 Pokud vlastnost tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vrátí hodnotu false nebo pokud token výjimky neodpovídá tokenu úlohy, <xref:System.OperationCanceledException> je zpracována jako normální výjimka, což způsobuje přechod úlohy do chybového stavu. Přítomnost dalších výjimek rovněž způsobí, že úloha přejde do stavu Chyba. Ve vlastnosti můžete získat stav dokončené úlohy <xref:System.Threading.Tasks.Task.Status%2A> .  
  
 Je možné, že úloha bude pokračovat ve zpracování některých položek poté, co bylo požádáno o zrušení.  
  
## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](../threading/cancellation-in-managed-threads.md)
- [Postupy: Zrušení úlohy a podřízených elementů](how-to-cancel-a-task-and-its-children.md)
