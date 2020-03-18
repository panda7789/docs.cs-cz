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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138027"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Postupy: Naslouchání požadavkům zrušení dotazováním
Následující příklad ukazuje jeden způsob, jak může kód uživatele v pravidelných intervalech dotazování tokenu zrušení, aby zjistil, zda bylo požadováno zrušení z volajícího vlákna. Tento příklad <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> používá typ, ale stejný vzor platí pro asynchronní <xref:System.Threading.ThreadPool?displayProperty=nameWithType> operace <xref:System.Threading.Thread?displayProperty=nameWithType> vytvořené přímo typem nebo typem.  
  
## <a name="example"></a>Příklad  
 Dotazování vyžaduje nějaký druh smyčky nebo rekurzivní kód, který může <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> pravidelně číst hodnotu boolean vlastnost. Pokud používáte <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typ a čekáte na dokončení úlohy v volajícím <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> vlákně, můžete použít metodu ke kontrole vlastnosti a vyvolání výjimky. Pomocí této metody zajistíte, že je vyvolána správná výjimka v reakci na požadavek. Pokud používáte <xref:System.Threading.Tasks.Task>, pak volání této metody je lepší <xref:System.OperationCanceledException>než ruční vyvolání . Pokud není třeba vyvolat výjimku, pak stačí zkontrolovat vlastnost a vrátit se `true`z metody, pokud je vlastnost .  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> je velmi rychlé a nezavádí významné režie ve smyčkách.  
  
 Pokud voláte <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, stačí explicitně <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> zkontrolovat vlastnost, pokud máte jinou práci v reakci na zrušení kromě vyvolání výjimky. V tomto příkladu uvidíte, že kód skutečně přistupuje k vlastnosti dvakrát: jednou v explicitní přístup a znovu v metodě. <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> Ale protože akt čtení <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnosti zahrnuje pouze jeden nestálý instrukce pro čtení na přístup, dvojitý přístup není významné z hlediska výkonu. Je stále vhodnější volat metodu, spíše než <xref:System.OperationCanceledException>ručně hodit .  
  
## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
