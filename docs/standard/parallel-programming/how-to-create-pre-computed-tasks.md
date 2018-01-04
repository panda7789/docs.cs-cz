---
title: "Postupy: Vytváření předvypočítaných úloh"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 262aa626e9e426da94de0d2ad5f2ef04a5bbc5f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-pre-computed-tasks"></a>Postupy: Vytváření předvypočítaných úloh
Tento dokument popisuje postup použití <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metoda načíst výsledky stahování asynchronní operace, které jsou uložené v mezipaměti. <xref:System.Threading.Tasks.Task.FromResult%2A> Metoda vrátí dokončení <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje zadaná hodnota jako jeho <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost. Tato metoda je užitečná při provádění asynchronní operace, která vrátí <xref:System.Threading.Tasks.Task%601> objektu a výsledek této <xref:System.Threading.Tasks.Task%601> objektu již je počítaný.  
  
## <a name="example"></a>Příklad  
 Následující příklad stáhne řetězce z webu. Definuje, `DownloadStringAsync` metoda. Tato metoda asynchronně stáhne řetězce z webu. Tento příklad také používá <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objekt pro ukládání do mezipaměti výsledky předchozí operace. Pokud je v této mezipaměti adresu vstupní `DownloadStringAsync` používá <xref:System.Threading.Tasks.Task.FromResult%2A> metoda k vytvoření <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje obsah na této adrese. V opačném `DownloadStringAsync` stáhne soubor z webu a přidává výsledek do mezipaměti.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Tento příklad vypočítá čas, které je nutné stáhnout vícenásobných řetězců dvakrát. Druhá sada stažení operace by měla trvat kratší dobu, než první sady, protože výsledky jsou uložené v mezipaměti. <xref:System.Threading.Tasks.Task.FromResult%2A> Metoda umožňuje `DownloadStringAsync` metodu pro vytvoření <xref:System.Threading.Tasks.Task%601> objekty, které mají tyto předvypočítaných výsledky.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `CachedDownloads.cs` (`CachedDownloads.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
