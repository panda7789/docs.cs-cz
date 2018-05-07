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
ms.openlocfilehash: f6e257ced27812f8383edf9eb9688e9f48cfde02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Postupy: Naslouchání požadavkům zrušení dotazováním
Následující příklad ukazuje jeden ze způsobů, který uživatelského kódu můžete dotazovat token zrušení v pravidelných intervalech zobrazíte zrušení požádal z volající vlákno. Tento příklad používá <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typ, ale stejného vzoru platí pro asynchronní operace, které jsou vytvořené přímo pomocí <xref:System.Threading.ThreadPool?displayProperty=nameWithType> typu nebo <xref:System.Threading.Thread?displayProperty=nameWithType> typu.  
  
## <a name="example"></a>Příklad  
 Dotazování vyžaduje nějaký druh smyčky nebo rekurzivní kód, který může číst pravidelně hodnota logická hodnota <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost. Pokud používáte <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu a čekají na dokončení na volající vlákno úlohy, můžete použít <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metodu pro kontrolu vlastnosti a vyvolat výjimku. Pomocí této metody je zajistit, že je správný výjimka vydána v reakci na žádost. Pokud používáte <xref:System.Threading.Tasks.Task>, pak voláním této metody je lepší, než ručně vyvolání <xref:System.OperationCanceledException>. Pokud nemáte má být vyvolána výjimka, pak právě Zkontrolujte vlastnost a vrátit z metody, pokud je vlastnost `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Volání metody <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> je velmi rychlý a nezavádí významné režijní náklady v smyčky.  
  
 Při volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, budete muset explicitně zkontrolovala <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost, pokud máte jinou práci udělat v reakci na zrušení kromě způsobující výjimku. V tomto příkladu vidíte, že kód ve skutečnosti přistupuje k vlastnosti dvakrát: jednou v výslovný přístup a znovu v <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metoda. Ale protože v rámci čtení <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost zahrnuje pouze jeden volatile instrukce za přístup pro čtení, double přístup není významné z hlediska výkonu. Je stále vhodnější volat metodu než ručně throw <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Viz také  
 [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
