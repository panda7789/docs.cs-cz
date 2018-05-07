---
title: 'Postupy: Zápis do textového souboru (Průvodce programováním v C#)'
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: 6d3f1bc238bd3129a25d4af29341c27d52b71ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Postupy: Zápis do textového souboru (Průvodce programováním v C#)
Tyto příklady znázorňují různé způsoby zápisu textu do souboru. První dva příklady používají statické usnadňující metody na <xref:System.IO.File?displayProperty=nameWithType> třída pro psaní každý prvek všech `IEnumerable<string>` a řetězec do textového souboru. Příklad 3 ukazuje, jak přidat text do souboru při každém řádku jednotlivě zpracovat, protože zapisovat do souboru. Příklady 1 – 3 přepsat všechny existující obsah v souboru, ale příklad 4 ukazuje, jak přidat text do existující soubor.  
  
 Tyto příklady všechny textové literály zápis do souborů. Pokud chcete k formátování textu zapisují do souboru, použijte <xref:System.String.Format%2A> metoda nebo C# [řetězec interpolace](../../../csharp/language-reference/tokens/interpolated.md) funkce.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Soubor existuje a je určen jen pro čtení.  
  
-   Název cesty je pravděpodobně příliš dlouhý.  
  
-   Disk je pravděpodobně plný.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)  
 [Ukázka: Uložit kolekci do úložiště aplikací](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
