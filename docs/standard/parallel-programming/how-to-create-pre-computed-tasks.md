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
ms.openlocfilehash: 88f0782380d21858bc5dd0fc0fbf63bbf85403b8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289990"
---
# <a name="how-to-create-pre-computed-tasks"></a>Postupy: Vytváření předvypočítaných úloh
Tento dokument popisuje, jak použít <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metodu k načtení výsledků asynchronních operací stažení, které jsou uloženy v mezipaměti. <xref:System.Threading.Tasks.Task.FromResult%2A>Metoda vrátí dokončený <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje poskytnutou hodnotu jako <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost. Tato metoda je užitečná při provádění asynchronní operace, která vrací <xref:System.Threading.Tasks.Task%601> objekt a výsledek tohoto <xref:System.Threading.Tasks.Task%601> objektu je již vypočítán.  
  
## <a name="example"></a>Příklad  
 Následující příklad stahuje řetězce z webu. Definuje `DownloadStringAsync` metodu. Tato metoda stahuje řetězce z webu asynchronně. Tento příklad také používá <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objekt k ukládání výsledků předchozích operací do mezipaměti. Pokud je vstupní adresa uložena v této mezipaměti, `DownloadStringAsync` používá <xref:System.Threading.Tasks.Task.FromResult%2A> metodu k vytvoření <xref:System.Threading.Tasks.Task%601> objektu, který obsahuje obsah na dané adrese. V opačném případě `DownloadStringAsync` stáhne soubor z webu a přidá výsledek do mezipaměti.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Tento příklad vypočítá čas, který je vyžadován ke stažení více řetězců dvakrát. Druhá sada operací stahování by měla trvat kratší dobu než první sada, protože výsledky jsou uchovávány v mezipaměti. <xref:System.Threading.Tasks.Task.FromResult%2A>Metoda umožňuje `DownloadStringAsync` metodě vytvářet <xref:System.Threading.Tasks.Task%601> objekty, které obsahují tyto předem vypočítané výsledky.  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování založené na úlohách](task-based-asynchronous-programming.md)
