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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123127"
---
# <a name="how-to-create-pre-computed-tasks"></a>Postupy: Vytváření předvypočítaných úloh
Tento dokument popisuje, jak <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> použít metodu k načtení výsledků asynchronní operace stahování, které jsou uloženy v mezipaměti. Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> vrátí hotový <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje zadali hodnotu jako jeho <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost. Tato metoda je užitečná, když provedete asynchronní operaci, která vrátí <xref:System.Threading.Tasks.Task%601> objekt a výsledek tohoto <xref:System.Threading.Tasks.Task%601> objektu je již vypočítán.  
  
## <a name="example"></a>Příklad  
 Následující příklad stáhne řetězce z webu. Definuje metodu. `DownloadStringAsync` Tato metoda stahuje řetězce z webu asynchronně. Tento příklad také <xref:System.Collections.Concurrent.ConcurrentDictionary%602> používá objekt do mezipaměti výsledky předchozích operací. Pokud je vstupní adresa uložena `DownloadStringAsync` v <xref:System.Threading.Tasks.Task.FromResult%2A> této mezipaměti, používá metodu k vytvoření objektu, <xref:System.Threading.Tasks.Task%601> který obsahuje obsah na této adrese. V `DownloadStringAsync` opačném případě stáhne soubor z webu a přidá výsledek do mezipaměti.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Tento příklad vypočítá čas, který je nutný ke stažení více řetězců dvakrát. Druhá sada operací stahování by měla trvat kratší dobu než první sada, protože výsledky jsou uloženy v mezipaměti. Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> umožňuje `DownloadStringAsync` metodu <xref:System.Threading.Tasks.Task%601> vytvořit objekty, které drží tyto předem vypočítané výsledky.  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
