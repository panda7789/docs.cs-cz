---
title: 'Postupy: Naslouchání požadavkům zrušení dotazováním'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
ms.openlocfilehash: df76674e3003bbb77ef062e90b1dc3283f681d35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138027"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Postupy: Naslouchání požadavkům zrušení dotazováním
Následující příklad ukazuje jeden ze způsobů, jak může uživatelský kód dotazovat token zrušení v pravidelných intervalech, aby bylo možné zjistit, zda bylo zrušení požadováno z volajícího vlákna. V tomto příkladu se používá typ <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, ale stejný vzor se vztahuje pouze na asynchronní operace vytvořené přímo pomocí <xref:System.Threading.ThreadPool?displayProperty=nameWithType> typu nebo typu <xref:System.Threading.Thread?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Dotazování vyžaduje určitý typ smyčky nebo rekurzivního kódu, který může pravidelně číst hodnotu vlastnosti Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A>. Pokud používáte typ <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a čekáte na dokončení úlohy ve volajícím vlákně, můžete použít metodu <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> a ověřit vlastnost a vyvolat výjimku. Pomocí této metody zajistíte, aby byla v reakci na požadavek vyvolána správná výjimka. Pokud používáte <xref:System.Threading.Tasks.Task>, pak volání této metody je lepší než ruční vyvolání <xref:System.OperationCanceledException>. Pokud nemusíte vyvolat výjimku, můžete pouze zaškrtnout vlastnost a vrátit se z metody, pokud je vlastnost `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> je mimořádně rychlé a nezavádí v cyklech významnou režii.  
  
 Pokud voláte <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, stačí pouze explicitně zaškrtnout vlastnost <xref:System.Threading.CancellationToken.IsCancellationRequested%2A>, pokud máte jinou práci v reakci na zrušení Kromě vyvolání výjimky. V tomto příkladu vidíte, že kód ve skutečnosti přistupuje k vlastnosti dvakrát: jednou v explicitním přístupu a znovu v metodě <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>. Vzhledem k tomu, že operace čtení vlastnosti <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> zahrnuje pouze jednu nestálou instrukci čtení pro přístup, je přístup typu Double nevýznamný z hlediska výkonu. Je stále vhodné volat metodu místo ručního vyvolání <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Viz také:

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
