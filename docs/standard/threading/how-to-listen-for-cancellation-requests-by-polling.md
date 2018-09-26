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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1794b47db87f636cc2ccdf2eecb9e7ca334ae659
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192872"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Postupy: Naslouchání požadavkům zrušení dotazováním
Následující příklad ukazuje jeden ze způsobů, který uživatelský kód může dotazovat token zrušení v pravidelných intervalech, pokud chcete zobrazit, zda bylo vyžádáno zrušení z volajícího vlákna. V tomto příkladu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu, ale stejný vzor se vztahuje na asynchronní operace, které jsou vytvořené přímo nástrojem <xref:System.Threading.ThreadPool?displayProperty=nameWithType> typu nebo <xref:System.Threading.Thread?displayProperty=nameWithType> typu.  
  
## <a name="example"></a>Příklad  
 Dotazování vyžaduje určitý druh smyčky nebo rekurzivní kód, který může číst pravidelně hodnotu datový typ Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost. Pokud používáte <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typ a čekají na dokončení na volajícím vlákně úlohy, můžete použít <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metodu pro kontrolu vlastnosti a vyvolá výjimku. Tímto způsobem zajistíte, že je vyvolána správná výjimka v reakci na žádost. Pokud používáte <xref:System.Threading.Tasks.Task>, je lepší než vyvolávání ručně voláním této metody <xref:System.OperationCanceledException>. Pokud nemáte k vyvolání výjimky, pak stačí Zkontrolujte vlastnost a vrácení z metody, pokud je vlastnost `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> je velmi rychlý a nezavádí významné režijní náklady v smyčky.  
  
 Při volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, budete muset explicitně zkontrolovala <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnosti, pokud máte jinou práci v reakci na zrušení kromě vyvolat výjimku. V tomto příkladu vidíte, že kód ve skutečnosti přistupuje k vlastnosti dvakrát: jednou na explicitní přístupu a znovu <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody. Ale protože operace čtení <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost je pouze jeden těkavých instrukce na přístup pro čtení, double přístup není významné z hlediska výkonu. Je stále vhodnější pro volání metody spíše než ručně vyvolat <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Viz také:

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
