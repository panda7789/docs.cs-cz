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
ms.openlocfilehash: 6f70ce75b1d6a3d4d7e8a38d739005a261b07241
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279553"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Postupy: Naslouchání požadavkům zrušení dotazováním
Následující příklad ukazuje jeden ze způsobů, jak může uživatelský kód dotazovat token zrušení v pravidelných intervalech, aby bylo možné zjistit, zda bylo zrušení požadováno z volajícího vlákna. Tento příklad používá <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typ, ale stejný vzor se vztahuje pouze na asynchronní operace vytvořené přímo pomocí <xref:System.Threading.ThreadPool?displayProperty=nameWithType> typu nebo <xref:System.Threading.Thread?displayProperty=nameWithType> typu.  
  
## <a name="example"></a>Příklad  
 Dotazování vyžaduje určitý typ smyčky nebo rekurzivního kódu, který může pravidelně číst hodnotu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnosti Boolean. Pokud používáte <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typ a čekáte na dokončení úlohy ve volajícím vlákně, můžete použít <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metodu ke kontrole vlastnosti a vyvolání výjimky. Pomocí této metody zajistíte, aby byla v reakci na požadavek vyvolána správná výjimka. Pokud používáte <xref:System.Threading.Tasks.Task> , pak volání této metody je lepší než ruční vyvolání <xref:System.OperationCanceledException> . Pokud nemusíte vyvolat výjimku, můžete pouze kontrolovat vlastnost a vracet se z metody, pokud je vlastnost `true` .  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> je mimořádně rychlé a nezavádí v cyklech významnou režii.  
  
 Pokud zavoláte <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> , stačí explicitně zaškrtnout <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost pouze v případě, že v reakci na zrušení Kromě vyvolání výjimky dojde k jiné práci. V tomto příkladu vidíte, že kód skutečně přistupuje k vlastnosti dvakrát: jednou v explicitním přístupu a znovu v <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metodě. Vzhledem k tomu, že operace čtení <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnosti zahrnuje pouze jednu nestálou instrukci čtení pro přístup, není přístup typu Double důležitý z hlediska výkonu. Je stále vhodné volat metodu místo ručního vyvolání <xref:System.OperationCanceledException> .  
  
## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](cancellation-in-managed-threads.md)
