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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa95eccfa39073bb8ccb3cb9c49e099ac1f90ab1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638941"
---
# <a name="how-to-create-pre-computed-tasks"></a>Postupy: Vytváření předvypočítaných úloh
Tento dokument popisuje způsob použití <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody k načtení výsledků asynchronní operací stažení, které jsou uloženy v mezipaměti. <xref:System.Threading.Tasks.Task.FromResult%2A> Metoda vrátí dokončení <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje zadaná hodnota jako jeho <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost. Tato metoda je užitečná při provádění asynchronní operace, která vrátí <xref:System.Threading.Tasks.Task%601> objektu a výsledek tohoto objektu <xref:System.Threading.Tasks.Task%601> již je vypočítán.  
  
## <a name="example"></a>Příklad  
 Následující příklad stáhne řetězce z webu. Definuje `DownloadStringAsync` metody. Tato metoda asynchronně stáhne řetězce z webu. Tento příklad také používá <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objektu pro ukládání do mezipaměti výsledky předchozí operace. Pokud je vstupní adresu je uložena v mezipaměti, `DownloadStringAsync` používá <xref:System.Threading.Tasks.Task.FromResult%2A> metodu za účelem vytvoření <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje obsah na této adrese. V opačném případě `DownloadStringAsync` stáhne soubor z webu a přidává výsledek do mezipaměti.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Tento příklad zjistí čas, který je potřeba ke stahování vícenásobných řetězců dvakrát. Druhou sadu operací stažení by měla trvat kratší dobu než první sady, protože výsledky jsou uloženy v mezipaměti. <xref:System.Threading.Tasks.Task.FromResult%2A> Metoda umožňuje `DownloadStringAsync` metodu pro vytvoření <xref:System.Threading.Tasks.Task%601> objekty, které obsahují tyto předem vypočítané výsledky.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `CachedDownloads.cs` (`CachedDownloads.vb` v jazyce Visual Basic), a pak spuštěním následujícího příkazu na příkazovém řádku pro vývojáře pro Visual Studio okno.  
  
 Visual C#  
  
 **csc.exe CachedDownloads.cs**  
  
 Visual Basic  
  
 **vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
