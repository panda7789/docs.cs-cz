---
title: 'Postupy: Vytváření předvypočítaných úloh'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: f5d2a70685fe0401d0219b99ada6936ac04691f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123127"
---
# <a name="how-to-create-pre-computed-tasks"></a>Postupy: Vytváření předvypočítaných úloh
Tento dokument popisuje, jak použít metodu <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> k načtení výsledků asynchronních operací stažení, které jsou uloženy v mezipaměti. Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> vrátí dokončený objekt <xref:System.Threading.Tasks.Task%601>, který obsahuje poskytnutou hodnotu jako vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A>. Tato metoda je užitečná při provádění asynchronní operace, která vrací objekt <xref:System.Threading.Tasks.Task%601> a výsledek tohoto objektu <xref:System.Threading.Tasks.Task%601> již je vypočítán.  
  
## <a name="example"></a>Příklad  
 Následující příklad stahuje řetězce z webu. Definuje metodu `DownloadStringAsync`. Tato metoda stahuje řetězce z webu asynchronně. Tento příklad také používá objekt <xref:System.Collections.Concurrent.ConcurrentDictionary%602> k ukládání výsledků předchozích operací do mezipaměti. Pokud je vstupní adresa uložena v této mezipaměti, `DownloadStringAsync` používá metodu <xref:System.Threading.Tasks.Task.FromResult%2A> k vytvoření <xref:System.Threading.Tasks.Task%601> objektu, který obsahuje obsah na dané adrese. V opačném případě `DownloadStringAsync` stáhne soubor z webu a přidá výsledek do mezipaměti.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Tento příklad vypočítá čas, který je vyžadován ke stažení více řetězců dvakrát. Druhá sada operací stahování by měla trvat kratší dobu než první sada, protože výsledky jsou uchovávány v mezipaměti. Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> umožňuje, aby metoda `DownloadStringAsync` vytvořila objekty <xref:System.Threading.Tasks.Task%601>, které obsahují tyto předem vypočítané výsledky.  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
